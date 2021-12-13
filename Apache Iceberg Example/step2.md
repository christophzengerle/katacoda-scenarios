Apache Iceberg kommt mit sogenannten Katalogen, durch welche standart SQL-Befehle, sowie DDL-Commands zur Definition von Tabellen verwendet werden können. 
<br>
Sö können auf die Tabellen beispielsweise folgende Befehle angewendet werden:

    - CREATE TABLE
    - ALTER TABLE
    - DROP TABLE
    - INSERT INTO
    - SELECT
    - UPDATE
    - ...
<br>
Als ersten Schritt wird ein neuer Katalog mit der Bezeichnung `local` erstellt. Dazu wird zunächst ein Spark-Shell gestartet und anschließend der Katalog erstellt. 

`spark-shell --packages org.apache.iceberg:iceberg-spark3-runtime:0.12.1\
    --conf spark.sql.extensions=org.apache.iceberg.spark.extensions.IcebergSparkSessionExtensions \
    --conf spark.sql.catalog.spark_catalog=org.apache.iceberg.spark.SparkSessionCatalog \
    --conf spark.sql.catalog.spark_catalog.type=hive \
    --conf spark.sql.catalog.local=org.apache.iceberg.spark.SparkCatalog \
    --conf spark.sql.catalog.local.type=hadoop \
    --conf spark.sql.catalog.local.warehouse=$PWD/warehouse
    println("Neuer Katalog angelegt")`{{execute}}
  

Durch diesen Katalog können alle Tabellen in dem Verzeichnis `warehouse` bearbeitet werden. 
