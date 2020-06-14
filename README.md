# Weathering-Storms: Smart Suit

[![License](https://img.shields.io/badge/License-Apache2-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0) [![Slack](https://img.shields.io/badge/Join-Slack-blue)](https://callforcode.org/slack) [![Website](https://img.shields.io/badge/View-Website-blue)](https://code-and-response.github.io/Project-Sample/)

A basic GitHub repository example for Call for Code submissions and those projects that join the Code and Response initiative. Not all sections or files are required. You can make this as simple or as in-depth as you need.


## Contents

1. [Description](#description)
1. [Long Description](#long-description)
1. [Video Pitch](#video-pitch)
1. [Architecture of proposed solution](#architecture-of-proposed-solution)
1. [Getting started](#getting-started)
1. [Built with](#built-with)
1. [Contributing](#contributing)
1. [Versioning](#versioning)
1. [Authors](#authors)
1. [License](#license)
1. [Acknowledgments](#acknowledgments)

## Description

### What is the problem?

With Climate change increasing global temperatures, and being in tropical Singapore, we are experiencing increasingly dangerous daily temperatures. Along with the Urban Heat Island Effect (https://en.wikipedia.org/wiki/Urban_heat_island), we are exposed to high ambient temperatures that could lead to life-threatening conditions.

Firefighers are subjected to greater dangers as the nature of their job and their equipment restrict airflow to cool their bodies. This together with higher ambient temperatures lead to a increased risk of heat injury. The risk is further exaggerated during training and operations where their close vicinity to fire drastically increases the already high ambient temperatures. This becomes a major safety issue as we want to ensure the safety of our responders.

### How can technology help?

By leveraging on data collection, analysis, and artificial intelligence, we are able to make better informed decisions to solve the problem at hand. As the job of responders often deal with lives-at-stake, it is essential that we are able to make the best decision before and during the operation to provide the casualty with the highest chance of survival. Therefore, it is imperative that we use technology to aid us, simplifying difficult decisions. 

### What is your team's idea?

Through the use of Internet of Things (IoT), we decided to use temperature sensors to track the body temperature of each firefighter during training and in operation. By tracking each individual's body temperature, the commander-in-charge can be alerted of any personnel being at high risk of heat injury. Precautionary action can be taken before the personnel experiences heat injury, evacuating the firefighter before any serious injury can take effect. 

Through the use of temperature sensors, data will be collected and sent to IBM Cloud and Watson Services. The data can then be analysed and plotted on a real-time graph. This allows the commander to easily track the firefighter's body temperature relative to the time they have been inside the incident area. As such, this tracking capability ensures the safety of our responders and provides us with the confidence in deploying sections of firefighters.

## Long description

[Please click here to access the full proposal](DESCRIPTION.md)

## Video Pitch

[![Watch the video](https://github.com/Code-and-Response/Liquid-Prep/blob/master/images/IBM-interview-video-image.png)](https://youtu.be/vOgCOoy_Bx0)

## Architecture of proposed solution

![Video transcription/translation app](https://developer.ibm.com/developer/tutorials/cfc-starter-kit-speech-to-text-app-example/images/cfc-covid19-remote-education-diagram-2.png)

1. The user navigates to the site and uploads a video file.
2. Watson Speech to Text processes the audio and extracts the text.
3. Watson Translation (optionally) can translate the text to the desired language.
4. The app stores the translated text as a document within Object Storage.


## Getting started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. While there are many steps in establishing a connection between the IoT device and IBM's cloud, it ensures smooth flow of information once we start programming the IoT device itself.

### Installation

You will need to install the required software as shown below:

```bash
dnf install wget
wget https://www.arduino.cc/en/main/software
wget https://projects.eclipse.org/projects/iot.paho/downloads
curl -LO https://github.com/ibm-messaging/iot-arduino.git
```
To load Paho mqtt into Arduino IDE, download the zip file but do not unzip it
In Arduino IDE, click on 'Select Sketch' -> 'Import Library' -> 'Add to Library' (select the zip file)

Once the software have been installed, connect Arduino Uno to your computer
The samples folder of this repository (https://github.com/ibm-messaging/iot-arduino) contains 2 folders, each containing 1 flow –
1. Quickstart flow
2. Registered flow
Compile the 2 sketch codes (corresponding to the flows)
Depending upon the requirement, push one of the flows to the Arduino device

1) Modify the AUTHTOKEN in the sketch code
2) Modify the MS_PROXY, in the sketch code, by providing the values in the following format "uguhsp.messaging.internetofthings.ibmcloud.com", by replacing "uguhsp" with your organization
3) Modify the CLIENT_ID, in the sketch code, by providing the values in the following format "d:uguhsp:iotsample-arduino:00aabbccde03", by replacing "aabbccde03" with the Device Id and "uguhsp" with the organization and "iotsample-arduino" with the device type that you entered when creating the device.
4) Use mqttpublisher / mqttsubscriber to publish and subscribe the commands / events sent to / received from the Arduino Uno
5) Modify the mac Address (given in the sample as { 0x00, 0xAA, 0xBB, 0xCC, 0xDE, 0x03 } ) by the MAC Address of the Ethernet shield. This applies only for Arduino Uno, no change required in Arduino Yun sketch.

### Connection with IBM Watson IoT Platform

Using the Sketch program, key in the following code. Look at the lower part of the Sketch pad window to check that the COM connection is shown as active.

```bash
#include <Wire.h>
#include <Adafruit_MLX90614.h>

Adafruit_MLX90614 mlx = Infrared Thermometer();

void setup() {
  Serial.begin(9600);

  Serial.println("Infrared Thermometer Display");  

  mlx.begin();  
}

void loop() {
  Serial.print("Ambient = "); Serial.print(mlx.readAmbientTempC()); 
  Serial.print("*C\tObject = "); Serial.print(mlx.readObjectTempC()); Serial.println("*C");

  Serial.println();
  delay(3000);
}
```
Through the whole set of code, we have started the system and the sensor have begun collecting data.
The data is collected in 3 second intervals and would output the ambient temperature and object temperature in Celsius.
Check if the information is shown as we expected.

### IBM Watson IoT Platform

To enable us to use IBM Watson IoT Platform, we would need to setup and register our device into the cloud network.

Use the following guide to register the device into IBM Watson Internet of Things Platform (https://developer.ibm.com/recipes/tutorials/how-to-register-devices-in-ibm-iot-foundation/).

1. During the device registration process, you will receive file configuration information with the following information:
                Organization ID, Device Type, Device ID, Authentication Method, Authentication Token
2. Copy this information to the clipboard to use in the configuration file.
3. Use the device credentials obtained during registration to modify the fields in the Sketch code
4. Save the configuration file in the sketch program.

Disclaimer:

By default, the Watson IoT Platform only accepts secure connections. So, unless the sketch program has been configured, the Arduino device, by default initiates Insecure connection to Watson IoT Platform. In such cases, you might experience connectivity issues while initiating the connection between the device / gateway & WIoTP.

However, to facilitate all connections ( both Secure and Insecure)  to WIoTP, the Platform provides a security configuration, that helps you to take a well informed decision to allow Insecure connections, under your supervision.

### Data Visualization

Now that a connection between the device and Watson IoT Platform has been established, we can begin to use the IoT Platform to perform analysis for us. We can start to create visualization charts for the real time data from the sensors.

With that completed, we have successfully connected the device with IBM's cloud and are able to extract and analyze the data for us to better understand the situation.

## Built with

* [IBM Cloudant](https://cloud.ibm.com/catalog?search=cloudant#search_results) - The NoSQL database used
* [IBM Cloud Functions](https://cloud.ibm.com/catalog?search=cloud%20functions#search_results) - The compute platform for handing logic
* [IBM API Connect](https://cloud.ibm.com/catalog?search=api%20connect#search_results) - The web framework used
* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags).

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/Code-and-Response/Project-Sample/graphs/contributors) who participated in this project.

## License

This project is licensed under the Apache 2 License - see the [LICENSE](LICENSE) file for details

## Acknowledgments

* Based on [Billie Thompson's README template](https://gist.github.com/PurpleBooth/109311bb0361f32d87a2).
