# Smart Dancing Robot

Project aims to create a robot that is able to dance under any music by counting the BPM (Beats per minute) and and realize a real-time dance by using Raspberry Pi (Python language) and EV3 brick. In other words the robot dances by feeling the rhythm of the music. This program consist of two parts: BPM counter and dance part. 


### Robot's algorithm
##### 1. BPM Counter for Raspberry Pi
-  Input has two modes: microphone (doesn't work effective in practice because of motor noises) or file (.wav).
-  Analysing inputs: making correlation between amplitude and frequency.
-  Finding peaks and predicting coming peaks.
-  Counting BPM and sending it to EV3.  
##### 2. EV3 Programs
- Waiting for BPM value.
- Receiving from Raspberry Pi.
- Converting BPM to motor power (calculated equation).
- Movement sequence random generating.
- Execution.
### How to install, use and run
- I used Wi-Fi adapter to control Raspberry Pi with SSH Protocol.
- Install libraries (links).
- Install this image file on your EV3 to control it with Raspberry Pi (you can use this guideline.
- Connect your EV3 with Raspberry Pi (via USB) and send codes to Raspberry Pi by SSH.
- BPMFinal.py must stay in Raspberry Pi, but others should be sended to EV3 via SSH.
- Preferred music file should have .wav extension, otherwise program wouldn't run it.
- Finally rename your music file's name to "demo.wav". 
- Change the IP address in 147th line of BPMFinal.py program.
- Run this "sudo python BPMFinal.py && aplay demo.wav"


References:
- https://drive.google.com/open?id=0BySUMIW0s8zZUGhGZDNxTXp2dDg
- https://2017.spaceappschallenge.org/challenges/ideate-and-create/bring-your-own-solution/teams/untitled_1/project
- https://gist.github.com/virtuald/c30032a5b8cdacd1a6c0



#### Have fun :) 






Dancing Rover
putty 
https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

#### Տեխնիկական մաս
Micro SD Card-ը միացնել EV3-ին։ Քարտի մեջ կա EV3dev http://www.ev3dev.org/.
Մանիպուլյատոռ հորիզոնական ձախ- A
աջ- C
Մանիպուլյատոռ ուղղահայաց  ձախ - B
աջ- D
MiniUSB-ով միանցնեք Raspberry Pi-ին ու EV3-ով ստուգենք IP գրում է թե ոչ։ Եթե չի գրում միացնում ենք ձեռքով EV3 (Wireless and Networks -> All Network Connections -> Wired -> Connect).

#### Համակարգչային մաս
1.Բացենք 2 հատ putty (մեկով միշտ կպած ենք EV3-ին մյուսով կպած ենք Raspberry Pi-ին)
2.Ստուգում ենք Wi-Fi գտնում USSR և միանում
Password- Vodka2017
3.Raspberry Pi IP միշտ նույնն է- 192.168.42.1 (2 putty -ի համար սա ենք գրում)
Raspberry Pi
4.login- pi
5.password- raspberry

#### EV3 (Ընդհանուր տվյալներ) 
login - robot
password - maker

6.sudo ssh robot@169.254........(IP) միայն մեկի համար
7.yes
8.maker


**
#### Այն դեպքում եթե Raspberry Pi-ի և EV3 -ի մեջ ֆայլեր չկան։
Միացնում ենք ֆլեշկան (2-րդի համար)

1.sudo mount /dev/sda1 /mnt/usbstorage/
#### Եթե չստացվեց՝ 
1* sudo reboot now
#### Գտնում ենք մեր ֆայլերը (Raspberry Pi)
2. cd /mnt/usbstorage/Vsyakaya Vsyachina/BPMFINAL/
3. ls
4. sudo cp BPMFinal.py /usr/PythonProgramms/
5. sudo cp michael.wav /usr/PythonProgramms/
#### Գտնում ենք մեր ֆայլերը (EV3)
2. cd /mnt/usbstorage/Vsyakaya Vsyachina/BPMFINAL/
3. ls
4. sudo cp TestMotorDelete.py /home/robot/
5. sudo cp write.py /home/robot/



**

##### Raspberry Pi-ի տերմինալի մեջ
9. cd /usr/PythonProgramms/
10. sudo nano BPMFinal (Բացում ենք, BPMFinal-ի մեջ փոխում ենք IP-ին)
11. Իջնում ենք մինչև "Special for Tatev" տողը և փոխում ենք IP-ին։ Եթե չենք գտնում, ապա փորձում ենք գտնել հետևյալ տողը՝
connnection = ssh ("169.254...", "robot", "maker")
12. Փակում ենք (Ctrl + X -> Y -> Enter)
13. Միացնում ենք էլեկտրոնիկան․
    Միացնում ենք էլեկտրոնիկան միկրոֆոնի ելքին 
    Սեղմում ենք սպիտակ կոճակը, որը գտնվում է այն պլատայի վրա 2 հատ ռեոստատ կա։
14. sudo python BPMFinal.py && sudo aplay michael.wav


#### EV3-ի տերմինալի մեջ
1. cd /home/robot/
2. sudo python3 TestMotorDelete.py

Եթե ցանկանում ենք պռոցեսի ընթացքում անջատել ծրագիրը 
Ctrl +C հետո գրել sudo python3 Stop.py (կամ ուղղակի Ctrl + C, անջատում ենք EV3-ի մոտոռի լարերը)

Եթե ցանկանում ենք փոխել երաժշտությունը 
1. sudo nano BPMFinal բացում ենք ֆայլերը և գտնում ենք "Special for Tatev"- ից ներքև uri-ով սկսվող տողը փոխում "michael.wav" ֆայլը մեր ուզած ֆայլի հետ։
