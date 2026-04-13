# Project Portfolio
A pointer to different projects or contents I have been working on throught the years.

## TOTP-M5 (2021)
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

### TOTP-S3 (2024)
Later I migrated this code to a new board: WT32-SC01.

<img width="362" height="375" alt="image" src="https://github.com/user-attachments/assets/085d38cd-ef3e-4390-83aa-0f8de4f89a07" />


The code is mostly the same except for the one required for displaying the TOTP codes in the much bigger screen (3.5" instead of 1.14").

## Pokémon (2022)
This project was part of a hiring challenge in the Quantum group. The process required creating a tool which allowed to manage Pokémons. 
I had no idea of what Pokémons were. So I had to request for my daughter's advice.

Instead of going the easy way using the tools I was used to (Java + DB2), I decided to transform this challenge into an opportunity to learn and test new options.
So, I chose **Node.js** for the backend, **JavaScript** for the front end (with **Bootstrap** and **jQuery**) and **MongoDB** to store the database and giving NoSQL a try instead of using a SQL option. 

This was an interesting challenge back in 2022. There was no AI so I had to build the application from scratch without any assisstants.

<img width="1204" height="818" alt="image" src="https://github.com/user-attachments/assets/e328e36e-06d8-406a-91ea-954024d8a0ed" />

