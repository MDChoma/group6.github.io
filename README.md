# group6.github.io

<html>
<head>
<title>ThingSpeak</title>
  
<link rel="stylesheet" href="https://pyscript.net/alpha/pyscript.css" />
<script defer src="https://pyscript.net/alpha/pyscript.js"></script>
</head>


<body>

import urllib
import re
from bs4 import BeautifulSoup

#Sensor 3 Temperature 
datafromwebsite=urllib.request.urlopen(" https://api.thingspeak.com/channels/1738066/fields/1.json?results=1");
select=repr(datafromwebsite.read());
select=select[::-1]
pick=re.search('}]}(.+?):"1dleif',select)
m=repr(pick);
m=m[::-1]
fannie=re.search('field1":"(.+?)"',m)
if fannie:
  print(fannie.group(1));
x= float(fannie.group(1))
print(x)
if x > 10:
  telegramtemp1=urllib.request.urlopen("https://api.telegram.org/bot5351217346:AAECgdjzWMdRZFd0YPiSn1glvbODjEfhM1M/sendMessage?chat_id=@dfctunnel&text=Hi.%20Kindly%20ignore%20this%20message%20if%20you%20are%20not%20in%20the%20DFC%20Mining%20Tunnel%20%20%20%20%20%20%20%20Sensor%203%20has%20detected%20temperatures%20above%2050%20degree%20celcius%20.%20Stay%20alert")
print("Sensor 3 has reached temperature greater than 10");


#Sensor 3 Humidity
datafromwebsite=urllib.request.urlopen(" https://api.thingspeak.com/channels/1738066/fields/2.json?results=1");
select=repr(datafromwebsite.read());
select=select[::-1]
pick=re.search('}]}(.+?):"2dleif',select)
m=repr(pick);
m=m[::-1]
fannie=re.search('field2":"(.+?)"',m)
if fannie:
  print(fannie.group(1));
  x = float(fannie.group(1))
  print(x)
  if x > 10:
    telegramhum1=urllib.request.urlopen("https://api.telegram.org/bot5351217346:AAECgdjzWMdRZFd0YPiSn1glvbODjEfhM1M/sendMessage?chat_id=@dfctunnel&text=Hi.%20Kindly%20ignore%20this%20message%20if%20you%20are%20not%20in%20the%20DFC%20Mining%20Tunnel%20%20%20%20%20%20%20%20Sensor%203%20has%20detected%20humidity%20above%2050%20percent%20.%20Stay%20alert")
print("Sensor 3 has reached humidity greater than 10");



</body>

</html>
