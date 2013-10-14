##Mobile developer review of the HPAnywhere Mobile Platform from this weekend's "mobile enterprise hack"

![Image](screenshots/splash700x400.png?raw=true)

This past weekend I attended the Mobile Enterprise Hack at [Parimosa CoWorking space](http://www.parisoma.com/) in SOMA.
The event kicked off on Saturday with talks from HP outlining their new mobile app development platform, and ended with the Sunday selection for the over $20,000 in prizes and awards. 

The [HPAnywhere Mobile App development platform] (http://www8.hp.com/us/en/software-solutions/mobile-application-development.html ) is an Eclipse IDE based Mobile Hybrid Web workflow that allows developers to build web apps 
leveraging HTML tooling and frameworks such as [Angular] (http://angularjs.org/), PhoneGap ( Cordova ) and [Sencha Touch](http://www.sencha.com/products/touch), jQuery Mobile that easily integrate with HP Cloud services and connectors.  These applications are then deployed into the HPAnywhere container app available on 
the [Apple iTunes store ] (https://itunes.apple.com/us/app/hp-anywhere/id624128594?mt=8) and [Google Android Play Market] (https://play.google.com/store/apps/details?id=com.hp.ee&hl=en).  The hybrid web app lives inside the HPAnywhere Container app with other corporate applications.

The [hpAnywhere developer portal ] (http://developer.hpanywhere.com/) has developer downloads, resources, and some simple sample applications to get you started.  Providing clear documentation for both Windows and Apple OSX dev environments.

###Hybrid mobile web on HP infrastructure
HPAnywhere leverages the web container to insure that end-point http service requests are caught by the HPA container shell inside the application and modified to route securely to [HP Web Services
](http://www.hpwebos.com/us/)  hosted in the corporate cloud or On-Premises.

HPAnywhere cloud environment provides access to enterprise cloud connected services such as SalesForce, and SAP; and also provides convenience services for storing user and application data, authentication, and device information.  Full documentation for the client and server API can be found on the [HP Anywhere API reference ](http://developer.hpanywhere.com/wp-content/uploads/2013/06/HP_Anywhere_10_10_API_Reference/webframe.html)

Since the technology leverages [PhoneGap, Cordova] (  http://cordova.apache.org/) for the hybrid mobile web bridge developers can access PhoneGap supported device services such as the camera, local storage, contacts, and any other mobile device feature supported by the Cordova bridge.

###Dev workflow experience

I was able to install and stand up the sample application in a less than an hour ( mostly download time, JVM configuration, and of course waiting for eclipse to warm up and launch ).  I created a small sample app (working from one of the Angular templates ) to provided a retails sales floor manager a mobile dashboard with engagement metrics for the stores employees, and customers in their loyalty program; more on that later.

The development environment experience leverages eclipse out of the box and requires the developer to run an Apache Cassandra Java server on the host machine to support the web simulator for the mobile app.

The development flow for creating an HTML/JS application in eclipse, running the local web simulator and iterating was frustrating and slow for me when compared to my normal HTML/JavaScript client and Node.js backend work flow.  Inevitably most of this frustration was due to using eclipse and in some cases restarting the 'app server' to get my application to refresh.  HPAnywhere supports "Hot Deployments" making the flow easier. It is also awkward as mobile developer to have my mobile experience running inside another mobile app.  HPAnywhere apps are only visible to the user by opening the HPAnywhere iPhone (or Android) App thumbing through the other apps in the corporate catalog and then opening the mobile web 'app' .

The prescribed environment have several benefits:
- Provides a standardized workflow with a 'browser web emulation' environment that does not require developers to install the iOS and Android Native SDK's or tooling.
- Eclipse is popular, configurable, and enterprise established.
- The tooling can be largely ignored for a significant portion of the Development workflow ( I built my app first in stand-alone Angular, and then 'dropped' it in later.

After exploring the recommended IDE and workflow, I eventually ditched the Eclipse IDE and built out my sample application using my standard Node.js , Inspector, and Chrome Dev tools. Then copy past integrated the application into the provided template.  The integration of my standalone Angular app into the HPAnywhere template was well documented and easy. 

There are some questions regarding HP's choice of developer tooling:
- Why did HP adopt a legacy Java Server development environment and Cassandra data store, when the client code is HTML and JavaScript?  
  
A NPM Node.js based Dev flow would have been more responsive, required less configuration, and more in line with modern web developers tool chain.

- Why no native iOS and Android SDK ? 

Hybrid web container strategies are popular with internal enterprise applications ( similar strategies using the sample components have been adopted by IBM's worklite and SAP's Sybase Unwired Platform ,SUP ) where users have little choice and most of the mobile use cases are around publishing dashboards or simple user workflows.  Providing an SDK would allow best of breed mobile applications to leverage HP Services without the experience or feature debt that occurs with Mobile web.

Why so very ... well HP ?  

The enterprise Hack was very well run, friendly and informative.  The technology was robust and very usable.  However,  It would have been great to see more Angular, Javascript, or web speakers at the conference to compliment the hybrid technologies they are using. The modern technology stack is mosaic of frameworks, tooling and vendors; requiring an equally open perspective.

###Mobile Apps on HPAnywhere

Mobile developers creating HPAnywhere apps will be under the same limitations ( and advantages ) of traditional PhoneGap, Cordova Apps. Since the applications UI is running inside a 'chrome-less' browser on the users device and any UI updates such as transitions, labels, table's and charts will be traversing the mobile device browser's HTMLS DOM you can expect a reduction in responsiveness.   This also prevents your application from conforming to the [mobile Human Interface Guidelines](https://developer.apple.com/library/ios/documentation/userexperience/conceptual/mobilehig/) provided by the platform vendors.  Developers must also pay close attention to the web browser version running since mobile web fragmentation may impact support for the HTML/Javascript features your mobile application may use.

Back to my application development experience; I got to a rough prototype within the 48 hours but I failed to get the final native configurations.  In my 'Retail Manager' use-case I was trying to access native Bluetooth Low Energy and iBeacon features; so the floor manager can get a clear picture of the Sales Associates engagement times inside the retail store by 'ranging' the Associates mobile app with department specific BLE beacons;  providing a sort of in-store analytics on their employee's engagements and activities.

An early screen shot of my app as I was hacking the code together during the event:

![Image](screenshots/image1.png?raw=true)

I will make sure and publish my HPAnywhere sample application in a follow up post;  if you want to see the native Objective-C equivalent keep an eye out next week for the "Capturing BlueTooth Low Energy engagement analytics with Node.js " for a pure native iOS equivalent.

In the meantime make sure and check out the Enteprise Hack winners at [Apps-for-Mobile](http://h30499.www3.hp.com/t5/Apps-for-Mobile/That-s-a-wrap/ba-p/6234487#.Ulw2umRATHA) and ongoing updates on the [HP Apps for Mobile Blog] (http://h30499.www3.hp.com/t5/Apps-for-Mobile/bg-p/apps-for-mobile)




