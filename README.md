HP Kicks off its HPAnywhere Mobile Platform with an Enterprise Hackathon
=========

![Image](screenshots/splash700x400.png?raw=true)

This past weekend I attended the Mobile Enterprise Hack at [http://www.parisoma.com/] (Parimosa CoWorking space) in SOMA.  The event kicked off on Saturday with talks from HP outlining their new mobile app development platform, and ended with the Sunday selection for the over $20,000 in prizes and awards.

The [http://www8.hp.com/us/en/software-solutions/mobile-application-development.html] (HPAnywhere Mobile App development platform) is an Eclipse IDE based Hybrid Web workflow that allows developers to build web apps leveraging HTML tooling and frameworks such as Angular, PhoneGap ( Cordova ) and Sencha Touch, Enyo and jQuery Mobile.  These applications are then deployed to the mobile device inside the HPAnywhere mobile catalog app available on the [https://itunes.apple.com/us/app/hp-anywhere/id624128594?mt=8] (Apple iTunes store) and [https://play.google.com/store/apps/details?id=com.hp.ee&hl=en] ( Google Android Play Market ).

The [http://developer.hpanywhere.com/] (hpAnywhere develper portal) has developer downloads, resources on getting started, and some simple sample applications to get you started.

HPAnywhere leverages the web container to insure that end-point service requests are caught by the HP web container inside the application and modified to route securely to HPCloud services ( Hosted in the cloud or On-Premises ).  Additionally public facing end-points can be called from the web container.

HPAnywhere cloud environment provides access to enterprise cloud connected services such as SalesForce, A and B; and also provides convenience services for storing user and application data, authentication, and device information.

Since the technology leverages [http://cordova.apache.org/] ( PhoneGap, Cordova) for the hybrid web bridge; giving you access to PhoneGap supported device services such as access to the camera, local storage, contacts, etc.

I was able to install and stand up the sample application in a little over an hour ( mostly download time, JVM configuration, and of course waiting for eclipse to warm up and launch ).  I created a small sample app (working from the Angular template ) conforming to the enterprise app theme that provided a Retails Sales floor manager access to a dashboard and quantitative metrics for the stores employees and customers in their loyalty program; more on that later.

The development environment experience leverages eclipse out of the box and requires the developer to run Cassandra and a JAVA server to build and develop their application.

The development flow of creating an HTML/JS application in eclipse, running the publish and show app was frustrating and slow when compared to my normal HTML/js client and Node.js backend work flow.  I also had difficulty getting "Hot Deployment" to work correctly, however this is mostly likely my issue since many of the other developers PC based developers were able to leverage it out of the box. It is also awkward as mobile developer to have my app only accessible by running inside another app, only visible to the user by opening the HPAnywhere iPhone (or Android) App and thumbing through the catalog shelf.  It leaves questions as to how the platform will support application specific push notification, or inter-app intents or url events.

The prescribed environment does have several benefits:
- Provides a standardized workflow with a 'browser web emulation' environment that is popular with Enterprise use cases.
- Developers don't need to install any iOS or Android Native SDK's or tooling.
- Eclipse is popular, configurable, and enterprise established.
- The tooling can be largely ignored for a significant portion of the Development workflow ( I built my app first in standalone Angular, and then 'dropped' it in later.

After exploring the recommended IDE and workflow, I eventually ditched the Eclipse IDE and built out a client application using my standard Node.js , Inspector, and Chrome Dev tools.


Left me with the following questions :
- Why did HP adopt a legacy Java Server development environment and Cassandra data store, when the client code is HTML and JavaScript?  A NPM Node.js based Dev flow would have been more responsive, required less configuration, and more in line with modern web developers tool chain.
- Why no native iOS and Android SDK ? Hybrid web container strategies are popular with internal enterprise applications ( similar strategies using the sample components have been adopted by IBM's worklite and SAP's Sybase Unwired Platform ,SUP ) where users have little choice and most of the mobile use cases are around publishing dashboards or simple user workflows.  Providing an SDK would allow best of breed mobile applications to leverage HP Services without the experience or feature debt that occurs with Mobile web.
- Why so very ... well HP ?  The conference and the technology are a great start for HP.  Which as traditionally ( and in some cases still is ) myopic in its view of Mobile and Web.  It would have been great to see more Angular, Javascript, or web speakers at the conference to compliment the hybrid technologies they are using. The modern technology stack is mosaic of frameworks, tooling and vendors; requiring an equally open perspective.

Back to my application development experience; I got to a rough prototype within the 48 hours but I failed to get the final native configurations.  In my 'Retail Manager' use-case I was trying to access native Bluetooth Low Energy and iBeacon features; so the floor manager can get a clear picture of the Sales Associates engagement times inside the retail store by 'ranging' the Associates mobile app with department specific BLE beacons;  providing a sort of in-store analytics on their employee's engagements and activities.

An early screen shot of my app as I was hacking the code together during the event:

![Image](screenshots/image1.png?raw=true)

I will make sure and publish my HPAnywhere sample application in a follow up post;  if you want to see the native Objective-C equivalent keep an eye out next week for the "Capturing BlueTooth Low Energy engagement analytics with Node.js " for a pure native iOS equivalent.

