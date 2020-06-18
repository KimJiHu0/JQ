# selector02

> **id, class title**을 사용해서 태그를 불러온 후 기능을 추가하는 법.
>
> 1. **hide() :** 해당된 태그들을 모두 숨겨주는 기능을 한다.
>
> 2. **show() :** 해당된 태그들을 모두 보여주는 기능을 한다.
>
> 3. **css() :** 내가 선택한 태그에게 속성을 줄 수 있다.
>
> 4. **slideUp() :** 위로 슬라이드 되면서 해당 태그를 숨겨주는 기능.
>
> 5. **slideDown() :** 아래로 슬라이드 되면서 해당 태크를 부드럽게 보여주는 기능.
>
>     
>
>     
>
>    **[ css 기능 넣기 ]**
>
>    ```html
>    function resize(){
>    	$("img").css({"width" : "200px", "height" : "200px"});
>    }
>    ```
>
>    이미지태그의 width와 height를 200px로 바꾸자는 명령문
>
>    버튼을 클릭하면 onclick이벤트가 발생하셔 resize() 함수를 실행하게 된다.
>
>    ```html
>    <h1>이미지들의 크기를 모두 200px X 200px 로 바꾸자.</h1>
>    <button onclick="resize();">click</button>
>    ```
>
>     ![](https://postfiles.pstatic.net/MjAyMDA2MThfOTcg/MDAxNTkyNDM1OTMyOTIx.b6c5YHWi-QXQJarwZoltOVHMwW5x75_dWu6i0YaYM4Qg.5S8n55X_P7uFWNCvqr480nFNHvi7tKEcvKggDMcEbL8g.PNG.rgusqls/image.png?type=w773)
>
>     클릭을 하게되면 이미지의 기본 사이즈인 width : 100px, height : 100px 에서 200px으로 바뀌었다
>
>     
>
>    **[ id로 찾아와서 숨기기 ]**
>
>    ```html
>    function idSelector(){
>    	$("#selId").hide();
>    }
>    ```
>
>    id를 찾아오는 것은 js와 똑같이 #을 사용해주면 된다. 
>
>    hide() 괄호 안에 시간을 넣어줄 수 있다.
>
>    밀리세컨드로 계산하기 때문에 1000을 넣어주면 1초라는 뜻이다.
>
>    ""를 넣어주면 default값이 0.4초이고, 아무것도 넣지 않으면 바로 사라진다.
>
>    **show();**도 hide와 똑같이 작성하면 보여지게 할 수 있다.
>
>    이 두개를 합쳐놓은 것이 **toggle()**이라는 명령어다.
>
>     
>
>     ```html
>    <h1>이미지들 중 아이디가 selId인 태그를 찾아서 숨기자.</h1>
>    <button onclick="idSelector();">click</button>
>     ```
>
>    ![](C:\Users\rgusq\AppData\Roaming\Typora\typora-user-images\image-20200618083244192.png)
>
>     위의 click버튼을 클릭하게 되면 id가 selId인 첫번째 사진이 사라지는걸 볼 수 있다.
>
>     
>
>    **[ css로 투명도 설정하기 ]**
>
>      ```html
>    function classSelector(){
>    	$(.selClass).css("opacity", "50%");
>    }
>      ```
>
>    js와 같이 . 을 사용해서 클래스이름을 가져올 수 있다.
>
>    .selClass라는 것은 class이름이 selClass를 가져온다는 것을 의미한다.
>
>    opacity는 투명도를 설정하는 css이고, 그 위에는 투명도를 설정할 수 있다.
>
>    ```html
>    <h1>이미지들 중 class가 selClass인 태그를 찾아 투명도를 50%로 설정하자</h1>
>    <button onclick="classSelector">click</button>
>    ```
>
>    ![](https://postfiles.pstatic.net/MjAyMDA2MThfMTc2/MDAxNTkyNDM3MTU1ODMw.rrHpwmim50P1h-VQKZHXdWWKOrkRZttKSKA_Ii_e5-cg.FLcWTco27-lQFZR14MVDjjz1brd1UbTV1tz-asJuKbgg.PNG.rgusqls/image.png?type=w773)
>
>    selClass가 class이름인 오른쪽 4개의 사진의 투명도가 50%인 것을 볼 수 있다.
>
>     
>
>    **[ title로 찾아서 slideUp 적용 ]**
>
>    ```html
>    function propImg(){
>    	$("img[title*='02']").slideUp();
>    }
>    ```
>
> - **[title*=]** 속성값에 주어진 문자열이 포함되는 태그를 찾아내는 선택자
> - **[title=]** 속성값에 주어진 문자열과 정확히 똑같은 태그를 찾아내는 선택자
> - **[title!=]** 속성값에 주어진 문자열이 포함되지 않는 태그를 찾아내는 선택자
> - **[title^=]** 속성값에 주어진 문자가 첫번째로 시작하는 태그를 찾아내는 선택자
> - **[title]$=]** 속성값에 주어진 문자가 마지막으로 등장하는 태그를 찾아내는 선택자
> - **[title]** title이라는 속성이 존재하는 태그를 찾아내는 선택자
> - **[title] [id]** title과 id가 둘 다 존재하는 태그를 찾아내는 선택자
>
>   
>
>  sildeUp과 slideDown 괄호 안에는 시간을 넣을 수 있다.
>
> ```html
> <h1>이미지들 중 title속성값으로 탐색하여 slideUp 기능 적용하기</h1>
> <button onclick="propImg();">click</button>
> ```
>
>  
>
> ![](https://postfiles.pstatic.net/MjAyMDA2MThfMTcz/MDAxNTkyNDM3NzM0NTYw.G1RnEI956RDTpU6nvU4B08O7vily3jkvuQus1ySnkswg.ZzPifzBITPNUQ-U1ynn2w0F2xR9Wnb1espXrIUIVSNkg.PNG.rgusqls/image.png?type=w773)
>
>  사진으로는 보이지 않지만 자연스럽게 넘어가는걸 볼 수 있다.
>
> sildeDown오 이와 같다.
>
>  
>
> **[ prop를 이용한 이미지 바꾸기 ]**
>
>  ```html
> function changeImg(){
> 	$("td > img").prop("src","resources/img/img04.jpg");
> }
>  ```
>
>  td태그 자식으로 있는 img태그에 속성을 추가한 것이라고 볼 수 있다.
>
>  prop이랑 attr 두가지가 있다.
>
> - attr : html속성 
> - prop : js속성
>
> 속성을 추가해주는 것은 같다.
>
> ```html
> <h1>5.이미지 바꾸기</h1>
> <p>(td의 자식요소인 img만 선택해서 바꾸자)</p>
> <button onclick="changeImg();">click</button>
> ```
>
> ![](https://postfiles.pstatic.net/MjAyMDA2MThfMjM2/MDAxNTkyNDU5OTU0MTEz.ykJ3k0eVtkta3RSvIZmpiusQTXp3gnSi3P1e6ttgrgog.3HhHKASagC_Bmjm68mA97tR3dj5D8G1nD60Ywdgwp3Ag.PNG.rgusqls/image.png?type=w773)
>
> td의 자식인 img태그를 img04로 바꿔주었다.





selector선택자를 잘 이용해야한다.

