# 브라우저가 html 파일을 화면에 그려내는 과정

## 1.파싱
![](https://velog.velcdn.com/images/dyflower/post/2522eb6c-0a20-467d-b498-417b76974cb0/image.png)

브라우저는 우선 html 파일을 DOM으로 변환(파싱)한다.

 - 오타 혹은 잘못된 문법을 사용했을 경우 예외처리를 한다.
 - `<link>`,`<img>` 와 같은 태그를 만나면 리소스를 다운한다.
 - `<script>`태그를 만나면 DOM파싱을 중단하고 자바스크립트를 해석한다.



 
## 2.스타일 계산

![](https://velog.velcdn.com/images/dyflower/post/ac0f5389-bba4-4e02-b276-7e7674741a68/image.png)

CSS도 파싱하여 CSSOM으로 변환한다.

 - CSSSOM 정보를 통해 돔 노드에 대한 스타일을 결정한다.
 - 결정된 스타일은 크롬 개발자 도구의 computed 항목에서 확인 가능한다.
## 3. 레이아웃
![](https://velog.velcdn.com/images/dyflower/post/cf801649-3df5-4b2d-9035-77db1c62da76/image.png)


CSSOM 정보를 토대로 레이아웃 트리(렌더 트리)를 생성한다.

- 돔과 계산된 스타일을 따라가며 요소의 크기나 좌표와 같은 정보를 담은 레이아웃 트리를 생성한다.
- 화면에 표현되는 정보만 트리에 담기게 된다.(display:none X, 가상요소 O)

## 4. 페인트


![](https://velog.velcdn.com/images/dyflower/post/0ef97d4b-a21d-4e7e-8ab0-148a8b714e17/image.png)

레이아웃 트리(렌더트리)가 생성되면 이 트리를 따라 페인트 기록이 생성된다.

 - 페인트 기록에는 요소를 렌더링하는 순서가 저장된다. 그리고 지금까지의 정보를 바탕으로 한 페이지를 여러개의 레이어로 나눈 뒤 그 위에 텍스트, 색, 이미지, 보더, 그림자 등의 모든 시각적 부분을 그리는 작업이 진행된다.
 
## 5. 컴포지팅
![](https://velog.velcdn.com/images/dyflower/post/f77251db-6b11-4048-a180-3c4c1f0edaf7/image.png)

각각의 레이어를 스크린에 픽셀로 표현하고 (레스터링) 나누었던 레이어들을 합성해 페이지를 그린다. 
