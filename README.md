# jasper-report
## jasper report 한글문서
### jasper report에 대한 한글문서입니다. 
### jasper report, 재스퍼리포트라 부르며, 리포팅툴입니다. TIBC jaspersoft에서 개발하였습니다.


### jasper server 셋팅 가이드
>>
### jasper studio 셋팅 가이드
>>
### jasper+spring+mysql 연동 가이드
>>
[[xx. Jasper Report Server 설치 및 설정]]

1, 설치 url

https://community.jaspersoft.com/project/jasperreports-server/releases



2. 테스트 환경

1. os : ubuntu 14.04 / 64 bit

2. test 버젼 : jasper report server 6.4

3. tomcat 8



3. 설치 방법

step 1. install 파일 다운로드 - https://community.jaspersoft.com/project/jasperreports-server/releases

step 2. run : TIB_js-jrs-cp_6.4.0_linux_x86_64.run(로컬 환경에 맞춰 설정)

step 3. start : cd [jasperserver_dir] >> ./ctlscript.sh start 

step 4. url 접속 : http://localhost:8080/jasperserver/



4. tomcat&mysql 연동 방법

step 1. tomcat, mysql 다운로드

step 2. bin.zip 다운 : https://community.jaspersoft.com/project/jasperreports-server/releases

- mysql 연동하려면, jr-server 빌드시, jasperresport.war 가 필요한데, bin.zip 폴더에 있음

step 3. bin.zip 압축 해제

- 압축 해제후 폴더에 보면 jasperresport.war파일이 있고, 그 war 파일을 위에 설치한 jr-server에 카피한다.

step 4. [jr-server-bin dir] buildomatic/sample_confs 에 보면 mysql_master.properties 파일이 있다.

- 이 파일은 jr-server 에서 mysql을 사용하기위한 프로퍼티 파일이다. 이 파일을 [jr-server-bin dir] buildomatic 에 default_master.properties 로 카피한다.

step 5. 카피한  default_master.properties 파일을 열어 설치된 톰켓 경로와 mysql 정보로 업데이트 한다.

ex)

appServerType = tomcat8

appServerDir = /home/devleesk/dev/jr-server/tomcat8

dbType=mysql

dbHost=127.0.0.1

dbUsername=root

dbPassword=password

dbPort=3306

(xe

step 6. 설정 후 저장하고 나와, ./js-install-ce.sh 를 실행한다.

- ./js-install-ce.sh minimal 로 아규먼트를 줘 실행하면 sample 데이터를 제외하고 빌드를 한다.

y * 3 ( 디비 정보 생성 유무 물어봄 )

step 7 정상적으로 완료가 되면 톰켓/webapp에 jasperreport 프로젝트가 생성될것이고, 서버 실행을 하면 8080포트/jasperreport/ 로 접속이 가능하다.

5. e-mail 스케쥴러 설정

step 1. [tomcat]/webapps/jasperserver/WEB-INF 에 applicationContext-report-scheduling.xml 파일에서, 

<prop key="mail.smtp.auth">true</prop> 부분을 false에서 true로 변경

<prop key="mail.smtp.starttls">true</prop> 추가

step 2./home/devleesk/dev/jr-server/tomcat8/webapps/jasperserver/WEB-INF 에 js.quartz.properties 파일에서

ex)

report.scheduler.web.deployment.uri=http://localhost:8080/jasperserver

report.scheduler.mail.sender.host=smtp@gmail.com

report.scheduler.mail.sender.username=tjsrn0524@gmail.com

report.scheduler.mail.sender.password=password

report.scheduler.mail.sender.from=tjsrn0524@gmail.com

report.scheduler.mail.sender.protocol=smtp

report.scheduler.mail.sender.port=587

(xe

설정

tomcat restart
