# effect01 효과주기

> 효과주기에는 여러가지가 있다.
>
> - **hide() :** 숨겨주는 기능
> - **show() :** 보여주는 기능
> - **toggle() :** 클릭할때마다 숨겨주고 보여주는 기능
> - **slideUp() :** 부드럽게 올라가는 모션을 주는 기능
> - **slideDown() :** 부드럽게 내려가는 모션을 주는 기능
> - **fadeOut() :** 서서히 사라지게하는 모션을 주는 기능
> - **fadeIn() :** 서서히 나타나게하는 모션을 주는 기능
> - **fadeTo() :** 투명도를 지정해주는 기능
> - **fadeToggle() :** 클릭할때마다 서서히 사라지고 나타나게하는 기능
> - **animation :** 효과를 주는 기능
>
>  
>
>  CSS작성
>
>  ```html
> <style type="text/css">
> img {
> 	width: 200px;
> 	height: 200px;
> 	position: absolute;
> 	left: 200px;
> 	top: 100px;
> 	background-color : red;
> }
> 
> p {
> 	width: 100px;
> 	border: 1px solid red;
> 	position: absolute;
> 	left: 10px;
> 	display: none;
> }
> </style>
>  ```
>
> HTML작성
>
>  ```html
> <b>이펙트 메서드</b>
> 	<div>
> 		<p>hide()</p>
> 		<p>show()</p>
> 		<p>toggle()</p>
> 		<p>slideUp()</p>
> 		<p>slideDown()</p>
> 		<p>slideToggle()</p>
> 		<p>fadeOut()</p>
> 		<p>fadeIn()</p>
> 		<p>fadeTo()</p>
> 		<p>fadeToggle()</p>
> 		<p>animation</p>
> 	</div>
> <img alt="img" src="resources/img/img01.jpg" id="img1" />
>  ```
>
>  
>
> jQuery 기능 주기
>
> ```javascript
> $(function(){
> 	$("b").click(function(){
>         $("p").toggle();
>         //b태그를클릭하면 p태그들(메뉴들)이 toggle된다.
>         $("p").each(function(){
>            $(this).animate({
>                "top" : 50 * ( i + 1 ) + "px"
>            }, 500); 
>         });
>         //b태그를 클릭하면 p태그들 하나하나를 전부 top속성을 준다. 0.5초만에 실행.
>         //메뉴들의 간격을 주기 위해서 사용하였다.
>     });
> });
> $("p").bind("click", function(){
> //p태그들을 묶어서 클릭 이벤트를 주었다.
>     var ele = $(this);
>     //클릭된 p태그를 ele에 넣어 주었다.
>     
>     ele.css("background-color", "hotpink");
>     //p태그를 클릭하면 배경색이 hotpink로 바뀐다.
>     ele.siblings("p").css("background-color", "white");
>     //내가 선택한 요소의 p태그의 형제요소들을 찾아주어서 배경색을 바꾼다.
>     //siblings() : 선택한 요소의 ()안의 태그들의 형제요소.
>     			//만약에 내가 클릭한 변수(p태그)가 hide라는 단어를 포함하고 있다면
> 			//이미지를 숨겨주고
> 			if(ele.is("p:contains(hide)")){
> 				$("img").hide();
> 			}
> 			//p태그가 show라는 단어를 포함하고 있다면 
> 			//이미지를 보여준다.
> 			if(ele.is("p:contains(show)")){
> 				$("img").show();
> 			}
> 			//p태그가 toggle를 포함하고 있으면 이미지에 토글이벤트를 주고
> 			if(ele.is("p:contains(toggle)")){
> 				$("img").toggle();
> 			}
> 			//slideUp을 포함하고 있으면 slideUp 이벤트를 주고
> 			if(ele.is("p:contains(slideUp)")){
> 				$("img").slideUp();
> 			}
> 			//slideDown이 포함되면 slideDown 이벤트를 주고
> 			if(ele.is("p:contains(slideDown)")){
> 				$("img").slideDown();
> 			}
> 			//slideToggle가 포함된다면 slideToggle 이벤트를 주고
> 			if(ele.is("p:contains(slideToggle)")){
> 				$("img").slideToggle();
> 			}
> 			//fadeOut이 포함되면 fadeOut 이벤트를 주고 ( 서서히 사라지게하는 메서드)
> 			if(ele.is("p:contains(fadeOut)")){
> 				$("img").fadeOut();
> 			}
> 			//fadeIn이 포함되면 fadeIn 이벤트를 주고 ( 서서히 나타나게하는 메서드 )
> 			if(ele.is("p:contains(fadeIn)")){
> 				$("img").fadeIn();
> 			}
> 			//fadeTo가 포함되면 fadeTo 이벤트 주고 ( 투명도를 주는 메서드 )
> 			if(ele.is("p:contains(fadeTo)")){
> 				$("img").fadeTo(5000, 0.1); //(시간, 투명도)
> 			}
> 			//fadeToggle가 포함되면 fadeToggle 이벤트를 주고
> 			if(ele.is("p:contains(fadeToggle)")){
> 				$("img").fadeToggle();
> 			}
> 			//animation이 포함되어있으면 animate 속성을 준다.
> 			if(ele.is("p:contains(animation)")){
> 				$("img").animate({
> 					"width" : "500px",
> 					"height" : "500px",
> 					"left" : "600px",
> 					"top" : "0px"
> 				}, 2000);
> 			}
> 		});
> });
> ```
>