# rimfrost-template-regel-subprocess

Det här är ett mallprojekt för en regelprocess i rimfrost-projektet.

En regelprocess är en kogito-subprocess som används av en flödesprocess och som via kafka meddelanden kommunicerar
med en mikrotjänst för en regel.

För övergripande flödesprocesser, se [template projekt för regelprocess](https://github.com/Forsakringskassan/rimfrost-template-process).

För maskinella regler, se [template projekt för maskinell regel](https://github.com/Forsakringskassan/rimfrost-template-regel-maskinell/).

För manuella regler, se [template projekt för manuell regel](https://github.com/Forsakringskassan/rimfrost-template-regel-manuell/).

## Minimum konfiguration av utvecklingsmiljö

Projektet förväntar sig att jdk (java version 21 eller högre)
och maven är installerat på systemet samt att
miljövariablerna **GITHUB_ACTOR** och **GITHUB_TOKEN** är
konfigurerade.

Notera att det GITHUB token som används förväntas ha repo access
konfigurerad för att kunna hämta vissa projektberoenden.

## Anpassningar som behöver utföras i projektet

Följande är en lista av anpassningar som behöver utföras för att 
skapa en ny regelprocess med denna template. Notera att vissa av
dess punkter även har märkts upp med TODO i relevanta filer.

1. Uppdatera det inkommande kafka-topic som finns i application.properties
2. Uppdatera det utgående kafka-topic som finns i application.properties
3. Uppdatera det ID som finns i template_regel.bpmn
4. Uppdatera de mellanliggande meddelanden som finns template_regel.bpmn att använda samma kafka topics som angavs i application.properties
5. Byt namn på template_regel.bpmn till lämpligt namn för regeln
6. Uppdatera artifactId i pom.xml

## Bygg artefakt för lokal testning

`./mvnw -s settings.xml clean package`

## Bygg artefakt och installera till lokal maven cache

`./mvnw -s settings.xml clean install`

## Github workflows

Två github workflows är inkluderade i projektet, bundle-maven-lib-ci och bundle-maven-lib-release.

bundle-maven-lib-release skapar som del av sitt flöde en artefakt.
Den publiceras till försäkringskassans [repository](https://github.com/Forsakringskassan/repository).

## Exempel implementation
Se [rimfrost-regel-rtf-maskinell-subprocess](https://github.com/Forsakringskassan/rimfrost-regel-rtf-maskinell-subprocess) för en färdig implementation av en regelprocess.
