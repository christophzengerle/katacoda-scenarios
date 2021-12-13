Durch die Funktion `spark.sql(...)` können SQL Befehle auf dem Iceberg Katalog und somit auf Tabellen in dem Verzeichnis `warehouse` angewendet werden. Nachfolgend werden beispielhaft einige SQL befehle ausgeführt.



1. Neue Beispiel-Tabelle erstellen:

    Zunächst wird eine Beispiel-Datenbank mit dem Namen `db` unter dem Verzeichnis `warehouse` angelegt. In diese Datenbank wird mit nachstehendem Befehl eine neue Tabelle `iceberg_table` erzeugt. 
    
    `spark.sql("CREATE TABLE local.db.iceberg_table (CustomerID bigint, CustomerName string, ContactName string, Address string, City string, PostalCode string, Country string) USING iceberg")`{{execute}}

    Der Parameter "USING iceberg" sorgt dafür, dass für das Management der Tabelle Apache-Iceberg mit all seinen Features verwendet wird.
    
2. Beispieldaten einfügen:
  
    Hierbei werden zwei Insert-Befehle ausgeführt, um eine Datenbewegung zu erzeugen.
  
    `spark.sql("INSERT INTO local.db.iceberg_table VALUES (1, 'White Clover Markets',    'Karl Jablonski',    '305 - 14th Ave. S. Suite 3B',    'Seattle',    '98128',    'USA'), (2,    'Wilman Kala',    'Matti Karttunen',    'Keskuskatu 45',    'Helsinki',    '21240',    'Finland'), (3,    'Wolski',    'Zbyszek',    'ul. Filtrowa 68',    'Walla',    '01-012',    'Poland'), (4, 'Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway'), (5,    'Ramesh',    'Ahmedabad 12',    'Bhopal',     'Sittensen',    '3214',    'Dheli')")`{{execute}}
   
    `spark.sql("INSERT INTO local.db.iceberg_table VALUES (6,    'Hekkan Burger',    'Gateveien 15',    'Sandnes',    'Helsinki',    '4306',    'Norway'), (7,    'Dachser', 'Georg Maier',    'Grüntenstr. 14',    'Immenstadt',    '87509',    'Germany')")`{{execute}}

3. Zeile löschen:
    
    Zum löschen einer Zeile kann folgender Befehl verwendet werden.
    
    `spark.sql("DELETE FROM local.db.iceberg_table WHERE CustomerID=3")`{{execute}}

4. Auslesen der Daten:

    Zuletzt kann die erzeugte Tabelle mit allen Daten ausgelesen werden.
    
    `spark.sql("SELECT * FROM local.db.iceberg_table ORDER BY CustomerID").show()`{{execute}}
