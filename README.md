SharpSCADA - 산업용 제어 게이트웨이, 경량 구성 소프트웨어.
===================
소개
-------------
사용된 기술:
개발 언어: C#
실행 환경: .NET Framework
데이터베이스: SQL 서버

기능:
-------------

* 1. 경량 산업용 제어 게이트웨이:
Siemens의 Profinet, AB의 EtherNetIP, Schneider의 Modbus 및 OPC와 같은 현재의 여러 주요 산업용 프로토콜을 지원합니다. OPC와 유사한 인터페이스 게이트웨이를 채택하십시오.

* 2. 데이터 수집, 보관, 조기 경고 및 구성 도구
실시간 데이터 수집, 기록 데이터 보관, 변수 트리거 경고 및 TagConfig 도구를 사용한 간단한 구성을 지원합니다.

* 3. 인간-기계 인터페이스(디자인 타임 및 런타임)

*디자인할 때:
Microsoft Visual Studio + 디자이너 플러그인 사용(VS2010-VS2015 Community Edition에서 테스트됨)
HMIControlBase 인터페이스를 상속하고 아주 적은 양의 코드를 작성하여 복잡한 기본 구성 요소를 구현할 수 있습니다.
프리미티브의 드래그 앤 드롭, 조합, 연결, 변수 바인딩 및 편집 기능을 지원합니다.

*런타임: Microsoft Visual Studio는 실행 파일로 컴파일 및 실행됩니다.


환경 준비
-------------
Windows: 지원되는 운영 체제: Windows 7/8/10/Server 2008
.NET 프레임워크 4.0/4.5/4.6
SQL서버 익스프레스 2014/2008

프로젝트 설치
-------------

최신 버전을 다운로드하고 압축을 푼다:

* 1. 프로젝트 엔지니어링 파일을 직접 열어 소스 코드를 테스트할 수 있습니다.
..\SCADA\Program에서 DataExchange.sln을 실행합니다(VS2010-2015 버전 지원).

* 2. 실행 가능한 실행 파일 테스트:
서버 측 테스트: ..\SCADA\Program\BatchCoreTest\bin\Debug 디렉터리에서 BatchCoreTest.exe를 실행합니다.
클라이언트 테스트: ..\SCADA\Program\CoreTest\bin\Debug 디렉터리에서 CoreTest.exe를 실행합니다.
문서 폴더의 "배포 프로세스" 및 "설계 프로세스" 튜토리얼을 참조하세요. 궁금한 사항이 있는 경우 "FAQ" 문서를 참조하세요.

빠른 시작
-------------
* 1. 데이터베이스 복원
* 2. 구성 파일을 수정하여 C 드라이브의 루트 디렉터리에 복사합니다.
* 3. 데이터베이스에서 드라이버 경로를 수정합니다.
* 4. 데모 실행
구체적인 프로세스는 "배포 프로세스"를 참조하세요.

개발 도구 권장 사항
-------------
Visual Studio/Blend: 구성 디자이너로서 VS2010 및 VS2015 버전을 권장합니다.

프로젝트 구조
-------------
드라이버는 현재 다음을 지원합니다.

* 게시:
메모리 데이터베이스
모드버스 TCP/RTU,
OPC DA,
지멘스 S300/200/1200/1500,
파나소닉,
AB EtherNetIP,
옴론 UDP
*다음 릴리스:
DDE,
미쓰비시

파일 디렉토리
-------------
* 데이터베이스 디렉터리 [데이터 파일 저장]:
db2014.bak 파일은 SQL Server2014 데이터 백업 파일입니다.
db2008.bak 파일은 SQL Server2008 데이터 백업 파일입니다.
test.opf는 Kepserver 4.5 데이터 파일입니다(이 소프트웨어를 통해 변수 테이블로 복원 가능).
두 개의 csv 파일은 두 개의 변수 세트입니다.

* DataConfig 디렉터리 [스토리지 구성 파일]:
host.cfg는 기본 구성 파일이며 첫 번째 줄은 게이트웨이 서버 이름/IP 주소입니다. 로컬에서 테스트하는 경우 기본 lochost를 누르십시오.
client.xml은 클라이언트 구성 파일입니다.
server.xml은 게이트웨이 서비스 구성 파일입니다.

* dll 디렉터리 [드라이버 및 타사 구성 요소 저장]:
예를 들어 OPCDriver는 OPC 통신 구성 요소입니다.
Dynamicdatadisplay: 오픈 소스 아카이브 데이터 표시 구성 요소, http://dynamicdatadisplay.codeplex.com/
WPFToolkit: WPF 오픈 소스 확장 도구 키트, http://wpftoolkit.codeplex.com
libnodave: Siemens 드라이버 오픈 소스 라이브러리(https://github.com/netdata/libnodave)

* TagConfig 디렉터리 [스토리지 구성 도구]:
드라이버, 그룹, 변수, 알람, 측정 범위 등의 정보를 쉽게 구성할 수 있습니다. 가져오기 및 내보내기를 지원합니다.

* 프로그램 디렉터리 [저장 소스 코드]:
BatchCoreTest 프로젝트는 게이트웨이 서버 테스트 코드(콘솔 디스플레이)입니다.
BatchCoreService 프로젝트는 BatchCoreTest와 동일하지만 Windows 서비스로 컴파일될 수 있습니다.
DataService 프로젝트는 프레임워크이자 기본 인터페이스 구성 요소입니다.
CoreTest 프로젝트는 샘플 파일입니다. 일련의 인터페이스 요소를 포함합니다.
HMIControl 프로젝트는 기본 구성요소입니다. 도구 모음 드래그 앤 드롭을 지원할 수 있습니다.
LinkableControlDesignTime 프로젝트는 Visual Studio 디자이너를 위한 플러그인을 지원합니다.
DataHelper 프로젝트는 SQL 데이터베이스 도움말 구성 요소이며 가변 데이터 보관을 지원합니다.
ClientDriver, ModbusDriver, OPCDriver 및 FileDriver는 다양한 통신 구성 요소입니다.

* 예시 디렉터리 [저장소 예시]:
데이터베이스를 복원하고 구성 파일을 수정하려면 문서/배포 프로세스를 참조하십시오.
BatchCoreTest.exe(서버)를 시작합니다.
CoreTest.exe(클라이언트)를 다시 시작합니다.

계획:
-------------
* .NET 코어를 지원합니다. (현재 CoreApp 폴더에 베타 버전이 있습니다)
* Omron, OPC UA 등과 같은 더 많은 통신 인터페이스 구현
* 더욱 풍부한 그래픽 구성요소: 빌딩 자동화, 화학 산업 및 기타 산업 등.
* 기능 확장: 데이터 추가 처리, 프로세스 제어 등
* 보안: 보안이 최우선 사항이며, 현재로는 충분하지 않습니다.

유리 진열장
-------------
![](https://github.com/GavinYellow/SharpSCADA/raw/master/Showcase/guage.png)
![](https://github.com/GavinYellow/SharpSCADA/raw/master/Showcase/Receiver1.png)
![](https://github.com/GavinYellow/SharpSCADA/raw/master/Showcase/scada1.png)

홈페이지
-------------
http://www.cnblogs.com/evilcat/

지도 시간
-------------
https://edu.csdn.net/course/detail/30835

연락처 정보
-------------
hijkl1999@yeah.net
QQ 그룹: 102486275

코드 기여
-------------
[topmail](https://github.com/topmail), [qwe7922142](https://github.com/qwe7922142), [tonyshen277](https://github.com/tonyshen277), [yangjingzhao123](https //github.com/yangjingzhao123), [xiebinghai](https://github.com/xiebinghai)

특허
-------------
LGPL
