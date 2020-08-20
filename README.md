# Bachelor-Project-vyo
Bachelor Project called vyo by Hannah Ackermann and Jasmin Julia Falk

vyo ist ein System, das Menschen, die aufgrund von Stress vermehrt (ungesunde) Nahrungsmittel konsumieren, dabei unterstützt ein gesundes Essverhalten zu entwickeln. Durch das Ausführen von vorgeschlagenen Aktivitäten, lernen Nutzer*innen ihre negativen Emotionen zu regulieren.

## Technischer Ablauf
Für den technischen Prototyp sind drei Hauptkomponenten erforderlich. Ein Arduino Uno, ein 1,5-Zoll-OLED-Display und ein MPR121-Touchsensor.

### Code
Der Code besteht aus zwei Dateien. In der Hauptdatei werden zu Beginn die notwendigen Bibliotheken aufgerufen. Danach werden die Variablen aus der externen Datei aufgerufen. In der externen Datei werden die selbst entworfenen Icons als Arduino lesbarer Code (Byte Arrays) festgehalten. In der Hauptdatei werden weiter die Dimensionen des Displays (128x128 Pixel) definiert. Daraufhin wird
die Anzahl der verwendeten Elektroden (in diesem Fall 2) und die Anschlüsse des Displays mit den Pins des Arduinos festgelegt. Im Code werden anschließend die für die Icons notwendigen Farben erfasst.
Nachdem mithilfe des Datentyps long eine Variable mit erweiterter Größe für die Nummernspeicherung und eine Zahl innerhalb der vorgegebenen Zufallsgenerierung definiert wurde, wird die serielle Verbindung gestartet. Über die serielle Schnittstelle werden Daten gesendet und empfangen. Die Baudrate bestimmt die Geschwindigkeit der Verbindung. Beim einfachen übertragen von Kommandos reicht eine Baudrate von 9600 Bit/s. Bit ist die Maßeinheit für den Informationsgehalt.
Über den seriellen Monitor der Arduino IDE lassen sich Variableninhalte oder Texte aus- geben. Durch den Serial.println Befehls wird eine Zeichenkette (String) mit einem Zeilenumbruch übermittelt.
Der Pseudozufallsgenerator (ein Zufallsgenerator, der ohne physikalische Messungen auskommt) verarbeitet einen Startwert, auch Seed genannt, zu einer beliebig langen Zufalls- folge. Damit sich die Folge an Werten in einer Sequenz unterscheidet, wird im analogRead() ein nicht angeschlossener Pin (im Prototyp ist das der Pin 0) definiert.
Anschließend wird der MPR121 Touchsen- sor mit der Adresse 0x5a initialisiert. Ist die Adresse des I2C Gerätes nicht bekannt, lässt sich diese leicht durch eine Code Abfrage er- mitteln. I2C ist ein serielles Kommunikations- protokoll, in dem die Daten über eine einzige
Leitung übertragen werden. Darauffolgend werden der Interrupt Pin und die Schwellen- werte bei Berührung und Nicht-Berührung festgelegt. Zudem müssen die Touch Daten bei jedem Start aktualisiert werden, damit die Messwerte immer auf dem neuesten Stand sind.
Im nächsten Schritt folgt die Aktivierung
des Displays. Zu Beginn wird ein schwarzer Hintergrund ausgegeben, auf den ein Start Icon folgt. Nach 5 Sekunden gibt das Display erneut einen schwarzen Hintergrund aus.
Im Loop wird eine Bedingung aufgestellt,
die beinhaltet, dass Berührungsmessungen immer wieder aktualisiert werden. Daraufhin soll der Sensor, wenn er an den Stellen 6, 5 oder 4 berührt wird, eine zufällige Zahl von 0 bis 12 ausgeben. Anschließend wird im Code festgehalten, dass korrigiert Werte, die dem vorherigen Wert entsprechen, um eins nach oben verschoben werden.
Abschließend wird jeder Zufallszahl eine Grafik zugeordnet. Wichtig zu erwähnen ist, dass auf die genau Größe der Pixelangaben geachtet werden muss. Wenn beispielsweise eine Grafik (in Code umgewandelt) 100x100 Pixel aufweist, muss diese Größe exakt in der Ausgabe der Grafik definiert werden, sodass die Grafiken nicht verpixelt ausgegegeben werden.
