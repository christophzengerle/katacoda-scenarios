Durch die Funktion `spark.sql(...)` können SQL Befehle auf dem Iceberg Katalog und somit auf Tabellen in dem Verzeichnis `warehouse` angewendet werden. Nachfolgend werden beispielhaft einige SQL befehle ausgeführt.



1. Neue Beispiel-Tabelle erstellen:

    Zunächst wird eine Beispiel-Datenbank mit dem Namen `db` unter dem Verzeichnis `warehouse` angelegt. In diese Datenbank wird mit nachstehendem Befehl eine neue Tabelle `iceberg_table` erzeugt. 
    
    `spark.sql("CREATE TABLE local.db.iceberg_table (customer_id bigint, name string, gender string, street string, number string, plz string, city string) USING iceberg")`{{execute}}

    Der Parameter "USING iceberg" sorgt dafür, dass für das Management der Tabelle Apache-Iceberg mit all seinen Features verwendet wird.
    
2. Beispieldaten einfügen:
  
    Hierbei werden zwei Insert-Befehle ausgeführt, um eine Datenbewegung zu erzeugen.
  
    `spark.sql("INSERT INTO local.db.iceberg_table VALUES (1, 'Monika Kranz',	'female',	'Am Postpark',	'5',	'72250',	'Freudenstadt'), (2,	'Erich Ziegler',	'diverse',	'Schloáberg',	'92',	'12121',	'Aufseá'), (3,	'Scharl, Hans',	'',	'Dr.-Martin-Luther-Straáe',	'1',	'92708',	'Mantel'), (4,	'Ralf Simon',	'male',	'Lange Str.',	'63',	'27711',	'Osterholz-Scharmbeck'), (5,	'Stein, Ursula',	'female',	'Kolberger Straáe',	'21',	'27419',	'Sittensen')")`{{execute}}
   
    `spark.sql("INSERT INTO local.db.iceberg_table VALUES (6,	'Hannelore Bamminger',	'',	'Mangfallstraáe',	'7A',	'83569',	'Vogtareuth'), (7,	'Rainer Schmid',	'male',	'Kapellenleite',	'6',	'99999',	'Huglfing'), (8,	'Ursula Stein',	'female',	'Kolberger Straáe',	'21',	'27419',	'Sittensen')")`{{execute}}

3. Zeile löschen:
    
    Zum löschen einer Zeile kann folgender Befehl verwendet werden.
    
    `spark.sql("DELETE FROM local.db.iceberg_table WHERE customer_id=3")`{{execute}}

4. Auslesen der Daten:

    Zuletzt kann die erzeugte Tabelle mit allen Daten ausgelesen werden.
    
    `spark.sql("SELECT * FROM local.db.iceberg_table ORDER BY customer_id").show()`{{execute}}
