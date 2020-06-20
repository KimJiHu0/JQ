# effect02

>  ul과 li태그로 메뉴들을 만들어준다.
>
> ```html
> 	<p>메뉴 만들기</p>
> 	<ul type="square" class="main_menu">
> 		<li class="sub_menu1"><b>(1)CSS 셀렉터</b>
> 			<ul type="circle" class="sub_menu2">
> 				<li>tag로 선택</li>
> 				<li>id로 선택</li>
> 				<li>class로 선택</li>
> 				<li>parent child로 선택</li>
> 				<li>parent &gt; child로 선택</li>
> 				<li>:nth-child(n/even/odd)로 선택</li>
> 				<li>:first-child로 선택</li>
> 				<li>:last-child로 선택</li>
> 			</ul>
> 		</li>
> 		<li class="sub_menu1"><b>(2)속성셀렉터</b>
> 			<ul type="circle" class="sub_menu2">
> 				<li>[attr]</li>
> 				<li>[attr=value]</li>
> 				<li>[attr!=value]</li>
> 				<li>...</li>
> 			</ul>
> 		</li>
> 		<li class="sub_menu1"><b>(3)폼셀렉터</b>
> 			<ul type="circle" class="sub_menu2">
> 				<li>:input type</li>
> 			</ul>
> 		</li>
> 		<li class="sub_menu1"><b>(4)사용자 정의 셀렉터</b>
> 			<ul type="circle" class="sub_menu2">
> 				<li>:eq(n)</li>
> 				<li>:first</li>
> 				<li>:last</li>
> 				<li>:even</li>
> 				<li>:odd</li>
> 				<li>:parent</li>
> 			</ul>
> 		</li>
> 	</ul>
> ```
>
> 
>
>  ```javascript
> $(function(){
>     //b태그인 (1),(2),(3),(4).. 를 클릭하게되면 함수가 실행된다.
>    $("b").click(function(){
>        $(this).next().slideToggle();
>        //내가 클릭한 b태그의 동일선상에 있는 태그를 slideToggle() 속성을 준다.
>        $(this).parent().siblings().find("ul").slideUp();
>        //내가 선택한 태그 외의 메뉴들을 보이지 않게 하기 위한 명령어다.
>        //내가 선택한 b태그의 부모인 li태그 (class가 sub_menu1인 태그)들
>        //안에 ul태그를 찾아서(class가 sub_menu2인 태그) sildeUp()속성을 준다.
>    }); 
> });
>  ```
>
> 
>
> --------------
>
> 
>
>  또다른 effect
>
> 이미지 3개를 준비하고 on/off와 이미지를 클릭했을 때  기능을 준다.
>
> ```javascript
> $(function(){
>     //id가 btn이라는 버튼을 클릭했을 때에 함수 실행
>    $("#btn").click(function(){
>        //버튼을 클릭했을 떄 img태그에게 버튼을 한번 누르면 onOffImg라는 class속성을 주고
>        //한번 더 클릭했을 때는 class속성을 빼주는 기능을 준다.
>        //toggleClass() : toggle속성과 마찬가지로 누를때마다 class속성을 줬다 뺐다 한다.
>        $("img").toggleClass("onOffImg");
>    }); 
>     //img태그를 클릭했을 때 함수 실행
>     $("img").click(function(){
>         //만일 내가 클릭한 이미지가 addSize라는 class속성을 가지고 있다면.
>         //hasClass() : class속성을 가지고 있는지 없는지 찾아주는 기능
>         if($(this).hasClass("addSize")){
>             //내가 선택한 이미지의 addSize라는 class속성을 제거하고
>             //tittle를 "이미지 축소"로 바꿔주고
>             $(this).removeClass("addSize").attr("tittle", "이미지 축소");
>         } else{
>             //그렇지 않다면 내가 선택한 이미지에 addSize라는 class속성을 추가하고
>             //tittle를 "이미지 확대"로 바꿔준다.
>             $(this).addClass("addSize").attr("tittle", "이미지 확대");
>         }
>     });
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
>
>  
>
> 