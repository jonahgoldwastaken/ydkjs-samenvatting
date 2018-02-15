# Hoofdstuk 2: Into JavaScript
## Values & Types
In JS hebben variabelen geen type, maar waardes wel. Deze types zijn er beschikbaar:
- `string`
- `number`
- `boolean`
- `null` en `undefined`
- `object`
- `symbol` (nieuw in ES6/ES2015)

JavaScript heeft een `typeof` operator die een waarde kan onderzoeken en het type ervan kan vertellen:
```js
var a;
typeof a; // "undefined"

a = "hello world";
typeof a; // "string"

a = 42;
typeof a; // "number"

a = true;
typeof a; // "boolean"

a = null;
typeof a; // "object" - huh? Is een bug

a = undefined;
typeof a; // "undefined"

a = { b: "c" };
typeof a; // "object"

a = Symbol();
typeof a; // "symbol"
```
`typeof` returned altijd een string.

Zoals je hierboven ziet kijkt `typeof` alleen naar het type van de waarde, niet het type van `a`. Zo zie je dus dat variabelen geen types hebben, en alleen containers zijn voor de waardes die je erin stopt.

## Objects
Het `object` type refereert naar een samengestelde waarde waar je properties (genoemde locaties) in kan zetten die elk een eigen waarde vasthouden.
```js
var obj = {
	a: "hello world",
	b: 42,
	c: true
};

obj.a; // "hello world"
obj.b; // 42
obj.c; // true

obj["a"]; // "hello world"
obj["b"]; // 42
obj["c"]; // true
```
Properties kunnen bereikt worden met *dot notation* (`obj.a`) of *bracket notation* (`obj["a"]`). Dot notation is korter en makkelijker te lezen, dus deze wordt vaker gebruikt.

Bracket notation is handig als je bijvoorbeeld spaties in je property naam (ook wel `key` genoemd) hebt zitten, aangezien je de naam uitschrijft in een string.

Bracket notation is ook handig als je een property wilt bereiken die in een aparte variabele zit, zoals hier:

```js
var obj = {
	a: "hello world",
	b: 42
}

var b = "a";

obj[b] // "hello world"
obj["b"] // 42
```

### Arrays
Een array is een object die waardes vasthoudt op een numerieke index i.p.v. met properties/keys.
```js
var arr = [
	"hello world",
	42,
	true
];

arr[0]; // "hello world"
arr[1]; // 42
arr[2]; // true
arr.length; // 3

typeof arr; // "object"
```
Je moet `0` gebruiken om de eerste waarde uit de array te kunnen pakken, niet `1`.

### Functions
Functies zijn ook een objecttype.
```js
function foo() {
	return 42;
}

foo.bar = "hello world";

typeof foo; // "function"
typeof foo(); // "number"
typeof foo.bar; // "string
```

## Built-in Type Methods
De ingebouwde types en subtypes hebben veel gedragingen als properties en methods die krachtig en handig zijn.
```js
var a = "hello world";
var b = 3.14159265;

a.length; // 11
a.toUpperCase(); // "HELLO WORLD"
b.toFixed(4); // "3.1416"
```

Hoe dit werkt is vrij ingewikkeld, maar elke primitive type (`string`, `number`, `boolean` etc.) heeft een omwikkelend object met properties en methods die je uit kan voeren op waardes van dit type. Een `string` bijvoorbeeld heeft een `String` object, waar de properties en methods automatisch van worden uitgevoerd als je er eentje op een `string` aanroept (zoals het `a.toUpperCase()` voorbeeld hierboven).

## Comparing Values
Er zijn twee hoofdmanieren voor het vergelijken van waardes in JS: *equality*  en *inequality*. Wat je terugkrijgt uit elke vergelijking is altijd een `boolean` (`true` of `false`), maakt niet uit welke types je vergelijkt.

### Coercion
Coercion komt in twee vormen in JS: *explicit* en *implicit*. Explicit coercion is dat je heel makkelijk terugziet in je code dat de conversie van een type naar een ander plaatsvindt. Implicit coercion is wanneer de conversie van types plaatsvindt als een soort side-effect van een bepaalde `statement` die je uitvoert.

```js
// Explicit coercion
var a = "42";
var b = Number(a);
a; // "42"
b; // 42

// Implicit coercion
var a = "42";
var b = a * 1; // Hier vindt de conversie plaats, maar je ziet het niet direct.
a; // "42"
b; // 42 - Het getal

```

### Truthy & Falsy
Wanneer niet-`boolean`s omgezet worden naar `boolean`s, kunnen ze dus alleen `true` of `false` worden, maar wanneer is iets nou `true` (*truthy*), en wanneer `false` (*falsy*)?

#### Falsy waardes in JS
- “” (lege string)
- `0`, `-0`, `NaN` (*Not a Number* - ongeldig getal)
- `null`, `undefined`
- `false`

#### Truthy waardes in JS
Alles wat niet in het lijstje hierboven zit. Hier zijn een paar voorbeelden:
- `"hello"`
- `42`
- `true`
- `[  ]`, `[1, “2”, 3]` (arrays)
- `{  }`, `{ a: 42 }` (objects)
- `function foo() { .. }` (functions)

Niet-`boolean`s nemen alleen deze *truthy* of *falsy* coercion aan wanneer ze ook worden geconverteerd naar een `boolean`, op alle andere momenten is het gewoon het type wat je hebt meegegeven.

### Equality
Er zijn vier gelijkheidsoperatoren: `==`, `===`, `!=` en `!===`. De `!` vormen staan voor “niet gelijk aan”.

- `==`: waarde is gelijk aan, ongeacht het waardetype (`42 == "42"` returned `true`)
- `===`: waarde is *strict* gelijk aan, vergelijkt ook waardetype (`42 === “42"` returned `false`, maar `42 === 42` returned `true`)

Met `==` gaat JS door een set van conversies totdat de waardetypes van beide waardes gelijk zijn aan elkaar. Hier vindt dus *implicit coercion* plaats; conversie die je niet ziet als je niet weet wat er precies plaatsvindt.
Met `===` vindt die *implicit coercion* niet plaats, dus zijn verschillende waardetypes altijd `false`.

Er zijn een paar regels waar je je aan kunt houden met vergelijkingen:
- Als een van de twee waardes de `true` of `false` waarde kunnen zijn, gebruik dan `===`.
- Als een van de twee waardes een van deze specifieke waardes is (`0`, `""`, `[]`), gebruik dan `===`.
- In elk ander geval kan je gerust `==` gebruiken. Het is niet alleen veilig, maar versimpeld heel vaak ook je code door onnodige conversies weg te laten.

`!=` is de *niet gelijk aan* variant van `==`. `!==` van `===`.

Met niet-primitieve waardes (`objects`, `arrays` & `functions`) moet je rekening houden dat alleen de referentie naar de types wordt vergeleken, dus de waardes die je in verwerkt in de types komen nergens terug.

### Inequality
De `<`, `>`, `<=` & `>=` operatoren worden gebruikt voor ongelijkheid. Ze worden typisch gebruikt voor makkelijk te vergelijken waardes als `number`s (`3 < 4` returned `true`).

Het gebruiken van strings in inequality vergelijkingen kan, zolang de string maar juist geconverteerd kan worden naar een `number` (`3 < “4”` returned `true`, maar `"foo" < 4` returned `false` omdat `foo` geen getal (`NaN`) is).

## Variables
In JavaScript moeten variabele-namen en functienamen juiste *identifiers* zijn.

Identifiers moeten beginnen met `a`-`z`, `A`-`Z`, `$` of `_`, en het kan deze karakters alleen bevatten + de getallen `0` - `9`.

*reserved words* die al worden gebruikt in JavaScript (zoals `for`, `if`) kunnen alleen gebruikt worden voor property-namen, niet voor variabele namen.

### Function Scopes
Je gebruikt het `var` sleutelwoord om een variabele te declareren in de huidige scope van de functie, of in de globale scope wanneer je buiten alle functie werkt.

#### Hoisting
Waar een `var` ook maar neergezet wordt in een scope maakt niet uit, je kan overal toegang krijgen tot de variabele in die scope.
```js
var a = 2;
foo(); // declaratie van de functie "foo" is "hoisted" bovenaan de globale scope.

function foo() {
	a = 3;
	console.log(a); // 3
	var a; // de variabele is "hoisted" bovenaan foo()
}

console.log(a); // 2
```

### Nested scopes
Variabelen die je declareert zijn overal in de scope te gebruiken, zowel in scopes in die scope.
```js
function foo() {
	var a = 1; // In foo(), bar() en baz() scope te gebruiken.
	
	function bar() {
		var b = 2; // In bar() en baz() scope te gebruiken.
		
		function baz() {
			var c = 3; // Alleen in baz() scope te gebruiken.
			
			console.log(a, b, c); // 1 2 3
		}
		baz();
		console.log(a, b); // 1 2
	}
	bar();
	console.log(a); // 1
}
foo();
```

Wanneer je een variabele een waarde geeft in de verkeerde scope, krijg je een `ReferenceError` (Variabele is niet gedefinieerd of `undefined`). Als je een waarde wilt toewijzen aan een variabele die nog niet is gedeclareerd, krijg je de kans dat die variabele aan de globale scope wordt toegevoegd. Dit is slecht! Als je strict mode aan hebt staan, krijg je gewoon een `is undefined` error.

Sinds ES6 heb je ook het sleutelwoord `let` om variabelen te declareren. Met dit sleutelwoord wordt de variabele direct vastgemaakt aan het codeblok waarin je de variabele declareert, en is hij nergens te bekennen buiten het codeblok.
```js
function foo() {
	var a = 1; // beschikbaar in de gehele functie

	if (a >= 1) {
		let b = 2; // alleen beschikbaar in deze if statement

		while (b < 5) {
			let c = b * 2; // alleen beschikbaar in de huidige iteratie van de while loop
			b++;
			console.log( a + c );
		}
	}
}

foo();
// 5 7 9
```

## Conditionals
Naast `if` statements heeft JS ook andere vormen van conditionals:
```js
if (a == 2) {
	// Doe iets
} else if (a == 10) {
	// Doe iets anders
} else if (a == 42) {
	// Doe nog iets anders
} else {
	// Als niks hierboven true is doe dan dit
}
```

Deze structuur werkt, maar is wel erg letterlijk en vereist elke keer een nieuwe vergelijking met `a`. Dit kan simpeler met `switch` statements:
```js
switch (a) {
	case 2:
		// Doe iets
		break;
	case 10:
		// Doe iets anders
		break;
	case 42:
		// Doe nog iets anders
		break;
	default:
		// Als niks hierboven true is doe dan dit
}
```

De `break` statements zijn erg belangrijk, omdat als de code van een `true` case wordt uitgevoerd hij niet automatisch stopt maar doorgaat bij de volgende case (zonder deze eerst te vergelijken met a). Dit heet “fall through” en kan soms wenselijk zijn.

```js
switch (a) {
	case 2:
	case 10:
		// Doe iets
		break;
	case 42:
		// Doe iets anders
		break;
	default:
		// standard uitvoeren
}
```
Hier wordt “Doe iets” uitgevoerd wanneer `a` gelijk is aan `2` of `10`.

Een andere conditional vorm is de *conditional operator* of *ternary operator*. Het is een verkorte versie van de `if…else` statement.
```js
var a = 42;
var b = (a > 41) ? "helllo" : "world";

// werkt hetzelfde als
/* if (a > 41) {
	b = "hello";
} else {
	b = "world";
} */
```
Je kan ternaries ook op andere plekken gebruiken, maar bij toewijzingen worden ze het meest gebruikt.

## Strict mode
Strict mode bestaat sinds ES5, en scherpt bepaalde regels aan als het gaat om het schrijven van code. Het zorgt ervoor dat je code beter geoptimaliseerd is, en dus ook sneller draait in je browser.

Je kan strict mode overal instantieëren, maar het liefst doe je dat aan het begin van je applicatie om strict mode over te hanteren.
```js
function foo() {
	"use strict"; // De code in foo() is nu strict

	function bar() {
		// Hier is de code ook strict
	}
}

// De code hier is niet strict
```
Dit wil je dus niet hebben, je wilt strict mode zo vroeg mogelijk instantieëren in je applicatie:
```js
"use strict";

function foo() {
	// Code is in strict mode
	function bar() {
		// Code is ook in strict mode
	}
}
// Code hier is in strict mode
```

Een verbetering met strict mode is het verplichten van het `var` sleutelwoord wanneer je een waarde toewijst aan een variabele die nog niet is gedeclareerd:
```js
function foo() {
	"use strict";
	a = 1; // `var` mist - ReferenceError
}

foo();
```