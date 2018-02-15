[Terug naar inhoudsopgave](./index.md)

# Hoofdstuk 1: Into Programming
## Code
Een *program* is een set speciale instructie die de computer vertelt welke taken het moet uitvoeren, opgeslagen in een tekstbestand.
`program = code || source code`

De regels voor juiste formattering en combinaties van die instructies wordt *computer language* genoemd, en is vergelijkbaar met grammatica- en spellingsregels in mensentalen.
`computer language = syntax`

### Statements
In een computertaal is een groep woorden, nummers en operatoren die een specifieke taak uitvoeren een statement. Voorbeeld:
`a = b * 2;`

De letters `a` en `b` hier zijn *variabelen*. Simpele dozen waar je je zooi in kwijt kan. In programma’s houden variabelen waardes vast om vervolgens gebruikt te worden door het programma.  `2` is in dit geval een waarde die je op zou kunnen slaan in een variabele.

De meeste statements in JavaScript sluit je af met een `;` (puntkomma/semicolon).

### Expressions
Statements worden opgemaakt uit meerdere *expressions*. Expressies zijn alle verwijzingen naar variabelen of waardes, of een set van variabelen en waardes samengevoegd met operatoren.

In het voorbeeld `a = b * 2` zitten de volgende expressies:
- `2` is een *letterlijke waarde expressie* (literal value expression).
- `b` is een *variabele expressie* (variable expression), wat betekend dat het de waarde in de variabele ophaalt.
- `b * 2` is een *rekenkundige expressie* (arithmetic expression), die in dit geval `b` vermenigvuldigt met `2`.
- `a = b * 2` is een *toewijzende expressie* (toewijzende expressie), het wijst de vermenigvuldiging van `b` met `2` toe aan variabele `a`.

Expressies die op zichzelf staan worden ook wel een *expression statement*, en uitvoeringen van functies *call expression* statements.

### Executing a Program
Een collectie van statements moeten *uitgevoerd* (executed) worden voordat ze ook echt wat doen.
`executing a program = running a program`

De code die jij schrijft is geen code die de computer ook gelijk begrijpt. Een *interpreter* of *compiler* zet je code om naar een taal die de computer begrijpt (ook wel bytecode of binary genoemd, maar dat is niet zo interessant).

De *interpreter* compileert de code op het moment dat het uitgevoerd wordt. Het interpreteert letterlijk wat jouw code verwacht dat de computer doet en vertaalt de code op die interpretaties.

De *compiler* compileert je code voordat het uitgevoerd wordt. De vertaalde code wordt in deze instantie later uitgevoerd (denk aan een .exe bestandje in Windows). Dit wordt Ahead-Of-Time (AOT) genoemd, omdat de code pas later wordt uitgevoerd dan wanneer het wordt gecompileerd.

JavaScript is dan weer net even apart. De geschreven code wordt eigenlijk vlak voordat het wordt uitgevoerd *gecompileerd* en dan gelijk uitgevoerd (genaamd Just-In-Time, of JIT in het kort).

## Try It Yourself
De beste manier om deze concepten te beoefenen is om gelijk code te schrijven. Dit kan makkelijk in een DevTools console in alle browsers (Chrome, Firefox of Safari.. F*** IE).

De beste manier om code te schrijven in de console is om een nieuwe tab te openen en in de adresbalk `about:blank` te schrijven. Zo weet je zeker dat je geen onverwachte errors krijgt omdat de JS van een pagina met jouw code zit te knoeien (of andersom, het is maar net hoe je het bekijkt).

Ter referentie in de komende stukken, het stukje code wat wordt gebruikt in het boek als leidraad:
```js
a = 21;

b = a * 2;

console.log( b );
```

### Output
Met `console.log` output je tekst in de console. De `console` is het object waar de functie `log` zig in bevindt. Daarom roepen we eerst het `console` object aan en doen daarna een *function call* naar de `log` functie in dat object.

Je kan ook tekst outputten door middel van de `alert` functie, waarmee een browser popup de tekst die je meegeeft als parameter laat zien. Een nadeel aan `alert` is is dat het alle uitvoeringen van JavaScript op dat moment onderbreekt (in het tabblad waar de alert wordt aangeroepen), waardoor je eerst op oké moet klikken voordat je JS verder gaat.
`onderbrekend = disrupting`

### Input
De meest voorkomende vorm van input is form inputs in een HTML pagina.  Al heb je ook een `prompt` functie die, net zoals `alert`, een browser popup opent waarin je gegevens in kan voeren in een tekstveld.

De `prompt` functie neemt een stuk tekst aan als parameter, wat dan wordt laten zien in de popup. 

Je kan `prompt` gebruiken om jezelf uit te dagen en gaan spelen met output die zich aanpast aan verschillende inputs.

## Operators
Operators (operatoren) gebruiken we om acties op variabelen en waardes uit te voeren. `=` en `*` zijn twee operatoren. Hier is een overzichtje van alle operatoren:

### Toewijzing en berekeningen
- `=`. Toewijzen van waardes aan variabelen.
- `+`, `-`, `*`, en `/` voor berekeningen.
- Samengestelde toewijzing (berekening direct op de waarde van een variabele): `+=`, `-=`, `*=`, `/=` (`a += 2` is hetzelfde als `a = a + 2`).
- `++` en `--`: 1 bij een getal optellen of aftrekken (increment/decrement).
- `.`: het bereiken van object *properties* (`console.log`)

### Vergelijkingen
- `==`: Is gelijk aan
- `===`: Is strict gelijk aan (string kan hier niet vergeleken worden met een nummer, bij `==` wel)
- `!=`: Is niet gelijk aan
- `!==`: Is strict niet gelijk aan
- `<`: Is minder dan
- `>` Is meer dan
- `<=`: Is minder dan of gelijk aan
- `>=`: Is meer dan of gelijk aan
- `&&`: En (de vergelijkingen voor en na `&&` moeten waar zijn)
- `||`: Of (één van de vergelijkingen voor en na `||` moeten waar zijn)

## Values & types
In JavaScript heb je verschillende soorten (types) values (waardes) genaamd:
- number: een nummer, bijvoorbeeld `25`
- string: een stuk tekst, bijvoorbeeld `'hallo'`
- boolean: kan `true` of `false` zijn.
- array: lijst van meerdere variabelen, bijvoorbeeld `[1, 2, 3, 'hoi', 'doei']`
- object: een object met eigenschappen (properties) en eigen methodes (methods), bijvoorbeeld 
```js
object: {
	eigenschap: 'dit is een eigenschap',
	methode: function() {
		console.log('dit is een methode');
	}
}
```
- functions: een blok code die los staat van de rest van de code, bijvoorbeeld
```js
function printImportantData() {
	console.log('This is very very important!');
}
```

Er zijn er nog meer, maar dit zijn de meestgebruikte types.
Variabelen die direct in de broncode worden gebruikt worden `literals` genoemd. Een string literal wordt bijvoorbeeld altijd omringt met `"` of `'`.

### Converting between types
Je kan het type variabele omzetten naar een ander type, genaamd conversie. Dit proces heet in JavaScript *coercion* (letterlijk dwang). Je kan op verschillende manieren het type van een variabele omzetten:
```js
var a = "42";
var b = Number(a); // Number hier zet de string "42" om in het getal 42

console.log(a)	// "42"
console.log(b)	// 42
```

Het gebruik van `Number` wordt aanschouwd als een *explicit coercion*. De schrijver van de code zet de variabele zelf om in een getal.

Wanneer je `"42"` met `42` vergelijkt, zou je kunnen zeggen dat ze gelijk aan elkaar zijn. Alleen is dat niet helemaal waar. De ene is namelijk een string, en de andere een nummer. In dit geval zou je zeggen dat *loosely equal* zijn.

Met `==` kan je variabelen met twee verschillende types met elkaar vergelijken, en toch *waar* zijn. `"42" == 42` zou dus *kloppen*, en de code die je eronder hebt staan zou uitgevoerd worden als het afhankelijk zou zijn van deze vergelijking.

Het gebruik van `==` met twee verschillende variabele types wordt aanschouwd als een *implicit coercion*, de omzetting van types wordt gedaan zonder dat de programmeur de conversie zelf uitvoert. Het is *implied*.

## Code comments
Code is niet alleen voor de computer. Sterker nog, code is misschien zelfs meer voor de ontwikkelaar bestemd i.p.v. voor de compiler.

De computer geeft alleen om de nulletjes en eentjes die uit de compiler komen. De juiste volgorde van nulletjes en eentjes kunnen op talloze manieren worden geschreven. De keuzes die je maakt over hoe je je programma schrijft maken veel uit, ook voor je teamgenoten en je toekomstige zelf.

Programma’s moeten zo geschreven worden, dat ze ook logisch klinken als de code wordt doorgelezen. Comments zijn ook een een belangrijk deel van leesbaarheid. Comments zijn puur bedoeld voor lezers van je code, en worden genegeerd door interpreter/compiler. 

Er zijn geen standaarden over hoe je comments moet achterlaten in je code, maar er zijn wel een paar regels:
- Code zonder comments is niet suboptimaal.
- Teveel comments (bijvoorbeeld een per regel) is een teken van slecht geschreven code.
- Comments moeten uitleggen waarom, niet wat. Ze kunnen ook uitleggen hoe, als dat nog vrij verwarrend is.

In JavaScript heb je meerdere soorten comments:
```js
// Dit is een single-line comment
/* Dit is een multi-line comment die
	 meerdere regels beslaat. Het is
   echt onwijs handig want je kan zo
	 veel tekst kwijt. */
```

Multi-line comments kunnen ook op een enkele rij komen te staan, of zelfs `var a = /* tussen code door */ 42`.

## Variables
Variabelen kan je gebruiken om bepaalde waardes bij te houden in je programma. Ze worden variabelen genoemd, omdat de waarde die aan de variabele is toegewezen *variabel* kan zijn.

Sommige programmeertalen gebruiken types wanneer je een variabele declareert. Dit staat bekent als *static typing* of *type enforcement*, en houdt in dat je de type van een variabele niet kan veranderen. Het wordt aanschouwt als een voordeel voor correctheid en het vermijden van programmafouten veroorzaakt door verkeerde types.

Een alternatief voor static typing is *dynamic typing* (of *weak typing*), wat JavaScript hanteert. *Dynamic typing* staat toe dat een variabele elke type waarde kan vasthouden, en ook tussen types kan wisselen. 

*In het boek wordt een uitgebreid voorbeeld gegeven over hoe dynamic typing werkt. Ik heb geen zin om het voorbeeld over te nemen, dus [hier is een link naar het hoofdstuk op GitHub](https://github.com/getify/You-Dont-Know-JS/blob/master/up%20%26%20going/ch1.md)*

## Blocks
Codeblokken zijn stukken code afgesloten met `{}`.
```js
var getal = 3;
{
	getal = getal * 3;
	console.log(getal); // 9
}
```

Dit is valide code, alleen plak je meestal nog een statement eraan vast zoals een `if` statement.
```js
var getal = 3;
if (getal > 1) {
	getal = getal * 3;
	console.log(getal); // 9
}
```
Hier wordt het codeblok pas uitgevoerd als getal groter is dan 1.
Codeblokken hoeven niet afgesloten te worden met `;`.

## Conditionals
Conditionals zijn beslissingen die worden genomen in je code. Dit betreft vaak een codeblock die alleen uitgevoerd mag worden als een bepaalde voorwaarde is voldaan.
Er zijn meerdere expressies voor conditionals, waarvan `if` het meest gebruikt wordt.

Met een `if` statement zeg je eigenlijk *wanneer deze voorwaarde is voldan, doe dan dit* met dit verwijzende naar het code block direct achter de statement.
```js
var getal = 3;
if (getal > 2) {
	getal = getal * 3;
	console.log(getal); // 9
}
```

De `if` vereist een vergelijking die kan uitkomen op `true` of `false`. 
Je kan hiernaast ook een `else` gebruiken:
```js
var getal = 3;
if (getal > 2) {
	getal = getal * 3;
	console.log(getal); // 9
} else {
	console.log('Het getal is te klein!);
}
```
`else` wordt in dit geval uitgevoerd wanneer `getal` gelijk is aan of kleiner is dan 2. 

Met `if` statements vindt implicit coercion plaats als het type variabele anders is dan verwacht wordt. Wil je een getal met een string vergelijken? Dan wordt de string omgezet naar getal om de vergelijking rond te maken.

Waar je ook mee te maken krijg is “truthy” en “falsy” waardes. Lege strings omgezet naar een boolean worden geïnterpreteerd als `false` (dus is de string “falsy”). Hetzelfde geld voor het getal 0. Strings met tekst erin en getallen boven de 0 worden geïnterpreteerd als `true` wanneer ze worden omgezet naar een boolean.

Naast `if` statements heb je ook `switch` statements. Deze kunnen gebruikt worden i.p.v. een reeks aan if..else statements. 

## Loops
Loops zijn codeblocks die blijven draaien totdat een voorwaarde niet meer voldaan is. Ze maken dus gebruik van conditionals om te kijken of de code nog uitgevoerd moeten worden. Elke keer wanneer een loop wordt uitgevoerd noemen we een iteratie.

Een `while` loop  of een `do…while` loop zijn goede voorbeelden van het herhalen van code totdat een voorwaarde niet meer voldoet.
```js
while (getal < 3) {
	console.log(getal);
	getal++;
}

// of:

do {
	console.log(getal);
	getal++
} while (getal < 3);
```

Het verschil tussen deze twee is dat de `do…while` altijd één keer wordt uitgevoerd voordat er wordt gekeken of de voorwaarde voldoet, bij een standaard `while` loop wordt eerst gekeken naar de voorwaarde voordat de loop voor het eerst wordt uitgevoerd.

Met de `break` statement kan je loops vroegtijdig stoppen.
```js
var i = 0;

// Deze loop blijft voor altijd draaien, omdat true altijd true is.
while (true) {
	// Stop de loop wanneer variabele i groter is dan 9
	if ((i <= 9) === false) {
		break;
	}

	console.log(i);
	i++;
}
// 0 1 2 3 4 5 6 7 8 9
```
Dit doe je normaal nooit trouwens, je geeft gewoon de juiste conditie mee aan de `while` loop.

Naast `while` en `do…while` heb je ook een andere vorm van loop vorm genaamde de `for` loop:
```js
for (var i = 0; i <= 9; i++) {
	console.log(i);
}
// 0 1 2 3 4 5 6 7 8 9
``` 
De for loop heeft 3 clausules: de initialisatie clausule ( `var i = 0` ), de voorwaarde-toetsingsclausule ( `i <= 9` ) en de update clausule ( `i++` ).

## Functions
Je programma zal vast en zeker stukken code bevatten die op meerdere momenten opnieuw aangeroepen moeten worden. De beste manier om dit te doen is met `function`.

Een functie is een genaamde stuk code die aangeroepen (called) kan worden met die naam, waarna de code in het blok uitgevoerd wordt:
```js
function printGetal() {
	console.log(getal);
}

var getal = 3;

printGetal(); // 3

getal = getal * 3;

printGetal(); // 9
```

Functies kunnen ook argumenten (parameters) meekrijgen. Dit zijn waardes die je meegeeft aan de functie. Ze kunnen ook een waarde teruggeven. Dit is allemaal niet verplicht.
```js
function printNumber(nr) {
	console.log(nr);
}

function convertToEuro(nr) {
	return "€" + nr + ",-";
}

var getal = 3;
printNumber(getal); // 3

var getalTwee = converToEuro(1284);
printNumber(getalTwee); // "€1284,-"
```

### Scope
Scope (ookwel *lexical scope*) is een term die het bereik van variabelen en waardes representeert. Wanneer je een variabele in een functie aanmaakt, is deze niet te gebruiken buiten die functie of in een andere functie.
```js
function one() {
	var a = 1;
	console.log(a);
}

function two() {
	var a = 2;
	console.log(a);
}

one(); // 1
two(); // 2
```

Scopes kunnen ook genest worden, waardoor de binnenste scope toegang heeft tot variabelen in de omringende scopes:
```js
function outer() {
	var a = 1;
	
	function inner() {
		var b = 2;

		// Hier kunnen we bij 'a' en 'b'
		console.log(a + b); // 3
	}

	inner();
	
	// Hier kunnen we alleen bij 'a'
	console.log(a); // 1
}
outer();
```