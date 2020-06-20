# replace

>  **replaceWith() :** 선택한 모든 요소를 지정된 요소로 대체한다.
>
> ```javascript
> $(function(){
>    $("button:first").click(function(){
>       $("p").replaceWith("<p><b>replaceWith()</b></p>"); 
>    }); 
> });
> ```
>
> ```html
> <div>
>     <p>dom 대체</p>
>     <p>test</p>
> </div>
> <button>바꾸기(replaceWith)</button>
> ```
>
> 버튼태그의 첫번째를 클릭하게 되면 함수가 실행된다.
>
> 내가 선택한 모든 p태그를 뒤에 언급한 replaceWith라는 문구로 대체해준다.
>
> replaceWith의 인수로 HTML코드형식의 문자열, jQuery객체, HTML, DOM요소, 배열 등을 전달받을 수
>
> 있다.
>
> 위의 경우 p태그인 애들이 지정된 b태그로 대체된다.
>
> target.replaceWith(New) : 타겟을 지우고 new라는 것을 새로 만든다. (함수도 들어갈 수 있다.)
>
>  
>
> 
>
> **replaceAll() :** 선택한 요소를 지정된 요소로 대체한다.
>
> ```javascript
> $(function(){
>    $("button:last").click(function(){
>        $("<p><b>replaceAll()</b></p>").replaceAll("p");
>    }); 
> });
> ```
>
> ```html
> <div>
>     <p>dom 대체</p>
>     <p>test</p>
> </div>
> <button>바꾸기(replaceAll)</button>       
> ```
>
> 마지막 버튼태그를 클릭했을 때 함수가 실행된다.
>
> 앞의 요소를 생성해서 p태그로 대체할 수 있다.
>
> new.replaceAll(target) : 바꿀게 뒤로 올거고 새로만들게 앞으로간다. 함수는 들어갈 수 없다.
>
> replaceAll의 인수로 jQuery 객체, HTML, DOM요소, 배열 등을 전달받을 수 있다.

