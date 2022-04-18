# Projektseite-boids

![Boids](https://user-images.githubusercontent.com/88386035/163671548-1aeb06dd-2108-4ae3-b496-82953d4b9ea8.PNG)

## Inhaltsverzeichnis 


[1.   Greenfoot](#1)

[2.   Idee](#2)

[3.   Umsetzung der Idee](#3)

[4.     Actor](#4)

[5.    Smooth Mover](#5)

[6.    Boid](#6)

[6.1  constructor](#7)

[6.2  setSwarmRotationGetCloser](#8)

[6.3   setSwarmRotationGetAway](#9)

[6.4  turnAtWorldEdge](#10)

[7.    Reflexion des Projekts](#11)

[8.    Stundenblog](#12)

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

### <a name="4"></a>  Actor: 
 
Der Actor  ist ein Objekt, dass in der Greenfoot Welt existiert. Jeder Actor hat einen Ort in der Welt und ein Erscheinungsbild. Jedes Objekt, das in der Welt erscheinen soll muss eine Unterklasse vom Actor sein. Die Actor-Methoden stehen allen Unterklassen von Actor zur Verfügung. Die Unterklassen können ihr eigenes Verhalten und Ausssehen definieren.
 
### <a name="5"></a>  Smooth Mover:
 
Der Smooth Mover ist eine Unterklasse von Actor. Dieser ermöglicht kleine präzise Bewegungen (z. B. Bewegungen von 1 Pixel oder weniger), die nicht an Präzision verlieren. Der Smooth Mover kommt schon mit bestimmten Funktionen, genau wie der Actor. Diese Funktionen stehen den Unterklassen zu Verfügung. 

Zu dem Code des Smooth Mover habe ich zwei neue Codes hinzugefügt. 

Einmal die Funktion atWorldEdge. Mit dieser wird getestet, ob der Boid sich an einer der Kanten von der Welt befindet. Wenn dieses der Fall ist wird "true" zurückgeben und wenn dies nicht der Fall ist wird "false" zurückgegeben.

 ![AtWorldEdge](https://user-images.githubusercontent.com/88386035/163636217-6b202c5e-2dcf-4655-a4c8-20adea4af3af.PNG)

Außerdem habe ich noch die Funktion hinzugefügt, die die Winkel zu bestimmten Position berechnet. 

![Degree ding](https://user-images.githubusercontent.com/88386035/163636303-d29fc047-8837-4452-90a4-864e86100e62.PNG)

Diese beiden Funktionen sind später wichtig um den Code für den Boid zu verstehen.

### <a name="6"></a>  Boid:
 
<a name="7"></a> constructor:

Der constructor wird aufgerufen, sobald das Objekt erstellt wird. Der Code bewirkt in dem Fall, dass die Größe des Objekts kleiner wird. Das Objekt war nähmlich anfangs zu groß und musste daher verkleinert werden.

![constructor](https://user-images.githubusercontent.com/88386035/163671330-6627df9c-6994-45b3-ac78-d5b8bca00816.PNG)

<a name="8"></a> setSwarmRotationGetCloser: 

SetSwarnRotationGetCloser bewirkt, dass der Boid sich an andere Boids in der Umgebung anpasst. Genauer gesagt passt er seine eigene Rotation an die Rotation der anderen Boids in der Umgebung an. 

Damit der Boid seine Rotation anpasst, wird als estes eine Liste von den Boids gemacht, die sich im Radius von 80 befinden. Von diesen wird dann die Rotationen gemessen. Die Rotationen werden addiert. Außerdem wird pro Boid der counter um 1 erhöht. 

Wenn der counter ungleich 0 ist, wird dann die neue Rotation berechnet. Dafür rechne ich erstmal den Mittelwert aus den Rotationen aus, indem man die addierten Rotationen durch den Counter rechnet. Davon nehme ich 10 Prozent und addiere dies mit 90 Prozent der eigenen Rotation. Dies bewirkt eine Anpassung an den anderen Boid, aber dadurch, dass man 90 Prozent von der eigenen Rotation nimmt, passiert die Anpassung nicht zu schnell. 

![Get Closer](https://user-images.githubusercontent.com/88386035/163673682-e6bfecde-8d17-4f4c-8419-71fed25f71e8.PNG)

<a name="9"></a> setSwarmRotationGetAway:

SetSwarmRotationGetAway bewirkt, eine Abstoßung zwischen den Boids, sobald sie sich zu nahe kommen.

Damit die Boids sich abstoßen, wird als erste eine Liste von den Boids gemacht, die sich im Radius von 40 befinden. Von diesen Boids wird dann die Rotation gemessen und diese werden addiert. Außerdem misst man den Winkel zu den Nachbarn (DegreesToNeighbor). Außerdem wird der counter um 1 erhöht pro Boid. 

Wenn all diese Werte vorhanden sind und der counter ungleich Null ist wird dann eine neue Rotation für den Boid berechnet. Dabei ist es wichtig, dass die neue Rotation ähnlich zu den Nachbarn ist, jedoch auch eine Abstoßung bewrikt.

Um dies zu erreichen, nehme ich 10 Prozent vom Mittelwert der Rotation der Nachbarn. Dies passiert, indem man die Rotation der Nachbarn durch den counter rechnet. Die 10 Prozent des Mittelwerts addiert man dann mit 90 Prozent der eigenen Rotation. Dazu wid jetzt noch 5 Porzent des Winkels zu den Nachbarn addiert. Daduch wird der Boid abgestoßen, jedoch bleibt er auch in der Nähe der anderen Boids. 

![GetAway version 2](https://user-images.githubusercontent.com/88386035/163673688-2af2a003-8236-4d92-89e0-84cb6e51db49.PNG)

<a name="10"></a> turnAtWorldEdge:

turnAtWorldEdge führt dazu, dass der Boid sich von der Kante und der Ecke entfernt. 

Ersteinmal wird getestet, ob der Boid sich überhaupt an einer der 4 Kanten befindet. Dies passiert mit der Funktion atWorldEdge aus dem Smooth Mover. Wenn dies 
Kante: 

Ecke:

![1](https://user-images.githubusercontent.com/88386035/163673705-af37f9d5-a8db-4bf8-bdb9-6d068c5b6b44.PNG)
![2](https://user-images.githubusercontent.com/88386035/163673715-bdf5ff89-f597-4d44-a29d-7b22ce7371ea.PNG)
![3](https://user-images.githubusercontent.com/88386035/163673716-98b33937-0dda-4820-90d1-8982b5fb85d9.PNG)

 
## <a name="11"></a>  Reflexion des Projekts:

Die Boids efüllen alle drei Regeln die sie bei dieser Simulation befolgen sollen. Mit mehr Zeit hätte man jetzt noch das Problem lösen können das sie sich andauernd ständig gegenseitig anpassen. Dadurch befinden sie sich immer noch sehr oft zu nah beeinander und bewegen sich dann längere Zeit auf einem Fleck. Dies könnte man noch verbessern, indem man die Boids in eine Rangfolge setzt und es so einen Anführer gibt, an den sich dann alle anpassen. Der Anführer könnte dann auch immer wieder wechseln, wie bei einen richtigen Vogelschwarm. Außerdem könnte man dann auch eventuell das Porblem lösen, dass manchmal einer sich vom Schwarm entfernt. Dadurch wird das Problem gelöst werden und die Simulation würde noch besser funktionieren. Trotzdem ist meiner Meinung nach das Projekt ganz gut gelungen, trotz meiner zuerst wenigen Kentnisse von Java. 

 
## <a name="12"></a> Stundenblog

Der Link zu meinen Stundenblog des zweiten Projekts:
https://github.com/laurasoenitz/Informartik-Projekt-2
