This is an easy Audio library that can help user to easily record live audio from web, upload audio 
to server , synthesis of sounds etc in very simple 1 line step.


1. Initialization process
	<html>
	<script src="lib.js" type="text/javascript" charset="utf-8" async defer></script>	
	<body>
	</body>
	<script>
		window.onload=function(){
			AudioContext = window.AudioContext || window.webkitAudioContext || window.msAudioContext;
			var audiocontext=new AudioContext();
			// just create an object now

			audio=new A_Audio(audiocontext); // and yes this object have a lot of power in it

		}
	</script>
 	

2. Recording audio live from microphone
	<script>
	audio.record_live(error_callback,success_callback);
	function error_callback(){}
	function success_callback(){console.log('Recording');}

			// OR
	audio.record_live(function(){},function(){console.log('Recording...')});

	</script>

and this is how easy it is to record live from mic on web browser now....


3. Pause the Reocrding on click of a button..

	audio.pause();

WEW!! Never this simple before right.
To start from paused use the same function 
audio.record_live(error_callback,success_callback);
it will not over write the whole previous data until u clear it using audio.clear();

4.  Display/stop and clear the previous recording and start again

	audio.stop(err,success,[createLink]);
	
On using stop function it stops recording but donot clear it from memory , fr tht use clear
now it have 3 arguments, 2 are normal success and error callback. 3rd one is optional and
a great feature.
Suppose u want to output the recorded file somewhere on the dom, so just pass its refrence 
example
	<div id="output"></div>

	<script>
		var x=document.getElementById('output');

		audio.record_live(error_callback,success_callback);
		setTimeout(function(){
			audio.stop(err,success,output);	
			audio.clear();
			},5000); // stop recording after 5 sec
	</script>

this could be any simpler, it will simply output the recorded file into this div, and thn
after using clear, next recording gets appended to this place

5. If you dont use clear stop will just stop recording but recrding stay in memory!
	you can then use this function to output tht recording whereever you want.
	
	(output_place  means same as that of stop ! simply pass refrence to div or nywhere u want it to
	output)

	audio.ouput_recorder_audio(ouput_place); // if not cleared thn usme data recorded will stay
	audio.clear() // remove previous recording from memory , and make place for new recrding

6. Make it ready to upload to server (php/node/any server)
	
If you havent performed audio.clear() , as said it remains in the memory!!
From there you can retrieve it in form of formData which can then be uploaded easily using
ajax/post request or anything u prefer .

	formdata=audio.get_file_formdata(); //returns formData object which thn can be passed along with ajax/php whtever u want
And it return your recorded file into formdata(); There are varous ways to thn upload it to server!
(see example for this)

7. audio.clear();

This is a final step! Use this to simply clear all of the recording recorded which is stored yet!
VERY IMPORTANT FUNCTION! MUST BE PERFORMED BEFORE ANY NEW RECORDING ELSE IT WILL KEEP USING 
PREVIOUS RECORDED DATA...

8. You want how loud/slow the user is speaking on mic.
	Or you might be making a game based on how loudness of user. 100% means user spoke very loud
	and decreases with soft speak
	THis amplitude function return amplitude of the sound made while live singing/speaking

	 audio.get_liveData_Amplitude(err,function(loudness){
		console.log(loudness);
	},[donot_output=true/false]);
// 		gives_output 0-100% depending on sound produced at input 
There are 3 functions passed,
1st is error function 
2nd is success, when there is success , it continuously watches sound comming from 
mic and tell its loudness..
3rd argument is to output the sound ,incomming from mic (default is false)


// rest are still in process functions 
IGNORE BELOW

// audio.get_spikes_live(function(){},function(spikes){console.log(spikes)},64) // default 32 and power of 2 and spikes values returned is in percentage, 100 means full
// audio.get_spikes_media(function(){},function(spikes){console.log(spikes)},64,media_file);

