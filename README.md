# -
노드js 필기 저장

Node.js 프로그래밍

PC나 스마트폰에서 여러 가지 프로그램을 사용하고 
이 프로그램을 애플리케이션이라고 부르고 스마트폰에서는 App이라고 부른다

API란 프로그램을 쉽게 제작할 수 있게 미리 만들어 놓은 것들의 모음
Ex) 예를 들면 Windows 라는 PC용 운영체제(OS)에서 동작하는 프로그램을 쉽게
만들 수 있도록 Windows용 API가 제공된다.

클라이언트 – 다른 곳에 있는 단말에 데이터를 달라고 요청하는 프로그램
서버 – 다른 곳에서 요청받은 명령을 처리해 주는 프로그램

만든 프로그램을 인터넷에 연결하기 위해서는 단말에 네트워크 카드가 있어야 하고
두 개의 서로 다른 단말에 모두 네트워크가 들어있다면 한쪽은 클라이언트,
다른 한쪽은 서버 역할을 할 수 있다. 이때 서버는 포트를 지정하여 해당 포트로 요청을
받을 수 있다. 하나의 단말에서 사용할 수 있는 포트는 보통 0 ~ 65535 중 하나를 
지정해서 사용하고 각 포트 영역은 다음과 같이 구분된다.

 포트번호
 설명
 0번 ~ 1023번
 잘 알려진 포트(Well-known port)
 1024번 ~ 49151번
 등록된 포트(Registered port)
 49152번 ~ 65535번
 동적 포트(Dynamic port)


윈도우나 안드로이드 같은 OS가 시작될 때는 이미 잘 알려진 포트(0~1023번)에서
대부분을 사용한다. 따라서 여러분이 직접 만드는 서버 프로그램은 보통 1024번 이상의 포트 번호를 사용한다

서버를 만들어 실행 시 지정된 포트에서 클라이언트로부터 요청을 받아 처리,
또한 많은 경우에 서버는 데이터베이스에 연결할 수 있도록 구성되기 때문에 
클라이언트에서 보내온 데이터를 저장하거나 저장된 데이터를 조회한 후 클라이언트에
보낸다. 서버 중에서 평소에 많이 사용하는 웹 브라우저에서 접속하는 서버를 
웹 서버라고 하며, HTTP 프로토콜을 사용한다.
프로토콜이란 데이터를 서로 어떤 형태로 주고받을 것인지 정한 것 = 데이터의 형태
스마트폰과 같은 모바일 단말에서는 웹 문서를 웹 서버가 아닌 단말 내부에 저장해
두었다가 화면에 띄운 후 웹서버로 필요한 데이터만 요청하는 방식을 사용하기도 한다.
이때 에이잭스(Ajax) 방식으로 데이터만 받아오는 경우가 많다.
이렇게 하면 필요한 데이터만 가져온 후 부분 갱신하여 화면 처리속도가 빨라진다.

대표적인 서버 유형

채팅서버, 위치 기반 서비스 서버, 모바일 서버, JSON-RPC 서버
웹서버 – 익스프레스, 몽고디비, 뷰 템플릿, 패스포트

웹 서버의 기능

웹 서버는 웹 바르우저에서 웹 문서를 요청할 때 필요한 기능을 수행한다.
localhost(로컬 호스트)는 PC 자신을 나타내는 인터넷 주소,
인터넷상에 있는 다른 PC나 단말에 연결시도 시 IP와 같은 단말 주소를 사용하는데,
이때 다른 단말이 아닌 자기 자신을 가리킬 때 localhost라고 한다.

JSON-RPC
JSON-RPC 서버는 서버 쪽에 함수를 만들어 두고 클라이언트에서 함수를 호출하듯이
데이터를 요청하면 응답하는 서버, 주로 웹 문서가 아닌 데이터만을 주고 받을 때 사용
JSON은 어떤 형식으로 데이터를 주고 받을지를 정해 놓은 표준 데이터 포맷이고,
RPC(Remote Procedure Call) 방식으로 데이터를 주고 받는다.
RPC는 서버 쪽에 함수를 만들어 두고 클라이언트에서 함수를 호출하듯이 데이터를 
요청할 수 있도록 만들어 주는 표준이고 JSON과 RPC 표준을 함께 사용하면 서버 쪽에 
구축해야 하는 기능을 함수별로 명확하게 구분하여 만들 수 있다. = 서버관리가 쉬움

위치 기반 서비스 서버
위치 정보는 공간 데이터(Spatial Data)라고도 한다. 만약 현재 위치에서 가장 가까운
커피숍을 찾아 달라고 위치 기반 서비스에 요청하면 서버는 현재 위치에서 가장 가까운 
커피숍의 위치를 데이터베이스에 검색한다. 이때 검색 속도가 떨어지지 않도록
공간 인덱싱(Spatial Indexing) 방법을 사용한다.(보통은 B-Tree 인덱싱 방법 사용)
커피숍 관련 데이터 조회시 먼저 커피숍 데이터 저장이 가능해야하는데, 클라이언트에서
커피숍 데이터를 확인 후 서버에 데이터 추가 요청 후 위치 기반 서비스 서버는
요청 데이터를 받아 저장후 특정 영역을 지정, 그 영역 안에 있는 커피숍을 모두 찾는다
모바일 서버
모바일 단말을 사용할 때 필요한 기능을 제공하는 서버,
웹 서버를 만든 후 모바일 서비스 위주로 사용할 때도 모바일 서버라고 부르기도 한다.

노드를 만든 이유(2009년 라이언 달[Ryan Dahl])
그 당시 웹 서버에 파일 업로드 시, 업로드 완료 전까지 웹서버에서 데이터 조회등의
다른작업 불가, 이러한 문제 해결 위해 만든 서버 개발 도구가 노드

웹 브라우저에서 내 PC에 있는 문서 파일 업로드를 하고자 할 때 먼저 웹 서버에
업로드를 요청해야 한다. 이때 웹 서버는 파일 업로드 기능을 담당하는 핸들러를 하나
만든다. 

노드의 비동기 입출력 방식
하나의 요청 처리가 끝날 때 까지 기다리지 않고 다른 요청을 동시에 처리할 수 있는
비동기 입출력(논블로킹 입출력, Non-Blocking IO) 방식을 적용했다

비동기 입출력 방식이 노드의 대표적인 특징이고, 비동기 입출력 방식을 이해하려면
반대되는 의미의 동기 입출력(블로킹, Blocking IO) 파일을 읽는 과정을 먼저 알아야 한다

비동기 / 동기
비동기 방식 = 파일 시스템에 요청을 한 후에 프로그램이 대기 하지 않고 다른작업 진행
             프로그램에서 해당 파일의 내용을 처리할 수 있는 시점에 콜백함수 호출

콜백함수
자바스크립트는 변수에 함수를 할당할 수 있다. 따라서 변수에 할당된 함수를 다른 함수의 파라미터로 전달할 수 있다. 이렇게 파라미터로 전달된 다른 함수의 내부에서 호출하는 것이 콜백 함수이다.

