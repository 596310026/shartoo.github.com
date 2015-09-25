---
layout: post
title: spark��������
description: spark������
category: blog
---

## spark overview

### UC Berkeley ��spark���ݷ���ջ
![](http://i.imgur.com/OWyTF1M.png)

��ʹ�÷�ʽ����

- ����������Mlib��Graphs��
- ����ʽ��ѯ��spark SQL��
- ʱʵ���㣨spark streaming��

### spark��Դ����
![](http://i.imgur.com/rtY99ub.png)

- stanalone
-  mesos
-  yarn


  ��������ʹ�õ���yarn��Դ���ȣ�Ҳ��������spark job��Ⱥ������Դ�ķ�ʽ��hadoop��һ���ģ�����resourcemanger��Ȼ����nodemanager������container����applicationMaster,����excutor

  yarn���ύjob��ʽclient��cluster
   - client�ύ��ʽ��driver program�������ύ������
   - cluster��ʽ��driver program�������ڼ�Ⱥ�е�ĳ��worker��


### spark VS hadoop
- Ӧ�ó���
   
   - hadoop��mapreduce�ʺ��������ݼ�������������
   - hadoop�������ܵģ�С���ݼ��������ܴ����С���ݼ�ɱ����ţ�������Լ����ӵĵ������㣬ʵʱ���㣬���߷���������Ϊ������spark�ĳ��ֺܺõ��ֲ���hadoop�Ĳ���֮������Ϊspark�ǻ����ڴ�ļ����ܣ��ʺϸ��ӵĵ������㣬spark streaming�ֲ�ʵʱ����Ŀ�ȱ��stormʵʱ�Ը��ߣ����������ݴ���ȱ����spark���Ժ����spark���ݴ����lineage��ʵʱ������storm�ĶԱȣ�

- ����Ч��
  - spark����Ч�ʱȽ�
  ![](http://i.imgur.com/nTBmin9.png)
  - �����о�����ͬ��ʵ�ʵĲ��Ա���

```
   Spark������������MR����ȱȽϽ�����߸�����13.6% 
    ������� 
    ֮ǰ��Hadoop�汾����������ҵ������23����ҵ����ҵ֮��Ĺ�����ʽΪ��
 ǰһ����ҵ���������������ض�Ŀ¼�У���Ϊ֮����ҵ���������ݡ�������һ�����ļ������ǽ���Ϊ�м����ʱ���ݴ��ڣ�
������ҵ�����󽫻ᱻ������������ÿ��Hadoop��ҵ����ִ��һ��MapReduce���̣�
����� ��ͨ��Spark�ı�̽ṹ���Ը���Ϊ������ģ�������ҵ���֣�ÿ����ҵ��ʵ�ֶ��ԭ��MapReduce�Ĺ��ܣ�
���м�������������̲�����һ����ҵ�����¶���Ĺ��̼�ΪSpark�е��м仺������������ڴ��С�
�������ܵ�������Ҫ�����ڴˣ����Ż����м����ݵ��������IOʱ�䡣���⣬����ʡ���ķ�����ҵ���ԣ�
�������µ��ص㣬�����������������ܴﵽ�������ἰ��һ���������ĸ���Ч���� 
    ��һ��ԭʼ������������Ļ������������ھ޴󣬵��´�����ʱ�仨���ڵ�һ�εĴ������ݶ�ȡ�ϣ�
���ʱ��ֻȡ���ڴ���IO���ʺ��ļ��� С������ֲ�ʽ����ģʽ�޹ء�ʡ��������ҵ���ݴ�����ڴ����ܼ��ͣ�
�����ݶ�ȡ��ʱ����ȣ������ʱ��ķѱ��ؽ��ᣬʹ��Hadoop��Spark�����ܱ��ֲ��첻�� 
    �ڶ���ʡ�����ݷ��������ݣ���������ڵ��εļ����������ͳ�ƴ����ͻ��ܵĹ�����
�ⷽ��Hadoop�����ܿ��Լ��õķ��ӳ�����Spark������ �ڶ�һ��С��ģ�������ݵģ������������㣬�����ļ��Ķ�ȡʱ���С��
���������ʮ�ָ��ӣ�����������ڴ�ļ��㷽�����Ը���ֵ�չ�����ơ�����ǰһ�׶��У�
ʹ�÷ֲ�ʽ�Ծ�����м���Ĺ��������ֵ���Ϊ���ԣ�Ч�����Խӽ��������ἰ��һ�������������� 

```

- ����Ч�ʱȽ�
  - spark����rdd�Ĳ�������mapreduce�ĳ������ṩ���ǻ���rdd�ḻ�Ľӿڣ���filter��disinct��reducebykey�ȵȣ���hadoop��Щ������Ҫ�û���map��reduce��combine�Լ�����ʵ�֣�
  - ����дmapreduce����ÿ��job��Ҫдmaper�࣬reducer�ࣨ��Ȼ��Щjob���Բ�дreducer�࣬��sqoop�������ݿ��ֻ��maper�������ܻ�Ҫдpartition��combiner�࣬����д��job����Ҫ����job��job֮��ִ�е�˳���������ϵ����������ļ�ֵ���͵ȣ�
   - ��spark�ǲ���Ҫ��ô���飬��rddִ�ж��transform�󣬵�ִ��һ��action�����󣨺��潫����rdd�Ĳ��������Զ�����һ������rdd��DAG�����޻�ִ����ҵͼ��ʹ�ù�pig��ͬ��������ᣬ�������pig��pig�Ľ������Ὣ�������ݼ�����������̣�ת��ΪDAG��job������spark������pig�������������̿��ƣ�pig��Ϊһ�����������ԣ�ȱ�����̿��ƣ��ֲڵĹ��̿�����Ҫһ�Ŷ�̬�Ľű�������python��javascript��ʵ�֣�����pig��hiveֻ�ʺ���ͳ�Ʒ�����ҵ����Ը��ӵĴ�����dougelas�������ߵ�ѹ������Ҫ��mapreduce��spark����

### ��������֧��
 - ԭ������scala
 - java
 - python
 - spark1.4��֧��R����

### spark�ĺ���RDD
  ��ҿ�����ⵯ�Էֲ�ʽ���Ͼ���һ�����ݼ��ϣ���������ж��partition��ɣ�����Щpartition�ֲ�����Ⱥ�и��ڵ��worker

 - ����RDD�ķ�ʽ
  - �����ڴ漯��
    ��1��100����Range��Ϊrdd��val data = sc.parallelize(1 to 100)
  - �ⲿ�洢ϵͳ����hbase��cassandra��hdfs�ȣ� ��val data = sc.textfile("dataPath")
  
 - ����rdd�Ĳ���
   - Transformations����
   ��map��filter��groupbykey�ȵȣ���������ɲο�[spark����](http://spark.apache.org/docs/latest/programming-guide.html#transformations)
   
   - action����
    top��count��reducebykey��saveastexrfile�ȵȣ���������ɲο�[spark����](http://spark.apache.org/docs/latest/programming-guide.html#actions)
      

  transform��lazyִ�еģ�Ҳ����˵ֱ��������rdd��ִ��action�������Ż�����job��ִ�м��㣬����˼���scala���Ե�lazyʮ�����ƣ�����ͨ��һ���򵥵�scala�������������˼��
   
 
```

package com.haohandata.dnsApp
import scala.io.Source._
import scala.io.Source
/**
 * @author xizhououyang@163.com
 * @desription lazy deamon
 */
object LazyDeamon {
  /*
������ͣ�����������һ�������ڵ��ļ��������ִ��forѭ�����ļ����ж�ȡ��program���������쳣��Ҳ����˵����һ������Ϊlazy
�󣬵����Ƕ���������ֵʱ�򣬲Ż�������У����������java�ķ�����ƣ���̬����
*/
  def  main(args:Array[String]){
  lazy  val  file = Source.fromFile("/home/osun/pgadmin.logxx")
  for(line<- file.getLines)
    println(line)
  val word ="learning spark"
   println(word)
  
  }

}

```


### �㲥����

�㲥�����Ƿַ���ÿ��worker��ֻ�����������޸ģ�������hadoop�ķֲ�ʽ�������ƣ�

  Ŀǰ��dns��Ŀʵսʹ�õ�������Դ������������ݼ���С���ݼ��Ĺ���������Ź㲥�����У�ͨ��mapת��������������ע��㲥������һ��ֻ���������������޸ġ�

### ������

��ҵ��ȫ�ֵ�һ������������hadoop�ļ��������ƣ�����İ��������ƽʱ����mr����pig��ʱ������������ͼ�������ͳ�ƣ�
Framkework��������job��������hdfs�ļ�ϵͳ��������ע��spark�еļ������ǲ�����task����ֵ��ֻ����driver program����ֵ
   
  ��dns��Ŀ��ͳ�Ƹ��û�Ⱥ������Ӫ�̣�top10��icp��ÿ��icp��ͳ��top10 ��host��������ÿ��partition��ͳ��top10��icp��top10��host��Ȼ�󱣴浽�����������У�Ȼ�󽫾ۺϺ�����������ֻ�������������е�host��icp���������Ա����ε�������rdd.top��10������N*N��job��ȡ�����СƬ���ݣ�����n*n��������rdd.top��ʽ���ɿ����Ҫ����Сʱ����������1800���Сjob������������Сʱ�����ü��������˷�ʽ��4�ֶ��Ӿ���������ʵ�����postgresql

### rdd����
- narrow��������rdd��ͬһ��partion���ֻ����rddһ��partion������
- wide��������rdd��ͬһ��partion����rdd���partion������
![](http://i.imgur.com/UE5Od8S.png)

### С�ᣬ�Ӽ��㣬�洢���ݴ�̸̸rdd

- ����

![spark����code](http://gitlab.hudoumiao.com/TopLevel/Knowledge_Base/uploads/ba527855ed3b360d8c82840c62b0b3ab/spark����code.png)

ע�⣺����ʱ���ϵ��ֱ�ӽ������˻���ͼ��deamon�д���һ��error����ȷ�Ĵ���Ӧ����map(parts=>(parts(0),parts(1).toInt)),��һ��map��transform�õ�����RDD[Array[String]],����RDD[List[String]]

code.png)![spark����code����](http://gitlab.hudoumiao.com/TopLevel/Knowledge_Base/uploads/e82db4ea22a47be62bc7355505d06ba2/spark����code����.png)

 
ÿ��job���ֲ�ͬ��stage��ÿ��stage����һ��Set[task]����  

![spark�ύ��ҵ����](http://gitlab.hudoumiao.com/TopLevel/Knowledge_Base/uploads/8f0a48da38c9da65b84ed5af5262562f/spark�ύ��ҵ����.png)

  spark����ҵ���ȣ���DAGshedule����taskshedule��������hadoop��jobtraker��tasktracker������������
- �洢
 
 - MEMORY_ONLY
 - MEMORY_AND_DISK
 - MEMORY_ONLY_SER
 - MEMORY_AND_DISK_SER
 - DISK_ONLY
 - MEMORY_ONLY_2, MEMORY_AND_DISK_2

  ������spark��rdd�ĸ��ִ洢���ԣ���spark�������У�Ĭ����Ϊ�ظ�����rdd��Ҫ��ʱ���ȴӴ����ж�ȡ���ݽ��е�io����Ч�ʸߣ�
 ���Ĭ�����е�rdd��persist��ʽ���Ǵ����ڴ��У����ڴ治��󣬻ᶪ�������rdd����Ҫʱ���ٸ���lineage
���ƴ��¼��㣬ʵ�ʿ������������Ϊ���������rdd����Զ�Ƚ���io����ʱ�ɸ������ѡ�������־û����ԣ�����dns��Ŀ�У���Ҫ����ppp��result��record�������rdd����ȡMEMORY_AND_DISK_SER��ʽ�ĳ־û�
- �ݴ�lineage��

����һ��С���£�

```

  ��˧��С������һ���Ҵ�������ѵ��������һ�������´���ÿ���˿��ܶ�������ұ���
ÿ��������ⱦ����е��ܸ��죬��Ƕ�뱦ʯ������שʯ��ĳ��С�����ɿ����ˣ�������Ҫ����������ұ���
�����컯Ū�ˣ�����Ҫ����ʱ�򣬷��ִ��ұ������ˣ�������С�������Ȼ�ȷ�����ְ��Ƿ��Ѿ���������ﴫ�˸�����
���ȷ���ǣ����Ὣ�ڷ����Լ������ң����������û��������ֱ��ȥ�����׵�ס���ң�����������裬
����游�ǻ�û�ҵ�������һֱ���ݵ������游�ǣ�ֱ���ҵ����ұ���Ȼ����һ�����ش���С����
С���õ���������հ�������

``` 

�����龰:
- rdd�ͺñȴ��ұ�
- �龰�е�ÿ������ͺñȲ�ͬʱ��Ⱥ�еļ���ڵ��е�worker
-  С����������ͺñ�ִ����һ��action�������ύjob
-  ��ÿ���˶Ա������һ����ʯ���ͺñ�rdd��transform����
-  rdd���ݴ���lineage���ƣ��������spark�ύjob��ʱ�򣬻ṹ�����rdd������DAG����ҵ������ʱ���л���rdd��������������������ĳ��rdd��ʧ�ˣ�����Ӹ�rdd�����¼��㣬�����rdd�����ڣ���һֱ������ȥֱ���ҵ�����rdd��Ȼ������������������ִ�м��㣬���ִ��action����


## spark����Ŀ��ʵսӦ��
### �ܹ�ͼ
![](http://i.imgur.com/VdB2LPU.png)
### ��Ŀ����

http://gitlab.hudoumiao.com/applications/User_Mobility_Analysis/tree/master/sparkcode/src/main/scala/com/haohandata


## spark streaming

### spark streaming vs Storm�������������о�����ͬ�µĸ��������߶Աȵı������ݣ�
 
```
 Storm��Spark Streaming���Ƿֲ�ʽ������Ŀ�Դ��ܡ���Ȼ���߹������ƣ�����Ҳ����һ�������� 

- ����ģ�� 

��Ȼ��������ܶ��ṩ����չ�Ժ��ݴ���,���Ǹ����������������ǵĴ���ģ�͡� 
Spark Streaming�ǽ���ʽ����ֽ��һϵ�ж�С����������ҵ�������������������Spark��
Ҳ���ǰ�Spark Streaming���������ݰ���batch size  ����1�룩�ֳ�һ��һ�ε����� ��Discretized Stream����
ÿһ�����ݶ� ת����Spark�е�RDD  ��Resilient Distributed Dataset ����Ȼ��Spark Streaming �ж�DStream��Transformation������Ϊ���Spark�ж�RDD��Transformation��������RDD������������м����������ڴ��С�������ʽ�������ҵ���������Զ��м�Ľ�����е��ӣ����ߴ洢���ⲿ�豸�� 
 
��Storm�У���Ҫ���һ������ʵʱ�����ͼ״�ṹ�����ǳ�֮Ϊ���� ��topology ����
������˽��ᱻ�ύ����Ⱥ���ɼ�Ⱥ�е����ؽڵ� ��masternode ���ַ����룬���������������ڵ� ��worker node ��ִ�С�
һ�������а���spout��bolt���ֽ�ɫ������spout������Ϣ��������������tupleԪ �����ʽ���ͳ�ȥ��
��bolt����ת������������bolt �п�����ɼ��㡢���˵Ȳ�����bolt ����Ҳ������������ݷ��͸�����bolt ��
��storm�У�ÿ������tuple�ǲ��ɱ����飬��Ӧ�Ź̶��ļ�ֵ�ԡ� �����֮��Storm��������������㣬
��Spark Streaming��ʹ�����������ݡ� 

- �ӳ٣�storm����
Spark Streaming����С��Batch Size��ѡȡ��0.5~2����֮�䣬��Storm Ŀǰ��С���ӳ���100ms���ң�
����Spark Streaming�ܣ����������ʵʱ��Ҫ��ǳ��� �����Ƶʵʱ���ף�֮���������ʽ׼ʵʱ���㳡����
����ʵʱ��Ҫ��ĳ�����Ӧ�ý���Storm����ɡ� 

- �ݴ�spark streaming���� 

���ݴ����ݱ�֤�����Ȩ���ǣ�Spark Streaming�ṩ�˸��õ�֧���ݴ�״̬���㡣
��Storm��,ÿ�������ļ�¼����ͨ��ϵͳʱ���뱻���٣����� Storm�ܹ����ٱ�֤ÿ����¼��������һ�Σ�
�����ڴӴ����лָ�����ʱ����������ظ���¼������ζ�ſɱ�״̬���ܲ���ȷ�ر��������Ρ� 
��һ�� �棬Spark Streamingֻ��Ҫ����������и��ٴ�����˿�����Ч�ر�֤ÿ��mini-batch����ȫ������һ�Σ�
����һ���ڵ㷢�����ϡ� 

- ��������spark streaming��ǿ 
   Spark Ŀǰ��EC2�����ܹ�������չ��100���ڵ� ��ÿ���ڵ�4Core ����������������ӳٴ���6GB/s�������� ��60M records/s ������������Ҳ�����е�Storm��2��5���� 



ʹ��ѡ�� 

�������Ҫ����һ��������������ĸ����¼�����ϵͳ��Storm�������ѡ��
������Ӧ�����ڿͻ��˵ȴ������ͬʱ����һ�����зֲ�ʽ���������ʹ�ÿ��伴�õķֲ�ʽRPC  ��DRPC���Ϳ����ˡ�
���ͬ����Ҫ��ԭ��Stormʹ��Apache Thrift ����������κα����������д���˽ṹ��
�������Ҫ״̬������ͬʱ/���ߴﵽǡ��һ�εĴ���Ч����Ӧ���������߲����Trdent API����ͬʱҲ�ṩ��΢������ķ�ʽ�� 
����������״̬�ļ��㣬ǡ��һ�εĵ��ͣ����Ҳ�������ӳٵĻ�����ô���Կ���Spark Streaming��
�ر�����㻹�ƻ�ͼ�β���������ѧϰ���߷���SQL�Ļ���ApacheSpark��stack�����㽫һЩlibrary������������ 
��Spark SQL��Mllib��GraphX�������ǻ��ṩ��ݵ�һ�廯���ģ�͡�
�������������㷨 �����磺K��ֵ��ý�壩����Sparkʵʱ���ߵĴٽ��� 

```

### ����DStream
- Dstream���
  Dstream��һ����ʱ��Ϊ��������һ��rdd
![](http://i.imgur.com/H5GA2XL.png)
- Dstream������Դ

![](http://i.imgur.com/ya40qiL.png)

- DStream��transformations����
- DSstream��action����

### ʹ�ó�������
-  ��״̬

ÿ��������receiver���յ����ݶ���Ϊ����Dstream����

-  ��״̬updateStateByKey(func)

  ���μ��㣬��Ҫ�õ��ϴ�������Ľ����
����spark streaming��������ʱ��������ӣ���ҵ���У�����Ҫͳ�ƻ�����haohandata.com.cn�ӳ������к�ÿ����Ӻ�haohandata.com.cn����������ۼӵķ���������ʱ���ǻ����ϴ�������Ϊkey�ķ��ʴ��������ϱ��������������õ����

-  windowns

���ڴ��ڵĲ�����������ʱ�䣬�������ڣ����ڴ�С
DNSʵʱ����ʵ����Ŀ�У�ͳ����������ȸ�rcode�Ĵηֲ���
���ڴ��ڱ߽����ݣ�����İ취��ȡ�����Ϊ������ʱ�䣬��������Ϊ����ӣ����ڴ�СΪ10���ӣ�ÿ�ν���reduceByKeyAndWindow�󣬻���й��ˣ�ֻ�����windown�е��м���������ݣ������cassandra

## dns��Ŀ��spark streamingʵʱ���㣨ʵ������Ŀ��
### DNS��Ŀ��������ͼ
![](http://i.imgur.com/7EatbDK.png)

### ��Ŀ����



   




