CrestJson
==========

CrestJson 0.01 (pronounce like Crest-John)
Beta Build

This is an open source html5 configurable script that will allow Andriod devices, Windows ie Chrome/Firefox, Windows Phones, Mac (yuck), 
and other compatible html5 devices access your crestron control system. This appliction uses a CrestJson server a proxy 
to communication with the actual devices via Json objects.


Release Notes
=============
Android/Iphone/Netbook/Chrome aka (html5 compatible) multi-zone software 

I've been working on an open source html5 application that can run on all my device in my house (andrioid/win xp/win7/windows server 2012/ubuntu/slax).
It seems like html5 was the obvious solution.  I have it in an open source repository on get hub http://www.github.com/SinnerDC2/CrestJson/ .  
It still very beta, but I'm actually using at my house (see demo video).  This application is modeled as a single page application which communicates using 
Json to a self hosting API controller so installation very simple.  Just copy the main.html to the crestron's web server or you can host on any web server.  Actually you can run it locally too.


What is included in the release
//the bad
1. You have to configure your rooms in the Json object inside the file.  You will need to know some info like Join/ID, 
but since this is a programmers forum I doubt anyone will have any problems.  Eventually I will make a 'Get' to the api controller and pull this 
info from the server.
2. The power buttons only turns off the system right now, this is a bug or an error in my understand out crestron system works.
3. The software that communicates between the html5's post and the crestron is a self hosting api controller.  
I dont know if I'm going to port this to other platforms.  There are options like writing a flash application, but 
since I have 3 windows servers in my rack I doubt I will do it.  Someone else can pick up that task.
4. since it runs on a lot of different devices it has plain interface.
//the good
1.  Its very configuration.  You are not limited on number of rooms or number of sources per room.  Just make sure you tag your sources as source = "true".  
  There can only be one volume control per room, but I doubt thats a problem.
2.  Its a single file thats easy to install assume you have you access to the internet.
3.  It can be installed locally, on the crestron, or any share or web server




Below is an example of a room found in the file:  
Room = name of the room, but it must be one word
id = the crestron id/join#
type = Digital/Analog/Serial
value = default value which executed
slot = I'm passing it on tot he device, but I've never used it. I dont know what it means.
soure = is it an audio source

Room.name = "Kitchen";
		Room.srclist =
		[{ name: "Power", id: "9", type: "D", value: "true", slot: "0",source:"false"  },
		{ name: "Mute", id: "3", type: "D", value: "true", slot: "0",source:"false"  },
		{ name: "XBMC", id: "17", type: "D", value: "true", slot: "0",source:"true" },
		{ name: "Android", id: "18", type: "D", value: "true", slot: "0", source: "true" },
		{ name: "Zune", id: "19", type: "D", value: "true", slot: "0",source:"true"   },
		{ name: "Shuffler", id: "20", type: "D", value: "true", slot:  "0",source:"true"  }]
		Room.volume = 
		{ name: "Volume", id: "1", type: "A", max: "45000", min: "0" }
		
Also dont forget to set the IP address of the API controller
	var URL = "http://localhost:8080/api/CrestJson";


Below is an Example of the config file for the API controller:

1.  You must run the API controller as adminstrator
2.  IPAddressPort is your local up for setting up the controller
3.  your lan ip for the crestron box
4.  The crestron box's cip port
5   the specific IPID you want to send the commands from the devices

    <add key="IPAddressPort" value="http://localhost:8080"></add>
    <add key="CrestronIP" value="192.168.0.3"></add>
    <add key="CrestronCIPPort" value="41794"></add>
    <add key="CrestronIPID" value="11"></add>
	
		


