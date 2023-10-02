## 1. JAVA 설치하기 전에

- Java를 설치하고 사용하기 위해서는 2가지 작업을 해야 합니다. 
1. JDK설치
2. 환경변수 설정 


###  JDK란?
-  JDK(Java Development Kit)는 Java라는 언어로 개발할 수 있는 개발도구 키트이고 JDK에는 컴파일러,JRE, JVM등 개발을 위한 다양한 도구들이 들어있습니다. 

	JDK 구성 :
	- 컴파일러 :
		Java 소스파일을 바이트 코드로 변환하는 도구
	- JVM : 
		Java Virtual Machine으로 Java가 실제로 동작하는 가상환경
		Java가 다양한 OS 기기에서도 원할히 실행할 수 있도록 해준다.
	- jdb:
		  자바 디버깅 툴 
	- JRE: 
		  Java Runtime Enviroment 자바 런타임 환경
		  자바 코드를 실행시키기 위한 도구들을 가지고 있다.
		JRM은 JVM이 원할히 작동할 수 있게 해준다.

### 환경변수를 설정하는 이유? 
우리가 컴퓨터에서 어떤 파일을 실행하기 위해서는 그 파일이 존재하는 디렉토리 경로를 찾아들어가야 합니다. 
(경로로 들어가서 실행하지 않으면 파일을 찾을 수 없다는 에러가 나옵니다.)

운영체제가 어떤 명령을 받았을 때 동작은 다음과 같습니다.
~~~
1. 현재 위치한 디랙토리에 해당 명령어가 있는지 확인한다.
2. Path라는 환경변수를 가지고 있는 모든 경로에 대해 입력된 명령어가 있는지 확인한다
3. 명령어를 발견하면 실행한다  / 없으면 오류메세지를 호출한다.
~~~


즉, 우리가 환경변수에 Java경로를 설정하게 되면 
어떤 경로에서든 JAVA 명령어를 실행할 수 있게 됩니다.  (명령어 ex. java -version)


Mac환경은 터미널에 환경에 따라 (Bash, zsh) 환경변수를 설정하는 방법이 다르며, 
아래 가이드는 zsh에서 환경변수를 설정하는 방법을 다루고 있습니다. 



### 설치  전 참고사항 

- Mac에서 자바를 설치하는 방법은 두가지가 있습니다. 
	1. Oracle 홈페이지에서 JDK 다운로드
	2. brew에서 openJDK 다운로드

이 중 1번은 로그인해야하는 번거로움이 있어 2번 방법을 권장하고 
2번 brew에서 openJDK를 설치하는 경우, Mac 사양에 따라 가이드가 다르니, 자신의 Mac 이 M1, M2인지 혹은 이전버전인지 확인하고 진행해야 합니다. 
> 아래 설치방법은 M1 맥북 기준 가이드 입니다. 


## 2. JDK 설치와 환경변수 적용하기
### 방법1. Oracle 홈페이지에서 파일 다운로드

아래 링크로 접속 해 원하는 버전의 jdk를 다운받습니다.
페이지 상단에는 최신버전의 jdk 다운로드만 보이지만 스크롤을 더 내리면 다른 버전의 jdk 다운로드 화면이 있습니다.저는 1.8버전을 다운받았습니다.
( **jdk-8u281-macosx-x64.dmg**)
[오라클 홈페이지 주소]([www.oracle.com/java/technologies/javase-downloads.html](https://www.oracle.com/java/technologies/javase-downloads.html))

![](https://i.imgur.com/mIctIrH.png)



### 방법2. 터미널 brew에서 JAVA 다운로드

저는 이 방법으로 진행하기를 권합니다.
#### 1. 터미널에 아래 명령어를 입력해 brew를 설치합니다.
~~~
		/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

~~~

- brew 설치 화면
![터미널에서 검색한 예시](https://i.imgur.com/s8L2B3P.png)



먼저 brew가 제대로 설치 됐는지 터미널에 아래 명령어를 쳐서 확인합니다.
~~~
	brew -v
~~~

![](https://i.imgur.com/Qo34bKs.png)

#### 2. 패키지 저장소 추가하기
설치할 openJdk를 저장할 공간을 확보합니다.
~~~
brew tap AdoptOpenJDK/openjdk
~~~


#### 3. 설치할 버전의 패키지 명 검색하기
~~~
brew search adoptopenjdk
~~~
설치된 jdk는 체크표시가 됩니다.
![](https://i.imgur.com/NIohC5U.png)


#### 4. OpenJDK 설치하기

아래 예시를 통해 원하는 자바jdk를 설치합니다. 
~~~
brew install --cask adoptopenjdk8

brew install --cask adoptopenjdk11
~~~



#### 5. 설치된 OpenJDK 확인하기 
~~~
/usr/libexec/java_home -V
~~~
1.8, 11버전이 설치된 모습 
![](https://i.imgur.com/HeSmNGj.png)


#### 6. 원하는 자바 버전을 선택해 환경변수 설정하기

1. zsh 터미널에 환경변수를 설정하는 페이지를 실행합니다. 

~~~
open ~/.zshrc
~~~


2. 아래 명령어를 입력해 설치한 자바버전의 환경변수를 적고 `command + S` 를 눌러 저장합니다.
~~~
export JAVA_HOME=/Library/Java/JavaVirtualMachines/zulu-11.jdk/Contents/Home
export PATH=${PATH}:$JAVA_HOME/bin
~~~
![](https://i.imgur.com/RrcIBLu.png)


3. 새로 기입한 환경변수를 적용합니다.
~~~
source ~/.zshrc
~~~

4. 환경변수가 잘 적용됐는지 자바버전을 확인합니다.

~~~
java -version
~~~
![](https://i.imgur.com/AjK8Nbr.png)



#### 7. 자바 버전을 다르게 해서 적용하는경우 
- 바꾸고자 하는 JDK를 설치하고 위 방법을 그대로 진행하면 됩니다.
