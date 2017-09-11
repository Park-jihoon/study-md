#NWJS https://nwjs.io/

---

##기본 설치

###1. NWJS 홈페이지(https://nwjs.io/) 방문

###2. 프로그램 다운로드

<pre>프로그램 내부에는 NodeJS 와 Chromium 이 함께 들어있다.
</pre>

###3. 압축 풀고 실행

<pre>Hello World!</pre>

---

##패키지로 묶기

1.	ZIP 으로 APPLICATION 폴더를 압축

2.	결과 ZIP 파일의 확장자를 .nw 로 변경

3.	윈도우 기준으로 아래와 같이 합쳐준다.

<pre><code>
    copy /b nw.exe+app.nw app.exe
</code></pre>

-	단 nwjs 폴더와 함께 배포해야 한다. (더이상 nw.exe 파일은 필요없음)

-	이게 싫다면 exe 로 한방에 묶어주는 프로그램을 사용하면 됨.

-	에니그마 버추얼 박스 http://enigmaprotector.com

