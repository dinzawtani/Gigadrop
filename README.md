# xdrop 

[xdrop](https://xdrop.net): local file sharing in your browser - inspired by Apple's Airdrop.

#### xdrop (Version 2) is built with the following awesome technologies:
* Vanilla HTML5 / ES6 / CSS3  
* Progressive Web App
* [WebRTC](http://webrtc.org/)
* [WebSockets](http://www.websocket.org/) fallback
* [NodeJS](https://nodejs.org/en/)
* [Material Design](https://material.google.com/)

## Support the Snapdrop Community
Snadprop is free. Still, we have to pay for the server. If you want to contribute, please use PayPal

Thanks a lot for supporting free and open software!


## Frequently Asked Questions

### Instructions
* [Video Instructions](https://www.youtube.com/watch?v=4XN02GkcHUM) (Big thanks to [TheiTeckHq](https://www.youtube.com/channel/UC_DUzWMb8gZZnAbISQjmAfQ))
* [idownloadblog](http://www.idownloadblog.com/2015/12/29/snapdrop/)
* [thenextweb](http://thenextweb.com/insider/2015/12/27/snapdrop-is-a-handy-web-based-replacement-for-apples-fiddly-airdrop-file-transfer-tool/)
* [winboard](http://www.winboard.org/artikel-ratgeber/6253-dateien-vom-desktop-pc-mit-anderen-plattformen-teilen-mit-snapdrop.html)
* [免費資源網路社群](https://free.com.tw/snapdrop/)

##### What about the connection? Is it a P2P-connection directly from device to device or is there any third-party-server?
It uses a P2P connection if WebRTC is supported by the browser. (WebRTC needs a Signaling Server, but it is only used to establish a connection and is not involved in the file transfer).

##### What about privacy? Will files be saved on third-party-servers?
None of your files are ever sent to any server. Files are sent only between peers. Snapdrop doesn't even use a database. If you are curious have a look [at the Server](https://github.com/RobinLinus/snapdrop/blob/master/server/). Even if Snapdrop was able to view the files being transfered, WebRTC encrypts the files on transit, so the server would be unable to read them.

##### What about security? Are my files encrypted while being sent between the computers?
Yes. Your files are sent using WebRTC, which encrypts them on transit.

##### Is SnapDrop a fork of ShareDrop?
No. ShareDrop is built with Ember. Snapdrop is built with vanilla ES6. 
I wanted to play around with Progressive Web Apps and then I got the idea of a local file sharing app. By doing research on this idea I found and analysed ShareDrop. I liked it and thought about how to improve it.
ShareDrop uses WebRTC only and isn't compatible with Safari browsers. Snapdrop uses a Websocket fallback and some hacks to make Snapdrop work due to the download restrictions on iDevices. 


### xdrop is awesome! How can I support it? 
* [File bugs, give feedback, submit suggestions](https://github.com/dinzawtani/xdrop/issues)
* Share xdrop on your social media.
* Fix bugs and make a pull request. 
* Do security analysis and suggestions

## Local Development
[Install docker with docker-compose.](https://docs.docker.com/compose/install/)

Clone the repository:
```
    git clone https://github.com/dinzawtani/xdrop.git
    cd xdrop
    docker-compose up -d
```

To restart the containers run `docker-compose restart`.
To stop the containers run `docker-compose stop`.


Now point your browser to `http://localhost:8080`.

### Testing PWA related features
PWAs require that the app is served under a correctly set up and trusted TLS endpoint.

The nginx container creates a CA certificate and a website certificate for you. To correctly set the common name of the certificate you need to change the FQDN environment variable in `fqdn.env` to the fully qualified domain name of your workstation.

If you want to test PWA features you need to trust the CA of the certificate for your local deployment. For your convenience you can download the crt file from `http://<Your FQDN>:8080/ca.crt`. Install that certificate to the trust store of your operating system.
- On windows make sure to install it to the `Trusted Root Certification Authorities` store.
- On macOS double click the installed CA certificate in `Keychain Access` expand `Trust` and select `Always Trust` for SSL.
- Firefox uses its own trust store. To install the CA point Firefox at `http://<Your FQDN>:8080/ca.crt`. When prompted select `Trust this CA to identify websites` and click OK.
- When using Chrome you need to restart Chrome so it reloads the trust store (`chrome://restart`). Additionally, after installing a new cert you need to clear the Storage (DevTools -> Application -> Clear storagae -> Clear site data).

Please note that the certificates (CA and webserver cert) expire after a day.
Also whenever you restart the nginx docker container new certificates are created.

The site is served on `https://<Your FQDN>:443`.
    
## Deployment Notes
The client expects the server at http(s)://your.domain/server.

When serving the node server behind a proxy the `X-Forwarded-For` header has to be set by the proxy. Otherwise all clients that are served by the proxy will be mutually visible.

By default the server listens on port 3000.

For an nginx configuration example see `nginx/default.conf`.

## Licences
* Thanks to [Mark DiAngelo]() for the [Blop Sound](http://soundbible.com/2067-Blop.html)



## Desktop App 
Note, if you are using Google Chrome you can easily install Snapdrop PWA on your desktop by clicking the install Button in the top-right corner.

If you are not using Chrome, you can install the [Snapdrop Desktop App](https://github.com/infin1tyy/snapdrop-desktop) built on top of Electrum. (Thanks to Infin1tyy!).


