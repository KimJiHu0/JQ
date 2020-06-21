# ajax01

>  **ajax :** ajax란 서버의 처리를 기다리지 않고 비동기 요청이 가능한 것을 의미한다.
>
> 비동기 : 서버 모르게 값을 가져온다.
>
> 원래 링크를 이동할 때 페이지가 깜빡거리면서 창이 뜨게 되는데 이것은 클라이언트와 서버의 요청과
>
> 응답이 이루진다는 뜻이다.
>
> 하지만 ajax 비동기를 이용하게 되면 그런 현상 없이 뒤에서 몰래 데이터를 가져올 수 있다.
>
>  
>
>  ![](https://postfiles.pstatic.net/MjAyMDA2MjFfMTU0/MDAxNTkyNzI0NzQ3NzEw.3Y9H5FCsJEtNYVFuMDs6QXYPe5qkQpWwLbtMp-lonn0g.uYSSPratAwwwzLtwcCKDQhWPMw_NQkPdFVMhx1hiW_8g.PNG.rgusqls/image.png?type=w773)
>
>  위와 같은 html을 만들어 비동기적으로 데이터를 가져오자.
>
> ```html
> <style type="text/css">
>     *{
>         margin : 0px;
>         paddind : 0px;
>     }
>     table{
>         width : 400px;
>     }
>     table tr:nth-child(odd){
>         background-color : orange;
>     }
>     fieldset{
>         width : 400px;
>     }
>     body{
>         width : 1000px;
>         margin : 50px auto;
>     }
> </style>
> 
> <h1>데이터 가져오기</h1>
> <fieldset>
>     <legend>사원정보 조회</legend>
>     <input type="text" name="empid"/>
>     <input type="button" id="emp_search" value="조회"/>
> </fieldset>
> <table>
> <tr>
> 	<th>사원번호</th>
>     <th><input typ="text" name="empid"</th>
> </tr>
> <tr>
> 	<th>이름</th>
>     <th><input type="text" name="lastname"/></th>
> </tr>
> <tr>
> 	<th>이메일</th>
>     <th><input type="text" name="email"/></th>
> </tr>
> <tr>
> 	<th>전화번호</th>
>     <th><input type="text" name="phone"/></th>
> </tr>
> <tr>
> 	<th>입사일</th>
>     <th><input type="text" name="hire"/></th>
> </tr>
> </table>
> ```
>
> 
>
>  ```javascript
> $(function(){
>    $("#emp_search").click(function(){
>        //id가 emp_search인 태그를 클릭했을 때
>        //input태그의 name이 empid인 태그의 value값을 empid라는 변수에 담는다.
>        var empid = $("input[name=empid]").val();
>        
>        //유효성 검사
>        
>        //만일 empid가 숫자이고 길이가 2보다 크면
>        //isNaN : 숫자가 아니다.
>        //!isNaN : 숫자이다.
>        if(!isNaN(empid) && empid.length > 2){
>            
>            //ajax가 실행된다.
>            $.ajax({
>                //전송할 페이지주소(./emplist.xml)
>                url : "emplist.xml",
>                //전송 방식
>                method : "GET",
>                //비동기(default), 동기(false)
>                async : true,
>                //전송받을 데이터타입(xml, json, html, script 형태로 받을 수 있다.)
>                dataType : "xml",
>                //전송할 데이터
>                //data : {"key", "value"},
>                
>                //만일 통신(연결)에 성공하면 
>                success : function(data){
>                    /*
>                    	data : 위에서 연결 성공한 xml 타입의 데이터를 의미한다.
>                    	이 데이터를 파라미터로 가져와서 사용한다.
>                    	그 중에서 find할 것인데 EMPLOYEE_ID가
>                    	내가 입력한 사원번호를 포함하고 있다면. 그의 부모를
>                    	즉, 사원번호가 100인 것의 부모 : ROW를 의미힌다.
>                    	그 ROW를 empInfo라는 변수에 담아준다.
>                    */
>                    var empInfo = 			 
>                        $(data).find("EMPLOYEE_ID:contains("+empid+")").parent();
>                    console.log(empInfo);
>                    
>                    /*
>                    	변수 empInfo에게 ROW라는 태그가 존재한다면
>                    	table의 하위태그 input태그들을 하나하나 가져온다.
>                    	그리고 내가 입력한 그 사원번호의 ROW한 줄의 value값의 자식들의
>                    	인덱스를 0부터 마지막번지까지 돌면서 text를 입력해준다.
>                    */
>                    if(empInfo.is("ROW")){
>                        $("table input").each(function(i){
>                            $(this).val($(empInfo).children().eq(i).text());
>                        });
>                        //그렇지 않으면 검색 대상이 좋재하지 않는다는 alert창을 띄운다.
>                    } else {
>                        alert("검색 대상이 존재하지 않습니다.");
>                    }
>                },
>                //연결이 되지 않았을 경우..
>                error : function(request, error){
>                    alert("code : "+request.status+"\n\n"+"message : " + 
>                          request.reponseText+"\n\n"+"error : " + error);
>                }
>            });
>        } else {
>            alert("사원번호를 다시한번 확인해주세요!");
>        }
>    }); 
> });
>  ```
>
> 
>
>  ![](https://postfiles.pstatic.net/MjAyMDA2MjFfOTIg/MDAxNTkyNzI2NjM5ODAw.FW6S3Q66Hd27daYZeSr52hPQZY-Zwfv9YLElWIrYupYg.ehkQYbm1XPLQYXq3DZs_gbpH0sqvwbqIcUQpWlKb11og.PNG.rgusqls/image.png?type=w773)
>
>  
>
> ---------
>
>  
>
> # ajax02
>
>  ![](https://postfiles.pstatic.net/MjAyMDA2MjFfMTQz/MDAxNTkyNzI2NzcxMjM3.hvQGwBlkGCgWIYdnGutV7MbpxuFrDLEGmJ6qNfKJM90g.xXuU85RSa1ZEOycO77ZMz285BpG4TdPVYrUpu0o61dkg.PNG.rgusqls/image.png?type=w773)
>
>  위의 표를 먼저 만든다.
>
>  ```html
> <style type="text/css">
> *{
> 	margin : 0px;
> 	padding : 0px;
> }
> table{
> 	width : 900px;
> }
> table tr:nth-child(1){
> 	background-color : skyblue;
> }
> fieldset {
> 	width : 400px;
> }
> body{
> 	width : 1000px;
> 	margin : 50px auto;
> }
> </style>
> 
> 	<h1>데이터 가져오기</h1>
> 	
> 	<fieldset>
> 		<legend>사원 전체 조회</legend>
> 		<input type="button" value="조회" id="emp_search"/>
> 	</fieldset>
>  ```
>
> 
>
>    
>
> 작업을 하기 전에 emplist.xml파일을 사용하려면 지금 우리가 html을 만들고 있는 폴더 밑으로 넣어주자.
>
> 
>
>  ```javascript
> //src경로에 있는 js파일을 사용하기 위해서 작성해줘야한다 꼭!
> <script type="text/javascript" src="resources/js/create_table.js"></script>
> 
> 
> 
> $(function(){
>    $("#emp_search").click(function(){
>        $.ajax({
>            url : "emplist.xml"
>            dataType : "xml",
>            success : function(msg){
>            var empRowList = $(msg).find("ROW");
>            $("body").append(makeTable(empRowList));
>        },
>            error : function(){
>                alert("통신 실패");
>            }
>        });
>    }); 
> });
>  ```
>
> id가 emp_search인 태그를 클릭을 하게 되면 ajax가 실행이 된다.
>
> url은 우리가 사용하기 위해서 넣어놓은 emplist.xml파일이다.
>
> datatype 역시 xml타입이다.
>
> 성올을 하게 된다면 function이 실행될 것이다.
>
> function()안에 들어간 파라미터는 이름을 정해놓은 건 아무 의미 없다.
>
> msg : 우리가 받은 , 통신이 성공해서 받은 xml파일을 파라미터로 받은 것이다.
>
> 사실 msg는 파일이 아니라 데이터들이다.
>
> datatype를 xml이라고 정해줬기 때문이다.
>
> 그것들이 데이터로 들어올 수 있고 사실상 String, 문자들이 들어온다.
>
>  
>
> 우리가 가져온 xml타입의 데이터들에서 ROW를 찾을 것이다. 그리고 그걸 empRowList라는 변수에
>
> 담아준다.
>
> 그 후에 body태그 안에 append해줄 것인데 makeTable(EmpRowList) 는 아직 생성해주지 않았다.
>
> 아직 table를 만들지 않았기 때문에 이제 만들러 가보자
>
> ```javascript
> //makeTable안에 파라미터로 들어온 elem은 위에서 만든 변수 empRowList를 뜻한다.
> //우리가 찾아온 ROW들을 모은 변수를 가져왔다.
> function makeTable(elem){
>     //var이라고 명시를 하면 지역변수이고
>     //그렇지 않으면 전역변수이다.
>     //전역변수로 테이블을 하나 만들어줬다.
>     $table = $("<table border = 1>");
>     
>     //이 부분은 가장 위에 row의 이름을 가져오기 위해 for문을 한번만 돌렸다.
>     for(var i = 0; i < 1; i++){
>         //tr을 하나 만들어 준 후에
>         $tr = $("<tr>");
>         //j를 0부터 우리가 가져온 row의 0번지에 있는 자식들 (사원번호 이름 이메일 번호 입사일)
>         //의 길이만큼 j를 증감해주면서 돌 것이다.
>         for(var j = 0; j < elem.eq(0).children.length; j++){
>             //td를 row의 0번지에있는 자식들의 길이만큼 돌면서 만들어주는데
>             //그 td안에는 우리가 가져온 row들 중 0번지의 자식의 0번지부터 마지막번지까지
>             //j for문을 돌며 tagName을 가져올 것이다.그리고 td에 담을 것이다.
>             $td = $("td").append(elem.eq(0).children().eq(j).prop("tagName"));
>             //그렇게 담긴 td변수를 tr변수에 담아주고
>             $tr.append($td);
>         }
>         //그렇게 담은 tr변수를 table변수에 담아주어 가장 윗줄을 완성했다.
>         $table.append($tr);
>     }
>     
>     //이제 본격적으로 사원들의 정보를 조회할 것이다.
>     //i를 0부터 가져온 row들의 길이만큼 i를 증감해주면서 for문을 돌 것이다.
>     for(var i = 0; i < elem.length; i++){
>         //그러면서 tr을 가지고 있는 row의 길이만큼 만들어준다.
>         $tr = $("<tr>");
>         //for문 j를 가져온 row들의 i번지의 자식들의 길이만큼 돌 것이다.
>         //0번지의 자식들을 다 돌게되면 1번지의 자식들을 다 돌것이다.
>         //이를 row의 마지막 row까지 갈때까지 반복한다.
>         for(var j = 0; j < elem.eq(i).children().length; j++){
>             //row의 자식들이 가진만큼 td를 만들면서 그 안에 row의 0번지의 자식의 0번지부터
>             //자식의 마지막번지까지, 그리고 다 찾았다면 row의 1번지부터 자식의 0~마지막번지
>             //의 text를 가져와서 td에 담을 것이다.
>             $td = $("<td>").append(elem.eq(i).children.eq(j).text());
>             //그리고 td에 담긴 정보들을 tr이라는 변수에 담아준다.
>             $tr.append($td);
>         }
>         //그리고 tr에 담진 정보들을 table이라는 변수에 담아주고
>         $table.append($tr);
>     }
>     //정보들이 다 담긴 table변수를 return해준다.
>     return $table;
> }
> ```
>
> 마지막에 작성한 return $table는 가장 위에서 만든
>
> ```javascript
> $("body").append(makeTable(empRowList));
> ```
>
> 부분에서 makeTable(empRowList)가 $table로 리턴이 된다는 뜻이다.
>
> 결국 우리가 다 만든 정보들을 body에 append해준다는 의미이다.
>
> 
>
>  ![](https://postfiles.pstatic.net/MjAyMDA2MjFfMTkg/MDAxNTkyNzI2NzkyMjQx.7TM5rL5gyj3ZASb3cBiUL5Jl0IfB85AIpa9i1FcIdcog.O3OqmL7gerdIrT0DqQnDOWSsXtse2cnc3lMS0dO_sUUg.PNG.rgusqls/image.png?type=w773)
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