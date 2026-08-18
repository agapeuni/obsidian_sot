---
title: "2023-10-07 223230511477 JavaFX - BarChart와 PieChart 그리기"
type: blog-archive
status: active
created: 2023-10-07
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223230511477&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223230511477
published: "2023. 10. 7. 14:30"
body_hash: fefa4018500cbf80c654b0b29c51f6c512a70d7f9c6cee043d35b3dc0a9d783f
visibility: private
rag: exclude
---
# 2023-10-07 223230511477 JavaFX - BarChart와 PieChart 그리기

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223230511477&categoryNo=982
- 게시일: 2023. 10. 7. 14:30

## 본문

![](https://postfiles.pstatic.net/MjAyNDA0MDNfMjY5/MDAxNzEyMDc1MTc2NzQz.tfIJBIXJ2GOhTD7RM832Eek7UTdq8AMARkmxa_9NRqIg.s8UdRnES06y9pdK-F5iOSWZmb6m3L6GjHiOfcFC86wwg.PNG/Chart-001_\(3\).png?type=w80_blur)

​

JavaFX는 Swing을 대체하기 위한 기술로 크로스 플랫폼에서 실행 가능하며 리치 애플리케이션을 개발하고 배포할 수 있다. JavaFX를 이용하여 간단한 BarChart와 PieChart를 표시해 본다.

​

먼저 애플리케이션을 실행하기 위한 AppMain 클래스를 만든다.

UI를 표현하는 stage.xml 을 읽어 root 변수에 저장한 뒤 Scene에 생성한다.

import javafx.application.Application; import javafx.fxml.FXMLLoader; import javafx.scene.Parent; import javafx.scene.Scene; import javafx.stage.Stage; public class AppMain extends Application { @Override public void start(Stage primaryStage) throws Exception { Parent root = (Parent) FXMLLoader.load(getClass().getResource("stage.fxml")); Scene scene = new Scene(root); primaryStage.setTitle("AppMain"); primaryStage.setScene(scene); primaryStage.show(); } public static void main(String[] args) { launch(args); } }

​

UI 항목을 담고 있는 "stage.fxml" 파일이다. FXML는 XML 기반의 마크업 언어로 JavaFX의 UI 레이아웃 정보를 담고 있다.

<?xml version="1.0" encoding="UTF-8"?> <?import javafx.scene.chart.*?> <?import java.lang.*?> <?import javafx.geometry.*?> <?import javafx.scene.layout.*?> <?import javafx.scene.control.*?> <HBox xmlns:fx="http://javafx.com/fxml" fx:controller="ChartController" prefHeight="450" prefWidth="850"> <children> <BarChart fx:id="barChart"> <xAxis> <CategoryAxis side="BOTTOM" /> </xAxis> <yAxis> <NumberAxis side="LEFT" /> </yAxis> </BarChart> <PieChart fx:id="pieChart" /> </children> </HBox>

​

ChartController는 데이터를 생성하여 BarChart와 PieChart에 추가하는 클래스이다.

stage.fxml 파일에 보면 fx:controller="ChartController"에 기술되어 있다.

import java.net.URL; import java.util.ResourceBundle; import javafx.collections.FXCollections; import javafx.fxml.FXML; import javafx.fxml.Initializable; import javafx.scene.chart.BarChart; import javafx.scene.chart.PieChart; import javafx.scene.chart.XYChart; import javafx.scene.chart.XYChart.Data; public class ChartController implements Initializable { @FXML private BarChart barChart; @FXML private PieChart pieChart; @Override public void initialize(URL location, ResourceBundle resources) { barChart.getData().add(getSeriesJapan()); barChart.getData().add(getSeriesChina()); barChart.getData().add(getSeriesKorea()); PieChart.Data data1 = new PieChart.Data("Angular", 23.5); PieChart.Data data2 = new PieChart.Data("Vue.Js", 27.3); PieChart.Data data3 = new PieChart.Data("Node.Js", 22.8); PieChart.Data data4 = new PieChart.Data("React", 30.3); pieChart.setData(FXCollections.observableArrayList(data1, data2, data3, data4)); } private XYChart.Series getSeriesJapan() { XYChart.Series series1 = new XYChart.Series(); series1.setName("Japan"); Data<String, Integer> data1 = new XYChart.Data<String, Integer>("2018", 55); Data<String, Integer> data2 = new XYChart.Data<String, Integer>("2019", 50); Data<String, Integer> data3 = new XYChart.Data<String, Integer>("2020", 45); series1.setData(FXCollections.observableArrayList(data1, data2, data3)); return series1; } private XYChart.Series getSeriesChina() { XYChart.Series series2 = new XYChart.Series(); series2.setName("China"); Data<String, Integer> data1 = new XYChart.Data<String, Integer>("2018", 45); Data<String, Integer> data2 = new XYChart.Data<String, Integer>("2019", 50); Data<String, Integer> data3 = new XYChart.Data<String, Integer>("2020", 55); series2.setData(FXCollections.observableArrayList(data1, data2, data3)); return series2; } private XYChart.Series getSeriesKorea() { XYChart.Series series3 = new XYChart.Series(); series3.setName("Korea"); Data<String, Integer> data1 = new XYChart.Data<String, Integer>("2018", 40); Data<String, Integer> data2 = new XYChart.Data<String, Integer>("2019", 50); Data<String, Integer> data3 = new XYChart.Data<String, Integer>("2020", 60); series3.setData(FXCollections.observableArrayList(data1, data2, data3)); return series3; } }

​

AppMain을 실행하면 아래와 같이 차트가 표시되는데 상당히 깔끔하고 심플하다.

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMTAx/MDAxNjk2NjUyMTUzMTU1.L4VsGUo5aIbcIvUPQGpSD06L4vrF9g6sq3_T2lRS85cg.JxnN0TVTykiZJBSB1LTDwTru9_ySp8FeD2mVL14CXaMg.PNG.agapeuni/img.png?type=w80_blur)

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

`

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMjY1/MDAxNjk2NjUyMDI4MTkx.XCNcxjMauiWhX3CELfUtxkJyAnQLTjbSFnXVKtjLG1og.mZKwBkQc9lG_IIFoeZOMXs7Llqb3eCOmlrX4FHYj_Ycg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
