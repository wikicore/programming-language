# Classes e Objetos em Pascal

## Pré-requisitos

Conhecimentos necessários:
* Conceitos básicos em Pascal
* Paradigma orientado a objetos

<br>

## Criando Uma Classe

Criando uma classe pessoa:

```pascal
{ interface }
type
  People = class
    private
      name: string;
      age: Integer;
    public
      procedure setName(nameParam: string);
      procedure setAge(ageParam: Integer);
      function toString(): string;
  end;

var
  p1: People;

{ implementation }
procedure People.setName(nameParam: string);
begin
  name := nameParam;
end;

procedure People.setAge(ageParam: Integer);
begin
  age := ageParam;
end;

function People.toString(): string;
begin
  toString := 'name: ' + name + ', age: ' + IntToStr(age);
end;
```

<br>

## Instanciando um Objeto

Instanciando um objeto da classe pessoa criada anteriormente:

```pascal
var
  p1, p2: People;

begin
  { instantiates an object }
  p1 := People.Create;
  p1.setName('Jonathan');
  p1.setAge(24);

  p2 := People.Create;
  p2.setName('Guilherme');
  p2.setAge(19);

  Writeln(p2.toString);
  Writeln(p1.toString);
end.
```