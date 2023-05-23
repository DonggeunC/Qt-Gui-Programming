# Qt-Gui-Programming

## Qt파일 기본 작성

- Qt파일의 헤더는 항상 QApplication 사용

- QLabel,QButton 등의 객체 생성 시 첫 번째 매개변수는 입력하고자하는 내용, 두 번째 매개변수는 부모 레이아웃

- 생성된 Project파일에 QT += widgets 추가 (리눅스에서 직접 QMake시)

- 빌드 순서는 qmake -project 후 qmake로 Makefile 생성, 그 다음 make

## Qt cpp파일 작성

- Connect 함수는 sender,Signal,receiver, method(slot),type(optional) 의 형태를 가짐 -> ex) connect(button, SIGNAL(clicked()), &app, SLOT(quit()));

- Connect의 3번째 매개변수인 목적지가 빠진 상태면 this를 나타냄

- Customwidget의 cpp파일에서 사용된 this는 parent를 가르킴 -> main window로 볼 수 있음

- 사용자 정의 시그널을 만든 후 emit을 사용하여 시그널과 슬롯을 연결 -> 시그널 포워딩으로 cpp에서 슬롯 대신 signal(),signal()을 이용하여 main에서의 시그널과 슬롯 연결 가능

## Qt Creator

- qApp = 객체 전역 변수

- Help의 Index를 통해 라이브러리 검색 가능

- ui의 Design을 통해 widget 배치, 배치된 ui의 widget을 클래스 cpp파일에서 ui를 통하여 호출 ex) ui->pushButton

- 클래스 파일에서 함수를 바로 사용하면 this가 적용되어 main window에 작용

- Signal에 의해서 사용되는 함수로 사용하기 위해 Slot함수(processClick()) 등록 -> connect(ui->pushButton,SIGNAL(clicked()),this,SLOT(processClick()));

- QFile의 객체인 pFile을 생성하여 "/dev/ledkey_dev"를 오픈, pFile의 handle()함수를 이용하여 파일 디스크립터를 반환

- 새로 생성한 QSocketNotifier객체인 pKeyLedNotifier를 통해 handle로 반환 받은 소켓의 데이터가 Read할 수 있는지 확인 후 시그널 출력 (SIGNAL(activated()))

- activated시그널이 입력되면 부모 객체의 readKeyData슬롯을 연결

- readKeyData슬롯에서 키 입력이 인식되면 updateKeyDataSig라는 시그널을 보냄 -> KeyLed 객체인 pKeyLed에서 시그널을 받아 체크박스에 업데이트하는 슬롯을 연결 -> 키입력에 따라 체크박스 체크 or 해제

- UI의 다이얼을 돌리면 pDialLed객체에서 valueChanged 시그널을 발생시키고 그 시그널이 발생하면 Led가 숫자에 맞추어 Binary로 작동, 그리고 pProgressBar 객체에 setValue슬롯 작동

- Signal과 Slot의 함수의 매개변수는 일치해야됨

- 토글 버튼으로 작동하게 하기 위하여 signal의 clicked함수의 매개변수를 bool을 주고 slot역시 매개변수가 일치해야 되므로 bool을 준다.

## Qt 작성 후 배포

- Release모드를 활성화 후 빌드, 빌드된 Release폴더에서 실행파일(exe)만 새로운 폴더를 만든 후 가져옴

- Qt-cmd(Qt 프롬프트)를 열고 windeployqt [실행파일 경로] 명령어 입력

- 실행 파일만 있던 폴더에 dll파일들이 생기면서 실행이 가능해짐

- window에서 작성한 프로젝트를 리눅스로 samba를 통해 옮김(pro.user 제외) -> cp로 가져온 후 qmake와 make한 후 사용

## Qt Tab Widget 작성

- 참조연산자 & -> 포인터처럼 주소공간을 이용, 변수의 공간을 참조하여 값을 리턴할 수 있도록 함

- main widget에서 tab widget을 생성 후 각각의 탭에 따라 class파일을 작성

- main widget에서 각 탭의 포인터 변수의 setLayout함수를 이용하여 각각의 클래스 파일이 작성한 탭을 main ui로 연결
