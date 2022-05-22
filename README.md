# Heart-Rate-Sensor-Tivaware
<img width="600" alt="image" src="https://user-images.githubusercontent.com/93160540/169710600-c4ebd129-f4dc-41e9-bc1a-7bf009324da4.png">

## How does Heart Rate Sensor work? 
<img width="400" alt="image" src="https://user-images.githubusercontent.com/93160540/169711314-4020839f-d24b-46ad-8f80-7badaba57c07.png">

- Hemoglobin rich in oxygen absorbs more green light than hemoglobin with depleted oxygen. As Systolic push of heart pumps the blood to capillaries at the tip of finger, the light penetration rate changes. The photoreceptor detects the change in heart rate, then sends the analog signal which is processed through MCP6001 Op-Amp 


## How does display work? 

<img width="538" alt="image" src="https://user-images.githubusercontent.com/93160540/169711518-c0a56101-fdaf-4bda-9c30-7cd61fa3a5a0.png">
<img width="506" alt="image" src="https://user-images.githubusercontent.com/93160540/169711554-ed227455-95d4-4e68-84d7-1a78f22d75a1.png">

- the display is two parallel 4-digit 7-segment display. All of the segments will be connected together, so the whole display would require total of 8 + 7 = 15 ports. 

### Pin Configuration 

#### Analog Heart Rate Sensor 

Sensor   | Port 
------------- | -------------
\+  | Vcc
\-  | GND 
Analog Signal | PE3 


Display Input | Port Configuration
------------- | -------------
a  | PB6
b  | PB5
c  | PB4 
d  | PB3 
e  | PB2
f  | PB1 
g  | PB0 
Digit 7 | PA7 
Digit 6 | PA6 
Digit 5 | PA5 
Digit 4 | PA4 
Digit 3 | PF3 
Digit 2 | PF2 
Digit 1 | PF1 
Digit 0 | PF0



### Changing period 

Period  | Description 
------------- | -------------
display_refresh_period| This is display refresh rate. (Time required to shift digit to right)
ADC_update_period| ADC sampling speed. Default is 10Hz. IF you want higher sampling rate for heart rate sensor, raise this number 
initial_load_message_period | initial message refresh rate. If you want message to be displayed slower, raise this number 

```
unsigned long display_refresh_period = 10000000/400; //Screen Refresh Rate 
unsigned long ADC_update_period = 10000000/10; //Timer 1A delay for ADC update. 10 Hz.
unsigned long initial_load_message_period = 10000000*1; //Initial message refresh

```




