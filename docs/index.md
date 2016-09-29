---
layout: page
title:
description:
group:
---
<!--
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->
{% include JB/setup %}
<br />
<div class="row">
  <div class="col-md-6" style="padding-right:0">
    <h1 style="color:#4c555a">다목적 Notebook</h1>
    <p class="index-header">
      이 Notebook은 당신이 원하는 모든 것을 위한 장소입니다.
    </p>
    <ul style="list-style-type: none;padding-left:10px;" >
      <li style="font-size:18px; margin: 5px;"><span class="glyphicon glyphicon-import" style="margin-right:10px"></span> 데이터 처리</li>
      <li style="font-size:18px; margin: 5px;"><span class="glyphicon glyphicon-eye-open" style="margin-right:10px"></span> 데이터 검색</li>
      <li style="font-size:18px; margin: 5px;"><span class="glyphicon glyphicon-wrench" style="margin-right:10px"></span> 데이터 분석</li>
      <li style="font-size:18px; margin: 5px;"><span class="glyphicon glyphicon-dashboard" style="margin-right:10px"></span> 데이터 시각화 & 협업</li>
    </ul>
  </div>
  <div class="col-md-6" style="padding:0">
    <img class="img-responsive" style="border: 1px solid #ecf0f1;" src="./assets/themes/zeppelin/img/notebook.png" />
  </div>
</div>

<br />
## 다양한 언어의 백엔드
[아파치 제플린 인터프리터](./manual/interpreters.html) 구성은 어떤 백엔드 데이터 처리 언어도 제플린에 연결될 수 있도록 합니다.
현재 아파치 제플린은 아파치 스파크, 파이썬, JDBC, 마크다운, 쉘과 같은 많은 인터프리터를 지원합니다.

<img class="img-responsive" width="500px" style="margin:0 auto; padding: 26px;" src="./assets/themes/zeppelin/img/available_interpreters.png" />

새로운 백엔드 언어를 추가하는 것은 아주 쉽습니다. [당신만의 인터프리터를 만드는 방법](./development/writingzeppelininterpreter.html#make-your-own-interpreter)을 알아봅시다.

#### 아파치 스파크 통합
아파치 제플린은 특별히 내장 [아파치 스파크](http://spark.apache.org/) 통합을 제공합니다. 그래서 별도의 모듈이나 플러그인을 구성할 필요가 없습니다.

<img class="img-responsive" src="./assets/themes/zeppelin/img/spark_logo.png" width="140px" />

스파크와 통합된 아파치 제플린은 아래 항목을 제공합니다.

- SparkContext와 SQLContext 자동 주입
- maven 저장소나 로컬 파일 시스템으로부터 runtime jar dependency를 로딩. [dependency loader](./interpreter/spark.html#dependencyloading)에 대해 배워봅시다.
- job 취소 및 진행 상황 출력

아파치 제플린의 아파치 스파크에 대한 더 많은 정보는 [아파치 제플린에 대한 스파크 인터프리터](./interpreter/spark.html)를 참조할 수 있습니다.

<br />
## 데이터 시각화

아파치 제플린에는 기본적인 몇 가지 차트가 포함되어 있습니다. 시각화는 스파크 SQL 쿼리에 제한되어 있지 않으며, 모든 백엔드 언어로부터의 모든 결과물은 시각회될 수 있습니다.


<div class="row">
  <div class="col-md-6">
    <img class="img-responsive" src="./assets/themes/zeppelin/img/graph1.png" />
  </div>
  <div class="col-md-6">
    <img class="img-responsive" src="./assets/themes/zeppelin/img/graph2.png" />
  </div>
</div>

### 피벗 차트

아파치 제플린은 간단하게 드래그 앤 드롭으로 값을 종합하고 피벗 차트에 출력합니다. 총합, 카운트, 평균, 최소, 최대를 포함한 다양한 집계 값을 쉽게 차트로 만들 수 있습니다.

<div class="row">
  <div class="col-md-12">
    <img class="img-responsive" style="margin: 16px auto;" src="./assets/themes/zeppelin/img/screenshots/pivot.png" width="480px" />
  </div>
</div>

아파치 제플린의 [출력 시스템](#display-system)을 알아봅시다.

<br />
## 동적 양식

아파치 제플린으로 notebook에서 몇 가지 입력 양식을 동적으로 생성할 수 있습니다.

<div class="row">
  <div class="col-md-12">
    <img class="img-responsive" style="margin: 16px auto;" src="./assets/themes/zeppelin/img/screenshots/dynamicform.png" />
  </div>
</div>
[동적 양식](./manual/dynamicform.html)에 대해 더 알아봅시다.

<br />
## Notebook & Paragraph 공유를 통한 협업
공동 협력자들 사이에 notebook URL을 공유할 수 있습니다. 그러면 아파치 제플린은 구글 문서 도구로 협업하는 것처럼 실시간으로 변경 사항을 방송합니다.

<div class="row">
  <div class="col-md-12">
    <img class="img-responsive" style="margin: 20px auto" src="./assets/themes/zeppelin/img/screenshots/publish.png" width="650px"/>
  </div>
</div>

아파치 제플린은 notebooks 안의 버튼이나 메뉴를 포함하지 않는 결과 페이지만 출력하는 URL을 제공합니다.
이 방법으로 웹 사이트의 iframe으로 쉽게 삽입할 수 있습니다.
이 기능에 대해 더 알고싶으면 [이 페이지](./manual/publish.html)를 참조할 수 있습니다.

<br />
## 100% 오픈소스

<img class="img-responsive" style="margin:0 auto; padding: 15px;" src="./assets/themes/zeppelin/img/asf_logo.png" width="250px"/>

아파치 제플린은 아파치2 라이센스 소프트웨어입니다. [소스 저장소](http://git.apache.org/zeppelin.git)와 [기여하는 방법](https://zeppelin.apache.org/contribution/contributions.html)을 확인할 수 있습니다.
아파치 제플린 개발자 커뮤니티는 매우 활동적입니다.
[메일링 리스트](https://zeppelin.apache.org/community.html)에 가입하고 [Jira Issue tracker](https://issues.apache.org/jira/browse/ZEPPELIN)에 이슈를 보고합니다.

## 다음은 무엇입니까?

####빠른 시작

* 시작하기
  * 아파치 제플린 [설치](./install/install.html) 기본 지침
  * 아파치 제플린을 위한 [구성](./install/install.html#apache-zeppelin-configuration) 목록
  * [아파치 제플린 UI 경험](./quickstart/explorezeppelinui.html): 아파치 제플린 홈의 기본 컴포넌트
  * [튜토리얼](./quickstart/tutorial.html): 아파치 스파크 백엔드를 사용한 간단한 튜토리얼
* 기본 기능 가이드
  * [동적 양식](./manual/dynamicform.html): 동적 양식을 만드는 단계별 가이드
  * 외부 웹 사이트에 [Paragraph 결과 공개](./manual/publish.html)
  * 너의 notebooks 중 하나로 [제플린 홈페이지 꾸미기](./manual/notebookashomepage.html)
* 더 많은 정보
  * [제플린 버전 업그레이드](./install/upgrade.html): 아파치 제플린을 수동으로 업그레이드하는 방법

####인터프리터

* [아파치 제플린의 인터프리터](./manual/interpreters.html): 인터프리터 그룹은 무엇인가? 아파치 제플린에 어떻게 인터프리터를 설정할 수 있는가?
* 사용법
  * [인터프리터 설치](./manual/interpreterinstallation.html): 커뮤니티에서 관리하는 인터프리터를 비롯하여 제3 인터프리터 설치
  * 인터프리터에 외부 라이브러리를 포함시킬 때 [인터프리터 종속성 관리](./manual/dependencymanagement.html)
* 사용가능한 인터프리터: 현재 아파치 제플린에서는 약 20 개의 인터프리터를 사용할 수 있습니다.

####출력 시스템

* 기본 출력 시스템: [텍스트](./displaysystem/basicdisplaysystem.html#text), [HTML](./displaysystem/basicdisplaysystem.html#html), [테이블](./displaysystem/basicdisplaysystem.html#table)을 사용할 수 있습니다.
* Angular API: 백엔드와 프론트엔드 AngularJS API에 대한 설명과 예제
  * [Angular (backend API)](./displaysystem/back-end-angular.html)
  * [Angular (frontend API)](./displaysystem/front-end-angular.html)

####더 많은 정보

* Notebook 저장소: 외부 저장소에 notebooks을 저장하는 방법
  * [Git 저장소](./storage/storage.html#notebook-storage-in-local-git-repository)
  * [S3 저장소](./storage/storage.html#notebook-storage-in-s3)
  * [Azure 저장소](./storage/storage.html#notebook-storage-in-azure)
  * [ZeppelinHub 저장소](./storage/storage.html#storage-in-zeppelinhub)
* REST API: 아파치 제플린에서 사용할 수 있는 REST API 목록
  * [인터프리터 API](./rest-api/rest-interpreter.html)
  * [Notebook API](./rest-api/rest-notebook.html)
  * [구성 API](./rest-api/rest-configuration.html)
  * [자격 증명 API](./rest-api/rest-credential.html)
* 보안: 아파치 제플린에서 사용할 수 있는 보안 지원
  * [NGINX를 사용한 인증](./security/authentication.html)
  * [Shiro 인증](./security/shiroauthentication.html)
  * [Notebook 인증](./security/notebook_authorization.html)
  * [데이터 소스 인증](./security/datasource_authorization.html)
* 고급
  * [Vagrant VM에서 아파치 제플린](./install/virtual_machine.html)
  * [스파크 클러스터 모드에서 제플린 (Docker를 통한 Standalone)](./install/spark_cluster_mode.html#spark-standalone-mode)
  * [스파크 클러스터 모드에서 제플린 (Docker를 통한 YARN)](./install/spark_cluster_mode.html#spark-on-yarn-mode)
  * [스파크 클러스터 모드에서 제플린 (Docker를 통한 Mesos)](./install/spark_cluster_mode.html#spark-on-mesos-mode)
* 기여하기
  * [제플린 인터프리터 작성](./development/writingzeppelininterpreter.html)
  * [제플린 어플리케이션 작성 (실습)](./development/writingzeppelinapplication.html)
  * [기여하는 방법 (코드)](./development/howtocontribute.html)
  * [기여하는 방법 (웹 사이트 문서)](./development/howtocontributewebsite.html)

#### 외부 리소스
  * [메일링 리스트](https://zeppelin.apache.org/community.html)
  * [아파치 제플린 위키](https://cwiki.apache.org/confluence/display/ZEPPELIN/Zeppelin+Home)
  * [StackOverflow 태그 `apache-zeppelin`](http://stackoverflow.com/questions/tagged/apache-zeppelin)
