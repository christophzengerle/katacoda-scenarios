Ein besonderes Feature von Apache-Iceberg ist die time-travel-Funktion. <br>
Diese "Zeitreisen" werden durch die `Snapshot-Technologie` von Iceberg möglich. Iceberg speichert den Stand (eine Abbildung oder Snapshot) nach einer Änderung an der Tabelle in einer Log-Datei ab. Dies erlaubt einen einfachen Rollback zu einem älteren Stand, reproduzierbare Abfragen auf den gleichen Tabellen-Snapshots oder einen einfach nachzufollziehenden Verlauf der getätigten Änderungen an der Tabelle zu erstellen. Durch diese Snapshot-Technologie können beispielsweise verschiedene Snapshots einer Tabelle einfach miteinander verglichen werden. (siehe Buckenhofer, Skript Datenqualität, S.34)

1. Snpashots anzeigen:

    Zum anzeigen der vorhandenen Snapshots einer Tabelle wird folgender Befehl verwendet:
    
    `spark.sql("SELECT * FROM local.db.iceberg_table.snapshots").show()`{{execute}}

2. Abruf eines bestimmten Snapshots:

    Wenn man einen bestimmten Stand einer Tabelle abrufen möchte, gibt es dazu zwei Möglichkeiten. Einerseits kann über die Funktion `.option("snapshot-id", Snapshot_Id)` ein bestimmter Tabellenstand nach der Snapshot-ID gesucht werden. Zum Anderen kann ein Abbild zu einem bestimmten Timestamp abgefragt werden. 
    In folgendem Beispiel wird der Stand über die Snapshot-ID gesucht. Über nachfolgenden Befehl, werden zunächst alle Snapshot-IDs abgefragt, anschließend der älteste Stand ermittelt und die Tabelle zum Stand der ersten Änderung ausgegeben. 
    
   `val snapshot_ids = spark.sql("SELECT snapshot_id FROM local.db.iceberg_table.snapshots")
    val firstSnapshotID = snapshot_ids.first()(0).asInstanceOf[Number].longValue
     spark.read.option("snapshot-id", firstSnapshotID).format("iceberg").load("warehouse/db/iceberg_table").show()`{{execute}}
    
   Die ausgegebene Tabelle ist der älteste Stand nach dem ersten hinzufügen von Daten.



Durch diese Snapshot-Technologie können sehr einfach Tabellenveränderungen nachvollzogen und verlichen werden oder ein Rollback zu einem früheren Zeitpunkt durchgeführt werden.
