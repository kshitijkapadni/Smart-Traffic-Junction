# Smart-Traffic-Junction

## Working Demo here

[Video](https://www.linkedin.com/feed/update/urn:li:activity:6521835939793334272)

## This repository contains the partial code and implementation of the system explained below, full code will be released soon

## Introduction
Aim of the project was to present technologically advanced, comprehensive traffic light system that would be the perfect alternative for the prevailing systems. This traffic light system consists of a traffic light controlling system has an ‘Intelligent’ aspect for priority recognition and decision making by the system itself and an easy way to monitor and control the traffic lights remotely. It is more energy saving than the existing system. This project was heavily dependent on two main fields of Digital Image Processing & Internet of Things. Digital Image Processing was used for vehicle identification and traffic load sensing purpose. Internet of Things is used to read the cameras through a network and also to send and receive real time information of traffic junction to traffic controllers. This can be done by combining IoT with REST API.

## A. Exiting System
The major problem of the existing traffic light systems is that the signal transition timing slots are static and they have fixed time cycle. Even if a particular lane has less traffic, the lane is allocated with the same fixed time which results in inefficient management of traffic. Although road traffic authorities in India try to mitigate the problem by switching different fixed time traffic signal timing on basis of the time-of-day plan, this is ineffective as traffic is generally random for the larger time period, which is taken to be on an hourly basis. This leads to an irregular traffic delay during transit in the urban areas. Due to this, not only the vehicles get trapped in the unnecessary traffic jam but also some time in the regular condition they have to wait for a long time-span even if the traffic density is very less in all the lanes. One of the substantial situations in the traffic light system concerns the passage of emergency vehicles as higher priorities through the roads junction. An emergency vehicle includes ambulances, rescue vehicles, fire brigade, police, and VIP persons that could get stuck in the traffic congestion. Also, there is no special hardware that can detect the traffic violators. 

## B. Proposed System
All the above mention flaws in the existing system can be solved by using a smart machine vision and IoT based traffic management system. The proposed system is able to identify the lanes having less traffic and according to that it reduces or increases the green time of that particular lane intelligently. This ultimately reduces the total cycle time required and results in efficient traffic management. This operation can be monitored remotely by a traffic controller. Also, the system will identify if there is an emergency vehicle in any lane and then that lane will be set green until the emergency vehicles are passed and then resume its operation from where it stopped. The proposed system is able to detect if there are any traffic violators. If found then the image of the traffic violator will be send immediately to the traffic controller in the form of notification. 
      
Raspberry Pi (A credit card sized computer) can read the live video feeds from IP (Internet Protocol) supported cameras connected in a network through Wi-Fi or Ethernet. We can also use normal cameras connected directly using USB cable. Motion detection can be implemented using image processing techniques to determine the amount and intensity of traffic present on particular side of the junction. The traffic lights can also be controlled by the Pi accordingly based on the intensity of traffic. If the traffic on particular side of the junction is more than the duration of green light for that particular side will be set more. If the traffic is less then duration of the light will be less. The junction will be fully automated and will also be able to control the traffic more efficiently. The real time status of the junction will be able to monitor from everywhere in the world using Internet. The historical data will also be used for improvements and making system more accurate.

## Implementatiion
• The CCTV cameras on the junction will be connected in a network (with router) with Raspberry Pi using Ethernet cables or Wi-Fi directly. Raspberry Pi will be able to read the real time video feeds using the IP addresses of the cameras. It will read from 4 different cameras at the same time. 
<br>
• Once the video is fetched in real time, the Pi will process the video for motion detection using OpenCV library tools. The Pythagorean distance based motion detection algorithm will efficiently calculate the amount of motion on the road. Approximately 95% of motion on the road is caused by vehicles. Other motion is caused by pedestrians, birds and other objects. The algorithm will efficiently filter the non-vehicle motion by ignoring very small motion detections and will calculate the motion just caused by vehicles. Amount of motion detected will be then used to calculate the load percentage of that particular lane or side. 
<br>
• Load percentage will give us the intensity of traffic present on the road. If the load percentage is greater then that road has more traffic and if it is less then that side has less traffic. Based on load percentage of the lane or side the time duration for green light will be calculated. Pi will set the duration of green light longer if the load is high or shorter if the load is low. Another algorithm will control the lights of signals. Signal lights for 4 sides will be operated in a cycle (clockwise or anticlockwise). The duration of green light for a particular side or lane will be updated dynamically by motion detection algorithm. Both algorithms will work in a sync to manage the junction.
<br>
• The signal controlling algorithm will read the updated duration for that particular side or lane and will set and operate signals lights in a cycle for each side accordingly. In this way, all lanes will have a balanced routine and traffic will be managed efficiently.
<br>
• The Pi will have internet connection and will be able to communicate with the web server over the internet. Pi will dynamically update the values locally in its local storage and globally in the database present on the cloud. This database will contain values of traffic in real time such as load percentages of each lane and current value of each signal that is signal is red, green or yellow in real time. The database will be dynamically updated in real time by Pi as it will continuously send data to the server. The traffic controller will be able to monitor the real time traffic of the junction from anywhere in the world by a website or web application or mobile application.
<br>
• The website will show the real time values in the database using AJAX calls and JSON objects which will retrieve values from cloud server in real time and show it on the website. The real time status of the traffic junction can be monitored from anywhere with internet. We can also log out the collected data and perform historical analysis to improve the efficiency.
<br>
• As the signal controlling and vehicle load sensing is carried out, simultaneously emergency vehicle detection algorithm and traffic violation algorithm will be working on the lanes having red signal. The cameras of red signal lanes are read and emergency vehicles are tried to detect emergency vehicles. If emergency vehicle is detected, the next signal to be turned green will be the signal of emergency vehicle lane. This will break the cycle to allow passage of emergency vehicle on priority. Once the emergency vehicle is detected, before breaking the cycle the system will automatically send the notification with the picture of detected vehicle to the traffic controller. 
<br>
• To detect traffic law violation, the real time video feed is read from the cameras with red signal lane. If the motion tracking is detected towards the opposite is found, then the photo of tracked vehicle will be sent to the traffic controller with a notification.
