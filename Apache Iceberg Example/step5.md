Apache-Iceberg bietet des Weiteren einen historischen Verlauf. Dabei speicher Iceberg alle getätigten Aktionen und Veränderungen an der Tabelle in einer Log-Datei ab. Diese lassen sich über nachstehenden Befehl chronologisch ausgelesen und darstellen:


`spark.sql("select h.made_current_at, s.operation, h.snapshot_id, h.is_current_ancestor, s.summary['spark.app.id'] from local.db.iceberg_table.history h join local.db.iceberg_table.snapshots s on h.snapshot_id = s.snapshot_id order by made_current_at").show()`{{execute}}


Hierbei werden alle getätigten Insert-, Update- und Delete-Operationen angezeigt.
