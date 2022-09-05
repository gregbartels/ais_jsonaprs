# ais_jsonaprs
This is a improvement code based on the  github project created by https://github.com/hsiboy/ais_json  the idea is continue the code usage to upload  AIS packages to   APRS.fi website, used for Ham radio amateur operators around the world to track positions via Radiofrequency instead of depends of GPS positioning.


# ais_json

This is a simple AIS parser that reads a UDP stream from [aisdispatcher](http://www.aishub.net/ais-dispatcher) parses it into JSON and posts the output via http to the aprs.fi endpoint.

requires libais: https://pypi.org/project/libais/

aprs.fi accepts the ais message in the following format:

```json
{
 "protocol": "jsonais",
 "encodetime": "20131231235959",
 "groups": [
  {
   "path": [ { "name": "MYACCOUNT", "url": "http://www.example.com/" } ],
   "msgs": [
    {
     "msgtype": "18",
     "mmsi":123456789,
     "callsign":"C4LL5GN",
     "shipname":"MY BOAT NAME",
     "shiptype":37,
     "status":5,
     "speed":0,
     "lon":0.00000,
     "lat":0.00000,
     "course":0.0,
     "heading":0.0,
     "length":12,
     "width":2,
     "ref_front":6,
     "ref_left":1,
     "draught":1,
     "rxtime":"20131231235959"
    }
   ]
  }
 ]
}
```

## usage:

1. Receiving the data from the receiver: use AISDispatcher (http://www.aishub.net/ais-dispatcher)  to recieve the stream on your machine.

2. Decoding raw NMEA messages: use ais_json to decode and upload data to APRS.fi. 

This code reads the AISdispatcher UCP stream, so for example, set AISDIspatcher output to  `PORT = 5000, IP='127.0.0.1'` this script  (ais_json) needs to be running in the background.

edit settings.py to include your aprs.fi account name and SeCrEtKeY

Your AIS SeCrEtKeY can be found in https://aprs.fi/account/ under "AIS password"


## install

* git clone https://github.com/hsiboy/ais_json.git
* pip install libais
* pip install termcolor
* $ cd ais_js/

Run in the background
* $ ./ais_json.py &


