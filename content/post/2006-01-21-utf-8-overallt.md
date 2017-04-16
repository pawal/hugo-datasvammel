---
author: pawal
categories:
- Linux
date: 2006-01-21T19:10:28Z
guid: http://datasvammel.blipp.com/?p=10
id: 10
title: UTF-8 överallt
url: /linux/utf-8-overallt
---

Nu har jag snart konverterat min sista desktop-miljö till att köra UTF-8 fullt ut. Det som släpar efter är alla filsystem som fortfarande har filnamn lagrade som ISO-8859-1. Dessvärre finns ingen information i filsystemet om hur det hanterar kodning av filnamn. Så det verkar som om det blir väldigt mycket jobb att konvertera alla dessa namn till UTF-8.

En snabb genomletning i Debians programarkiv ger att det finns ett litet program som heter <code>convmv</code>. Efter ett par provkörningar så har jag kommit fram till att det inte går att köra på en hel partition, då den gärna översätter redan översatta namn en gång till (om man konverterar latin-1 till UTF-8). Då får man ännu värre filnamn med helt utomjordiska tecken. Så det enda vettiga sättet att göra det är att översätta kataloger man har full koll på vad de innehåller. <code>/home/mp3</code> blir rätt jobbig att översätta med andra ord.

En liten önskning är att framtida filsystem har betydligt bättre metainformation om saker som filnamn.