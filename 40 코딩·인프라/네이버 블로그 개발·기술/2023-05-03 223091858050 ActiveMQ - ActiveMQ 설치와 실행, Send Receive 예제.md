---
title: "2023-05-03 223091858050 ActiveMQ - ActiveMQ 설치와 실행, Send Receive 예제"
type: blog-archive
status: active
created: 2023-05-03
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223091858050&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223091858050
published: "2023. 5. 3. 0:23"
body_hash: 44192955b664f1f2529becffcf71d869a7d23f996e13adfa41c8aa93f5f316ac
visibility: private
rag: exclude
---
# 2023-05-03 223091858050 ActiveMQ - ActiveMQ 설치와 실행, Send Receive 예제

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223091858050&categoryNo=982
- 게시일: 2023. 5. 3. 0:23

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTJfNTAg/MDAxNzQ0NDIzOTM0NTgy.w9dAJa1vJ9WIDrCPS7a32uL9xEH_80sfnciGzpbeutcg.M2O9C3x3hExsdz4MYxS2ATJ4MegpZrF2jwy5ic6qVAUg.PNG/%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC-001_\(4\).png?type=w80_blur)

​

1\. ActiveMQ 개요 

ActiveMQ는 Apache 소프트웨어 재단에서 개발되어 가장 널리 사용되는 Java 기반 메시지 브로커다. 메시징 브로커는 분산 시스템에서 데이터를 안전하고 신속하게 전송하는 데 사용되는 중앙 집중식 메시지 큐이다. ActiveMQ는 업계 표준을 지원하고 JavaScript, C, C++, Python, .Net 등 다양한 언어로 작성이 가능하다. 마이크로 서비스 아키텍처의 서비스 간 통신을 제공할 수 있다. Apache ActiveMQ는 Apache Kafka와 RabbitMQ와 더불어 가장 인기 있는 오픈소스 메시지 브로커이다.

​

ActiveMQ는 다양한 프로토콜을 지원하여 다른 프로그래밍 언어나 플랫폼에서도 쉽게 사용할 수 있다. STOMP, AMQP, MQTT, OpenWire 등을 지원하며 다양한 배달 보증(QoS) 수준을 지원하므로 메시지 전송과 수신에서 발생하는 문제에 대한 대처가 가능하다. ActiveMQ는 대규모 분산 시스템에서 사용되며, 클러스터링 및 장애 복구 기능을 제공하여 고가용성을 보장한다. Spring Framework와 같은 다른 프레임워크와 통합이 쉬우며, Camel이라는 라우팅 엔진을 사용하여 복잡한 메시지 라우팅을 구현할 수 있다.

​

2\. ActiveMQ 방식 

메시지 브로커틑 Queue(대기열)와 Topic(주제)와 같이 두 가지 방법으로 구현할 수 있다.

​

**2.1 Queue(대기열) 방식**

대기열 방식은 여러 클라이언트에 메시지 송수신에 사용할 수 있다. 각 메시지는 정확히 하나의 클라이언트에 한 번만 처리된다. Producer(생산자)가 보낸 Message를 Queue(대기열)에 저장하면 등록된 Consumer(소비자)에게 Message가 배포되는 방식이다. 

![](https://postfiles.pstatic.net/MjAyMzA1MDNfMTM5/MDAxNjgzMDQwNTI2NDMz.3G3mm927tTyxC22mrMgM-EZCXCNXjCLRxfSKha1y8Ecg.CNa91HrnTxkn8rD4fRmkbbtYGa6D0mqhgw-511Krsaog.JPEG.agapeuni/img.jpg?type=w80_blur)

[출처] https://aws.amazon.com/message-queue/

​

**2.2 Topic(주제) 방식**

주제 방식은 여러 클라이언트가 동일한 메시지를 받을 때 사용한다. 메시지를 받으려는 클라이언트는 메시지 브로커에게 관심 있는 주제를 구독하게 된다. 해당 주제에 관한 메시지가 전달되면 주제를 구독하고 있는 모든 클라이언트에게 메시지를 보낸다. 이때 메지시를 송신하는 클라이언트를 Publisher(게시자)라고 하고 메시지를 수신하는 클라이언트를 Subscriber(구독자)라고 한다.

![](https://postfiles.pstatic.net/MjAyMzA1MDNfMjY3/MDAxNjgzMDQwNTM0MDMz.nO1pYiF4KgQeK2tlfAvc7QSb219ZTPVUPKDLMsOAbkog.-EAF4iaV8AOjlYmt7v1CxTtbIS-DXolSnLnkXXZWR_8g.JPEG.agapeuni/img.jpg?type=w80_blur)

[출처] https://aws.amazon.com/pub-sub-messaging/

​

3\. ActiveMQ 다운로드

2023년 2월 25일자 ActiveMQ Classic 버전을 다운로드한다.

파일 : apache-activemq-5.17.4-bin.zip (윈도우용)

​

<https://activemq.apache.org/components/classic/download/>

[ **ActiveMQ** These are the current releases. For prior releases, please see the past releases page. It is important to verify the integrity of the files you download. ActiveMQ 5.18.1 (Apr 14th, 2023) Release Notes | Release Page | Documentation | Java compatibility: 11+ Windows apache-activemq-5.18.1-bin.zip SHA... activemq.apache.org ](https://activemq.apache.org/components/classic/download/)

​

아래의 폴더에 압축 해제를 하였다.

D:\app\apache-activemq-5.17.4

​

4\. ActiveMQ 실행

D:\app\apache-activemq-5.17.4\bin 폴더에서 아래의 명령을 실행한다.

> activemq start

![](https://postfiles.pstatic.net/MjAyMzA1MDNfMTMg/MDAxNjgzMDQwNjAxODU1.EMQuObSu7rxJo9XRrL8yaKSiKy0wRxElihLVTkeaxysg.WC2-wiWc57XGr_GHlrZDM5TOwEqkkzLroX2bK30rWjwg.PNG.agapeuni/img.png?type=w80_blur)

​

ActiveMQ WebConsole에 접속해 보자. ActiveMQ가 실행되면 아래에 ActiveMQ WebConsole URL이 표시된다.

![](https://postfiles.pstatic.net/MjAyMzA1MDNfMjUy/MDAxNjgzMDQwNjA2Mzgz.7IFfCQdbix74r88b9kAmOOgWdb5N4qGrZj8XWIZoQMwg.DFgb4PzrfVh6uolfPFh66DfFuh_QCj-RMivoEfF69-Mg.PNG.agapeuni/img.png?type=w80_blur)

​

ID와 패스워드는 변경하지 않았다면 admin / admin이다.

![](https://postfiles.pstatic.net/MjAyMzA1MDNfMTIg/MDAxNjgzMDQwNjE4MDQ2.XmD5KLmRx__XaFyg4QvMY8En3hey_6qU9UJe4iB44eog.Yqan4qARRGiF2zj_sqMVb9JdLFpVRGqO02e5g5Tsbwog.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MDNfMTcw/MDAxNjgzMDQwNjI0ODM2.JrYPA5P1bhlPDkSaNA2_vf8bRG9guj70yhd9RAOd2J0g.so0HMNgpiM1GwmXmZvX4_nLKEjRBxBrTp457Imyxiv4g.PNG.agapeuni/img.png?type=w80_blur)

​

5\. 메시지 보내기(Send)

Java 코드로 ActiveMQ를 이용하여 메시지 보내기(Send)를 구현해 보자.

메시지 보내기 (Send) : ActiveMQSend.java

package activemq; import javax.jms.Connection; import javax.jms.Destination; import javax.jms.Message; import javax.jms.MessageProducer; import javax.jms.Queue; import javax.jms.Session; import org.apache.activemq.ActiveMQConnectionFactory; import org.apache.activemq.command.ActiveMQQueue; public class ActiveMQSend { String receiveQueueName = "ActiveMQ"; String sendQueueName = "ActiveMQ"; public void send() throws Exception { ActiveMQConnectionFactory factory = new ActiveMQConnectionFactory("tcp://localhost:61616"); Connection connection = factory.createConnection(); Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE); Queue queue = new ActiveMQQueue(sendQueueName); MessageProducer producer = session.createProducer(queue); Destination destination = session.createQueue(receiveQueueName); Message message = session.createTextMessage("MESSAGE 1"); message.setJMSReplyTo(destination); producer.send(queue, message); System.out.println("[SEND] " + message.toString()); message = session.createTextMessage("MESSAGE 2"); message.setJMSReplyTo(destination); producer.send(queue, message); System.out.println("[SEND] " + message.toString()); session.close(); connection.close(); } public static void main(String args[]) throws Exception { ActiveMQSend qsr = new ActiveMQSend(); qsr.send(); } }

먼저 ActiveMQConnectionFactory를 생성하고 Connection을 만든다. 그다음에는 Connection을 사용하여 Session을 만든다. Session을 사용하여 MessageProducer와 Queue를 만든다. send() 메서드로 메시지를 전달한다.

​

▣ 보내기 로그

[SEND] ActiveMQTextMessage {commandId = 0, responseRequired = false, messageId = ID:DESKTOP-AGK6MQP-1649-1677837086390-1:1:1:1:1, originalDestination = null, originalTransactionId = null, producerId = null, destination = queue://ActiveMQ, transactionId = null, expiration = 0, timestamp = 1677837086834, arrival = 0, brokerInTime = 0, brokerOutTime = 0, correlationId = null, replyTo = queue://ActiveMQ, persistent = true, type = null, priority = 4, groupID = null, groupSequence = 0, targetConsumerId = null, compressed = false, userID = null, content = null, marshalledProperties = null, dataStructure = null, redeliveryCounter = 0, size = 0, properties = null, readOnlyProperties = false, readOnlyBody = false, droppable = false, jmsXGroupFirstForConsumer = false, text = MESSAGE 1}​[SEND] ActiveMQTextMessage {commandId = 0, responseRequired = false, messageId = ID:DESKTOP-AGK6MQP-1649-1677837086390-1:1:1:1:2, originalDestination = null, originalTransactionId = null, producerId = null, destination = queue://ActiveMQ, transactionId = null, expiration = 0, timestamp = 1677837086903, arrival = 0, brokerInTime = 0, brokerOutTime = 0, correlationId = null, replyTo = queue://ActiveMQ, persistent = true, type = null, priority = 4, groupID = null, groupSequence = 0, targetConsumerId = null, compressed = false, userID = null, content = null, marshalledProperties = null, dataStructure = null, redeliveryCounter = 0, size = 0, properties = null, readOnlyProperties = false, readOnlyBody = false, droppable = false, jmsXGroupFirstForConsumer = false, text = MESSAGE 2}  
---  
  
​

6\. 메시지 받기(Receive)

Java 코드로 ActiveMQ를 이용하여 메시지 받기(Receive)를 구현해 보자.

메시지 받기 (Receive) : ActiveMQReceive.java

package activemq; import javax.jms.Connection; import javax.jms.Destination; import javax.jms.Message; import javax.jms.MessageConsumer; import javax.jms.MessageListener; import javax.jms.Session; import javax.jms.TextMessage; import org.apache.activemq.ActiveMQConnectionFactory; public class ActiveMQReceive { String receiveQueueName = "ActiveMQ"; public void receive() throws Exception { ActiveMQConnectionFactory factory = new ActiveMQConnectionFactory("tcp://localhost:61616"); Connection connection = factory.createConnection(); Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE); Destination destination = session.createQueue(receiveQueueName); MessageConsumer consumer = session.createConsumer(destination); consumer.setMessageListener(new MessageListener() { public void onMessage(Message message) { try { System.out.println("message = " + ((TextMessage) message).getText()); } catch (Exception e) { e.printStackTrace(); } } }); connection.start(); System.out.println("Listening..."); Thread.sleep(15000); session.close(); connection.close(); } public static void main(String args[]) throws Exception { ActiveMQReceive qsr = new ActiveMQReceive(); qsr.receive(); } }

ActiveMQConnectionFactory를 생성하고 Connection을 만든다. Connection을 사용하여 Session을 만든다. Session을 사용하여 MessageConsumer를 만든다. onMessage() 메서드로 메시지를 수신한다.

▣ 받기 로그

Listening... [RECEIVE] MESSAGE 1 [RECEIVE] MESSAGE 2

​

7\. 참고 URL

<https://activemq.apache.org/>

[ **ActiveMQ** Apache ActiveMQ® is the most popular open source, multi-protocol, Java-based message broker. It supports industry standard protocols so users get the benefits of client choices across a broad range of languages and platforms. Connect from clients written in JavaScript, C, C++, Python, .Net, and more... activemq.apache.org ](https://activemq.apache.org/)

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#ActiveMQ #메시지브로커 #ApacheActiveMQ #메시지큐 #분산시스템 #Java기반 #메시징 #프로토콜지원 #클러스터링 #고가용성 #Spring연동 #Java #마이크로서비스 #STOMP #AMQP #MQTT #OpenWire #메시지큐구조 #Queue방식 #Topic방식 #메시지전송 #메시지수신 #Apache소프트웨어재단 #RabbitMQ #ApacheKafka #메시지라우팅 #Camel #대기열 #소비자생산자 #PublisherSubscriber #메시지보내기 #메시지받기 #웹콘솔

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
