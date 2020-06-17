# selector

> 먼저 jquery를 사용하기 위해서는 jquery 라이브러리를 가져와야한다.
>
> ```html
> <script type"text/javascript"></script>
> <!-- 원래는 이 안에 js 혹은 jq를 작성했지만 jquery의 라이브러리를 가져오기 위해서는 src를 작성해 주어야 한다. -->
> 
> <script type"text/javascript" src="resources/js/jquery-3.5.1.min.js"></script>
> <!-- 이렇게 작성해주면 jquery의 라이브러리를 가져오는데 성공했다. 그리고 js혹은 jq를 저 script 태그 안에서 작성하면 안된다. 절대! -->
> ```
>
> 
>
> **selector**에는 js와 비슷하게 여러가지가 있다.
>
> ```html
> <script type="text/javascript" src="resources/js/jquery-3.5.1.min.js">
> 	/*
> 		밑의 방식은 javascript에서 window.onload와 같은 의미로 사용된다.
> 		화면이 켜졌을 때 바로 실행되는 것을 의미한다.
> 		불러오는 속도는 document가 더 빠르다.
> 	*/
>  
>  //eq의 의미는 0번지 인덱스에 위치한 div를 칭한다.그에 속성을 준거다.
>  $(document).ready(function(){
>      $("div:eq(0)").css({"border" : "1px solid red", "width" : "400px", 		           "height" : "200px"});
>      $("#view").css({"border" : "1px solid red", "width" : "400px", "height" :         "100px"});
>  });
>  
>  function answer01(){
>      //TagName selector
>      $("span").css("color", "blue");
>      //Id selector ( # )
>      $("#view").text('$("span").css("color", "blue");');
>  }
>  function answer02(){
>      //$()가 아닌 다른 방법도 있으나 너무 길어서 사용하지 않는다.
>      jQuery("#t1").css("color", "pink");
>      jQuery("#view").text('jQuery("#t1").css("color", "pink");');
>  }
>  function answer03(){
>      //Class selector
>      $(".t2").css("color", "yellowgreen");
>      $("#view").text('$(".t2").css("color", "yellowgreen");');
>  }
>  function answer04(){
>      //하위선택자. li 안에 있는 span 태그를 불러온다.
>      $("li span").css("color", "silver");
>      $("#view").text('$("li span").css("color", "silver");');
>  }
>  function answer05(){
>      //자식선택자. li의 바로 밑의 자식인 span태그를 불러온다.
>      $("li > span").css("color", "gold");
>      $("#view").text('$("li > span").css("color", "gold");');
>  }
>  function answer06(){
>      //nth-child() : ()안에 숫자를 넣으면 그것에 대한 x번째 [인덱스아님]
>      //odd : 홀수를 의미한다. 1,3,5,7,9 .. 번째
>      $("li:nth-child(odd)").css("color", "lime");
>      $("#view").text('$("li:nth-child(odd)").css("color", "lime");');
>      //even : 짝수를 의미한다. 2,4,6,8,10.. 번째
>      $("li:nth-child(even)").css("color", "red");
>      $("#view").text('$("li:nth-child(even)").css("color", "red");');
>  }
>  function answer07(){
>      //first-child : xx태그의 첫번째 자식을 의미한다.
>      $("li:first-child").css("background-color", "black");
>      $("#view").text('$("li:first-child").css("background-color", 	                   "black");');
>      
>      //last-child : xx태그의 마지막 자식을 의미한다.
>      $("li:last-child").css("background-color", "skyblue");
>      $("#view").text('$("li:last-child").css("background-color", "skyblue");');
>  }
>  //초기화버튼을 누르면 원래상태로 돌아오게하는 함수
>  function reset(){
>      //공백은 아무것도 안해준다는 의미이다.
>      $("il").css("color","black").css("background-color","");
>      $("span").css({"color" : "black", "background-color" : ""});
>      $("#view").text('$("span").css({"color" : "black", "background-color" : 		""});');
>  }
> </script>
> ```
>
> - 아무것도 쓰지않고 태그네임을 쓰는 것은 태그선택자이다.
> - #을 사용하고 id이름을 사용하는 것은 id선택자이다.
> - .을 사용하고 class이름을 사용하는 것은 class선택자이다.
>
>  
>
> ```html
> <!-- body부분 작성 -->
> <body>
> 	<h1>selector 표현식</h1>
> 	
> 	<div>
> 		<ul>
> 			<li><span>tag로 선택</span></li>
> 			<li id="t1">id로 선택</li>
> 			<li class="t2">class로 선택</li>
> 			<li><span>parent child로 선택</span></li>
> 			<li><b><span>parent &gt; child</span></b>로 선택하기</li>
> 			<li>:nth-child(n / odd / even)로 선택하기</li>
> 			<li>first-child로 선택하기</li>
> 			<li>last-child로 선택하기</li>
> 		</ul>
> 	</div>
> 	
> 	<hr/>
> 	
> 	<div>
> 		<button onclick="answer01();">태그선택(span)</button>
> 		<button onclick="answer02();">id선택(t1)</button>
> 		<button onclick="answer03();">class선택 (t2)</button>
> 		<button onclick="answer04();">p c 선택</button>
> 		<button onclick="answer05();">p &gt; c 선택</button>
> 		<button onclick="answer06();">nth-child 선택</button>
> 		<button onclick="answer07();">first-child 선택</button>
> 		<button onclick="answer08();">last-child 선택</button>
> 		<br/>
> 		<button onclick="reset();">reset</button>
> 	</div>
> 	
> 	
> 	<h2>code</h2>
> 	
> 	<div id="view"></div>
> </body>
> ```
>
>  
>
> ![](https://postfiles.pstatic.net/MjAyMDA2MTdfMjYz/MDAxNTkyMzg3NDI5MTU0.0Mvhpl4TLI_LrDTsL5_4wvPHl0mUo8xL0b2LL_MNLxkg.RSrus4jaNdO75kRrDcOwaIivUFtxauZWEg3Eu0DBUBwg.PNG.rgusqls/image.png?type=w773)