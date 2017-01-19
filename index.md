<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width">
	<title>clock ui</title>
	<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>
	<script src="https://cdnjs.cloudflare.com/ajax/libs/jQuery-Knob/1.2.13/jquery.knob.min.js"></script>
	<style>
		*{ margin: 0; }
		.container{
			max-width: 1200px;
			margin: 0 auto;
			/*border: 1px solid red;*/
		}
		header > h1{ 
			padding: 20px; 
			font-weight: normal;
		}
		figure{
			background: #333;
			padding: 20px 0px;
			text-align: center;
		}
		figure > .form-group{
			display: inline-block;
			margin: 0 10px;
			min-width: 25%; 
		}
	</style>
</head>
<body>
	<div class="container">
		<header>
			<h1>Knob Clock</h1>
		</header>
		<figure>
			<div class="form-group">
				<input type="text" value="0" class="hour" data-width="200" />  	
			</div>
			<div class="form-group">
				<input type="text" value="0" class="min" data-width="200" />  	
			</div>
			<div class="form-group">
				<input type="text" value="0" class="sec" data-width="200" />  	
			</div>
		</figure>
	</div><!-- end container -->

<script>

$(function(){

  function go_clock(){
    var d = new Date(),
    	hour = d.getHours(),
    	min = d.getMinutes(),
    	sec = d.getSeconds();

    // 트리거로 시간 표시
    $('.hour').val(hour).trigger('change');    
    $('.min').val(min).trigger('change');    
    $('.sec').val(sec).trigger('change');    
  }
  
  // knob 생성
  $('.hour, .min, .sec').knob(); 

  // knob 옵션 설정
  $('.hour, .min, .sec').trigger(
      'configure',
      {
      	"inputColor": "white",			// 글자 색상
         "bgColor": "rgba(0,0,0,0.3)",	// 배경색
         "skin":"tron",
         "displayInput": true				// 글자 표시
      }
  ); 

  $('.hour').trigger(
      'configure',
      {
          "min":0,
          "max":24,
          "fgColor":"#FF8C01"
      }
  ); 

  $('.min').trigger(
      'configure',
      {
          "min":0,
          "max":60,
          "fgColor":"#87CEEB"
      }
  ); 

  $('.sec').trigger(
      'configure',
      {
          "min":0,
          "max":60,
          "fgColor":"#66EE66"    
      }
  ); 

  setInterval(go_clock, 1000);  
  
});
	
</script>	

</body>
</html>
