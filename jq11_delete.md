# delete

> - **remove() :** 나 자신이 완전히 삭제
> - **empty() :** 내 밑에 있는 애들을 삭제
> - **detach() :** 짤라내고 나중에 붙일 수 있음
>
>  
>
>  ```html
> <style type="text/css">
> 	div{
> 		border : 2px solid red;
> 		width : 200px;
> 		padding : 10px 10px;
> 	}
> 	p{
> 		background-color : orangered;
> 	}
> 	h1{
> 		border : 1px solid blue;
> 	}
> </style>
> 
> <h1>앨리먼트 제거하기</h1>
> <div>
>     <p>remove</p>
>     <p>empty</p>
>     <p>detach</p>
> </div>
>  ```
>
> 
>
> ![](https://postfiles.pstatic.net/MjAyMDA2MjFfMjE5/MDAxNTkyNzIwNDA4Nzgx.hautnYsJH-5XFKwxk4TtSMc3jjnfzVatLI70kJtSJ3gg.4lNBEmgFddjSKL6qGk5Wh4lLh_QM4TUs4e4mMTOHyJwg.PNG.rgusqls/image.png?type=w773)
>
>  만들어진 html에서 삭제기능 3가지를 넣어보자.
>
> ```javascript
> $(document).ready(function(){
>     $("p:eq(0)").click(function(){
>         $(this).remove();
>     });
> });
> ```
>
> p태그 중 0번지를 클릭했을 때 클릭한 자신이 삭제가 된다.
>
> remove라는 p태그가 완전히 삭제된다.
>
>  
>
> ```javascript
> $(document).ready(function(){
>    $("p:eq(1)").click(function(){
>       $(this).parent().empty(); 
>    }); 
> });
> ```
>
> p태그의 1번지를 클릭하게 되면 클릭한 것의 부모인 div태그를 삭제하는데
>
> div태그 뿐만아니라 그 밑에있는 요소들까지 삭제한다.
>
>  
>
> ```javascript
> $(document).ready(function(){
>    $("p:eq(2)").click(function(){
>        var ele = $(this).detach();
>        $("h1").append(ele);
>    }); 
> });
> ```
>
> p태그의 2번지를 클릭하면 클릭한 것을 짤래니거 ele라는 변수에 담는다.
>
> 그리고 h1태그에 ele라는 변수를 붙인다.
>
> detach는 잘라내기라는 기능을 가지고 있다.