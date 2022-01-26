# LA1550 Robocode | Mein eigener Roboter: Jynx
### Aufagbenstellung
----
Wir hatten in dem Lernattelier die Aufgabe mit der Applikation Robocode einen eigenen Junior Roboter zu erstellen. Mit diesem Portfolio stelle ich die Taktik und das Verhalten meines Roboters vor.
### Ziele
---
1. . Strategie meines Roboters meinem Leser verständlich zu machen

### Inhalt 1 | Die Strategie
--- 
Mein Roboter Jynx hat eine einfache aber teilweise auch sehr effektive Strategie. Er versucht so viel Schaden wie möglich zu machen indem er den Feind trackt und ihn beschiesst. Dabei versucht er um den Gegner zu "straven" um auzch potenziellen Schaden zu vermeiden.
Ich habe hier die wichtigsten elemente meines Roboters unten aufgezählt.
#### Jynx's Bewegungsmuster
```java
public void run() {
		setColors(orange, blue, white, yellow, black);
		
		Random rnd = new Random();//Zufallsgenerator
		turnTo(rnd.nextInt(1, 360)); //Drehung laut Zufallsgenerierte Richtung
		ahead(40); // Bewegung nach Vorne
		
		while(true) //Schleife {
            //Bewegungen
			ahead(80);
			turnGunLeft(60);
			ahead(60);
		}
	}
```
Das Bewegungsmuster von Jynx's besitzt kein richtiges "Muster" da ich die Beweungung von Jynx mit einem Zufallsgenerator geschrieben habe. Dadurch bewegt sich der Roboter immer anders, was es den Gegnern schwer macht ihn zu treffen.
#### Jynx's Tracking
```java
turnTo(rnd.nextInt(1, 360)); //Drehung  der Waffe laut Zufallsgenerierte Richtung

public void onScannedRobot() {
	int distance = scannedDistance;
	turnGunTo(scannedAngle);
```
Das Tracking ist zeimlich ersichtlich. Jynx dreht seine Waffe in eine Zufallsgenerierte Richtung und Sobald er ein Opfer gefunden hat, dreht sich seine Waffe genau auf das getrackte Ziel und befeuert es konstant.
#### Jynx's Angriff
```java
turnGunTo(scannedAngle);
		if (scannedDistance < 200)
		{
			fire(3);
		}
		else
		{
			fire(1);
		}
```
Der Angriiff von meinem Roboter ist zielich aggressiv. Er hat mithilfe seines Trackings nun ein Ziem im Visier und befeurt es nun. Dabei habe ich 2 einfache Befehle gegeben: 
1. Wenn das Ziel weniger als 200 Pixel entfernt ist, soll er mit strakem Geschoss feuern.
2. Wenn das Ziel mehr ale 200 Pixel entfernt ist, soll er mit normalen Projektilen schiessen

### Inhalt 2 | Mein Vollständiger Code
---

```java
package DelvecchioNico;
import robocode.*;
import java.util.Random;

/**
 * Jynx - a robot by (Delvecchio Nico)
 */
public class Jynx extends JuniorRobot
{	
	int Start = 0;
	/**
	 * run: Jynx's default behavior
	 */
	public void run() {

		setColors(orange, blue, white, yellow, black);
		
		Random rnd = new Random();
		turnTo(rnd.nextInt(1, 360));
		ahead(40);
		// Robot main loop
		while(true) {

			ahead(80);
			turnGunLeft(60);
			ahead(60);
		}
	}

	/**
	 * onScannedRobot: What to do when you see another robot
	 */
	public void onScannedRobot() {
	int distance = scannedDistance;
	turnGunTo(scannedAngle);
		if (scannedDistance < 200)
		{
			fire(3);
		}
		else
		{
			fire(1);
		}
		// Replace the next line with any behavior you would like
		
	}
	

	/**
	 * onHitByBullet: What to do when you're hit by a bullet
	 */
	public void onHitByBullet() {
		back(10);
	}
	
	/**
	 * onHitWall: What to do when you hit a wall
	 */
	public void onHitWall() {
		// Replace the next line with any behavior you would like
		Start = 1;
		back(20);
		turnTo(90);
	}	
}

```
Das hier ist mein vollständiger Code von Jynx.


### Inhalt 3 | Video zu Jynx
Hier ist ein Video wie mein Roboter sich verhält und wie er im Vergelich zu allen anderen Robotern steht.
[![Watch the video](https://cdn.discordapp.com/attachments/872223445889450044/935839218188566528/csm_robocode_feld_b316433185.png)](https://www.youtube.com/watch?v=sm9BlHS-cPs)

[Video zu Jynx](https://www.youtube.com/watch?v=sm9BlHS-cPs)


### Verifikation & Reflexion

#### Verifikation
Ziel 1:
Ich habe mein Portfolio 2 von meinen Mitschülern gezeigt und sie hatten mir Bestätigt, dass mein Portfolio verständlich ist.

#### Reflexion
Ich habe zu beginn einige Probleme mit Robocode gehabt doch das hat sich in mit der Zeit geändert. Ebenfalls war es für zuerst mich schwierig in eine andere Sprache zu wechseln(von C# zu Java). Alles in allem war es ein Projekt was für mich in Ordnung war, jedoch gefiel mir die Applikation Robocode nicht ganz.
Ich hatte mich teilweise ablenken lassen, da ich den Umgang mit dem Source Editor von Robocode nicht mochte. Ich habe dann als Lösung dazu einfach Visual Studio Code verwendet um ein Syntax-Highlighting zu erhalten.

##### VBV:
- mich schneller an den Sprachwechsel gewöhnen.
- nicht ablenken lassen auch wen mir was nicht gefällt.
- Tips und Tricks zu den Applikationen holen um den Umgang zu vereinfachen.








