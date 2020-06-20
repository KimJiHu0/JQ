# event

>  jQuery에서 함수를 만들어 event를 주었을 때 전파를 막기 위한 요소가 3가지가 있다.
>
> **이벤트 전파 : 각 요소가 서로 포함관계(중첩)인 경우, 요소 중 하나에 이벤트가 발생하면**
>
> **중첩된 요소들도 이벤트가 전파된다.**
>
> 
>
>  **[ 이벤트 전파 막는 방법 ]**
>
> - **stopPropagation() :** 부모태그로의 이벤트 전파를 stop 중지하라는 의미.
>
>   사용자가 작성한 이벤트 핸들러의 동작을 막아준다.
>
> - **preventDefault() :** 클릭 이벤트 외에 별도의 브라우저 행동을 막가 위해 사용.
>
>   기본이벤트 동작(사이트로 이동하는 것)을 막아준다.
>
> - **return false; :** 위의 두가지 기능들을 동시에 해주는 것.
>
>  
>
>  ![](https://postfiles.pstatic.net/MjAyMDA2MjBfNTgg/MDAxNTkyNjM3NjA4MDcy.uYEgv5F0GQHFeEpdxIhDfuXNr9tRKZxf6LtY-LuxDA8g.CRHg3j9b0_3EguRXmNIKA4ISGVZ8aDGj_x5kVjjJHREg.PNG.rgusqls/image.png?type=w773)
>
>  위와 같이 만들고 나서 전체코드를 보며 이해하자.
>
> ```html
> <!-- css속성 주기. -->
> <style type="text/css">
> 	div{
> 		width : 400px;
> 		height : 200px;
> 		border : 2px solid blue;
> 		padding : 20px;
> 		overflow : auto;
> 	}
> 	div p:first-child{
> 		float : left;
> 		border : 1px solid red;
> 		width : 150px;
> 		height : 150px;
> 		text-align : center;
> 		line-height : 150px;
> 	}
> 		div p:last-child{
> 		float : right;
> 		border : 1px solid red;
> 		width : 150px;
> 		height : 150px;
> 		text-align : center;
> 		line-height : 150px;
> 	}
> </style>
> 
> <!-- html부분 작성하기 -->
> 	<span>unbind() : 이벤트 해제</span>
> 	<div>
> 		<p>
> 			<a href="http://www.naver.com">클릭!</a>
> 		</p>
> 		<p>클릭!</p>
> 	</div>
> 	
> 	<div>
> 		<p>
> 			<a href="http://www.google.com">클릭!</a>
> 		</p>
> 		<p>클릭!</p>
> 	</div>
> 	<button>요소추가</button>
> ```
>
> 이제 jQuery를 이용하여 이벤트를 주고 막기를 하자.
>
> ```javascript
> $(function(){
>    $("a:eq(0)").click(function(e){
>        alert("a클릭");
>        e.stopPropagation();
>    });
>     $("p").click(function(e){
>         alert("p클릭");
>         e.preventDeault();
>     });
>     $("div").click(function(){
>         alert("div클릭");
>     });
>     /*
>     	위와 같이 작성을 하였을 때 a태그의 0번지를 클릭하였을 때 사용자가 지정한 a클릭, p클릭 		div클릭이 alert창에 출력이 되어야 한다.
>     	하지만 stopPropagation을 작성함으로써 사용자가 지정한 이벤트 들을 막아주고
>     	a태그를 클릭하였을 때 일어나는 alert창과 naver링크로 이동하는 이벤트만 작동한다.
>     	jQuery에서 생성한 이벤트들을 막아주어서 a클릭만 뜨고 브라우저로 이동한다.
>     	
>     	p태그를 클릭했을 때 p태그의 부모태그인 div도 영역에 있기 때문에 같이 클릭이 되어서
>     	p출력 div출력이 순차적으로 뜬다.
>     	하지만 stopPropagation()을 주게 된다면 jQuery에서 발생하는 다음 이벤트를 막기 때문에
>     	div출력이 출력되지 않고,
>     	preventDefault()를 해준다면 브라우저로 이동하는 이벤트를 막기 때문에 p출력과
>     	div출력이 뜨게 된다. 하지만 여기선 브라우저를 설정해주지 않았기 때문에 아무일도 일어
>     	나지 않는 것처럼 보인다.
>     	
>     	div태그를 클릭했을 때에는 그냥 div출력만 뜬다.
>     */
> });
> ```
>
> 
>
>   **[ bind이용하기 ]**
>
> **bind() :** 개체와 이벤트를 묶어주는 역할.
>
>  
>
> ```javascript
> $("a:eq(1)").bind({
>    "mouseover" : function(){
>        $(this).css("background-color", "skyblue");
>    },
>     "mouseout" : function(){
>         $(this).css("background-color" : "");
>    }
>     /*
>     	a태그의 1번지에 이벤트를 묶어서 넣어줬다.
>     	a태그의 1번지에 mouseover을 하게 되면 function이 실행된다.
>     	mouseover한 그 태그의 css를 변경해 주고,
>     	mouseout한 경우 그 부분의 배경을 없애준다.
>     */
> });
> 
> $("span").click(function(){
>     alert("span click");
>     $("a:eq(1)").unbind();
> });
> //span태그를 클릭하게 되면 alert창이 뜨게 되고 a의 1번지에 있는 이벤트를 삭제시킨다.
> 
> $("button"),click(function(){
>     $("body").append("<p>새로 추가된 p태그</p>");
> });
> $("body").on("click", " > p", function(){
>    alert("새로 추가된 태그에도 이벤트 적용!"); 
> });
> /*
> 	버튼을 클릭하게 되면 body부분 안에 append()괄호 안의 문구가 추가된다.
> 	그리고 on으로 이벤트를 주는데, on은 새로만들어진 태그들에게도 이벤트를 적용시킨다.
> 	$(function(){ }); 같은 경우에는 만들어져 있는 태그들에게만 이벤트를 적용시킨다.
> 	body의 자식태그인 p태그들을 클릭하는 이벤트를 만들고 function으로 alert창을 띄운다.
> */
> ```

