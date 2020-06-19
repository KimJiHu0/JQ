# selector04

>  ![](https://postfiles.pstatic.net/MjAyMDA2MTlfMzAw/MDAxNTkyNTU1NTc1Mjgy.Gs-0tqY0ouT3oJI3NcPuEyL7nvcfrn5S-yppeFnxUfcg.-zEXpAPoygNWmE4xmpcKM6-ps5QaM2HhIK44_cu938cg.PNG.rgusqls/image.png?type=w773)
>
>  위와 같이 User ID를 입력하지 않고 [입력하기] 버튼을 클릭하면 빨간색 글씨로 [반드시 입력해 주세요!]라는 문구가 뜨고, ID를 입력하고 [입력하기] 버튼을 클릭했을 때에는 NAVER로 가도록 하자.
>  	하단에 전체선택을 클릭하면 모두 선택되고 또 한번 클릭하면 모두 체크가 해제되고
>  전체선택을 누른 상태에서 하나라도 체크가 되어있지 않다면 전체선택 체크란이 체크가 해제되도록 하자.
>  체크박스를 체크하고 확인을 눌렀을 때
>  선택한 책 가격과 각자의 가격과 총 가격을 출력하도록 하자.
>
>  
>
>  **[ 틀 만들기 ]**
>
>  ```html
>  <form action="http://www,naver.com" id="signal" method="get">
>  <!--action : 네이버로 이동하게 해주는 속성 id를 signal로 주고 전송방식은 get방식으로 값을 숨기지 않고 전달한다.-->
>   <div>
>     	<span class="label">User ID</span>  
>       <input type="text" class="infobox" name="userId"/>
>       <span class="error" hidden="" style="color : red;">반드시 입력해주세요</span>
>       <!--hidden이란 숨겨놓는다는 속성이다.""안에 아무것도 없으면 숨긴다는 뜻이다.-->
>   </div>
>   <input type="submit" class="submit" value="입력하기"/>
>   
>   <hr/>
>      <fieldset style="300px">
>  		 <legend>체크 여부 확인</legend>
>  		 <input type="checkbox" name="all" onclick="allchk(this.checked);"/>전체선택<br/>
>   		<input type="checkbox" name="chk" value="30000"/><b>java</b><br/>
>   		<input type="checkbox" name="chk" value="25000"/><b>javascript</b><br/>
>   		<input type="checkbox" name="chk" value="20000"/><b>jquery</b><br/>
>   		<input type="button" value="확인" id="confirm"/><br/><span>선택한 책가격</span>
>   <div id="result"></div>
>   <!-- div를 만들어준 이유는 각 책들의 가격과 총 가격을 div에 담기 위해서이다. -->
>       </fieldset>
>  </form>
>  ```
>
>  
>
>  이제 모든 기능을 넣어보도록 하자.
>
>   
>
>  ```javascript
>  //입력하기 버튼을 누르면 실행되는 함수
>  $(function(){
>  	$("#signal").submit(function(){
>  		if($(".infobox").val() == null || $(".infobox").val() == ""){
>  //만약에 class이름이 infobox의 value값이 null이거나 없다면
>  			$(".error").show();
>  //class가 error인 "반드시 입력해 주세요!" 라는 문구가 보여지게 된다.
>  			retrun false;
>  //return false : 이벤트의 전파를 막는 것이다. 
>  
>  //form태그에서 submit버튼을 클릭하면 submit이벤트가 발생하고 form태그 action 속성에 들어있는 경로로 form 태그 내부의 name속성의 값을 전달한다. 
>  }
>  });
>  });
>  ```
>
>  ```javascript
>  //전체선택을 클릭하면 전부 선택되고 하나라도 빠지만 전체선택 해제하기
>  $("input[name=chk]").click(function(){
>  //input의 name이 chk인 것들을 클릭하게 되면 function 실행.
>  if($("input[name=chk]").length == $("input[name=chk]:checked").length){
>  //만약에 input의 name이 chk인 수와 input의 name이 chk, 체크되어있는 길이가 같다면
>  $("input[name=all]").prop("checked", true);
>  //input의 name이 all인 애들의 체크 속성을 찾아서 true해주자(체크해주자)
>  } else{
>  $("input[name=all]").prop("checked",false);
>  //그렇지않고 하나라도 체크가 되어있지 않다면 name이 all인 input 체크박스를 false로 바꿔주어 체크를 풀어주자
>  }
>  ```
>
>  ```javascript
>  //선택된 체크박스들의 value값을 가져와서 계산하고 출력하자-
>  $("#confirm").click(function(){
>  $("#result").empty();
>  
>  if($("input[name=chk]:checked").length == 0){
>  alert("하나이상 체크해주세요!");
>  //만약에 체크되어있는 애들이 == 0 이라면 alert창을 띄어준다.
>  }
>  //하나 이상이라면 (값을 계산하는 부분)
>  else{
>  var total = 0;
>  $("input[name=chk]:checked").each(function(i){
>  ///체크되어있는 애들을 for each문을 돌면서 하나씩 가져오고 function안에 i는 인덱스 의미
>  var chk = $(this);
>  //chk변수에 선택된 자신를 담는다.
>  var book = chk.next().text();
>  //input태그 찾아서 다음태그의 text를 담는다.
>  var price = chk.val();
>  
>  $("#result").append(book + " : " + price + "<br/>");
>  total += parseInt(price);
>  //total에 체크되어있는 ㄱ애들의 value값을 하나씩 더해주는 것이다.
>  parseInt를 해준 이유는 jq에서는 뭐든 문자열로 반환한다.
>  그래서 parseInt를 써주지 않으면 20000과 30000의 합은 2000030000으로 출력이 될 것이다
>  이것을 숫자형으로 변환해주어야 값이 계산이 된다.
>  });
>  //그리고 id가 result인 태그에 가장 뒤에 ()안에 있는 문구를 더해준다.
>  }
>  });
>  ```
>
>  ```javascript
>  //체크박으 "all"을 체크하면 전체선택 되고 만일 전체선택 된 상황에서 chk가 하나라도 체크가 해제된다면 all의 체크박스도 해제되게 하자
>  
>  function allchk(bool){
>  $("input[name=chk]").each(function(){
>  			//.attr("attr name") / .prop("prop name") : 엘리먼트의 속성 값
>  			//.attr() : html의 속성(attribute)을 가져온다.
>  			//.prop() : javascript의 프로퍼티(property)를 취급하는 메서드
>  $(this).prop("checked",bool);
>  //위에서 찾아온 객체 하나하나를 의미한다.가져와서 name이 chk라는 곳에 checked 속성을 추가한다.
>  });
>  }
>  ```
>
>  위의 함수는 전체선택이라는 버튼을 클릭했을 때 전부다 클릭하게 만들어주는 함수이다.