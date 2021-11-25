# Confiar no certificado de desenvolvimento HTTPS no Ubuntu

## Pré-requisitos
* .NET SDK
* libnss3-tools

## Instale .NET SDK

```bash
sudo snap install dotnet-sdk --classic
```

<br>

## Instale libnss3-tools

```bash
sudo apt install libnss3-tools
```

<br>

## Crie um bash script

```bash
# Setup Firefox
echo "{
    \"policies\": {
        \"Certificates\": {
            \"Install\": [
            	\"aspnetcore-localhost-https.crt\"
            ]
        }
    }
}" > policies.json

dotnet dev-certs https -ep localhost.crt --format PEM

sudo mv policies.json /usr/lib/firefox/distribution/
mkdir -p ~/.mozilla/certificates
cp localhost.crt ~/.mozilla/certificates/aspnetcore-localhost-https.crt

# Trust Edge/Chrome
certutil -d sql:$HOME/.pki/nssdb -A -t "P,," -n localhost -i ./localhost.crt
certutil -d sql:$HOME/.pki/nssdb -A -t "C,," -n localhost -i ./localhost.crt

# Trust dotnet-to-dotnet (.pem extension is important here)
sudo cp localhost.crt /usr/lib/ssl/certs/aspnetcore-https-localhost.pem

# Cleanup
rm localhost.crt
```

<br>

## Defina a permissão de execução do script

```bash
chmod +x seu-script.sh
```

<br>

## Rode o script

```bash
./seu-script.sh
```

<br>

## Verifique o certificado

```bash
dotnet dev-certs https --trust --check
```

<br>

<br>

<br>

[[Https] dotnet dev-certs --trustsuporte em Linux # 32842](https://github.com/dotnet/aspnetcore/issues/32842)