# *Protokoll*  
## *Thema: AVR-Studio*
 Name:   Sebastian Strutz  
 Klasse: 4AHME  
 Datum: 26.09.2017  
 Anwesend: Strutz,Tuttner, Uhl, Waltl, Wieser, Zitz  
 
 ### *Mikroprozessor (µP)*
 Zuerst haben wir den prinzipiellen Aufbau einer CPU besprochen:  
 ![CPU Blockdiagramm](https://github.com/strsem13/test1/blob/master/Blockdiagramm_CPU.png)  
 Befehlsablauf (Von-Neumann-Architektur):  
 * Reset -> bringt das System CPU in einen Ausgangszustand, der Befehlszähler afu den Wert 0 gesetzt, und die bits im Status-Flag werden zurückgesetzt.
 * Takt -> auch Clock gennant, bestimmt den zeitlichen Ablauf.  
 * Steuerwerk -> lädt aus dem Speicher den nächsten Befehl.  
 * Befehls-Decoder -> dekodiert den Befehl, und erzeugt einen Maschinencode und Signale für die internen Steuerleitungen.  
 * ALU -> "Arithmetic Logic Unit" -> führt die Rechenoperationen durch.
 * Programcounter -> wird aktualisiert. 
 
 
 ### *Atmel Studio*  
Atmel Studio (früher AVR-Studio) ist eine Open-Source Software zur Programmierung der AVR-Mikroprozessoren. Es basiert auf der Visual Studio Shell von Microsoft und besteht aus einer Projektverwaltung, einem Editor, einem Debugger und Werkzeugen zum Beschreiben eines Mikroprozessors.  

Mit dem Atmel Studio kann in Assembler sowie in C/C++ programmiert werden.  
Mit Atmel Studio kann man die Ausführung eines Programms auf einem Atmel-Mikrokontroller simulieren. Man erhält detaillierte Informationen über die Maschinenbefehle, die aus dem Quellcode kompiliert wurden. Außerdem hat man Einblick in die Register des Controllers.  

### *ATmega328p*  
Wir verwenden in der Schule den Mikrocontroller ATmega328p von Atmel, dadurch dieser in Atmel Studio nicht verfügbar ist, verwendeten wir den Mikrocontroller ATmega328.  
[Datenblatt-ATmega238p](http://www.atmel.com/Images/Atmel-42735-8-bit-AVR-Microcontroller-ATmega328-328P_Datasheet.pdf)  
#### **Produktdaten**  
* 32 Register  
* 16MHz Mikroprozessor  
* 32kB Flash-Speicher  
* 2kB SRAM  
* 1kB EEPROM  

#### **XYZ-Register**  
Wird benötigt um Werte zu speichern, die größer als 255 sind.  
Setzt sich zusammen aus:  
* X= 26 & 27  
* Y= 27 & 28  
* Z= 30 & 31  


