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

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

You need to install Arduino software and use its console to continue

```bash
dnf install wget
wget https://www.arduino.cc/en/main/software
```

### Installing

Once Arduino has been successfully installed, open up Arduino.
Connect the circuit board with all the components attached to your computer via USB-A.
Once the software and drivers have been installed, we can proceed to code and use the device.

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
Through the whole set of code, we have started the system and the thermometer have begun collecting data.
The data is collected in 3 second intervals and would output the ambient temperature and object temperature in Celsius.

However, as there are currently no output display for the system to output the data, we will have to link this system with IBM Watson Cloud.

### Connection between board and IBM IoT Platform

```bash
curl localhost:3000
Thanks for looking at Code-and-Response!
```

End with an example of getting some data out of the system or using it for a little demo

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
