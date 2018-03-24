A fully working http2 example using Javalin

Javalin let you modify the jetty server, given that jetty supports http2 out of box. Here is a way to start the http2 server

First you need to generate the keystore using the following command

    keytool -genkey -alias jetty -storetype PKCS12 -keyalg RSA -keysize 2048 -keystore keystore.p12 -validity 3650
    
I'm using Conscrypt, which is the [recommended](https://webtide.com/conscrypting-native-ssl-for-jetty/) way by Jetty for both speed and security. 

When you run the main class, there will be a http 1.1 server on port 8080. and http2 server on 8443 with fall back to SSL http 1.1

Open chrome and go to https://localhost:8443 you'll see in the Developer tools under network tab, you are connecting using h2

Discussion in [github issue](https://github.com/tipsy/javalin/issues/151)


the api version you need to use is specific to the java 8 version you are running as per [here](https://www.eclipse.org/jetty/documentation/9.4.x/alpn-chapter.html#alpn-versions)