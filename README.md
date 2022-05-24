# Heart-Rate-Sensor-Tivaware
<img width="600" alt="image" src="https://user-images.githubusercontent.com/93160540/169710600-c4ebd129-f4dc-41e9-bc1a-7bf009324da4.png">



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

<img width="622" alt="image" src="https://user-images.githubusercontent.com/93160540/170086519-d9695027-88ad-42b9-b9e8-7e5b18bc7947.png">



## How does Heart Rate Sensor work? 
<img width="400" alt="image" src="https://user-images.githubusercontent.com/93160540/169711314-4020839f-d24b-46ad-8f80-7badaba57c07.png">

- Hemoglobin rich in oxygen absorbs more green light than hemoglobin with depleted oxygen. As Systolic push of heart pumps the blood to capillaries at the tip of finger, the light penetration rate changes. The photoreceptor detects the change in heart rate, then sends the analog signal which is processed through MCP6001 Op-Amp 

### Sampling Rate of Heart Rate 

- Too high sampling rate would require large array size to save all the data, and also inaccurate heart rate calculation. 
- Too low sampling rate can lead to inadequate samples to compare with previous / next value.
- Every 1 seconds, the ADC will evaluate 10 analong signals. 
- For total of 10 seconds, the Heart Rate Buffer array will save 100 points from the Heart Rate Sensor. 
- The array would calculate the 10 seconds average of heart rate reading, and compare it to individual array points. 
<img width="818" alt="image" src="https://user-images.githubusercontent.com/93160540/170085859-abb73476-69ba-4bc6-89ce-fe86ffa1f900.png">

- If the i<sup>th</sup> term of array value has higher value than i-1<sup>th</sup> value of array or i+1<sup>th</sup> term of array value and have higher value than 10 seconds average, then it would be considered as one heart rate. 
- 10 seconds heart rate * 6 = Heart Rate / min. 


## How does display work? 

<img width="538" alt="image" src="https://user-images.githubusercontent.com/93160540/169711518-c0a56101-fdaf-4bda-9c30-7cd61fa3a5a0.png">
<img width="506" alt="image" src="https://user-images.githubusercontent.com/93160540/169711554-ed227455-95d4-4e68-84d7-1a78f22d75a1.png">

- the display is two parallel 4-digit 7-segment display. All of the segments will be connected together, so the whole display would require total of 8 + 7 = 15 ports. 

### Display Refresh Rate 
<img width="500" alt="image" src="https://user-images.githubusercontent.com/93160540/170086942-041b7f46-32a4-417c-be9c-62852948a0c6.png">
<img width="500" alt="image" src="https://user-images.githubusercontent.com/93160540/170087015-55c32a38-adaa-4ea0-b28e-6d39364ff665.png">

- It takes 2.5ms for one digit to display and then shift to right digit. 
- 2.5ms * 8 digits = 20ms. 
- For one digit to refresh, it take 20ms. 


