JQ 기본 작성법

>### **Jquery 기본 작성법**
>
>**css selector(표현식) + javascript** 와 섞여있다.
>
>ex > 
>
>**$("selector").메서드();**
>
>**$("p").css("color", "red");**   p태그를 찾아서 color를 red로 바꿔주자는 의미.



> ### **기능 구현 2가지 방법**
>
> - 1번.
>
> - ```javascript
>   $(function() {
>   	//작성
>   });
>   ```
>
> - 2번.
>
> - ```javascript
>   $(document).ready(function(){
>       //작성
>   });
>   ```



> ### **함수 작성**
>
> ```html
> <!-- 이 부분은 script 태그 안에 작성한다. -->
> function hightlight(){
> 	$("#list01 > li").eq(0).css("background-color", "skyblue");
> 	<!-- id가 list01인 태그의 자식태그 li의 0번지 li의 css를 배경을 하늘색으로. -->
> }
> $(function(){
> 	$("img").click(function(){
> 		alert("이미지를 클릭했습니다.");
> 		$(this).hide();
> <!-- click했을 때 function이 실행된다. 그리고 자기 자신 img를 숨긴다. -->
> 	});
> });
> 
> function showImg(){
> 	$("img").show();
> <!-- 클릭해서 사라진 사진을 보여주는 함수이다. -->
> }
> 
> function resizeImg(){
> 	$("img").css("height", "100px").css("width", "100px");
> 	<!-- 100px * 100px 사이즈의 img로 바꿔준다. -->
> }
> function addImg(){
> 	$("img").last().after('<img src="resources/img/img01.jpg"/>');
> <!-- 이미지를 만들어서 추가해주는 함수. -->
> }
> function toggleImg(){
> 	$("img").toggle();
> <!-- 클릭해줄 때마다 이미지가 보여졌다 숨겨졌다 한다. -->
> }
> 
> 
> <!-- 이 부분은 body부분에 작성한다. -->
> <ul>
>     <li>1. 셀렉터 표현식</li>
>     <li>2. DOM탐색 메서드</li>
>     <li>3. 이벤트 메서드</li>
>     <li>4. 이펙트 메서드</li>
>     <li>5. ajax</li>
> </ul>
> <button onclick="hightlight();">리스트 강조하기!!</button>
> 
> <hr/>
> 
> 
> <button onclick="showImg();">이미지 보이기</button>
> <button onclick="resizeImg();">이미지 축소</button>
> <button onclick="addImg();">이미지 추가</button>
> <button onclick="toggleImg();">이미지 숨기기/보이기</button>
> 
> 
> <div>
>     <img alt="test" src="resources/img/img01.jpg"/>
> </div>
> ```



> 위의 예제는 아래 버튼을 클릭하게 되면 onclick 이벤트가 발생하고, 그로 인해 함수가 실행된다.
>
> [ **리스트강조하기** ] 버튼을 누르게 되면 [ **1.셀렉터 표현식** ] 의 배경색이 skyblue가 되고
>
> [ **img** ] 를 클릭하면 "이미지를 클릭했습니다." 라는 alert창이 뜨고 사진이 숨겨진다.
>
> [ **이미지보이기** ] 를 클릭하면 숨겨졌단 사진이 다시 보여지게 되고
>
> [ **이미지 축소** ] 를 누르면 지정해놓은 크기만큼 사진이 축소한다.
>
> [ **이미지 추가** ] 를 누르면 똑같은 사진이 추가가 되고
>
> [ **이미지 숨기기/보이기** ] 를 누르면 한번 누르면 숨겨지고 또 누르면 보여진다.

![](https://postfiles.pstatic.net/MjAyMDA2MTRfMjQ3/MDAxNTkyMTM1ODI5NDcw.-G7ao8yaC2Yd30KdZU3vFUAbqSkC0C_7Bu4V3EtiRYMg.e10-GQAskwzkAp29EUTNiXt2MNsHEcHTyRqbtzUlFqwg.PNG.rgusqls/image.png?type=w773)