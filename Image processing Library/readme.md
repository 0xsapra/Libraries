
Simple Image processing Library

USAGE:
	Include Library to your HTML <script src="lib.js" type="text/javascript" charset="utf-8" async defer></script>

	Then you must have a canvas element <canvas id=canvas height=600 width=600></canvas>

	Pass the Canvas element to the processing Library object 
		-image=new Processor(document.getElementById('canvas'));

	Add the Image to be processed to your object
		-image.addImage("1.png",function(){});	

	In the callback function you can use various options like
		-image.addImage("1.png",function(){
				image.effector="crazy";
				image.effect()
				 //effector can have values light, grayscale,crazy,pencil,sharpen,smooth
			});	
		-image.addImage("1.png",function(){
				 image.draw(); 				//	gives you paint brush to draw on screen
				 image.color="red"; 		//	to set the color of that paint brush
				 image.radius="1"; 			//	to set the size of stroke when painting
			});	

		-image.addImage("1.png",function(){
				 image.resize();  			//	call this function to resize the image to resize images
			});	

	Few more Stuff..