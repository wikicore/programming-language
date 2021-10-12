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

## Instanciando Um Objeto

Instanciando um objeto da classe pessoa criada anteriormente:

```pascal
var
  p1: People;

begin
  { instantiates an object }
  p1 := People.Create;
  p1.setName('Jonathan');
  p1.setAge(24);

  Writeln(p1.toString);
end.
```

<br>

## Construtores

Criando um construtor para a classe People:
```pascal
{ inside class }
    public
      constructor Create(nameParam: string; ageParam: Integer); overload;

{ implementation }
constructor People.Create(nameParam: string; ageParam: Integer);
begin
  name := nameParam;
  age := ageParam;
end;
```

<br>

## Herança

Criando uma nova classe e herdando da classe People:
```pascal
  User = class(People)
    private
      id: Integer;
    public
      procedure setId(idParam: Integer);
      function toString(): string;
  end;
```