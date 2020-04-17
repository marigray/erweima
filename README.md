# erweima
小程序二维码图片自定义中间的图片

var canvas = document.createElement("canvas");
		  canvas.width = 430;
		  canvas.height = 430;
		  var context = canvas.getContext("2d");
		  var myImage = new Image();
		  myImage.src = "./a.jpg";  //背景图片 你自己本地的图片或者在线图片

		  myImage.onload = function(){
			context.drawImage(myImage , 0 , 0 , 430 , 430);
			var myImage2 = new Image();
			myImage2.src = "./c.jpg";  
			myImage2.onload = function(){
					context.beginPath()
	    			context.arc(215,215,106,0,2*Math.PI);
	    			context.fillStyle="white";
	    			context.fill();
	    			//context.stroke();
	    			context.clip();//画了圆 再剪切  原始画布中剪切任意形状和尺寸。一旦剪切了某个区域，则所有之后的绘图都会被限制在被剪切的区域内
			  context.drawImage(myImage2 , 150 , 150 , 130 , 130);
			  var base64 = canvas.toDataURL("image/png"); //"image/png" 这里注意一下
			  var img = document.getElementById('avatar');
			  document.getElementById('avatar').src = base64;
			  img.setAttribute('src' , base64);
			}
		  }
