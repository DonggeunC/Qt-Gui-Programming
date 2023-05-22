# Qt-Gui-Programming

## Qt파일 기본 작성

- Qt파일의 헤더는 항상 QApplication 사용

- QLabel함수의 첫 번째 매개변수는 입력하고자하는 내용, 두 번째 매개변수는 부모 레이아웃

- 생성된 Project파일에 QT += widgets 추가 (리눅스에서 직접 QMake시)

- 빌드 순서는 qmake -project 후 qmake로 Makefile 생성, 그 다음 make
