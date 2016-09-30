---
layout: page
title: "Quick Start"
description: "This page will help you to get started and guide you through installation of Apache Zeppelin, running it in the command line and basic configuration options."
group: install
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

# 빠른 시작
아파치 제플린을 탐험하는 첫번째 관문에 오신 것을 환영합니다!
이 페이지는 제플린을 시작하는 데 도움일 주고, 앞으로 다룰 주제의 목록입니다.

<div id="toc"></div>

## 설치

아파치 제플린은 공식적으로 지원하고, 다음 환경에서 테스트 되었습니다.

<table class="table-configuration">
  <tr>
    <th>이름</th>
    <th>값</th>
  </tr>
  <tr>
    <td>Oracle JDK</td>
    <td>1.7 <br /> (set <code>JAVA_HOME</code>)</td>
  </tr>
  <tr>
    <td>OS</td>
    <td>Mac OSX <br /> Ubuntu 14.X <br /> CentOS 6.X <br /> Windows 7 Pro SP1</td>
  </tr>
</table>

아파치 제플린을 설치하기 위한 두 가지 옵션이 있습니다. 첫번째는 아카이브에서 [사전 구축된 바이너리 패키지 다운로드](#downloading-binary-package)해야합니다. 
최신 안정화 버전과 필요하다면 더 이전 버전을 다운로드 받을 수 있습니다.
두번째는 [소스 빌드](#building-from-source)입니다.
개발 상태이기떄문에 불안정할 수 있지만, 새로 추가된 기능을 체험할 수 있고, 원한다면 바꿀 수도 있습니다.

### 바이너리 패키지 다운로드

안정화된 바이너리 패키지를 설치하고 싶으면 [아파치 제플린 다운로드 페이지](http://zeppelin.apache.org/download.html)에서 다운받을 수 있습니다. 

`netinst` binary를 다운로드 받으면, 제플린을 시작하기 전에 [추가 인터프리터 설치](../manual/interpreterinstallation.html)가 필요합니다. 혹은 간단히  `./bin/install-interpreter.sh --all`로 설치할 수 있습니다.

압축 해제 후, [커맨드 라인으로 아파치 제플린 시작하기](#starting-apache-zeppelin-with-command-line) 섹션으로 이동합니다.

### 소스 빌드
소스로 빌드하고싶다면, 시스템에 아래 요구사항이 만족되어야합니다.

<table class="table-configuration">
  <tr>
    <th>이름</th>
    <th>값</th>
  </tr>
  <tr>
    <td>Git</td>
    <td></td>
  </tr>
  <tr>
    <td>Maven</td>
    <td>3.1.x or higher</td>
  </tr>
</table>

아직 설치되지 않았다면, [빌드 사전 작업](https://github.com/apache/zeppelin/blob/master/README.md#before-build) 섹션의 단계별 지침을 따라야합니다.

####1. 아파치 제플린 저장소 복제

```
git clone https://github.com/apache/zeppelin.git
```

####2. 옵션으로 소스 빌드
각 인터프리터는 다른 빌드 환경이 필요하다. 옵션에 대한 더 자세한 정보는 [빌드](https://github.com/apache/zeppelin#build) 섹션을 참고할 수 있다.

```
mvn clean package -DskipTests [Options]
```

몇 가지 옵션을 이용한 몇 가지 예제입니다.

```
# build with spark-2.0, scala-2.11
./dev/change_scala_version.sh 2.11
mvn clean package -Pspark-2.0 -Phadoop-2.4 -Pyarn -Ppyspark -Psparkr -Pscala-2.11

# build with spark-1.6, scala-2.10
mvn clean package -Pspark-1.6 -Phadoop-2.4 -Pyarn -Ppyspark -Psparkr

# spark-cassandra integration
mvn clean package -Pcassandra-spark-1.5 -Dhadoop.version=2.6.0 -Phadoop-2.6 -DskipTests

# with CDH
mvn clean package -Pspark-1.5 -Dhadoop.version=2.6.0-cdh5.5.0 -Phadoop-2.6 -Pvendor-repo -DskipTests

# with MapR
mvn clean package -Pspark-1.5 -Pmapr50 -DskipTests
```

소스로 빌드하는 더 자세한 정보는 제플린 저장소의 [README.md](https://github.com/apache/zeppelin/blob/master/README.md)를 확인하세요.

## 커맨드 라인으로 아파치 제플린 시작하기
#### 제플린 시작

```
bin/zeppelin-daemon.sh start
```

Windows를 사용한다면

```
bin\zeppelin.cmd
```

성공적으로 시작됐으면, 웹 브라우저에서 [http://localhost:8080](http://localhost:8080)으로 접속합니다.

#### 제플린 정지하

```
bin/zeppelin-daemon.sh stop
```

#### (선택 사항) 서비스 매니저로 아파치 제플린 시작

> **참고 :** 아래 설명은 Ubuntu Linx를 기반으로 작성되었습니다.

아파치 제플린은 **upstart**에 의해 관리되는 서비스같은 초기화 스크립트를 통해 서비스로 자동 시작될 수 있습니다.

아래는 `/etc/init/zeppelin.conf`로 저장될 upstart 스크립트의 예제입니다.
이것은 서비스가 아래와 같은 명령어로 관리될 수 있도록합니다.

```
sudo service zeppelin start  
sudo service zeppelin stop  
sudo service zeppelin restart
```

다른 서비스 매니저는 `upstart` 인수를 `zeppelin-daemon.sh` 스크립트에 전달해서 사용할 수 있습니다.

```
bin/zeppelin-daemon.sh upstart
```

**zeppelin.conf**

```
description "zeppelin"

start on (local-filesystems and net-device-up IFACE!=lo)
stop on shutdown

# Respawn the process on unexpected termination
respawn

# respawn the job up to 7 times within a 5 second period.
# If the job exceeds these values, it will be stopped and marked as failed.
respawn limit 7 5

# zeppelin was installed in /usr/share/zeppelin in this example
chdir /usr/share/zeppelin
exec bin/zeppelin-daemon.sh upstart
```

## 다음은 무엇입니까?
아파치 제플린 설치 성공을 축하합니다! 당신에게 필요할 두 가지 다음 단계가 있습니다.

#### 제플린을 처음 사용한다면
 * [아파치 제플린 UI 탐험](../quickstart/explorezeppelinui.html)에서 아파치 제플린 UI의 면밀한 개요를 볼 수 있습니다.
 * 아파치 제플린 UI에 익숙해진 후에, 아파치 스파크 백엔드를 사용하는 [Tutorial](../quickstart/tutorial.html)에서 간단한 연습을 즐기세요.
 * 아파치 제플린 구성 설정을 더 하고 싶으면, [아파치 제플린 구성](#apache-zeppelin-configuration)을 참조하세요.
 
#### 스파크와 JDBC 인터프리터 설정에 대해 더 많은 정보가 필요하다면
 * 아파치 제플린은 [아파치 스파크](http://spark.apache.org/)와 깊은 통합을 제공합니다. 더 많은 정보가 필요하면 [아파치 제플린을 위한 스파크 인터프리터](../interpreter/spark.html)를 참조하세요. 
 * 또한, 아파치 제플린에서 일반 JDBC 연결을 사용할 수 있습니다. [아파치 제플린을 위한 일반 JDBC 연결](../interpreter/jdbc.html)을 참조하세요.
 
#### 다중 사용자 환경이라면
 * 다중 사용자 환경에서 당신 notebooks을 위한 권한과 데이터 리소스에 대한 보안을 설정할 수 있습니다.  **More** -> **Security** 섹션을 참고하세요.
   
## 아파치 제플린 구성

`conf/zeppelin-env.sh` (`conf\zeppelin-env.cmd` for Windows)의 **환경 변수** 와 `conf/zeppelin-site.xml`의 **자바 프로퍼티** 로 아파치 제플린을 구성할 수 있습니다. 둘 다 정의됐으면 환경 변수가 우선 순위가 높습니다.

<table class="table-configuration">
  <tr>
    <th>zeppelin-env.sh</th>
    <th>zeppelin-site.xml</th>
    <th>기본값</th>
    <th class="col-md-4">설명</th>
  </tr>
  <tr>
    <td>ZEPPELIN_PORT</td>
    <td>zeppelin.server.port</td>
    <td>8080</td>
    <td>제플린 서버 포트</td>
  </tr>
  <tr>
    <td>ZEPPELIN_MEM</td>
    <td>N/A</td>
    <td>-Xmx1024m -XX:MaxPermSize=512m</td>
    <td>JVM mem 옵션</td>
  </tr>
  <tr>
    <td>ZEPPELIN_INTP_MEM</td>
    <td>N/A</td>
    <td>ZEPPELIN_MEM</td>
    <td>인터피리터 프로세스에 대한 JVM mem 옵션</td>
  </tr>
  <tr>
    <td>ZEPPELIN_JAVA_OPTS</td>
    <td>N/A</td>
    <td></td>
    <td>JVM 옵션</td>
  </tr>
  <tr>
    <td>ZEPPELIN_ALLOWED_ORIGINS</td>
    <td>zeppelin.server.allowed.origins</td>
    <td>*</td>
    <td>REST 및 웹 소켓의 ','로 구분된 목록을 지정. <br /> i.e. http://localhost:8080 </td>
  </tr>
    <tr>
    <td>N/A</td>
    <td>zeppelin.anonymous.allowed</td>
    <td>true</td>
    <td>익명의 사용자를 기본적으로 허용</td>
  </tr>
  <tr>
    <td>ZEPPELIN_SERVER_CONTEXT_PATH</td>
    <td>zeppelin.server.context.path</td>
    <td>/</td>
    <td>웹 어플리케이션의 컨텍스트 경로</td>
  </tr>
  <tr>
    <td>ZEPPELIN_SSL</td>
    <td>zeppelin.ssl</td>
    <td>false</td>
    <td></td>
  </tr>
  <tr>
    <td>ZEPPELIN_SSL_CLIENT_AUTH</td>
    <td>zeppelin.ssl.client.auth</td>
    <td>false</td>
    <td></td>
  </tr>
  <tr>
    <td>ZEPPELIN_SSL_KEYSTORE_PATH</td>
    <td>zeppelin.ssl.keystore.path</td>
    <td>keystore</td>
    <td></td>
  </tr>
  <tr>
    <td>ZEPPELIN_SSL_KEYSTORE_TYPE</td>
    <td>zeppelin.ssl.keystore.type</td>
    <td>JKS</td>
    <td></td>
  </tr>
  <tr>
    <td>ZEPPELIN_SSL_KEYSTORE_PASSWORD</td>
    <td>zeppelin.ssl.keystore.password</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>ZEPPELIN_SSL_KEY_MANAGER_PASSWORD</td>
    <td>zeppelin.ssl.key.manager.password</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>ZEPPELIN_SSL_TRUSTSTORE_PATH</td>
    <td>zeppelin.ssl.truststore.path</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>ZEPPELIN_SSL_TRUSTSTORE_TYPE</td>
    <td>zeppelin.ssl.truststore.type</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>ZEPPELIN_SSL_TRUSTSTORE_PASSWORD</td>
    <td>zeppelin.ssl.truststore.password</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>ZEPPELIN_NOTEBOOK_HOMESCREEN</td>
    <td>zeppelin.notebook.homescreen</td>
    <td></td>
    <td>아파치 제플린 홈화면에 출력될 notebook ID. <br />i.e. 2A94M5J1Z</td>
  </tr>
  <tr>
    <td>ZEPPELIN_NOTEBOOK_HOMESCREEN_HIDE</td>
    <td>zeppelin.notebook.homescreen.hide</td>
    <td>false</td>
    <td>아파치 제플린 홈화면에 notebook ID를 숨기고 싶을 때 "true"로 설정합니다.<br /> 상세한 정보는 <a href="../manual/notebookashomepage.html">제플린 홈페이지 꾸미지</a>를 참조하세요.</td>
  </tr>
  <tr>
    <td>ZEPPELIN_WAR_TEMPDIR</td>
    <td>zeppelin.war.tempdir</td>
    <td>webapps</td>
    <td>jetty 임시 디렉토리 경로</td>
  </tr>
  <tr>
    <td>ZEPPELIN_NOTEBOOK_DIR</td>
    <td>zeppelin.notebook.dir</td>
    <td>notebook</td>
    <td>notebook 디렉토리가 저장된 루트 디렉토리</td>
  </tr>
  <tr>
    <td>ZEPPELIN_NOTEBOOK_S3_BUCKET</td>
    <td>zeppelin.notebook.s3.bucket</td>
    <td>zeppelin</td>
    <td>noteook 파일이 저장될 S3 Bucket</td>
  </tr>
  <tr>
    <td>ZEPPELIN_NOTEBOOK_S3_USER</td>
    <td>zeppelin.notebook.s3.user</td>
    <td>user</td>
    <td>S3 bucket의 사용자 이름<br />i.e. <code>bucket/user/notebook/2A94M5J1Z/note.json</code></td>
  </tr>
  <tr>
    <td>ZEPPELIN_NOTEBOOK_S3_ENDPOINT</td>
    <td>zeppelin.notebook.s3.endpoint</td>
    <td>s3.amazonaws.com</td>
    <td>bucket에 대한 엔드 포인트</td>
  </tr>
  <tr>
    <td>ZEPPELIN_NOTEBOOK_S3_KMS_KEY_ID</td>
    <td>zeppelin.notebook.s3.kmsKeyID</td>
    <td></td>
    <td>S3의 데이터를 암호화할 때 사용할 AWS KMS Key ID (선택 사항)</td>
  </tr>
  <tr>
    <td>ZEPPELIN_NOTEBOOK_S3_EMP</td>
    <td>zeppelin.notebook.s3.encryptionMaterialsProvider</td>
    <td></td>
    <td> 3에서 암호화할 때 사용할 사용자 S3 암호 재료 제공 도구의 클래스명 (선택 사항)</td>
  </tr>
  <tr>
    <td>ZEPPELIN_NOTEBOOK_AZURE_CONNECTION_STRING</td>
    <td>zeppelin.notebook.azure.connectionString</td>
    <td></td>
    <td>Azure 스토리지 계정 연결 문자열<br />i.e. <br/><code>DefaultEndpointsProtocol=https;<br/>AccountName=&lt;accountName&gt;;<br/>AccountKey=&lt;accountKey&gt;</code></td>
  </tr>
  <tr>
    <td>ZEPPELIN_NOTEBOOK_AZURE_SHARE</td>
    <td>zeppelin.notebook.azure.share</td>
    <td>zeppelin</td>
    <td>notebook 파일이 저장될 Share</td>
  </tr>
  <tr>
    <td>ZEPPELIN_NOTEBOOK_AZURE_USER</td>
    <td>zeppelin.notebook.azure.user</td>
    <td>user</td>
    <td>Azure file share의 선택적인 사용자 이름<br />i.e. <code>share/user/notebook/2A94M5J1Z/note.json</code></td>
  </tr>
  <tr>
    <td>ZEPPELIN_NOTEBOOK_STORAGE</td>
    <td>zeppelin.notebook.storage</td>
    <td>org.apache.zeppelin.notebook.repo.VFSNotebookRepo</td>
    <td>콤마로 구분된 notebook 저장소 목록</td>
  </tr>
  <tr>
    <td>ZEPPELIN_NOTEBOOK_ONE_WAY_SYNC</td>
    <td>zeppelin.notebook.one.way.sync</td>
    <td>false</td>
    <td>여러 notebook 스토리지가 있다면, 첫번째 것을 유일한 소스로 다뤄야 하는가?</td>
  </tr>
  <tr>
    <td>ZEPPELIN_INTERPRETERS</td>
    <td>zeppelin.interpreters</td>
  <description></description>
    <td>org.apache.zeppelin.spark.SparkInterpreter,<br />org.apache.zeppelin.spark.PySparkInterpreter,<br />org.apache.zeppelin.spark.SparkSqlInterpreter,<br />org.apache.zeppelin.spark.DepInterpreter,<br />org.apache.zeppelin.markdown.Markdown,<br />org.apache.zeppelin.shell.ShellInterpreter,<br />
    ...
    </td>
    <td>
      Comma separated interpreter configurations [Class] <br/>
      <span style="font-style:italic">참고: 이 속성은 제플린-0.6.0 이후 사용되지 않으며, 제플린 0.7.0에서는 지원되지 않습니다.</span>
    </td>
  </tr>
  <tr>
    <td>ZEPPELIN_INTERPRETER_DIR</td>
    <td>zeppelin.interpreter.dir</td>
    <td>interpreter</td>
    <td>인터프리터 디렉토리</td>
  </tr>
  <tr>
    <td>ZEPPELIN_WEBSOCKET_MAX_TEXT_MESSAGE_SIZE</td>
    <td>zeppelin.websocket.max.text.message.size</td>
    <td>1024000</td>
    <td>웹소켓에 의해 수신받을 최대 텍스트 메시지의 크기</td>
  </tr>
</table>
