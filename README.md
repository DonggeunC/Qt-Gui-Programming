# Qt-Gui-Programming

## Qt파일 기본 작성

- Qt파일의 헤더는 항상 QApplication 사용

- QLabel,QButton 등의 객체 생성 시 첫 번째 매개변수는 입력하고자하는 내용, 두 번째 매개변수는 부모 레이아웃

- 생성된 Project파일에 QT += widgets 추가 (리눅스에서 직접 QMake시)

- 빌드 순서는 qmake -project 후 qmake로 Makefile 생성, 그 다음 make

## Qt cpp파일 작성

- Connect 함수는 sender,Signal,receiver, method(slot),type(optional) 의 형태를 가짐 -> ex) connect(button, SIGNAL(clicked()), &app, SLOT(quit()));

- Connect의 3번째 매개변수인 목적지가 빠진 상태면 this를 나타냄

- Customwidget의 cpp파일에서 사용된 this는 parent를 가르킴

- 사용자 정의 시그널을 만든 후 emit을 사용하여 시그널과 슬롯을 연결 -> 시그널 포워딩으로 cpp에서 슬롯 대신 signal(),signal()을 이용하여 main에서의 시그널과 슬롯 연결 가능

## Qt Creator

- Help의 Index를 통해 라이브러리 검색 가능

- ui의 Design을 통해 widget 배치, 배치된 ui의 widget을 클래스 cpp파일에서 ui를 통하여 호출 ex) ui->pushButton

- 클래스 파일에서 함수를 바로 사용하면 this가 적용되어 main window에 작용

- Signal에 의해서 사용되는 함수로 사용하기 위해 Slot함수(processClick()) 등록 -> connect(ui->pushButton,SIGNAL(clicked()),this,SLOT(processClick()));
