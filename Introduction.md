> # Introduction #

The library reads the temperature and humidty data from AOSONG AM2311 sensor. It makes the communication between Arduino and sensor easy.

![http://www.aosong.com/asp_bin/Products/AM2311.jpg](http://www.aosong.com/asp_bin/Products/AM2311.jpg)

> ## Function ##
This library is used to communicate with AM2311 through I2C.
> ## Hardware Required ##
  * Arduino board
  * [AOSONG AM2311 sensor](http://www.aosong.com/cn/products/details.asp?id=93)

> ## Software Required ##
  * Arduino IDE 1.0 or newer


> ## Library Required ##
  * Wire

> # Code example #
With this library, the work to read temperature and humidy from the sensor becomes very very simple.

```

#include <Arduino.h>
#include <HardwareSerial.h>
#include <ERxAM2311.h>
#include <Wire.h>

int iLoopIndex = 0;

ERxAM2311 amSensor;

void setup() {

	Serial.begin(9600);
	Serial.println("Starting...");
}

void loop() {

	Serial.print("Detect temperature and humidity => ");
	Serial.println(++iLoopIndex);

	int ret = amSensor.read();
	Serial.print("Read result: ");
	Serial.println(ret);

	Serial.print("Humidity (%RH): ");
	Serial.println(amSensor.humidity, 2);
	Serial.print("Temperature (C): ");
	Serial.println(amSensor.temperature, 2);
	Serial.println();

	delay(2000);
}
```

> # Practical example #
This sensor and library is used in the project [House Online](https://pachube.com/feeds/42131)
https://api.pachube.com/v2/feeds/42131/datastreams/0.png?width=702&height=250&colour=F15A24&duration=24hours&detailed_grid=true&show_axis_labels=true&timezone=

Figure 1 - Temperature from AM2311

https://api.pachube.com/v2/feeds/42131/datastreams/1.png?width=702&height=250&colour=F15A24&duration=24hours&detailed_grid=true&show_axis_labels=true&timezone=

Figure 2 - Humidity from AM2311