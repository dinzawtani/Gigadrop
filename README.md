# Gigadrop 

[Gigadrop](https://Gigadrop.net): local file sharing in your browser - inspired by Apple's Airdrop.

#### Gigadrop (Version 2) is built with the following awesome technologies:
* Vanilla HTML5 / ES6 / CSS3  
* Progressive Web App
* [WebRTC](http://webrtc.org/)
* [WebSockets](http://www.websocket.org/) fallback
* [NodeJS](https://nodejs.org/en/)
* [Material Design](https://material.google.com/)

##### What about the connection? Is it a P2P-connection directly from device to device or is there any third-party-server?
It uses a P2P connection if WebRTC is supported by the browser. (WebRTC needs a Signaling Server, but it is only used to establish a connection and is not involved in the file transfer).

##### What about privacy? Will files be saved on third-party-servers?
None of your files are ever sent to any server. Files are sent only between peers. Gigadrop doesn't even use a database. If you are curious have a look [at the Server](https://github.com/dinzawtani/gigadrop/blob/master/server/). Even if Gigadrop was able to view the files being transfered, WebRTC encrypts the files on transit, so the server would be unable to read them.

##### What about security? Are my files encrypted while being sent between the computers?
Yes. Your files are sent using WebRTC, which encrypts them on transit.


### Gigadrop is awesome! How can I support it? 
* [File bugs, give feedback, submit suggestions](https://github.com/dinzawtani/gigadrop/issues)
* Share Gigadrop on your social media.
* Fix bugs and make a pull request. 
* Do security analysis and suggestions

'''
    git clone https://github.com/dinzawtani/Gigadrop.git
    cd Gigadrop
    docker-compose up -d
'''


