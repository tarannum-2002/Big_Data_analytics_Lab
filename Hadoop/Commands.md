hduser@bmsce-OptiPlex-3060:~/Desktop$ start-all.sh
This script is Deprecated. Instead use start-dfs.sh and start-yarn.sh
23/05/11 14:03:45 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Starting namenodes on [localhost]
hduser@localhost's password: 
localhost: Permission denied, please try again.
hduser@localhost's password: 
localhost: starting namenode, logging to /usr/local/hadoop/logs/hadoop-hduser-namenode-bmsce-OptiPlex-3060.out
hduser@localhost's password: 
localhost: starting datanode, logging to /usr/local/hadoop/logs/hadoop-hduser-datanode-bmsce-OptiPlex-3060.out
Starting secondary namenodes [0.0.0.0]
hduser@0.0.0.0's password: 
0.0.0.0: starting secondarynamenode, logging to /usr/local/hadoop/logs/hadoop-hduser-secondarynamenode-bmsce-OptiPlex-3060.out
23/05/11 14:04:52 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
starting yarn daemons
starting resourcemanager, logging to /usr/local/hadoop/logs/yarn-hduser-resourcemanager-bmsce-OptiPlex-3060.out
hduser@localhost's password: 
localhost: starting nodemanager, logging to /usr/local/hadoop/logs/yarn-hduser-nodemanager-bmsce-OptiPlex-3060.out
hduser@bmsce-OptiPlex-3060:~/Desktop$ jps
2689 NameNode
3864 Jps
3738 NodeManager
3245 SecondaryNameNode
3023 DataNode
3407 ResourceManager
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs defs mkdir /tarannum
Error: Could not find or load main class defs
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs mkdir /tarannum
mkdir: Unknown command
Did you mean -mkdir?  This command begins with a dash.
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -mkdir /tarannum
23/05/11 14:06:26 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -mkdir /tarannum
23/05/11 14:06:35 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
mkdir: `/tarannum': File exists
hduser@bmsce-OptiPlex-3060:~/Desktop$ hadoop fs -ls /
23/05/11 14:07:15 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Found 4 items
-rw-r--r--   1 hduser supergroup          6 2023-05-08 10:38 /def.txt
drwxr-xr-x   - hduser supergroup          0 2023-05-08 10:41 /firstDir
drwxr-xr-x   - hduser supergroup          0 2023-05-08 10:36 /new_dir
drwxr-xr-x   - hduser supergroup          0 2023-05-11 14:06 /tarannum
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs pwd
pwd: Unknown command
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs /
/: Unknown command
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -put /home/hduser/Desktop/Welcome.txt /tarannum/WC.txt
23/05/11 14:11:38 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
put: `/home/hduser/Desktop/Welcome.txt': No such file or directory
hduser@bmsce-OptiPlex-3060:~/Desktop$ hadoop fs -ls /home
23/05/11 14:12:08 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
ls: `/home': No such file or directory
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -put /home/hduser/Desktop/abc.txt /tarannum/WC.txt
23/05/11 14:16:07 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
put: `/home/hduser/Desktop/abc.txt': No such file or directory
hduser@bmsce-OptiPlex-3060:~/Desktop$ hadoop fs -ls /
23/05/11 14:17:11 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Found 4 items
-rw-r--r--   1 hduser supergroup          6 2023-05-08 10:38 /def.txt
drwxr-xr-x   - hduser supergroup          0 2023-05-08 10:41 /firstDir
drwxr-xr-x   - hduser supergroup          0 2023-05-08 10:36 /new_dir
drwxr-xr-x   - hduser supergroup          0 2023-05-11 14:06 /tarannum
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -put /home/hduser/Desktop/Welcome.txt /home/tarannum/WC.txt
23/05/11 14:20:44 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
put: `/home/tarannum/WC.txt': No such file or directory
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -put /home/hduser/Desktop/Welcome.txt /home/tarannum
23/05/11 14:20:52 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
put: `/home/tarannum': No such file or directory
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -put /home/hduser/Desktop/Welcome.txt /home/hduser/tarannum
23/05/11 14:21:08 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
put: `/home/hduser/tarannum': No such file or directory
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -put /home/hduser/Desktop/Welcome.txt /home/hduser
23/05/11 14:21:24 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
put: `/home/hduser': No such file or directory
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -put /home/hduser/Desktop/Welcome.txt /abc/WC.txt
23/05/11 14:22:25 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
put: `/abc/WC.txt': No such file or directory
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -put /home/hduser/Desktop/Welcome.txt /tarannum/WC.txt
23/05/11 14:24:19 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -put /home/hduser/Desktop/Welcome.txt /tarannum/WC.txt
23/05/11 14:24:34 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
put: `/tarannum/WC.txt': File exists
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -copyFromLocal /home/hduser/Desktop/Welcome.txt /tarannum/WC.txt
23/05/11 14:26:14 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
copyFromLocal: `/tarannum/WC.txt': File exists
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -copyFromLocal /home/hduser/Desktop/Welcome.txt /tarannum/WC2.txt
23/05/11 14:26:25 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -copyFromLocal /home/hduser/Desktop/Welcome.txt /tarannum/WC2.txt
23/05/11 14:26:36 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
copyFromLocal: `/tarannum/WC2.txt': File exists
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -get /tarannum/WC.txt /home/hduser/Downloads/WWC.txt
23/05/11 14:30:36 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs ls /tarannum
ls: Unknown command
Did you mean -ls?  This command begins with a dash.
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -ls /tarannum
23/05/11 14:31:38 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Found 2 items
-rw-r--r--   1 hduser supergroup         27 2023-05-11 14:24 /tarannum/WC.txt
-rw-r--r--   1 hduser supergroup         27 2023-05-11 14:26 /tarannum/WC2.txt
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -getmerge /tarannum/WC.txt /tarannum/WC2.txt /home/hduser/Downloads/Merge.txt
23/05/11 14:33:39 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
hduser@bmsce-OptiPlex-3060:~/Desktop$ hadoop fs -getfacl /tarannum/
23/05/11 14:34:22 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
# file: /tarannum
# owner: hduser
# group: supergroup
user::rwx
group::r-x
other::r-x

hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -copyToLocal /tarannum/WC.txt /home/hduser/Desktop
23/05/11 14:35:20 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
hduser@bmsce-OptiPlex-3060:~/Desktop$ hdfs dfs -cat /tarannum/WC.txt
23/05/11 14:35:54 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Hello world hello world
hduser@bmsce-OptiPlex-3060:~/Desktop$ hadoop fs -mv /tarannum /FFF
23/05/11 14:36:40 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
hduser@bmsce-OptiPlex-3060:~/Desktop$ hadoop fs -ls /FFF
23/05/11 14:36:53 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Found 2 items
-rw-r--r--   1 hduser supergroup         27 2023-05-11 14:24 /FFF/WC.txt
-rw-r--r--   1 hduser supergroup         27 2023-05-11 14:26 /FFF/WC2.txt
hduser@bmsce-OptiPlex-3060:~/Desktop$ hadoop fs -cp /CSE /LLL
23/05/11 14:37:52 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
cp: `/CSE': No such file or directory
hduser@bmsce-OptiPlex-3060:~/Desktop$ hadoop fs -cp /tarannum /LLL
23/05/11 14:38:08 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
cp: `/tarannum': No such file or directory
hduser@bmsce-OptiPlex-3060:~/Desktop$ hadoop fs -cp /desktop/ /LLL
23/05/11 14:38:20 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
cp: `/desktop/': No such file or directory
hadoop fs -ls LLL
23/05/11 14:42:07 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
ls: `LLL': No such file or directory
hduser@bmsce-OptiPlex-3060:~/Desktop$ hadoop fs -ls /LLL
23/05/11 14:42:14 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Found 2 items
-rw-r--r--   1 hduser supergroup         27 2023-05-11 14:41 /LLL/WC.txt
-rw-r--r--   1 hduser supergroup         27 2023-05-11 14:41 /LLL/WC2.txt



