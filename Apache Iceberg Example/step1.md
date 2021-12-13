In diesem Schritt werden die benötigten Packages importiert und installiert. Apache Iceberg kann auf verschiedenen Wegen implementiert werden.
<br>
<br>
So stehen APIs für mehrere Engines wie:

- Spark
- Hive
- Flink
- PrestoDB


und für die Programmiersprachen Java und Python zur verfügung. Diese befinden sich teilweise noch in Entwicklung.

Wie bereits erwähnt, wird in diesem Katacoda-Scenario Iceberg mit Hilfe von Spark erklärt. Dazu wird ein Spark-Shell verwendet. 
<br>
<br>
Dazu müssen zunächst die Bibliotheken für Scala (Programmiersprache innerhalb Spark-Shell), sowie Apache-Spark selbst importiert und installiert werden. Beim starten dieses Kurses wurde Scala bereits installiert. 
<br>
<br>
Für die installation von Spark wird zunächst eine Datei von der Apache-Website heruntergeladen, anschließend entpackt und installiert. Dies kann über folgenden Code ausgeführt werden: 
<br>

`wget https://downloads.apache.org/spark/spark-3.1.2/spark-3.1.2-bin-hadoop2.7.tgz
tar xvf spark-*
sudo mv spark-3.1.2-bin-hadoop2.7 /opt/spark
echo "export SPARK_HOME=/opt/spark" >> ~/.profile
echo "export PATH=$PATH:/opt/spark/bin:/opt/spark/sbin" >> ~/.profile
echo "export PYSPARK_PYTHON=/usr/bin/python3" >> ~/.profile
source ~/.profile
clear
: Apache-Spark erfolgreich installiert`{{execute}}

   
   
