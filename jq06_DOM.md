# DOM탐색

>  **Docement OBbject Model** 이라고 한다.
>
> **HTML이나 XML같은 문서의 태그들을 조작 가능하도록 객체화** 시킨 것이다.
>
>  jQuery는 CSS에서 사용하던 **Selector 표현방식**으로 DOM요소를 쉽고 간결하게 접근할 수 있도록 하고
>
> 세밀하게 DOM접근을 할 수 있도록 고급 필터 또한 제공한다.
>
> 
>
> - **eq() 메서드 :** 선택한 엘리먼트들 중 인덱스로 탐색
> - **slice() 메서드 :** 선택한 엘리먼트들 중 인덱스 길이로 탐색
> - **first() 메서드 :** 선택한 엘리먼트들 중 가장 첫번째 요소 탐색
> - **last() 메서드 :** 선택한 엘리먼트들 중 가장 마지막 요소 탐색
>
>   
>
> ![](https://postfiles.pstatic.net/MjAyMDA2MjBfMjMz/MDAxNTkyNjMwMDkwMzUy.weaU5FyNf833uTrL-TcacwZSj83sR-F_8wI4Bcj9aacg.6W5XJpTpeB7zF7-a9ehSoBLTNCsCKXm16qSN2EOMDNUg.PNG.rgusqls/image.png?type=w773)
>
> 우선 위와 같은 html을 작성한다.
>
> ```html
> <pre>
> 	<b>eq() 메서드</b> : 선택한 엘리먼트들 중 인덱스로 탐색
> 	<b>slice() 메서드</b> : 선택한 엘리먼트들 중 인덱스 길이로 탐색
> 	<b>first() 메서드</b> : 선택한 엘리먼트들 중 가장 첫번째 요소 탐색
> 	<b>last() 메서드</b> : 선택한 엘리먼트들 중 가장 마지막 요소 탐색
> </pre>
> <div>
>     <p>1.eq()</p>
>     <p>2.slice()</p>
>     <p>3.first()</p>
>     <p>4.last()</p>
> </div>
> ```
>
> 
>
> 그리고 DOM탐색을 해줄 기능들을 jQUERY에서 만들어준다.
>
> ```javascript
> $(function(){
>     //div안에 자식태그인 p태그 중 0번째 인덱스를 클릭했을 때 [ "1.eq()"]
>     //pre태그의 하위태그인 b태그들 중에 0번째에 있는 ["eq() 메서드"]를 toggle()해준다.
>    $("div > p").eq(0).click(function(){
>        $("pre b").eq(0).toggle();
>    }); 
>     
>     //div태그의 자식태그인 p태그들 중 1번째 인덱스를 클릭했을 때 ["2.slece()"]
>     //pre태그의 하위태그인 b태그들 중 인덱스가 1부터 2까지 결국 1인덱스를 의미.
>     //에게 toggle()를 해준다.
>     $("div > p").eq(1).click(function(){
>         $("pre b").slice(1, 2).toggle();
>     });
>     
>     //div의 자식태그인 p태그들 중 2번째 인덱스를 클릭했을 때["3.first()"]
>     //pre의 하위태그인 b태그들 중 가장 첫번째에 있는 태그의 css 속성을 준다.
>     //color은 red로 바꾸고, text를 "연결됐다"로 바꾸어 준다.
>     //end() : 앞의 기능들을 수행해준 다음에 새로운 속성을 부여하겠다는 의미.
>     //2번째 인덱스에 있는 태그를 toggle()해주겠다는 의미.
>     $("div > p").eq(2).click(function(){
>         $("pre b").first().css("color", "red").text("연결됐		   다").end().eq(2).toggle();
>     });
>     
>     //div태그 중 자식태그인 p태그들 중 3번째 인덱스를 클릭했을 때["4.last()"]
>     //pre의 하위태그인 b태그들 중 마지막에 있는 태그를 toggle()해준다.
>     $("div > p").eq(3).click(function(){
>         $("pre b").last().toggle();
>     });
> });
> ```
>
> 
>
> --------
>
>  
>
> - **find("selector") :** 선택한 엘리먼트의 자손들 중에 탐색
> - **children("selector") :** 선택한 엘리먼트의 자식들 중 탐색
> - **parent()  / parents("selector") :** 선택한 엘리먼트의 부모/조상 탐색
> - **next("selector") :**  선택한 엘리먼트 다음 요소 탐색
>
>   
>
>  ```html
> 	<pre>
> 		<b>find("selector") : 선택한 엘리먼트의 자손들 중에 탐색</b>
> 		<b>children("selector") : 선택한 엘리먼트의 자식들 중에 탐색</b>
> 		<b>parent() / parents("selector") : 선택한 엘리먼트의 부모 / 조상 탐색</b>
> 		<b>next("selector") : 선택한 엘리먼트 다음 요소 탐색</b>
> 	</pre>
> 	
> 	<div>
> 		<p><b>1</b></p>
> 		<p id="chd">2</p>
> 		<p>3</p>
> 		<p>4</p>
> 		<p>5</p>
> 	</div>
>  ```
>
> 위와 같이 html을 작성해준다.
>
> ```javascript
> $(document).ready(function(){
>     //div태그 자손 중 b태그를 찾아 css속성을 바꾼다.
>    $("div").find("b").css({"font-size" : "50px", "color" : "yellowgreen"});
>     //div태그의 자식들 중 id가 chd인 태그를 찾아 text를 바꾼다,
>    $("div").children("#chd").text("children() 메서드!");
>     //p태그의 부모태그를 찾아(div태그) 배경을 skyblue로 바꾼다.
>     $("p").parent().css("background-color", "skyblue");
>     //p태그의 자식태그 b태그의 조상인 div의 css를 바꾼다.
>     $("p > b").parents("div").css("background-color", "dodgerblue");
>     //p태그의 0번지의 다음요소의 css를 바꾼다.(p태그의 다음요소인 b태그를 의미.)
>     $("p").eq(0).next().css({"font-size" : "30px", "color" : "lightyellow"});
> });
> ```
>
> 
>
>  ![](https://postfiles.pstatic.net/MjAyMDA2MjBfMTEx/MDAxNTkyNjMwODk0MTQ4.-Df_tDa1XaedXFFln88eRjD-qCLgZjqyfEGuTNa5JMcg.JZmrFBMtQ36ynJZOWea81cYCT2d3EiAjFQ-yX2ebWsYg.PNG.rgusqls/image.png?type=w773)
>
>  결과화면은 이러하다.
>
>   
>
> ---------
>
> - **add() :** 선택한 엘리먼트에 추가적으로 selector 표현식 작성,
> - **is() :** 선택한 엘리먼트 중에 구하는 엘리먼트가 있는지 확인.
>
>  
>
> ```html
> 	<div>
> 		<p>add()</p>
> 		<span>선택한 엘리먼트에 추가적으로 selector 표현식 작성</span>
> 		<p>is()</p>
> 		<b>선택한 엘리먼트 중에 구하는 엘리먼트가 있는지 확인</b>
> 	</div>
> ```
>
> 
>
>  ```javascript
> $(function(){
>    $("p:eq(0)").add("span").css("color","dodgerblue");
>     //p태그의 0번지와 span태그의 css를 바꿔준다.
>     //add()는 앞서 선택한 요소에 추가적으로 다른 요소를 선택해주는 의미.
>     //p태그의 0번째와 그리고 span태그를 css바꿔준다는 의미이다.
>     
>     $("div").children().click(function(){
>         //만일 내가 선택한div의 태그이름이 span이라면~
>         if($(this).prop("tagName")=="SPAN"){
>             //경고창으로 span클릭을 띄우고
>             alert("span클릭");
>             //내가 선택한 요소의 css를 바꾼다.
>             $(this).css("color", "darkblue");
>         }
>         //만일 내가 클릭한 요소들 중 p태그가 있다면
>         if($(this).is("p")){
>             //클릭한 요소의 css를 바꾼다.
>             $(this).css("background-color", "hotpink");
>         }
>     });
>     //b태그를 클릭하면
>     $("b").click(function(){
>         //div의 자식들의 css의 속성을 바꾼다.
>         $("div").children().css({"background-color" : "", "color" : ""});
>     });
> });
>  ```
>
> 
>
> ----------
>
>  
>
> #### 필터링 메서드, 트리 탐색 메서드, 기타 탐색 메서드
>
> - **필터링 메서드** : 선택한 요소를 필터링 하기 위한 메소드
> - - eq(), slice(), first(), last() ..
>
> - **트리탐색 메서드** : 관계를 맺고 있는 , 자식과 부모, 조상 , 손주 이런 식으로 나무처럼 구조를 맺고 있는 탐색
> - - find(), children(), parent(), parents(), next() ..
> - **기타 탐색 메서드**
> - - add(), is() ...
>
>  
>
>  ![](https://postfiles.pstatic.net/MjAyMDA2MjBfNTgg/MDAxNTkyNjMzODAyOTM2.g3gu46MditCqBHT1X3PvuElgY_k5fhy1a5BtdEr4wLAg.HwFuVq1k5vq86Kr_MJEoDKx93x4FvnHS_uOKqlTFNWIg.PNG.rgusqls/image.png?type=w773)
>
> 위와 같이 각 메뉴에 마우스를 올리면 메뉴가 내려오고 마우스를 떼면 사라지는 것을 구현해보자.
>
>  
>
> ```html
> 	<style type="text/css">
> 		.menu{
> 			width : 150px;
> 			background-color : skyblue;
> 			position : absolute;
> 		}
> 		#menu2{
> 			left : 170px;
> 		}
> 		#menu3{
> 			left : 340px;
> 		}
> 		a{
> 			text-decoration : none;
> 		}
> 	</style>
> ```
>
> CSS를 먼저 작성해 준 후에
>
> ```html
> 	<b>DOM탐색 메서드</b>
> 	<br/>
> 	<div id="menu1" class="menu">
> 		<a href="jq06_dom01.html">필터링 메서드</a>
> 		<div>.eq()</div>
> 		<div>.slice()</div>
> 		<div>.first()</div>
> 		<div>.last()</div>
> 	</div>
> 	<div id="menu2" class="menu">
> 		<a href="jq07_dom02.html">트리 탐색 메서드</a>
> 		<div>.find()</div>
> 		<div>.children()</div>
> 		<div>.parent()</div>
> 		<div>.next()</div>
> 	</div>
> 	<div id="menu3" class="menu">
> 		<a href="jq08_dom03.html">기타 탐색 메서드</a>
> 		<div>.add()</div>
> 		<div>.is()</div>
> 	</div>
> ```
>
> HTML부분을 작성해준다.
>
> ```javascript
> $(function(){
>     //class가 menu인 태그 중 하위요소인 div의 css를 숨긴다.
>     $(".menu div").css("display", "none");
>     
>     $(".menu").hover(function(){
>         //class name이 menu인 태그를 hover했을 때
>         //hover한 자신의 자식인 div요소들을 toggle해준다.
>        $(this).children("div").toggle(); 
>     });
> });
> ```