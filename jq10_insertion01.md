# insertion01

> - **prepend() :** 선택한 요소의 앞에 ()안에 문구를 추가한다.
> - **append() :** 선택한 요소 뒤에 ()안에 문구를 추가한다
>
>  
>
>  ![](https://postfiles.pstatic.net/MjAyMDA2MjFfMjIx/MDAxNTkyNzE1NTU2ODg2.ZhbiIU2SsDqoqptJvf74qw6LxvsjJ7QoPzTkm9UtQt4g.SM4OhnZ4ZBMvATWiaDPwA96DBEekM--uZde3ZU2YCVgg.PNG.rgusqls/image.png?type=w773)
>
>  위의 html을 작성하자.
>
> ```html
> <style type="text/css">
> 	div{
> 		border : 1px solid red;
> 	}
> 	.prepend{
> 		border : 1px dotted blue;
> 	}
> 	.append{
> 		border : 1px dotted green;
> 	}
> </style>
> --------------------------------------------
> 
> <button>prepend</button>
> <button>append</button>
> <button>html</button>
> <button>text</button>
> 
> <div>
>     <p>내부삽입하기1</p>
>     <p>내부삽입하기2</p>
> </div>
> ```
>
> 
>
>  ```javascript
> $(function(){
>    var cnt = 0;
>     
>     $("button:eq(0)").click(function(){
>         $("div").prepend($("<p>").addClass("prepend").text("prepend"+(cnt++)));
>     });
> });
>  ```
>
> 0번지 버튼을 클릭하게 되면 div에 p태그를 추가해 준다.그 p태그에는 Class속성 prepend를 주고
>
> text로 prepned1 ... div 안에 넣어준다. prepend이기 때문에 가장 앞에 붙는다.
>
>  
>
> ```javascript
> $(function(){
>    var cnt = 0;
>     
>     $("button:eq(1)").click(function(){
>         $("div").append($("<p>").addClass("append").text("append"+(cnt++)));
>     });
> });
> ```
>
> 1번지의 버튼을 클릭하게 되면 div에 p태그를 추가하고 append라는 Class속성을 추가한다.
>
> 그리고 text로 append1 ...을 div안에 넣어준다. append이기 때문에 가장 뒤에 붙어진다.
>
>  
>
>  ![](https://postfiles.pstatic.net/MjAyMDA2MjFfMjU5/MDAxNTkyNzE2NjUzMDk4.4zljC5H1hXq6vsrrS-5T6tKEYSbtsYl9GnU70vIDipgg.ujbX-0RulPoqOch2ojiEwf2lfj1sIq-7Qyt-GAzSihkg.PNG.rgusqls/image.png?type=w773)
>
>  
>
> - **text() :** text를 있는 그대로 출력을 한다.
>
> - ```javascript
>   $("button:eq(3)").click(function(){
>       $("div").text("<b>text요소를 바꾼다.</b>");
>   });
>   ```
>
>   text() 괄호 안에 있는 문구를 문구 그대로 출력을 해준다.
>
>    
>
> - **html() :** html 요소로 바꾸어준다.
>
> - ```javascript
>   $("button:eq(2)").click(function(){
>       $("div").html("<b>html요소로 바꾼다</b>");
>   });
>   ```
>
>   html()괄호 안에 있는 문구를 html속성에 따라 b태그로 바꾸어서 출력해준다.
>
> -------------
>
>  
>
> - **after() :** A.after(B); A뒤에 B를 추가한다.
> - **insertAfter() :** A.insertAfter(B); B뒤에 A를 추가한다.
> - **before() :** A.before(B); A앞에 B를 추가한다.
> - **insertBefore() :** A.insertBefore(B); B앞에 A를 추가한다
>
>  
>
>  ![](https://postfiles.pstatic.net/MjAyMDA2MjFfMTI2/MDAxNTkyNzE3NTM4NTc5.3c9nuYeDMJ2w4iU7TU1CahpLksdFdfe5Ytw1mrp0qYkg.2MN7TDVELx7xp-h4ZbecTVc80F-Wzf1BAjPtWpzQEl0g.PNG.rgusqls/image.png?type=w773)
>
>  
>
>  ```html
> <style type="text/css">
> 	div{
> 		border : 1px solid red;
> 	}
> </style>
> 
> -----------------------------------
> 
> 	<button>after()</button>
> 	<button>insertAfter()</button>
> 	<button>before()</button>
> 	<button>insertBefore()</button>
> 	
> 	<div id="base">
> 		<p>외부 삽입 메서드</p>
> 	</div>
>  ```
>
> 
>
> ```javascript
> $(function(){
>    $("button:eq(0)").click(function(){
>        $("#base").after("<div>새로운 엘리먼트(after)</div>");
>    }); 
> });
> ```
>
> A.after(B)의 형식으로 작성되며, id가 base인 태그 다음에 ()안의 문구를 추가한다.div는 태그로 만들어짐.
>
>  
>
> ```javascript
> $(function(){
>    $("button:eq(1)").click(function(){
>        $("<div>새로운 앨리먼트(insertAfter)</div>").insertAfter("#base");
>    }); 
> });
> ```
>
> B.insertAfter(A); 형식으로 작성되며 앞의 문구를 div태그로 만들어 id가 base인 태그 다음에 추가한다.
>
>  
>
>  ```javascript
> $(function(){
>    $("button:eq(2)").click(function(){
>        $("#base").before("<div>새로운 앨리먼트 추가(before)</div>");
>    }); 
> });
>  ```
>
> A.before(B); 형식으로 작성되며 id가 base인 태그 전에 ()안의 문구를 div태그로 만들어 추가한다.
>
>  
>
> ```javascript
> $(function(){
>     $("button:eq(3)").click(function(){
>         $("<div>새로운 앨리먼트(insertBefore)").insertBefore("#base");  
>     });
> });
> ```
>
> B.insertBefore(A); 형식으로 작성되며, ()안의 문구를 div태그로 새로 만들어 id가 base인 태그 전에 추가한다.
>
> ---------------------
>
>   
>
>  wrap() : 선택한 요소를 ()안의 것으로 감싸주는 것
>
> unwrap() : 선택한 요소를 ()안의 것을 벗기는 것
>
> wrapInner() : 선택한 요소 하나하나를 ()안의 것으로 감싸는 것
>
> wrapAll() : 선택한 요소를 전부 묶어서 ()안의 것으로 한번에 감싸는 것
>
>  
>
> 
>
>  
>
> ![](https://postfiles.pstatic.net/MjAyMDA2MjFfMTQ1/MDAxNTkyNzE4NTAzMDky.0LZpYEqEJcYjb3VOg-9lGGEisM_Wm00a6V3gGsbwJvYg.AiAeIPAFiyYeBHlbvRRHGLM6thuB5Il83Y8N9cTAciUg.PNG.rgusqls/image.png?type=w773)
>
>   
>
> ```html
> <style type="text/css">
>     .box{
>         border : 2px solid red;
>     }
>     #menu{
>         background-color : skyblue;
>         text-align : right;
>     }
>     a{
>         text-decoration : none;
>         font-size : 20px;
>     }
>     #menu div{
>         display : inline-block;
>         margin-right : 10px;
>     }
>     
> </style>
> 
> 
> <div id="menu">
>     <div class="sub_menu">
>         <a href="#"><span>국비지원</span></a>
>     </div>
>     
>     <div class="sub_menu">
>         <a href="#">훈련검색</a>
>     </div>
>     
>     <div class="sub_menu">
>         <a href="#">질문답변</a>
>     </div>
>     
>     <div class="sub_menu">
>         <a href="#">오시는길</a>
>     </div>
> </div>
> ```
>
> ```javascript
> $(function(){
>     //box라는 class속성을 가진 div태그를 만들어서 $box변수에 담아준다.
>     //.box라는 속성을 div태그를 만들어 넣어준것과 같은 의미.
>    var $box = $("<div>").addClass("box"); 
>     
>     //sub_menu라는 class이름을 가진 태그들 중 first인 태그에게 $box에 담은 div태그를 씌운다.
>     $(".sub_menu:first").wrap($box);
>     
>     $(".sub_menu").click(function{
>         //class이름이 sub_menu인 태그들을 전부 찾아와서,
>     	$(".sub_menu").each(function(){
>         	//만약 내가 선택한 태그의 부모가(내가 선택한 a링크의 부모) .box라는 class속성을
>         	//가지고 있다면
>         	if($(this).parent().is(".box")){
>                 //.box라는 class속성을 벗겨라.
>                 $(this).unwrap(".box");
>             }
>     	});
>     //그리고 내가 선택한 태그에게 $box를 씌어라.
>     $(this).wrap($box);
>     });
> //wrapInner() : 태그 하나하나에 span태그를 씌우는 것이다.
> //a태그가 10개가 있다면 그 하나하나를 찾아서 span태그를 씌우는 것.
> $("a").wrapInner("<span></span>");
> //wrapAll() : 태그의 전체에 b태그를 씌우는 것.
> //pre태그 전부를 싸잡아서 b태그로 씌운다.
> $("pre").wrapAll("<b></b>");
> });
> ```
>
> 
>
>  
>
>  
>
>  
>
> 