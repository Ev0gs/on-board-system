# On-board-system(C++/SHELL)
This project is one I've done for my studies, more precisly during my second year in Engineer school. It explains the fact I was in a project team of 3 classmates. The subject of this project is on-board system, linux and C++

# Introduction
### Context :
The International Meteorological Agency (IMAA) is embarking on an ambitious project: deploying surveillance ships equipped with onboard weather stations in the oceans, in charge of measuring the parameters influencing the formation of cyclones and other natural disasters. In this project, we are part of the start-up in which the engineer son of one of the leaders works, with the aim of creating the prototype.

### Problematic :
Comment réaliser une maquette fonctionnelle de la station météorologique imaginée par l’AIVM dans le but de prévoir des catastrophes naturelles ?

# System analysis
In order to make the IAML project clear, we decided to carry out an analytical study of the system. Indeed, in order to understand the latter, we started to create several different UML diagrams, adapted in SysML (on Modelio Software) such as use case, activity, sequence and component diagrams.\
Each diagram helps to understand different parts or functionalities of the system:
* The use case diagram represents the services or functionalities offered by the system. Each use case groups a set of functionalities.
* The activity diagram allows you to refine the use cases by specifying the different activities and actions required to carry them out. This type of diagram is closer to an algorithm.
* The sequence diagram is used to model the operational scenarios at the beginning of the modeling process, and then to model the collaboration between the blocks.
* Le diagramme de composants permet de décrire l’organisation du système du point de vue des éléments logiciels comme les modules, les données, ou encore les éléments de configuration. Il permet aussi de mettre en évidence les dépendances entre les composants.

### Use Case diagram
<p align="center">
  <img width="600" height="600" src="https://user-images.githubusercontent.com/93186642/139080010-43344040-e219-436b-a42a-6492a323cca1.png">
</p>

### Components diagram
<p align="center">
  <img width="800" height="600" src="https://user-images.githubusercontent.com/93186642/139080275-0092b4d3-fbcb-46ed-a259-6de46bce2947.png">
</p>

### Activity diagramm
For this type of diagram, we decided to make two of them which represent the most important of them :

<p align="center">
  <img width="300" height="300" src="https://user-images.githubusercontent.com/93186642/139081106-9c6c8b38-128a-4d92-bc9f-782059253d3c.png">
</p>
<p align="center">
  <img width="300" height="300" src="https://user-images.githubusercontent.com/93186642/139081179-2bba3416-c005-4b33-a2e0-d1097013011f.png">
</p>
<p align="center">
  <img width="300" height="300" src="https://user-images.githubusercontent.com/93186642/139081249-6384635e-4eef-43de-945b-814eacacb47d.png">
</p>

### Sequence diagram
In order to make this diagram, we had to study the functionality of saving data in standard mode, so we cut out each step of this functionality to obtain this diagram. Thus, when the user turns on the system with the buttons, it will launch the program, which will activate the sensors that will detect the weather data that will be saved on the SD card, and this will continue until the user deactivates the device, pressing a button that will stop the program and therefore the sensors. 

<p align="center">
  <img width="800" height="600" src="https://user-images.githubusercontent.com/93186642/139081651-94a23aa7-47e6-401f-90b6-54ff7a169e4d.png">
</p>

# Program's architecture
Then, in order to realize a clear and functional code we decided to make a clear algorithm of the program's architecture. Indeed, functions are not called in the main function because we forget it but the main features of the system are there.
This architecture is in the folder of the repository if you want to check it.

# Final code
Finally, we had a lot of problems during this project using the differents new notions of coding but we managed to implement the most features (on VS Code PlatformIO of a linux VM) that are for us the main of this system. This one has three modes with specific features for each :
* Standard Mode :
  * Green light (RGB LED)
  * Acquires data from sensors each 10 minutes
  * Saves data on timestamp line in a txt file on SD CARD

* Economy Mode :
  * Blue light (LED RGB)
  * Same functionalities than standard mode but time between each acquirement of data is multiplied by 2
  * GPS data are acquired 1 out of 2 times

* Configuration Mode :
  * Orange light (RGB LED)
  * Can change value of some settings
  * If you restart the system it reset the value of settings

* Maintenance Mode :
  * Red light (RGB light)
  * Stop writing data in SD CARD (so you can change SD CARD easily)
  * Show timestamp line with sensor values as it have to be save on sd CARD but it doesn't save.

_If the program can't access the txt file, the system show an error in the serial monitor and RGB light blink 1 time from red to white (time of white led 2 times longer than red one)._

We also made a bash script to create an auto compiler for our program but we had a problem with the libraries and the time before delivering our work.

__You can find the code in the files of this repository__

# Our weather station model
### Hardware
* Microcontroller: AVR ATmega328 which is integrated in the Arduino board that will be used to design the prototype.
* Components :
  * SD card reader (SPI) which will allow the saving of the sensors' data
  * RTC clock (I2C) that will allow the system to know the date and time of day.
  * RGB LED (2-wire) that will allow to communicate the status of the system
  * 2 push buttons (digital) that will allow interaction with the system
* Sensors :
  * Air pressure (I2C or SPI)
  * Air temperature (I2C or SPI)
  * Hygrometry (I2C or SPI)
  * GPS (UART)
  * Brightness (analog)
* Additional third-party modules that will be integrated into the project later:
  * Water temperature (analog)
  * Sea current force (I2C)
  * Wind force (I2C)
  * Fine particle rate (2-wire)

### Model
<p align="center">
  <img width="500" height="500" src="https://user-images.githubusercontent.com/93186642/139085506-af895460-9e7c-4bf6-988a-0b34f08acb7f.png">
</p>

__You will find videos to show you a demo of our system__



