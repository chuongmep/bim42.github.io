---
id: 1271
title: DIY temperature sensor
date: 2019-02-24T10:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1271
permalink: /2019/02/diy-temperature-sensors-and-forge-viewer
published: true
categories:
  - bimsync
image: /assets/2019/02/viewer.png
tags:
  - IOT
  - Forge
  - Visualization
description: A temperature and humidity sensor displayed in Forge
---
I recently had to work with the BMS system of my office building and study how to retrofit it with new web-based technologies. I am by no mean even slightly knowledgeable about these systems, but this gave me a few ideas to explore.

For example, I wanted to measure temperature and humidity in my apartment to understand thermal conditions and optimise comfort in my own home.

I first looked into integrated home monitoring systems, but they are more expensive that I wish to spend on this small experiment. Furthermore, they mostly work with proprietary software solutions and offer little possibility for tinkering.

Instead, I ordered two [Raspberry Pi Zero W](https://www.raspberrypi.org/products/raspberry-pi-zero-w/) along with two [DHT22](https://learn.adafruit.com/dht?view=all) humidity and temperature sensors to build my own Wifi enabled indoor thermometer and humidity monitor. Since I will need to use the GPIO interface of the Raspberry Pi, I ordered the [H version](https://www.raspberrypi.org/blog/zero-wh/) of the Raspberry Pi Zero W, with pre-soldered headers. This allows me to connect the DHT22 to the GPIO interface of the Raspberry Pi without having to solder it on the board. Following the instructions from [this post]( http://www.home-automation-community.com/temperature-and-humidity-from-am2302-dht22-sensor-displayed-as-chart/) in Home Automation Community, I quickly plug the sensor into the GPIO interface of the Raspberry.

![The Raspberry Pi with its attached sensor]({{ "/assets/2019/02/raspberry.JPG" | absolute_url }})

To read the values coming from the DHT22 sensors, I use the associated [Adafruit python library](https://github.com/adafruit/Adafruit_Python_DHT). Just run these commands to install pip, the python package manager and add the Adafruit_DHT library:

```text
sudo apt-get update
sudo apt-get -y install python3-pip
sudo pip3 install Adafruit_DHT
```

To store the values coming from these sensors, I am using an [Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) database. This solution come with a nice [Python library](https://docs.microsoft.com/en-us/azure/cosmos-db/create-sql-api-python) that I will use as well in my project:

```text
sudo pip3 install azure-cosmos
```

Using the sample provided by Adafruit, I wrote a small python script to read the values coming from the DHT sensors and upload the result to my online database. You can find the resulting script in this [Gist](https://gist.github.com/simonmoreau/a1a7572610e03e044c41d482e5a45977).

To run this script, I am using crontab, the Linux job scheduler. Don't forget to run the crontab with sudo, since the GPIO need sudo permission to be accessed:

```text
sudo crontab -e
```

To run the command every 5 min, I use the following crontab command:

```text
*/5 * * * * cd /home/smoreau/sources/ && /usr/bin/python3 /home/smoreau/sources/readings.py
```

This will go in my home dir *(cd /home/smoreau/sources/)*, use python3 *(/usr/bin/python3)* on the python file *(/home/smoreau/sources/readings.py)*.

Since I have two Raspberry Zero with a DTH22 sensor wired on each, I add the sensorId property to be able to differentiate the values coming from them.

Now that I have temperature and humidity values nicely stored in a database, I need to display them. I started with a simple line graph to get an idea of the evolution of the temperature and the humidity:

<iframe width="680" height="620" src="https://bmspi-232219.firebaseapp.com/graph" frameborder="0" allowFullScreen="true"></iframe>

As you can see, we can start seeing patterns here. For example, you can see a spike in the temperature around 6 PM every day, when the sun hit the sensor. We can also see that the humidity is inversely correlated to temperature.

But I wanted something a bit fancier to display the sensor values.

I found the work of [Kean Walmsley](https://twitter.com/keanw) on [Project Dasher](https://dasher360.com/) very interesting and I have often used it to showcase possibilities of connection between IOT and BIM. Inspired by this, I created my own visualization tool for this data.

To create this visualization tool, I am using the Forge viewer with the great [wrapper for Angular](https://github.com/theNBS/ng2-adsk-forge-viewer) published by [Alan Smith](https://twitter.com/alansmithnbs). With a few lines of code, I was able to create a nice visualization tool albeit not very useful:

<iframe width="680" height="530" src="https://bmspi-232219.firebaseapp.com/viewer" frameborder="0" allowFullScreen="true"></iframe>

You can hover over the red dots to display the values coming from the temperature and humidity sensors.

You can find the complete project [here](https://bmspi-232219.firebaseapp.com/).

As usual, the entire source code is available on Github. You can found the front end [here](https://github.com/simonmoreau/bms-pi) (viewer and charts) and the API used to retrieves values from the Cosmos database [here](https://github.com/simonmoreau/bmsPiFunction).