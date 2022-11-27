# Installing spark

## Linux

Installing necessary libraries: java, scala, py4j

```shell
$ sudo apt install java
$ sudo apt install scala
$ pip install py4j
```

Check installations:
``` shell
$ java -version
openjdk version "11.0.17" 2022-10-18
OpenJDK Runtime Environment (build 11.0.17+8-post-Ubuntu-1ubuntu220.04)
OpenJDK 64-Bit Server VM (build 11.0.17+8-post-Ubuntu-1ubuntu220.04, mixed mode, sharing)

$ scala -version
Scala code runner version 2.11.12 -- Copyright 2002-2017, LAMP/EPFL
```

Installing Apache Spark:

- Access https://spark.apache.org/downloads.html
- Used configuration:
  - Spark release: 3.3.1 (Oct 25 2022)
  - Package type: Pre-built for Apache Hadoop 3.3 or later
- Download .tgz file
- Move file to /home
- Unpack it with tar -zxvf
- Set environment variable with export \$SPARK_HOME=<path_to_spark>
- Add to path:
- Run:
  - export PYTHONPATH=\$SPARK_HOME/python:\$PYTHONPATH
  - export PYSPARK_DRIVER_PYTHON="jupyter"
  - export PYSPARK_DRIVER_PYTHON_OPTS="notebook"
  - export PYSPARK_PYTHON=python3
- Update folder permission
  - chmod 777 spark-3.3.1-bin-hadoop3
  - chmod 777 spark-3.3.1-bin-hadoop3/python
  - chmod 777 spark-3.3.1-bin-hadoop3/python/pyspark
  
```shell
$ mv spark-3.3.1-bin-hadoop3.tgz ~
$ cd 
$ tar -xvzf spark-3.3.1-bin-hadoop3.tgz
$ export SPARK_HOME="/home/rodolfo/spark-3.3.1-bin-hadoop3"
$ export PATH=$SPARK_HOME:$PATH
$ export PYTHONPATH=$SPARK_HOME/python:$PYTHONPATH
$ export PYSPARK_DRIVER_PYTHON="jupyter"
$ export PYSPARK_DRIVER_PYTHON_OPTS="notebook"
$ export PYSPARK_PYTHON=python3
$ chmod 777 spark-3.3.1-bin-hadoop3
$ cd spark-3.3.1-bin-hadoop3
$ chmod 777 python
$ cd python
$ chmod 777 pyspark
```

Creating conda environment:

```shell
$ conda create --name spark_course
$ conda install python=3.8.8
$ conda install -n spark_course ipykernel --update-deps --force-reinstall
$ pip3 install findspark
```

Inside python enviroment:
```python
import findspark
findspark.init("<path_to_spark>")
import pyspark
```

Loading environment from .yml :

```shell
$ conda env create -n <env_name> --file config/spark_course.yml
```