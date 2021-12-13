# Apache Iceberg
![Iceberg-logo](https://user-images.githubusercontent.com/63715581/143933082-92a4b82d-6629-46c5-97ea-c767a12a6000.png)

Tabellenformate gewinnen im Big-Data Umfeld immer mehr an Aufmerksamkeit. Gerade Projekte wie Apache Iceberg, Apache Hudi und Delta Lake werden aktiv weiterentwickelt und führen immer mehr zur Obsoleszenz von bestehenden Technologien. 
<br>
<br>
Apache Iceberg ist ein neues open source Tabellenformat zur Speicherung von großen, sich langsam-verändernden Tabellendaten. 
Konkret ist die Aufgabe solcher Tabellenformate zu bestimmen, wie Dateien in einer Tabelle gespeichert, verwaltet, verändert und nachverfolgt werden. Dadurch werden die Rahmenbedingungen für die einzelnen Dateien einer Tabelle, wie z.B. Parquet-Files gelegt.
<br>
<br>
Im Vergleich zu bestehenden Data-Lake-Implementierungen, bietet Apache Iceberg von Grund auf Cloud-Support. Weitere Vorteile sind beispielsweise Verbesserungen bei der Datenkonsistenz oder der Effizienz und Leistungsfähigkeit im Umgang mit großen Datenmengen und bieten neue Features wie ACID-Transaktionen oder sogenannte "time travel" und "point-in-time queries", sowie den Support für uptodate Frameworks, wie z.B. Apache Spark. 
<br>
<br>
Dieses Katacoda-Scenario erklärt die Grundlagen für die Verwendung von Apache Iceberg in Kombination mit Spark. 
<br>
<br>
Vorgehensweise:
- Erstellung einer einfachen Beispiel-Tabelle (Tabelle anlegen, Datensätze einfügen, etc.)
- Aufbau Iceberg-Tabelle
- Snapshot-Technologie (Time-Travel)
- Tabellen-Historie

<br>
<br>
Quellen: http://iceberg.apache.org/, https://medium.com/expedia-group-tech/a-short-introduction-to-apache-iceberg-d34f628b6799, https://blog.bigdataboutique.com/2019/06/the-apache-iceberg-table-format-is-the-bright-future-of-data-warehousing-huia9q

