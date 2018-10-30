# Laborprotokoll  
Name: Sebastian Strutz  
Gruppe: 4  
Klasse: 5AHME  
Datum: Mo, 22. Oktober 2018  
Ort: Automatisierungslabor, Htbla Kaindorf  

Anwesend: Strauß, Strutz, Tuttner, Uhl, Wieser, Zitz  
Abwesend: Waltl  

# Thema: Typescript Server mit Visual Studio Code  

## Theorie
Zuerst haben wir durchbesprochen welche Datein wir in der letzten Einheit von dem [Mechatronik Server](https://www.htl-mechatronik.at/gitweb/m14/?p=sx-la1.git;a=tree;f=5AHME/g3/rest-server1/src;h=7db76bd7654e762a352c2182386aa541feca6f97;hb=a4385316c2cee94cc5348ec8be6a3fb0022d5d41) gedownloadet haben:  
* src               -> In dem Ordner stehen die typescript-Datein    
* .vscode/          -> Is diesem Ordner befinden sich 4 Konfiguration-Datein:  
  Der Vorteil an Json Dateien ist das sie Textuell sind, und somit einfach zu lesen sind.  
    * keybindings.json: In dieser Datei befinden sich verschiedene Tastenkombinationen, für die Entwicklungsumgebung.  
    * launch.json: Hier wird fest gelegt wie ein Programm gestartet wird.  
    * settings.json: In der Settings Datei befinden sich Projektspezifische Einstellungen.   
    * tasks.json: In der Tasks.json Datei stehen bestimmte Aufgaben für Programme (clean, build ..)  
    
* package.json      -> Hier befinden sich Projektinfos + Abhängigkeiten:  
    * dependencies: Abhängigkeiten  
    * devDependencies: werden mit ``` npm install ``` installiert und werden in den node_modules ordner gespeichert.
    
* package-lock.json -> In dieser Datei befinden sich die verschiedene Versionen.  

* gulpfile.json     -> Gulp ist das Übersetzungstool für Typescript. In der Guplfile steht die Stuerung der Übersetzung. Andere Übersetzungstools: make (C), ant (Netbeans), gradle (Android studio)  

* tsconfig.json     -> In dieser Jason Datei befindet sich die Konfiguration für den Transpiler. Der Transpiler wandelt das Programm von Typescript in Javascript um.  

* tslint.json       -> Der tslint ist für die Überprüfung für das Design verantwortlich, in der Datei befindet sich die Designkonfiguration.  

## Visual Studio Code
Dabei handelt es sich um eine freie IDE, welche von Microsoft angeboten wird. Vs Code hat mit ihrer Namensschwester "Visual Studio" nicht wirklich viel gemeinsam.  
### Entwicklungsumgebung
![Visual Studio](https://github.com/HTLMechatronics/m14-la1-sx/blob/strsem13/strsem13/VS%20Code.png)  

### Aufbau  
Die klassische Menüleiste wird standartgemäß ausgeblendet. Stattdessen, hat man auf der linken Seite eine Leiste in der sich 6 Icons befinden. Der erste Menüpunkt ist der File-Explorer. Am 2. Menüpunkt hat man eine Suchleiste, wo man nach bestimmten Begriffen suchen kann. Der 3. Menüpunkt bietet die Möglichekit eine Versionsverwaltung (in unserem Falle Git) einzubinden. Der vierte Punkt ist der Debugger, und der fünfte Punkt ist zur Verwaltung von Erweiterungen gedacht. Der letzte Punkt ist im linken unteren Eck der Seite, heir befinden sich die Einstellungen. Eine Besonderheit dieser Entwicklungsumgebung ist der File - Explorer. Wenn man eine Datei dauerhaft öffnen will, muss man sie mit einem Doppelklick öffnen. Wenn man eine Datei mit nur einem Klick öffnet, und dann eine neue Datei mit einem Klick öffnet, wird die vorherige automatische geschlossen.  


### Programmstart

Um Visual Studio zu öffnen gibt es 2 Möglichkeiten:  
* Entweder man startet die IDE über den File Explorer, danach muss man jedoch erst das gewünschte Projektverzeichnis öffnen.  
* Die 2 einfachere Möglichkeit wäre, man muss im Terminal sich in das gewünschte Verzeichnis navigieren (```cd Schreibtisch/Labor/rest-server1/```) und danach muss man nurmehr den Befehl: ```code .``` eingeben, und VS Code öffnet sich automatisch im gewünschten Projektverzeichnis.    

### Konfiguration

Die Konfiguration der IDE erfolgt im Wesentlichen über eine Json Datein: 
* .vscode/settings.json   
In dieser Datei können diverse Einstellungen geänderet werden, z.B: das Ausblenden von Datein und Ordnern in der IDE.  

```
{
  "files.exclude":
      {
        "**/code_modules/": true,
        "**/.vscode/": true,
        "**/package-lock.json/": true
       }
 }
 ```  
 
## Unterschied zwischen Server in java und in Typescript  
 
In Java gibt es für die Realisierung eines Servers fertige Klassen und Bibliotheken wie z.B. ServerSocket. Mit dieser Klasse kann man einfach zu arbeiten und erleichtert das erstellen eines Servers erheblich. In Javascript/Typescript hingegen gibt es keine leicht anzuwendenten Klassen wie in Java. Es gibt zwar die Klassenhttp und https, aber der umgang mit diesen erweißt sich als recht unbequem. Um die Programmierung eines Servers mit Typescript zu erleichtern greifen wir auf das Toll **Express** zurück. Dieses stellt eine komfortable Möglichkeit dar einen Server zu realisieren und bietet viele hilfreiche Funktionen im Webbereich.  

## Programm Nr.1  
Es sollte ein Programm erstellt werden, welches einen einfachen Server realisiert. Der Server soll auf einen Anfrage warten, und dann mit einem *Hallo* antworten. Um Objektorientiert zu arbeiten haben wir zusätzlich zu der **Main.ts** eine weitere Klasse **Server.ts** erstellt.  
```
import * as express from 'express';
import * as bodyParser from 'body-parser';

export class Server {

    private port: number;
    private server: express.Express;

    constructor(port: number) {
        this.port = port;
        this.server = express();

        this.server.get('*', (req, resp) => this.handleGet(req, resp));


        this.server.listen(this.port);
    }

    private handleGet(req: express.RequestHandler, resp:express.Response) {
        resp.send('Hallo');
        resp.end;
}
```  
Der Serer horcht auf den Client, wenn er dann eine Anfrage erhält, sendet der Server eine Antwort mit *Hallo* zurück.  
## Prgoramm Nr.2  
Wir haben das 1. Programm erweitert, und haben ein Switch-Case eingebaut. Bei verscheidenen Anfragen sendet nun der Server verschiedene Antworten zurück.  
```
import * as express from 'express';
import * as bodyParser from 'body-parser';

export class Server {

    private _server: express.Express;

    constructor (port: number) {
        this._server = express();

        this._server.use(bodyParser.urlencoded({extended: false}));

        // this._server.get('/student', this.handleGetStudent.bind(this));
        this._server.get('/student', (req, resp, next) => this.handleGetStudent(req, resp, next));

        this._server.listen(port);
        console.log('HTTP server gestartet auf Port ' + port);
    }

    private handleGetStudent (req: express.Request, resp: express.Response, next: express.NextFunction) {
        console.log('Abfrage');
        resp.send('Antwort');
        console.log(req.query.htlid);
        switch (req.query.htlid) {
            case 'tutram12':
            resp.json({surname: 'Tuttner', fistname: 'Raphael'});
            break;

            case 'zitkam13':
            resp.json({surname: 'Zitz', fistname: 'Karlheinz'});
            break;

            case 'strlum14':
            resp.json({surname: 'Strauß', fistname: 'Lukas'});
            break;

            default:
            resp.status(404);
            resp.end();
        }
        resp.send('Anwort: ' + req.query.htlid);
    }
}
```  
Nun konnten wir erschiedene Anfragen senden, z.B. wenn man in einem Browser folgendes eingab : ```localhost:4711/student?tutram12 ``` antwortete der Server mit:   
  
surname: Tuttner  
firstname: Raphael  
