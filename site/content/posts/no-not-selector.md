---
title: "Warum ich auf die Pseudoklasse :not() in meinem CSS verzichte"
tags: ["sass", "css", "pseudo-class"] # Adds tags to the post
description: ""
cover: "" # Cover used for OpenGraph and Twitter Cards
date: 2019-05-16T17:29:48Z
draft: false
---

Die Pseudo-Klasse `:not()` kann verwendet werden, um Selektoren auszuschließen. Søren hat dem Selektor  einen Liebesbrief geschrieben (auf englisch): [polarbirke](https://annualbeta.com/blog/a-love-letter-to-the-css-not-pseudo-class)

In folgendem Fall wird jedes `div`, das nicht die Klasse `.home` hat, schwarz mit weißer Schrift angezeigt. 

~~~
div:not(.home) {
    background: black;
    color: white;
}
~~~

Auf den ersten Blick wirkt das furchtbar praktisch. Ich spare mir das Überschreiben von bestehenden Deklarationen. 

Aber für mich überwiegen die Nachteile.

Nachteil 1 - Lesbarkeit
-----------
Ich finde den Code schlechter lesbar. Vielleicht ist das nur mein persönliches Empfinden, aber ich verstehe Verneinungen und doppelte Verneinungen nicht. Wenn dann noch mehrere Selektoren ausgeschlossen werden, bin ich komplett abgehängt.

~~~~
.foo:not(.bar):not(.baz):focused {
    …
}
~~~~

Nachteil 2 – Spezifität
-----------------------
Vor Allem der Vorteil, dass ich HTML-Elemente, die keine Klasse haben damit explizit stylen kann, wirkt auch mit seinem gegebenen Setup sinnvoll. Der `:not()` Selektor verändert jedoch die Spezifität. Ein Element-Selektor hat eine Spezifität von 0-0-1. Mit einem `:not()` Selektor erhöht sich die Spezifität direkt auf 0-1-1. 

~~~~
/* Theme A */
ul { /* 0-0-1 */
    color: darkblue;
}

ul:not([class]) { /* 0-1-1 */
    color: darkblue;
}
~~~~

Das klingt wenig dramatisch, bis man anfängt mit weiteren Pseudo-Attributen wie `:hover` zu arbeiten oder sogar ein zweites Theme auf dieser Basis entwickelt. Denn nun benötigen wir immer eine höhere Spezifität, um einen Element-Selektor zu überschreiben.

~~~~
/* Theme B */
ul {
    color: green; /* greift nicht */
}

ul:not([class]) { /* überschreibt Theme A erfolgreich */
    color: red;
}
~~~~

Vielleicht sehe ich den `:not()`-Selektor anders als Søren, weil meine Ausgangslage eine Andere ist. Ich habe keine redaktionellen Eingaben aus einem CMS, die ich abfangen muss, sondern arbeiten an einer Pattern Library. Wir haben keine Element-Selektoren und können den Kunden darauf hinweisen, wenn sein Markup nicht unseren Vorgaben entspricht. 