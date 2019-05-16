---
title: "Pointer Events auf SVG"
tags: ["internet explorer", "svg", "javascript"] # Adds tags to the post
description: ""
cover: "" # Cover used for OpenGraph and Twitter Cards
date: 2019-05-16T11:29:48Z
draft: true
---

In den letzten Projekten ist es immer mal wieder vorgekommen, dass der Kunde oder <abbr title="Quality Assurance" lang="en">QA</abbr> meldete, dass ein Click auf ein Icon zu Fehlern führt.  Plötzlich erhielt man Tickets mit den Beschreibungen <q>"Klick auf schließen bringt den Internet Explorer zum Absturz!"</q>. 

Der Fehler ließ sich gut eingrenzen. Es war ein Javascript-Framework wie [React](https://reactjs.org/) oder [Angular](https://angular.io/) im Einsatz. 