---
title: "Client Side & Server Side Rendering"
notetype : feed
date : 04-11-2021
---

### Client Side Rendering
![[clientside.png]]


1️⃣   사이트 접속

2️⃣   서버로부터 빈 index.html 파일을 받아옴. 이때 사용자에겐 아무것도 보여지지 않음.

3️⃣   서버에게 웹사이트 구동에 필요한 모든 로직이 담긴 JS를 요청

4️⃣   서버로부터 동적으로 html을 생성할 수 있는 웹 어플리케이션 로직이 담긴 JS파일을 받아옴. 이때부터 사용자에게 보여지고, 클릭이 가능하게 됨. (viewable & interactable)







### Server Side Rendering
![[serverside.png]]

1️⃣   사이트 접속

2️⃣   서버로부터 이미 잘 만들어진 index.html 파일을 줌. 이때 사용자는 웹사이트 볼 수 있지만, 아직 동적으로 제어할 수 있는 JS파일은 받아오지 않아서, 클릭을 하더라도 아무일도 일어나지 않음. (only viewable)

3️⃣   서버에게 웹사이트 구동에 필요한 JS를 요청

4️⃣   서버로부터 JS파일을 받아옴. 이때부터 클릭 및 구동이 가능하게 됨. (interactable)







## 실전 example

✅ 웹 애플리케이션의 클라이언트-서버 아키텍처에서,  client = 웹페이지  /  server = node.js 프로그램

✅ 데이터베이스 입장에서 데이터베이스를 사용하는 node.js 애플리케이션은 클라이언트라고 볼 수 있다.

❗️client 와  server 는 정해진 게 아니라, 상황마다 다르게 정의된다.

​     ( 어떨 땐 node.js가 server역할, 어떨 땐 client 역할을 수행 )
