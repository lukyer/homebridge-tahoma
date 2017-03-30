# homebridge-tahoma

Supports Overkiz platform (TaHoma, Cozytouch) on HomeBridge

# Installation

1. Install homebridge using: npm install -g homebridge
2. Install this plugin using: npm install -g homebridge-tahoma
3. Update your configuration file. See bellow for a sample. 

# Configuration

Configuration sample:

 ```
    {
        "bridge": {
            ...
        },
        
        "description": "...",

        "accessories": [],

        "platforms":[
        	{
            	"platform": "Tahoma",
            	"name": "Tahoma",
            	"user": "yourusername",
            	"password": "yourpassword",
	    		"service": "Service name ('TaHoma' or 'Cozytouch')"
        	}
        ]
    }
```

| Parameter                  | Note                                                                                                                                                                  |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user`               		 | mandatory, your TaHoma/Cozytouch account username                                                                                                                     |
| `password`             	 | mandatory, your TaHoma/Cozytouch account password                                                                                                                     |
| `service`              	 | optional, service name in [TaHoma, Cozytouch], default: TaHoma                                                                                                        |
| `refreshPeriod`            | optional, device states refresh period in minute, default: 10 																										 |
| `exclude`		             | optional, list of protocols (hue,enocean,zwave,io,rts) or device (name) to exclude                                                                                    |
| `Alarm`		             | optional, Alarm configuration object																																	 |
|							 | | `STAY_ARM`| list of zones (A,B,C) to activate in "STAY" mode 																										 |                                                                              												     |
|							 | | `AWAY_ARM`| list of zones (A,B,C) to activate in "NIGHT" mode  																									 |                                                                              												     |
                                                                                												     																 |

Full configuration example:
 ```
    {
        "bridge": {
            ...
        },
        
        "description": "...",

        "accessories": [],

        "platforms":[
        	{
            	"platform": "Tahoma",
            	"name": "Tahoma",
            	"user": "yourusername",
            	"password": "yourpassword",
	    		"service": "TaHoma",
	    		"exclude": ["hue","rts","Garage Door"],
	    		"Alarm": {
	    			"STAY_ARM": "A,C",
	    			"NIGHT_ARM": "B"
	    		}
        	}
        ]
    }
```

# Limitation

Tested device : 
- RollerShutter

Read-only tested devices : 
- Alarm
- DoorLock
- GarageDoor
- Gate

Not tested devices : 
- HeatingSystem
- OnOff
- Light
- ContactSensor
- OccupancySensor
- SmokeSensor
- LightSensor
- TemperatureSensor

Sensor state is only updated every 10 minutes for the moment.

# Contribute

You are welcome to contribute to this plugin development by adding new kind of devices by adding implementation `.js` file in `accessories` folder.
Please have a look to `RollerShutter.js` file for example.
