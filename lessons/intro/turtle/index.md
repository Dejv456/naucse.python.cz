# 🐍 🐢

V této lekci si vyzkoušíš *želví kreslení*.

Pusť Python v *interaktivním módu* (bez souboru .py).

```pycon
$ python

>>>
```

> [note]
> (Znaky `>` a `$` píše počítač, ne ty.
> Na Windows bude místo `$` znak
> `>` a před `$` nebo
> `>` může být ještě něco dalšího.)

Pak napiš:

```python
from turtle import forward

forward(50)
```

Ukáže se okýnko se šipkou, které nezavírej.
Dej ho tak, abys viděla i příkazovou řádku
i nové okýnko.

## A kde je ta želva?

Želva je zrovna převlečená za šipku.
Ale funkce `shape` ji umí odmaskovat:

```python
from turtle import shape

shape('turtle')
```

Modul `turtle` obsahuje spoustu dalších funkcí, kterými můžeš želvu ovládat.
Pojďme se na ně kouknout zblízka.


## Otáčení

Želva se umí otáčet (doleva – `left` a doprave – `right`) a lézt po papíře
(dopředu – `forward`).
Na ocase má připevněný štětec, kterým při pohybu kreslí čáru.

```python
from turtle import forward, left, right

forward(50)
left(60)
forward(50)
right(60)
forward(50)
```

Zkus chvíli dávat želvě příkazy.
Když se ti výsledek nelíbí, můžeš buď zavřít kreslící okno
(nebo naimportovat a použít funkci `clear()`) a zkusit to znovu.


## Želví program

Interaktivní mód je skvělý na hraní,
ale teď přejdeme zase na soubory.

Vytvoř si v editoru nový soubor.
Ulož ho do adresáře pro dnešní lekci pod jménem `zelva.py`.

> [note]
> Jestli adresář pro dnešní lekci ještě nemáš, vytvoř si ho!
> Pojmenuj ho třeba `02`.

> [warning]
> Soubor nepojmenovávej `turtle.py` – z modulu `turtle` budeš importovat.

Jestli chceš pro soubor použít jiné jméno, můžeš, ale
nepojmenovávej ho `turtle.py`.

Do souboru napiš příkazy na nakreslení obrázku
a – pozor! – na konci programu zavolej funkci `exitonclick`
(naimportovanou z modulu `turtle`).

> [note] Otázka
> Co dělá funkce <code>exitonclick</code>, kterou voláš na konci programu?

Až to budeš mít hotové, zkus začít kreslit obrázky:

### Čtverec

Nakresli čtverec.

![Želví čtverec](static/turtle-square.png)

Čtverec má čtyři rovné strany
a čtyři rohy po 90°.

{% filter solution %}
```python
from turtle import forward, left, exitonclick

forward(50)
left(90)
forward(50)
left(90)
forward(50)
left(90)
forward(50)
left(90)

exitonclick()
```
{% endfilter %}

### Obdélník

Nakresli obdélník.

Zkus zařídit, aby se po nakreslení „dívala” želva doprava (tak jako na začátku).

![Želví obdélník](static/turtle-rect.png)

{% filter solution %}
```python
from turtle import forward, left, exitonclick

forward(100)
left(90)
forward(50)
left(90)
forward(100)
left(90)
forward(50)
left(90)

exitonclick()
```
{% endfilter %}

### Tři čtverce

Nakresli tři čtverce, každý otočený třeba o 20°.

![Tři želví čtverce](static/turtle-squares.png)

{% filter solution %}
```python
from turtle import forward, left, exitonclick

forward(50)
left(90)
forward(50)
left(90)
forward(50)
left(90)
forward(50)
left(90)

left(20)

forward(50)
left(90)
forward(50)
left(90)
forward(50)
left(90)
forward(50)
left(90)

left(20)

forward(50)
left(90)
forward(50)
left(90)
forward(50)
left(90)
forward(50)
left(90)

exitonclick()
```
{% endfilter %}

Tolik kódu! Tohle musí jít nějak zjednodušit!

Jde.
Pojďme se naučit jak v Pythonu nějakou činnost opakovat.


## Jak opakovat – a neopakovat *se*

Udělej v editoru nový soubor a ulož ho jako `cykly.py`.
Budeme v něm zkoušet *cykly*.

První opakovací program, který napíšeme, bude dělat tohle:

* Stokrát po sobě:
  * Napiš "Nikdy nebudu odsazovat o tři mezery!"

Do jazyka Python se to dá přeložit následovně:

```python
for i in range(100):
    print('Nikdy nebudu odsazovat o tři mezery!')
```

Na ono `for i in range(100)` se detailněji podíváme za chvíli,
teď to pro nás bude “hlavička”, která říká “opakuj stokrát”.

Podobnou “hlavičku” už jsi viděl{{a}}: příkaz `if`.
Stejně jako u `if` tu máme na konci dvojtečku a za hlavičkou následuje
odsazený blok – *tělo* příkazu; to na co se hlavička vztahuje.
Tělo příkazu `for` se opakuje stále dokola.


### Výčet

Zkus napsat ještě jeden vzorový program, který v češtině zní:

* Pro každý <var>pozdrav</var> z výčtu: „Ahoj“, “Hello”, “Hola”, ”Hei”, "SYN":
  * Vypiš <var>pozdrav</var> a za ním vykřičník.

V Pythonu se tento program zapíše jako:

```python
for pozdrav in 'Ahoj', 'Hello', 'Hola', 'Hei', 'SYN':
    print(pozdrav + '!')
```

Opět je tu hlavička a tělo příkazu.
Tentokrát se na hlavičku podívej pozorněji.
Pythonní <code>for <var>promenna</var> in <var>sekvence</var></code>
znamená „Pro každé <var>promenna</var> ze <var>sekvence</var>“.

Jméno proměnné si volíš {{gnd('sám', 'sama')}}.
Příkaz `for` danou proměnnou vždy na začátku bloku *nastaví* na aktuální
hodnotu.
Program výše funguje úplně stejně, jako kdybys napsal{{a}}:

```python
pozdrav = 'Ahoj'
print(pozdrav + '!')

pozdrav = 'Hello'
print(pozdrav + '!')

pozdrav = 'Hola'
print(pozdrav + '!')

pozdrav = 'Hei'
print(pozdrav + '!')

pozdrav = 'SYN'
print(pozdrav + '!')
```


### Range

Vraťme se k `for i in range(100)`.
Už víš, že to znamená „Pro každé <var>i</var> z `range(100)`“.
Co je ale to `range`? Když si ho vypíšeš, nevypadne nic vysvětlujícího:

```pycon
>>> range(100)
range(0, 100)
```

Je ale použité jako „sekvence“
v <code>for <var>promenna</var> in <var>sekvence</var></code>.
Je to nějaký výčet, nějaká posloupnost hodnot.
A teď už umíš vypsat, jaké to jsou!

```python
for i in range(10):   # Doporučuju použít jen 5 místo 100
    print(i)
```

Program spusť. Jaká čísla se vypíšou?

{% filter solution %}
Vypíšou se čísla od 0 do 4!
Program funguje steně, jako kdybys napsal{{a}}:

```python
i = 0
print(i)
i = 1
print(i)
i = 2
print(i)
i = 3
print(i)
i = 4
print(i)
```
{% endfilter %}

Funkce `range(n)` vrací *sekvenci čísel*.
Začíná od 0 a čísel v ní je přesně <var>n</var>.
(Na samotné <var>n</var> se tedy už nedostane.)

Často se `for i in range(n)` používá jako “Opakuj <var>n</var>-krát“.
V takovém případě nás proměnná <var>i</var> – „počitadlo“ – nezajímá.
V programu ji jednoduše nepoužijeme.

Teď by už mělo být jasné, jak funguje původní program:

```python
for i in range(100):
    print('Nikdy nebudu odsazovat o tři mezery!')
```

Python píše hlášky, jednu za druhou, a u toho si v promněnné <var>i</var>
počítá, jak už je daleko.


## Čtverec II

A znovu ke kreslení, tentokrát s použitím cyklů!

Nakresli čtverec. To se dělá následovně:

* Čtyřikrát:
  * Popojdi dopředu (a kresli přitom čáru)
  * Otoč se o 90°

![Želví čtverec](static/turtle-square.png)

{% filter solution %}
```python
from turtle import forward, left, exitonclick

for i in range(4):
    forward(50)
    left(90)

exitonclick()
```
{% endfilter %}

## Přerušovaná čára

Funkce `penup` a `pendown`
z modulu `turtle` řeknou želvě,
aby přestala, resp. začala kreslit.
Zkus si to:

```python
from turtle import forward, penup, pendown, exitonclick

forward(30)
penup()         # od teď želva nekreslí
forward(5)
pendown()       # od teď želva zase kreslí
forward(30)

exitonclick()
```

Zkus nakreslit dlouhou přerušovanou čáru.

![Želva a přerušovaná čára](static/turtle-dashed.png)

{% filter solution %}
```python
from turtle import forward, penup, pendown, exitonclick

for i in range(10):
    forward(10)
    penup()
    forward(5)
    pendown()

exitonclick()
```
{% endfilter %}

Pak zkus zařídit, aby jednotlivé čárky byly postupně
větší a větší.

![Želva a přerušovaná čára](static/turtle-dashed2.png)

> [note] Nápověda
>
> První čárka je dlouhá 1 jednotku, druhá 2 jednotky, třetí 3, atd.
>
> Dokonce můžeš na začátek dát prázdnou čárku (0 jednotek)
> a mít tak délky 0, 1, 2, 3, 4, …

{% filter solution %}
```python
from turtle import forward, penup, pendown, left, exitonclick

for i in range(20):
    forward(i)
    penup()
    forward(5)
    pendown()

exitonclick()
```
{% endfilter %}

### Tři čtverce

Nakonec nakresli 3 čtverce, každý otočený o 20°.
Tentokrát už víš, jak to dělat chytře: opakuj pomocí příkazu
`for`, ne kopírováním kódu.

![Tři želví čtverce](static/turtle-squares.png)

* Třikrát:
  * Nakresli čtverec (viz předchozí úloha)
  * Otoč se o 20°

{% filter solution %}
```python
from turtle import forward, left, right, speed, exitonclick

for i in range(3):
    for j in range(4):
        forward(50)
        left(90)
    left(20)

exitonclick()
```
{% endfilter %}


## Úkol navíc

Máš-li hotovo, zkus nakreslit schody:

![Želví schody](static/turtle-stairs.png)

A máš-li i schody, zkus nakreslit těchto šest (nebo sedm?) šestiúhelníků:

![Želví plástev](static/turtle-hexagons.png)


### Přepisování proměnných

Už víš, že:

```python
print("Tady je pár čísel:")

for cislo in 8, 45, 9, 21:
    print(cislo)
```

funguje jako:

```python
print("Tady je pár čísel:")

cislo = 8
print(cislo)

cislo = 45
print(cislo)

cislo = 9
print(cislo)

cislo = 21
print(cislo)
```

Zkus popsat, jak pracuje následující program.

```python
soucet = 0

for cislo in 8, 45, 9, 21:
    soucet = soucet + cislo

print(soucet)
```


{% filter solution %}
```python
soucet = 0

cislo = 8
soucet = soucet + cislo

cislo = 45
soucet = soucet + cislo

cislo = 9
soucet = soucet + cislo

cislo = 21
soucet = soucet + cislo

print(soucet)
```

Příkaz `soucet = soucet + cislo` vypočítá hodnotu
`soucet + cislo`, tedy přičte aktuální číslo k součtu.
Výsledek uloží opět do proměnné `soucet`.
Nová hodnota `soucet` se pak použije v dalším průchodu cyklem.

Na začátku je součet 0 a na konci se součet všech čísel vypíše.
{% endfilter %}
