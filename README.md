# Projektseite-boids

## Inhaltsverzeichnis 


[1.   Greenfoot](#1)

[2.   Idee](#2)

[3.   Umsetzung der Idee](#3)

[4.     Actor](#4)

[5.    Smooth Mover](#5)

[6.    Boid](#6)

[6.1   setSwarmRotationGetCloser](#7)

[6.2   setSwarmRotationGetAway](#8)

[6.3   turnAtWorldEdge](#9)

[7.    Reflexion des Projekts](#10)

[8.    Stundenblog](#11)

## <a name="1"></a> Greenfoot

Ich wollte das letzte Projekt ohne Blocksprache machen, da ich diese beim letzten Mal benutzt habe. Ich habe mich nach Absprache mit Herrn Buhl für Greenfoot entschieden. Greenfoot ist eine interaktive Java-Entwicklungsumgebung, die für Anfänger sehr gut geeignet ist. Dabei war mein Ziel das ich die Programmiersprache Java kennenlerne und vestehe. Die Entwicklung von Simulation und interaktiven Spielen ist mit Greenfoot gut zu erstellen und daher fand ich Greenfoot sehr ansprechend und habe es für mein Projekt ausgewählt.

## <a name="2"></a> Idee
 
Ich habe mich für die Simulation "Boids" entschieden. Diese simuliert das Schwarmverhalten von Vögeln. 

Dabei soll jeder Vogel bei seinem Flug die folgenden drei Regeln befolgen:
1. Separation: Gehe auf Abstand zu anderen Vögeln, wenn du ihnen zu nahe kommst.
2. Angleichung: Richte deinen Flug in die mittlere Flugrichtung der anderen Vögel in der Nähe aus.
3. Zusammenhalt: Bewege dich auf die mittlere Position der anderen Vögel in deiner Nähe zu.

Bei diesem Algoithmus ergibt sich für das Flugverhalten der Vögel ein sehr interessantes Bewegungsmuster. 

## <a name="3"></a> Umsetzung der Idee

 <a name="4"></a>  Actor: 
 
Der Actor  ist ein Objekt, dass in der Greenfoot Welt existiert. Jeder Actor hat einen Ort in der Welt und ein Erscheinungsbild. Jedes Objekt, das in der Welt erscheinen soll muss eine Unterklasse vom Actor sein. Die Actor-Methoden stehen allen Unterklassen von Actor zur Verfügung. Die Unterklassen können ihr eigenes Verhalten und Ausssehen definieren.
 
 <a name="5"></a>  Smooth Mover:
 
Der Smooth Mover ist eine Unterklasse von Actor. Dieser ermöglicht kleine präzise Bewegungen (z. B. Bewegungen von 1 Pixel oder weniger), die nicht an Präzision verlieren. Der Smooth Mover kommt schon mit bestimmten Funktionen, genau wie der Actor. Diese Funktionen stehen den Unterklassen zu Verfügung. 

Zu dem Code des Smooth Mover habe ich wei neue Codes hinzugefügt. Einmal die Funktion wo getestet wird, ob man nah an einer der Kanten von der Welt ist. Wenn dieses der Fall ist wird "true zurückgeben und wenn dies nicht der Fall ist wird "false" zurückgegeben.

 ![AtWorldEdge](https://user-images.githubusercontent.com/88386035/163636217-6b202c5e-2dcf-4655-a4c8-20adea4af3af.PNG)

Außerdem habe ich noch die Funktion hinzugefügt, die die Winkel zu bestimmten Objekten berechnet. 

![Degree ding](https://user-images.githubusercontent.com/88386035/163636303-d29fc047-8837-4452-90a4-864e86100e62.PNG)

Diese beiden Funktionen sind später wichtig um den Code für den Boid zu verstehen.

<a name="6"></a>  Boid:
 
<a name="7"></a> setSwarmRotationGetCloser:

<a name="8"></a>  setSwarmRotatiionGetAway: 

<a name="9"></a> turnAtWorldEdge:

 
<a name="10"></a>  Reflexion des Projekts:
 
 
## <a name="11"></a> Stundenblog

Der Link zu meinen Stundenblog des zweiten Projekts:
https://github.com/laurasoenitz/Informartik-Projekt-2
