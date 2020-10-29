# MQTT consumer

Diser Consumer verbindet sich mit dem RabittMQ (Broker) der auf dem localhost:1883 erreichbar ist.

Der consumer subscribiert sich an dem Topic home/room1 mit dem clientid subscriber1.

# Voraussetzung
RabittMQ ist installiert und laeuft auf dem port 1883

# Build
Das projekt wird mit maven gebaut (**im Powershell**)

```
cd mqttconsumer
mvn clean compile assembly:single
```

Nach dem build, es wird eine jar Datei im /target erstellt.
Der consumer liest eine Nachricht pro Sekunde von dem queue.

Um den Consumer zu starten braucht man den folgenden Befehl im Windows Powershell auszufuehren:
```
 java -jar .\target\mqttconsumer-0.0.1-SNAPSHOT-jar-with-dependencies.jar
```
wenn ein consumer Prozess startet, es wird ein queue dafuer im RabittMQ erzeugt. Das kan mann durch RabittMQ command line ueberpruefen:
```
rabbitmqctl list_queues
```

Wenn der Prozess stoppt, der queue wird aufgeraumt.
Wenn ein neuer Prozess mit dem gleichen clientid startet, der alte client wird abgebrochen.
