Javascript Sockets use the Socket functionality available in flash, and through an ExternalInterface with an swf embedded in a page, provide the ability to program sockets with javascript

---

### Installation ###
To install and run jssockets, checkout the code with
```
svn checkout http://jssockets.googlecode.com/svn/trunk/ jssockets-read-only
```
You need to be served the page through a server, so either checkout in
localhost or  upload the files to your webserver. then view

http://localhost/jssocket/ (or whatever server you uploaded to)

---

### Use ###
jssocket.swf is the only thing required, add the swf to the page, using standard embed mode or [swfobject](http://blog.deconcept.com/swfobject/), when the swf loads it will make a call to the function
```
function jssocket_init()
```
Once this function is called, you can now communicate with the swf. communication with the swf works by calling functions from the swf object on the page, The method of retrieving the object varies depending on how it was embedded, using swfobject below works
```
_jssocket = document.getElementById("mymovie");
```

Below is the functions you can call on the swf.
```
_jssocket.setCallBack(event, callback);
_jssocket.connect(ip,port);
_jssocket.write(message);
_jssocket.disconnect();
```

Below are the callbacks you can define, these are the functions the swf will call when certain events happen,
```
 _jssocket.setCallBack("connect",   "soc_connect");
 _jssocket.setCallBack("disconnect","soc_closed");
 _jssocket.setCallBack("recieve",   "soc_msg");
 _jssocket.setCallBack("ioerror",   "soc_error");
```

---

### Development ###
To develop the socket swf you need to have the flex compiler installed. to compile a new swf, simply type
```
mxmlc JsSocket.mxml
```