1.Angular-Cli 정리
==================

### 1.1. Angular-Cli란?

Angular CLI는 간단한 명령어를 사용하여 Angular 프로젝트를 생성, 실행, 빌드할 수 있으며 다양한 구성 요소를 선별적으로 추가할 수 있는 인터페이스이다.

가벼운 개발용 서버인 Serve를 내장하고 있어서 별도의 서버 설정 없이 프로젝트를 웹브라우저로 실행시켜 동작을 확인할 수 있다.

Angular CLI가 지원하는 기능은 아래와 같다. 자세한 내용은 [cli.angular.io](https://cli.angular.io/)를 참고하면 된다.

#### 1.1.1. Angular-Cli 프로젝트의 생성개요

```
  1.  Angular 프로젝트 생성
  2.  Angular 프로젝트에 컴포넌트, 디렉티브, 파이프, 서비스, 클래스, 인터페이스 등의 구성 요소 추가
  3.  내장 개발 서버를 사용한 Angular 프로젝트 실행
  4.  Unit/E2E(end-to-end) 테스트 환경 지원
  5.  배포를 위한 Angular 프로젝트 패키징(Webpack)
```

---

### 1.2. Angular-Cli 설치

#### 1.2.1. 주의사항

```
Angular CLI는 Node.js 6.9.0, npm 3.0.0 이상이 필요하다.
만약, Node.js가 6.9.0 이상 버전이 설치되어 있지 않다면 새로 설치한다.

Node.js 버전 확인은 아래와 같다.
```

<pre><code>$ node -v</code></pre>

#### 1.2.2. Node.js 설치

-	[nodejs.org](https://nodejs.org/ko/) 에서 Node.js 최신버전을 다운로드 받을 수 있다.
-	npm은 Node.js 설치시 함께 설치되므로 별도의 설치 과정이 필요없다.

#### 1.2.3. Angular-Cli 전역설치

-	아래의 커맨드로 Angular-Cli를 전역으로 설치한다.

	```
	$ npm install -g @angular/cli
	```

-	이미 Angular-cli가 설치되어 있고, 업그레이드를 하고 싶다면 아래와 같이 실행한다.

	```
	$ npm uninstall -g angular-cli
	$ npm cache clean
	$ npm install -g @angular/cli
	```

#### 1.2.4. 설치 완료 확인

-	설치가 완료되면 ng 명령어를 사용할 수 있다.

	```
	$ ng version
	```

#### 1.2.5. 기타 명령어 확인

-	Angular-Cli의 사용법을 자세히 알고싶다면 ng Help 명령어를 사용한다.

	```
	$ ng help
	```

---

### 1.3. 프로젝트 생성

-	Angular 프로젝트를 생성하기 위해서는 ng new 명령어를 사용한다. (my-app은 프로젝트 폴더명이다)

	```
	$ ng new my-app
	```

-	ng new 명령어가 실행되면 프로젝트명과 일치하는 my-app이라는 새로운 프로젝트 폴더가 생성되고 기본 골격(스캐폴딩)이 작성된다. 폴더 구조는 아래와 같다.

-	Root 폴더

	```
	my-app/
	├── e2e/
	├── node_modules/
	├── src/
	├── .angular-cli.json
	├── .editorconfig
	├── .gitignore
	├── karma.conf.js
	├── package.json
	├── protractor.conf.js
	├── README.md
	├── tsconfig.json
	└── tslint.json
	```

-	위 파일 및 폴더의 기본 골격 구조에 대한 자세한 설명은 [Angular 퀵스타트](https://angular.io/guide/quickstart) 를 참조하면 된다.

---

### 1.4. 프로젝트 실행

-	프로젝트는 가벼운 개발용 서버인 Serve를 실행하면 된다. 프로젝트 폴더로 이도 이동 후, ng serve 명령을 실행하면 된다. 만약, Serve 시동 후 웹브라우저가 즉시 열리기를 기대한다면 ng serve —open을 실행한다.

	```
	$ cd my-app //프로젝트 폴더로 이동
	$ ng serve  //Serve 시동
	```

-	ng serve명령어를 실행하면 Webpack을 사용하여 소스코드와 의존 모듈을 번들링(Bundling)하고 Angular CLI가 내장하고 있는 개발용 서버인 Serve를 실행한다.

-	브라우저에서 http://localhost:4200 로 개발용 서버에 접속하면 프로젝트가 실행된다.

---

### 1.5. 프로젝트 빌드

-	프로젝트의 개발 완료 이후 배포를 위해서는 ng build 명령어를 사용한다. 실행하면 프로젝트 폴더 내에 /dist 폴더에 트랜스파일 된 파일들이 생성된다.

	```
	$ ng build
	```

-	ng build 방식으로 생성된 결과물은 프로덕션 버전에 최적화 되어 있지는 않다. 최종적으로 프로덕션 버전으로 최적화 해서 빌드하고자 한다면 아래와 같은 명령을 실행한 후 배포한다.

	```
	 $ ng build -prod
	```

---

2.의존성 관리
=============

### 2.1. npm을 통한 의존성 관리

1.	각종 플러그인이나 라이브러리 등 외부 의존성 파일들은 기본적으로 npm을 통해 관리한다.
2.	오래된 플러그인이나 npm을 통한 의존성 관리가 용의치 않은 플러그인은 예외적으로 /src/assets/vendor 폴더 내에서 관리한다.

---

### 2.2. 모듈 관리

#### 2.2.1. 모듈설치

-	기본적으로는, npm은 모듈을 로컬모드로 설치한다. 로컬모드란, 패키지를 명령어를 실행한 디렉토리안에 있는 node_modules에 설치하는 것을 의미한다.

	아래와 같은 명령을 실행하면,

	```
	  $ npm install @ng-bootstrap/ng-bootstrap --save
	```

-	/src/node_modules폴더에 @ng-bootstrap/ng-bootstrap(모듈 이름) 폴더를 생성하고 그 안에 ng-bootstrap 기능이 패키징된다. 그리고, package.json 파일의 의존성 목록에 아래와 같이 기록한다.

	```
	    {  "name": "editor",
	      "version": "0.0.0",
	      "license": "MIT",
	      "scripts": {
	      "ng": "ng",
	      "start": "ng serve",
	      "build": "ng build",
	      "test": "ng test",
	      "lint": "ng lint",
	      "e2e": "ng e2e"
	    },
	      "private": true,
	      "dependencies": {
	      "@angular/common": "^4.0.0",
	       .......
	      "@angular/router": "^4.0.0",
	      "@ng-bootstrap/ng-bootstrap": "^1.0.0-beta.4",
	```

-	package.json에 npm을 통해 설치한 의존성 파일을 기록하기 위해서는 —save 옵션을 반드시 넣어주어야 한다.

---

#### 2.2.2. 모듈 제거

-	설치된 모듈을 제거하기 위해서는 아래와 같은 명령어를 실행한다.

	```
	$ npm uninstall @ng-bootstrap/ng-bootstrap --save
	```

-	package.json에서 @ng-bootstrap/ng-bootstrap 항목을 지우기 위해서는 —save 옵션을 반드시 추가해 주어야 한다.

---

#### 2.2.3. 모듈 업데이트

-	모듈을 업데이트하기 위해서는 아래와 같은 명령어를 실행한다.

	```
	$ npm update @ng-bootstrap/ng-bootstrap —save
	```

---

3.Node-Sass 사용
================

### 3.1. Node-sass 란?

-	sass는 css를 확장하는 스크립팅 언어(CSS pre-processor)로서, sass를 트랜스파일하여 브라우저에서 일반적으로 사용할 수 있는 css파일로 변환한다.

---

### 3.2. Node-Sass 설치

-	sass를 컴파일하는 방법은 여러 가지이지만, Node.js 환경에서 작업을 하므로, 아래 명령어로 node-sass를 설치한다.

	```
	// NPM 을 통하여 node-sass 글로벌 설치
	$ npm install -g node-sass
	```

### 3.3. Sass 트랜스파일

-	node-sass를 사용해 sass를 css로 트랜스파일한다.

	```
	// 컴파일하여 현재 디렉토리에 저장
	$ node-sass /디렉토리/app.scss –o .


	// style.scss 파일에 변화가 있을 떄 마다 자동으로 리컴파일
	$ node-sass /디렉토리/app.scss -w -o .
	```

<hr/>

박지훈 pohinian@gmail.com
