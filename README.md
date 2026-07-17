# ClusterIT!
ClusterIT! ist eine interaktive Shiny-Anwendung, die im Rahmen des BiMi-Projekts im Sommersemester 2026 erstellt wurde.

## Autorinnen und Autoren

- Wiktoria Cholewa
- Rosina Röckseisen
- Saliha Altan
- Johanna Kleidorfer
- Alisa Pesteritz
- Adrika Narasimhan
- Andreas Kasarinow
- Dominik Falk

## Anforderungen

ClusterIT! setzt R 4.1.0 oder neuer voraus. Das Paket enthält kompilierten Rcpp Code. 
Eine Installation des Source-Pakets auf Windows kann daher die Installation von Rtools erforderlich machen.

Alle benötigten R-Pakete sind in der ```DESCRIPTION-Datei``` gelistet. 
Für die schnelle Ausführung folgt hier ein Installationsbefehl für alle:
```
install.packages(c(
  "shiny", "htmltools", "dipaus", "shinydashboard", "jsonlite", "shinyFeedback",
  "shinyjs", "bslib", "bsicons", "shinyBS", "RSQLite", "DBI", "plotly", "RColorBrewer",
  "colorspace", "ggplot2", "reshape2", "viridis", "stringr", "qpdf"
))
```


## Installation

Das Paket ```bimiProjektPaket_1.0.0.tar.gz``` in ein geeignetes Verzeichnis ablegen und folgendes ausführen: 

```
install.packages(
  "path/to/bimiProjektPaket_1.0.0.tar.gz",
  repos = NULL,
  type = "source"
)
```

Hierbei sollte statt ```path/to/``` das eigentliche Verzeichnis in dem das Source-Paket abelegt wurde angegeben werden.

Alternativ, falls Abhängigkeiten fehlen:

```
remotes::install_local( 
  "path/to/bimiProjektPaket_1.0.0.tar.gz", 
  dependencies = TRUE )
```

## Anwendung ausführen

Nach der Installation:

```
library(bimiProjektPaket)

bimiProjektPaket::run_app()
```
Die Anwendung sollte sich im Shiny Viewer öffnen. Alternativ kann sie im Webbrowser geöffnet werden.

### Sonderfall Datenbank
Dieses Paket liefert eine zuvor erstellte Gendatenbank mit. Das R-Skript, das zu diesem Zweck genutzt wurde, befindet sich unter ```inst/extdata/setupDatabase.R```. Es wird als einziges nicht ausgeführt.

## Workflow

1. Datei hochladen (nur CSV-Format zulässig)
2. Bei Bedarf über NA-Werte entscheiden
3. Einen oder mehrere Pathways auswählen
4. Weiter zu der Parameterauswahl 
5. Linkage-Verfahren, Distanzfunktion, Normalisierungsmethode und Farbpalette auswählen
6. Auf Run Cluster Analysis drücken
7. Grafikpanel und Dendrogramme reviewen
8. Um einen Analysereport zu erstellen, auf PDF exportieren drücken

## Inkludierte Test-Datensätze

Das Paket enthält einige modifizierte Datensätze, die primär zum Testen verwendet wurden. Sie sind installiert im Verzeichnis inst/extdata/.

Um das Verzeichnis in R zu finden und alle CSV-Dateien darin zu listen: 

```
system.file( "extdata", package = "bimiProjektPaket" )
list.files( system.file( "extdata", package = "bimiProjektPaket" ), pattern = "\\.csv$", full.names = TRUE )
```
Um diese Datensätze in der Anwendung nutzen zu können, müssen sie in das aktuelle Arbeitsverzeichnis kopiert werden. 

```
example_files <- list.files( system.file( "extdata", package = "bimiProjektPaket" ), 
                             pattern = "\\.csv$", full.names = TRUE ) 

file.copy( example_files[1], getwd(), overwrite = TRUE )
```
Die so kopierten Datensätze können anschließend in der Anwendung ausgewählt und verarbeitet werden.

## Entwicklung

Dieses Paket wurde mit 

```
devtools::check()
devtools::build()
```
geprüft und erstellt. Die ```NAMESPACE``` und ```DESCRIPTION``` Dateien wurden manuell erstellt.
Das erstellte Paket wurde in einer separaten R-Session installiert und getestet.
