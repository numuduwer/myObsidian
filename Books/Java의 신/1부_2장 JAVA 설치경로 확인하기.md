

## 1. Java 설치 됐는지 확인하기 (Mac)

java를 설치해야 하는지
현재 내 컴퓨터의 어떤 버전의Java가 깔려있는지 확인하는 방법은 3가지 있다. 



### 방법1. Finder에서 찾기 

**Command + Shift + G 단축키를 누르면
Finder에서 직접 타이핑해서 원하는 경로를 들어갈 수 있다.

위 단축키를 입력해 Finder를 실행하고 
아래 명령어를 입력한다. 

~~~
/Library/Java/JavaVirtualMachines
~~~


![300](https://i.imgur.com/fjL2pZA.png)

해당 경로를 선택해 들어가주면,

![100](https://i.imgur.com/4osvObN.png)

설치한 JDK의 폴더가 나온다. 


### 방법2. 터미널에서 경로 찾아가기

1. 터미널을 연 후, 디렉토리 위치를 디폴트로 이동해준다. 
	  ~~~
	cd ~
	  ~~~
2. 터미널에 아래 커맨드를 입력해 해당 경로로 들어간다.
	~~~
	 cd /Library/Java/JavaVirtualMachines
	~~~
3. 'ls' 를 검색해 설치된 jdk 폴더를 확인한다.
	~~~
	ls
	~~~

![800](https://i.imgur.com/0kSxiRq.png)
