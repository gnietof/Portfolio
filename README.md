# Project Portfolio
A pointer to different projects or contents I have been working on throught the years.  
If you are interested in my latest investigations/learning follow this [link](./Skills.md).

## IoT

### IoT (MKR1000 + Raspberry)

In 2019 I attended an education on IoT provided by the UOC in Spain. The final terms exercise consisted of creating a project which combined the Arduino MKR1000 and Raspberry Pi to create a water heating system.

I developed a small board so that I could simulate a control panel and also interface with the reles. 

<img width="283" height="331" alt="image" src="https://github.com/user-attachments/assets/26b9680f-8a3a-484e-ac8b-65414ebd9e0e" />
<img width="316" height="381" alt="image" src="https://github.com/user-attachments/assets/a1d8bc0a-0e7a-4f84-8d2e-2c4574276fc2" />

The LED's in the board showed the status. The MKR1000 controlled the heating system and reported to the Raspberry Pi using MQTT. I created a dashboard using Grafana in the Raspbery Pi which displayed the historical evolution of different parameters received through that MQTT connection.
For the final demo, a resistor and a small engine were connected to the MKR1000 which simulated the heater.

<img width="973" height="453" alt="image" src="https://github.com/user-attachments/assets/5da64e72-8360-4c75-8e5a-06403f511d36" />

The code in the MKR1000 was developed using C/C++ while the one running on the Raspberry Pi was created using Node-RED.

The whole description of the solution can be found [here](./PLA9.pdf) (in Spanish).

### TOTP-M5 (2021)
I am lecturing cybersecurity at the University. One of the points I am covering is Identity Management. So I thought it might be interesting to implement a piece of code which was implementing the TOTP protocol in a small portable device which I might take to my lectures.

From the list of devices I own I selected a M5StickC by M5Stack.  
<img width="218" height="231" alt="image" src="https://github.com/user-attachments/assets/65dc4a7f-0611-45c3-afed-2014fb54c35a" />

Measuring only 48mm x24mm x 13mm it included all I needed:
- An ESP32 processor powerful enough for the required hashing and encryption.
- A WiFi connection which allowed the connection to the Internet for synchronizing the internal clock.
- A small display to display the codes.
- A battery which allowed me to run the demo for - at least - a few minutes.

The code was developed in C/C++ using different libraries for HTTPS communication, screen display and performing the SHA1 hash. I wrote the rest of code using a reference to understand the TOTP required calculations.

- When powered on, the device looks for a WiFi connection. Because changing the WiFi configuration was not easy on the fly, the code looks for the one shared by my mobile phone. 
- Once the connection to the Internet has been established through my mobile phone, the code synchronizes the internal clock with the current time using a NTP server. 
- Now the Internet connection is no longer required.
- The application starts showing a sequence of TOTP codes. The application is configured to display a new 6 digit code every 30 seconds.

Initially none of the codes match the one displayed in any application compatible with TOTP such as the one in https://totp.danhersam.com/. When students complain that none of the codes match the ones displayed in the app ... I provide the right password and ask them: What about now?

#### TOTP-S3 (2024)
Later I migrated this code to a new board: WT32-SC01.

<img width="362" height="375" alt="image" src="https://github.com/user-attachments/assets/085d38cd-ef3e-4390-83aa-0f8de4f89a07" />

The code is mostly the same except for the one required for displaying the TOTP codes in the much bigger screen (3.5" instead of 1.14").

### IoT + AR (2023)
This is a material for a lab I created for a module in another subject I am lecturing at the University which covers Industry 4.0.

The lab includes IoT and Augmented Reality. 
- Students build a small piece of code using Node-RED. This code runs on the Raspberry Pi + SenseHat emulator. The emulator includes the 8x8 RGB led display.

  <img width="968" height="505" alt="image" src="https://github.com/user-attachments/assets/c1d4ef14-c6e6-4be7-b00f-80f75255ad8c" />

- Each student chooses which color they want to display on their assigned 2x2 led block.
- The code sets the selected color on the emulator display and also sends the information to a Mosquito Broker on the cloud using the MQTT protocol.
- The code is also listening to that same topic so, the display for each student shows the colors selected by the other students.
- The teacher (me) has a real Raspberry Pi + Sense Hat which also runs the same code and displays each of the colors selected by the students.
- Finally, also using Node-RED, they add another piece of code which publishes a small HTML page. When they load this HTML page on their mobile phones and point the camera to the University logo, a 3D representation of the SenseHat appears in augmented reality.

<img width="224" height="398" alt="IoT - RA" src="https://github.com/user-attachments/assets/f9e6c8cb-46b9-4616-a475-16b18d0fddc8" />

### Weather + Paper Display
I bought a small (1.54 inches) two-color paper display. I did some tests where the paper displayed showed the weather prediction. The code run on a ESP32 board.
This project also included a backend service deployed on the IBM Cloud which retrieved the prediction from The Weather Channel and provided the required images to the board using a REST call using the HTTP protocol.  
All the possible icons required for the different weather conditions had previously been prepared for the limited capabilities of the paper display.

The picture below shows a testing phase where the retrieved image had been split in each of the two colors. On the top left the black component, on the top right the red component and in the lower part the whole image.

<img width="412" height="642" alt="IoT-Weather" src="https://github.com/user-attachments/assets/bdd78f33-4069-49bf-9bed-03fb7900a9c5" />

### IoT Clock
This project was an alarm clock which showed current time using a 4x7 segment LED display powered by an ESP32. 
The interesting part here was a small web application which allowed creating different alarm times. The ESP32 connected to this background REST service using HTTP and was capable of synchronizing the alarms with no intervention.

<img width="544" height="341" alt="IoT-Clock" src="https://github.com/user-attachments/assets/9141af4d-45a0-48fb-bcc7-850e6c2fcaf8" />

### Garmin 735XT

I bought a Garmin 735XT and also did some testing on the capabilities for creating custom applications using the [Moneky C](https://developer.garmin.com/connect-iq/monkey-c/ ) language which were executed on the watch.

<img width="199" height="253" alt="image" src="https://github.com/user-attachments/assets/77dff43d-a9e7-4f09-aacb-c1702826d9a8" />

#### Trains (2018)

A small application which displayed the next trains from my home location to Barcelona on the Garmin 735XT.

<img width="300" height="400" alt="image" src="https://github.com/user-attachments/assets/cb9e0089-f26b-47dc-921c-c10a0db932da" />

![IMG-20170608-WA0001](https://github.com/user-attachments/assets/3181bf44-04a0-405d-9550-3b8dd4657642)

#### Weather (2018)

Another small application which displayed the weather forecast on my position on the Garmin 735XT.

## Random Developments

### Raspberry Pi + Hadoop Cluster

### Pokémon (2022)
This project was part of a hiring challenge in the Quantum group. The process required creating a tool which allowed to manage Pokémons. 
I had no idea of what Pokémons were. So I had to request for my daughter's advice.

Instead of going the easy way using the tools I was used to (Java + DB2), I decided to transform this challenge into an opportunity to learn and test new options.
So, I chose **Node.js** for the backend, **JavaScript** for the front end (with **Bootstrap** and **jQuery**) and **MongoDB** to store the database and giving NoSQL a try instead of using a SQL option. 

This was an interesting challenge back in 2022. There was no AI so I had to build the application from scratch without any assisstants.

<img width="1204" height="818" alt="image" src="https://github.com/user-attachments/assets/e328e36e-06d8-406a-91ea-954024d8a0ed" />



