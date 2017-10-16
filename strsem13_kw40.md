# *Protokoll*  
## *Thema: AVR-Studio*
 Name:   Sebastian Strutz  
 Klasse: 4AHME  
 Datum: 26.09.2017  
 Anwesend: Strutz,Tuttner, Uhl, Waltl, Wieser, Zitz  
 
 ### *Mikroprozessor (µP)*
 Zuerst haben wir den prinzipiellen Aufbau einer CPU besprochen:  
 ![CPU Blockdiagramm]()  
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

