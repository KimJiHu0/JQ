# selector03

>  ![](![image-20200619162851395](C:\Users\rgusq\AppData\Roaming\Typora\typora-user-images\image-20200619162851395.png)
>
>  우선 이러한 html을 작성을 한다.
>
> ```html
> <form action="">
>     <input type="text"/>
>     <!-- text를 입력받는 input태그 만들기 -->
>     <input type="button" value="선택" onclick="c1();"/>
>     <!-- 일반 버튼을 만든 후 onclick event로 c1함수 실행 -->
>     <input type="radio" value="20-04-14" onclick="c2();"/>
>     <!-- radio버튼 타입의 input태그 만들고 onclick event로 c2함수 실행 -->
>     <input type="checkbox" value="(빅데이터 전문 개발자 과정)" onclick="c3();"/>
>     빅데이터 전문가
>     <!-- checkbox타입 input태그 만들고 onclick event로 c3함수 실행 -->
>     <div id="a">
>         <select>
>             <option value="1">one</option>
>             <option value="2">two</option>
>             <option value="3">three</option>
>         </select>
>     </div>
>     <!-- div영역 안에 select 안에 option을 만들기 -->
> </form>
> ```
>
> ------
>
>  ![](https://postfiles.pstatic.net/MjAyMDA2MTlfODcg/MDAxNTkyNTUyMjUwODU4._iZBcJWaBpGYq7T8A2v2oAd-EXIoI_OI4Mr0BTAy5ikg.xzUwGaJtdM744_39wJoEjwUAr-BRGnzESBarv5kLrgwg.PNG.rgusqls/image.png?type=w773)
>
>  input 타입이 text인 입력창 안에 입력하고 선택을 누르면 asd라는 alert창이 뜨게 만들기.
>
>  
>
> ```html
> function c1(){
> 	var doc=$("input:text").val();
> <!-- 변수 doc에 input의 타입이 text인 애의 입력값(value값)을 담아준다. -->
> 	alert(doc);
> }
> ```
>
>  
>
> ------
>
>  ![](https://postfiles.pstatic.net/MjAyMDA2MTlfMzkg/MDAxNTkyNTUyNDI2MjU2.IjdPadpzHavVj5Gd-Dp7L7520Dog1QBwrINy_nS5zoAg.yZQ15azWagXbfUgtJxsy5Gj3Czyo4rT3aJsHWgDde8Ig.PNG.rgusqls/image.png?type=w773)
>
> input 타입이 radio인 체크란을 체크하면 20-04-14라는 alert창이 뜨게 만들기.
>
> ```html
> function c2(){
> 	var doc=$("input:radio").val();
> 	<!-- 변수 doc에 input타입이 radio인 태그의 value값을 가져와서 담는다는 의미 -->
> 	alert(doc);
> 	<!-- 그래서 doc에 input타입이 radio인 태그의 value값을 저장, 이것을 alert에 출력 -->
> }
> ```
>
>  
>
> ------
>
> 
>
>  ![](C:\Users\rgusq\AppData\Roaming\Typora\typora-user-images\image-20200619164601933.png)
>
>  input 타입이 checkbox인 체크박스를 클릭하게 되면 아래에 (빅데이터 전문 개발자 과정)
>
> 이라는 문구가 띄어지게 하기
>
>  
>
> ```html
> function c3(){
> 	var doc=$("input:checkbox").val();
> <!-- input의 타입이 checkbox인 태그의 value값을 가져와 doc에 담는다. -->
> 	$("#a").html("<b>" + doc + "</b>");
> <!-- id가 a인 태그에 추가를 할건데 html()과 text()의 차이를 잘 알아야한다.
> html() : html은 html속성을 그대로 반영해서 입력을 해주는 것이다. 
> text() : text는 ()안의 문구를 그대로 text에 작성해주는 것이다.
> 위와 같은 예제를 보면 만약 text()를 사용했더라면 <b>빅데이터 전문 개잘자 과정</b>라는 문구가
> 뜰 것이고, html로 했기 때문에 <b>가 태그로 인식이 되어 폰트를 굵게 만들어주는 속성이 적용됐다.
> -->
> }
> ```
>
> ------
>
>  
>
>  ![](https://postfiles.pstatic.net/MjAyMDA2MTlfMjIz/MDAxNTkyNTUzMTI5MTA3.cN3T_ksEjqkxnFhkscCkL8lT_NVBAVgl-Wt9T9ay4o8g.8K5l3RT4pTg5kd777-XzyS1zfaI-kACLPdsG_gYoPLkg.PNG.rgusqls/image.png?type=w773)
>
>  
>
>  select안에 option을 눌렀을 때 alert창으로 클릭한 것에 해당하는 value값을 리턴하는 화면이다.
>
> ```html
> <!--
> JS에서 window.onload와 같은 의미를 가지고 있다.
> 아무런 action을 하지 않아도 사용하기 위해서 $(function(){})을 사용하는 것이다.
> JS에서 태그에 이벤트를 주기 위해서는 onclick 이벤트를 주고, 그에 맞는 함수를 설정해줬지만
> JQ에서는 그렇게 하지 않고도 이벤트를 실행해줄 수 있다.
> -->
> $(function(){
> 	var selElem = document.getElementsByTagName("select")[0];
> <!-- 태그네임이 select인 태그의 0번지를 selElem에 담았다.-->
> 	selElem.onchange=function(){
> <!-- 태그네임을 담은 변수 selElem이 onchange한다면(변한다면)함수를 실행시키라는 의미
> 태그네임 select의 0번지를 담은 selElem이 변한다면!-->
> 	alert(selElem.options[selElem.selectedIndex].value);
> <!-- 태그네임이 select인 태그의 0번지를 담은 selElem의 options[인덱스].value.
> options의 인덱스를 의미하는데 [selElem.selectedIndex]는 options의 인덱스를 지정한다.
> 그리고 내가 선택한 option의 index의 value값을 가져와서 alert창에 출력하게 된다
> one을 선택하면 그의 value값인 1이 출력이 되고
> two를 선택하면 그의 value값인 2가 출력이 되고
> three를 선택하면 그의 value값인 3이 출력이 된다-->
> }
> });
> ```
>
> 
>
>  