<img src="https://github.com/kolossos/Trees-in-QField/raw/master/images/Screenshot_20200501-213206_QField.jpg" width="251" title="Bäume nach Art">  <img src="https://github.com/kolossos/Trees-in-QField/blob/master/images/Screenshot_20200501-213228_QField.jpg" width="251" title="Bäume nach Alter">  <img src="https://github.com/kolossos/Trees-in-QField/raw/master/images/Screenshot_20200501-213348_QField.jpg" width="251" title="editierbare Details als Formular">

Dieses Projekt soll die mobile Benutzung der als OpenData verfügbaren Baumdaten von Städten vereinfachen. 
Sichtbar gemacht werden unter anderem die Baumart und das Alter(Pflanzjahr) für jeden Baum. Die App soll es auch ermöglichen unterwegs Daten zu editieren. So können von den Nutzern z.B. die Zustände von Baumen erfasst werden. 

Dazu wird mobil die Android-App [QField](https://qfield.org/) genutzt. Für die Datenaufbereitung und -auswertung kann auf dem Desktop das Programm QGIS genutzt werden, die Nutzung dieser sehr komplexen GIS-Anwendung ist aber kein Zwang für die reine mobile Nutzung.

Für die Nutzung installierst du dir die oben genannte App QField aus dem Playstore (Für Apple-Geräte gibt es keine QField Version, [Input-App](https://github.com/lutraconsulting/input) wäre vielleicht eine Alternative).

Dann gehst du in den Github-Ordner deiner Stadt und lädst dir zwei Dateien auf dein mobiles Gerät. Es empfielt sich die Nutzung eines Dateimanagers auf deinem Android-Gerät.
Eine Anleitung dafür gibt es [hier](https://qfield.org/docs/project-management/project-selection.html).

Bei den beiden Dateien handelt es sich erstens um eine [QGIS](https://qgis.org)-Projektdatei (*.qgs) diese enthält quasi die Formatierungsangaben wie die vers. Layer aussehen sollen. Die zweite Datei ist eine [GeoPackage](https://de.wikipedia.org/wiki/GeoPackage)-Datei (*.gpkg) diese enthält die Geodaten in einer räumlich indizierten SQLite-Datenbank.  
 
Auch wenn QField recht selbst erklärend ist gibt es eine kleine Anleitung [hier](https://qfield.org/docs/user-guide/index.html).
In den Formularen zu den einzelnen Bäumen kann man freigegeben Felder, wie den Baumzustand, selbst editieren. Die Änderungen bleiben dann zunächst lokal auf dem Gerät gespeichert. 

Hinweis: Unterwegs wird für den Bäumelayer kein Datenvolumen verbraucht, allerdings benötigt die OSM-Hintergrundkarte einen Datentransfer.

Die Fragen einer dezentralen Synchronisierung der von vielen Leuten unterwegs erfassten Daten ist noch offen. Aufgrund des verwendeten SQL-Lite Standards sollte es aber Möglichkeiten geben. 

## Motivation
Als Motivation für ein ähnliches Projekt kann dienen, dass die Opendata-Portale der Stadt auch Karten anbieten, dabei gibt es aber keine farbliche Differenzierung nach vers. Objekteigenschaften. Ebenso ist die Mobile Nutzung auf kleinen Handy-Displays bescheiden. Dieses soll keine Kritik an den Opendataportalen sein, diese sollen genau das, die Daten frei und maschinenlesbar anbieten. (Nebenbei gesagt, ist es ein riesen Fortschritt, dass die Städte jetzt solche Portale haben. Der Druck von Projekten wie OpenStreetMap hat da wohl auch geholfen. Noch schöner wäre es natürlich noch wenn die OpenData in Opensource-Protalen erscheinen würden, aber hauptsache man bekommt die Daten in vernünftigen, freien Formaten zum Download.)      
 
## Technische Hinweise für eigene Karten 
Wenn man sich dafür interessiert eigene Karten für QField zu erzeugen, sollte man sich zunächst mit QGIS etwas vertraut machen und am besten natürlich die Qfield-Doku lesen. Auf der anderen Seite ist das ganze Projekt ohne eine einzige Zeile eigenen Code entstanden. 

Eine existierende Karte kann den Einstieg in QGIS dabei erleichtern. Es gilt zuerst die Geodaten die als OpenData von der Stadt angeboten werden herunterzuladen und z.B. die GEOJSON-Datei in QGIS als Vectorlayer einzuladen. Da eine mittlere Großstadt schnell 10.000 Baume besitzt ist die Nutzung der GEOJSON Datei zwar auf einem leistungsstarken Desktop problemlos möglich aber auf einem mobilen Gerät nicht performant. Deshalb sollte in QGIS der GEOJSON-Layer als GeoPackage gespeichert werden (rechtsklick->Exportieren/Objekt speichern als) und anschließend erneut eingelesen werden. 

In QGIS können Daten sehr komfortabel nach einer Kategorisierung formatiert werden. Es können zufällige Farben genutzt werden, eine Farbskala oder eigene Farbzuordnungen. Bei dem Attributformular ist es sinnvoll viele Parameter auf nicht änderbar zu setzen und nur bei neuen Parametern wie dem Zustand diese änderbar zu machen. Wenn man mit dem ersten Layer zufrieden ist dupliziert man ihn und ändert die Formatierung. Am Ende schaltet man die Layer einzeln mit der Hintergrundkarte an und definiert noch Kartenthemen. Wenn man fertig ist, kann man beide Dateien auf sein mobiles Gerät übertragen, testen und ggf. veröffentlichen. 

Die Fragen einer dezentralen Synchronisierung der von vielen Leuten unterwegs erfassten Daten ist noch offen. Aufgrund des verwendeten SQL-Lite Standards sollte es aber Möglichkeiten geben. 
