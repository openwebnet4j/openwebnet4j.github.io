---
layout: default
---

**openwebnet4j** is a Java library for the [Open Web Net](https://developer.legrand.com/documentation/open-web-net-for-myhome/) protocol

It enables a Java client to communicate locally with a gateway supporting the Open Web Net protocol and to control devices in a BTicino/Legrand  BUS/SCS system ([MyHOME_Up](https://www.bticino.com/products-catalogue/myhome_up-simple-home-automation-system/) &reg;) or ZigBee wireless system ([MyHOME_Play](http://www.homesystems-legrandgroup.com/BtHomeSystems/productDetail.action?lang=EN&productId=061) &reg;, now out of production).

## Supported features

* Device discovery
* Feedback (monitoring events) from BUS/SCS and ZigBee wireless network 

### Supported frames

* `WHO=1` Lighting
* `WHO=2` Automation
* `WHO=4` Temperature control system
* `WHO=13` Gateway Management
* `WHO=18` Energy Management
* `WHO=15/25` CEN/CEN+ and DryContacts & IR

### Supported Open Web Net gateways
- *IP gateways* or scenario programmers, such as: BTicino F453 / F454 / F455, MyHOMEServer1,  MyHOME_Screen10, MH201 / MH202 / MH200N 
- *ZigBee USB Gateways*, such as: [BTicino 3578](https://catalogo.bticino.it/BTI-3578-IT), also known as Legrand 088328, to connect to wireless devices


## Dependency Management

### Maven

This library is available via Maven Central repository by adding the dependency in your POM.xml:

```xml   
    <dependency>
      <groupId>io.github.openwebnet4j</groupId>
      <artifactId>openwebnet4j</artifactId>
      <version>0.6.0</version>
    </dependency>
```


## Usage example
```java
// create BUS gateway connection with IP=192.168.1.50 and password=12345
BUSGateway myGateway = new BUSGateway("192.168.1.50", 20000, "12345");
myGateway.subscribe(this);
try {
    myGateway.connect();
    // turns light WHERE=51 ON
    Response res = myGateway.send(Lighting.requestTurnOn("51"));
    if (res.isSuccess()) {
        System.out.println("Request successful");
    }
    // requests status light WHERE=51
    myGateway.send(Lighting.requestStatus("51"));
} catch (OWNException e) {...}
```


## Projects using the library
This library is used by the **BTicino OpenWebNet binding** of the official [openHAB 3 distribution](https://www.openhab.org/).

For more information on openHAB and the OpenWebNet binding see: [https://www.openhab.org/addons/bindings/openwebnet/](https://www.openhab.org/addons/bindings/openwebnet/)


## Support this project
If you want to say "thanks!" and support this hobby project you can **make a donation**.

Donations will be used to buy new smart home hardware, or to get some good coffee/beer during the time and evenings spent on the project. 

Example donations:<br>
5€ "A coffee for you", 15€ "Thank you!", 25€ "I use it regularly and appreciate your work", 25+€ "Could you prioritize new feature XYZ?" (specify which feature in the donation message).

Any donation is appreciated! 

Make a donation using:

### PayPal
[<img src="/img/pp_donate2.png" width="130">](https://www.paypal.com/donate/?cmd=_s-xclick&hosted_button_id=EJHGYJ7SLESNY)

### BuyMeACoffee
<a href="https://www.buymeacoffee.com/mvcode" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

[<img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" width="217">](https://www.buymeacoffee.com/mvcode)

### Bitcoin
[<img src="img/bitcoin-donate-black.png" alt="bitcoin donate" width="110"> bitcoin:bc1qlnd8f6ffpega3w9phqn4hly34p52l6qpd9decp](bitcoin:bc1qlnd8f6ffpega3w9phqn4hly34p52l6qpd9decp?label=openwebnet4j%20Donation)


## Disclaimer
- This library is not associated by any means with BTicino or Legrand companies
- The Open Web Net protocol is maintained and Copyright by BTicino/Legrand. The documentation of the protocol if freely accessible for developers on the [Legrand developer web site](https://developer.legrand.com/documentation/open-web-net-for-myhome/)
- "Open Web Net", "MyHOME_Up", "MyHome", "MyHome_Play" and "Living Now" are registered trademarks by BTicino/Legrand
