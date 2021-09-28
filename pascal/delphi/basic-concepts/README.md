# Conceitos Básicos da Linguagem Pascal

## Pre-requisitos

Conhecimento necessários:
* Algoritimo
* Paradigma procedural
* IDE

<br>

## Instalando a IDE

[Download Delphi Community Edition](https://www.embarcadero.com/br/products/delphi/starter/free-download)

<br>

## Criando um Projeto

File > New > Console Application - Delphi <br><br>

Estrutura de um programa Console Application:

```pascal
program Project1;

{$APPTYPE CONSOLE}

{$R *.res}

uses
  System.SysUtils;

begin
  try
    { TODO -oUser -cConsole Main : Insert code here }
  except
    on E: Exception do
      Writeln(E.ClassName, ': ', E.Message);
  end;
end.
```

```program``` seguido pelo nome do programa.

```uses``` importa outros modulos, parecido com ```#include``` em C e ```import``` em Java.

```begin``` e ```end;``` começa e termina um bloco, procedimento, função e etc, parecido com ```{ }``` em C.

```end.``` finaliza o programa.

```try``` e ```except``` tratam uma exceção, parecido com ```try/catch``` em Java.

<br>

## Comentarios

Escrevendo comentarios:
```pascal
//one line comment
{ comment block }
(* less used *)
{$Special comment for compiler}
```
<br>

## Variáveis

Declarando e inicializando variáveis:

```pascal
var
  { declare }
  userName : string;

  { declare and initialize }
  age : Integer = 23;

begin
  try
  { initialize }
  userName := 'Jonathan';

  { ... }

  except
    on E: Exception do
      Writeln(E.ClassName, ': ', E.Message);
  end;

end.
```
<br>

Declaração de váriável local e global:

```pascal
var
  { Global scope variable }
  userName: string;

{ Variables into blocks, procedures and functions
  are local scope }
procedure exampleProcedure ();
begin
  { Local scope variable }
  var
    age: Integer;
end;
```
<br>

## Tipos

Tipos mais comuns:

```pascal
var
  { Variables }
  c: Char;
  numInt: Integer;
  numReal: Real;
  isOn: Boolean;
  text: string;

  { Subrange variables }
  num1To100: 1 .. 100;
  letterAToF: 'A' .. 'F';

type
  { Enumerated type variable }
  months = (Jan, Feb, Mar, Apr, May, Jun, Jul, Aug, Sep, Oct, Nov, Dec);

var
  { months type variable }
  month1: months;
```

[Tabela com outros tipos mais especificos como ```Int8``` e ```Int64```]()

<br>

## Condicionais

Declaração ```if else```:

```pascal
var
  x: Integer = 10;
  y: Integer = 5;

begin
  if x > y then
    Write('x is greater than y')
  else if x = y then
    Write('x is equal to y')
  else
    Write('x is less than y'); { Dot and comma is placed
    only in the last condition }
end.
```

[Tabela com todos os principais operadores como ```>=``` e ```and```.]()

<br>

## Laços

Laço ```while do```:

```pascal
var
  i: Integer = 0;

begin
  while i < 10 do
  begin
    Writeln(a);
    i := i + 1;
  end;
end.
```

Laço ```for do```:

```pascal
var
  i: Integer;

begin
  for i := 0 to 10 do
  begin
    Writeln(i);
  end;
end.
```

Laço ```repeat until```:

```pascal
var
  i: Integer = 0;

begin
  repeat
  Writeln(i);
  i := i + 1;

  until (i=10);
end.
```

<br>

## Funções e Procedimentos

Funções em Pascal sempre retorna um valor:

```pascal
{ This function takes two arguments of type Integer and
  returns an Integer value }
function sum (num1: Integer; num2: Integer) : Integer;
begin
  sum := num1 + num2;
end;
```
<br>

Procedimentos não retorna um valor, algo parecido com ```void function``` em C.

```pascal
{ This procedure takes an argument
  of type string, but unlike the function
  it does not return a value. }
procedure print (text: string);
begin
  Write(text);
end;
```