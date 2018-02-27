# Web Socket Trace

The connection is established with: wss://us-long.coolkit.cc:8080/api/ws

Updates from the device are sent asynchronously.

When an request is made, the server responds with a success message.

## Trace Script

When the connection is opened the client sends a "userOnline" action with various details about the client.

	{
	  "action": "userOnline",
	  "version": 6,
	  "imei": "D139421A-17B5-11E8-B642-0ED5F89F718B",
	  "ts": "1519293433",
	  "model": "iPhone8,4",
	  "os": "ios",
	  "romVersion": "11.2.5",
	  "at": "3c303f2cd81300278df1f299cbf7093bf921d797",
	  "userAgent": "app",
	  "apikey": "ea017bb3-892a-4ce0-8cd6-a4ad5e1b5843",
	  "appid": "koOxK9TnUzqA703xezqmF96RzEAoL6Vn",
	  "nonce": "3BDdpq43",
	  "sequence": "1519293433136",
	  "apkVesrion": "1.8"
	}

The API responds with an object that specifies "hb" properties which presumably define heartbeat parameters.

	{
	  "error": 0,
	  "apikey": "ea017bb3-892a-4ce0-8cd6-a4ad5e1b5843",
	  "config": {
	    "hb": 1,
	    "hbInterval": 145
	  },
	  "sequence": "1519293433136"
	}

The client requests that the device switch on when the temperature gets below 28 degrees celcius.

	{
	  "action": "update",
	  "apikey": "ea017bb3-892a-4ce0-8cd6-a4ad5e1b5843",
	  "deviceid": "babecafe11",
	  "params": {
	    "deviceType": "temperature",
	    "mainSwitch": "on",
	    "targets": [
	      {
	        "targetHigh": "28",
	        "reaction": {
	          "switch": "off"
	        }
	      },
	      {
	        "targetLow": "28",
	        "reaction": {
	          "switch": "on"
	        }
	      }
	    ]
	  },
	  "sequence": "1519293442952",
	  "userAgent": "app"
	}

The server responds with a simple success message.

	{
	  "error": 0,
	  "deviceid": "babecafe11",
	  "apikey": "ea017bb3-892a-4ce0-8cd6-a4ad5e1b5843",
	  "sequence": "1519293442952"
	}

The client requests that the device switch on when the temperature gets above 28 degrees celcius.

	{
	  "action": "update",
	  "apikey": "ea017bb3-892a-4ce0-8cd6-a4ad5e1b5843",
	  "deviceid": "babecafe11",
	  "params": {
	    "deviceType": "temperature",
	    "mainSwitch": "on",
	    "targets": [
	      {
	        "targetHigh": "28",
	        "reaction": {
	          "switch": "on"
	        }
	      },
	      {
	        "targetLow": "28",
	        "reaction": {
	          "switch": "off"
	        }
	      }
	    ]
	  },
	  "sequence": "1519293449395",
	  "userAgent": "app"
	}

The server responds with a simple success message.

	{
	  "error": 0,
	  "deviceid": "babecafe11",
	  "apikey": "ea017bb3-892a-4ce0-8cd6-a4ad5e1b5843",
	  "sequence": "1519293449395"
	}

The server asynchronously sends an update about the device's stats (no temp or humidity data).

	{
	  "action": "update",
	  "deviceid": "babecafe11",
	  "apikey": "ea017bb3-892a-4ce0-8cd6-a4ad5e1b5843",
	  "userAgent": "device",
	  "ts": 0,
	  "params": {
	    "rssi": -55,
	    "staMac": "2C:3A:E8:4F:54:59",
	    "fwVersion": "2.0.4",
	    "startup": "off",
	    "switch": "off"
	  },
	  "from": "device"
	}


The client requests that the device be switched off manually.

	{
	  "action": "update",
	  "userAgent": "app",
	  "apikey": "ea017bb3-892a-4ce0-8cd6-a4ad5e1b5843",
	  "deviceid": "babecafe11",
	  "params": {
	    "deviceType": "normal",
	    "mainSwitch": "off"
	  },
	  "sequence": "1519293454525"
	}

The server responds with a simple success message.

	{
	  "error": 0,
	  "deviceid": "babecafe11",
	  "apikey": "ea017bb3-892a-4ce0-8cd6-a4ad5e1b5843",
	  "sequence": "1519293454525"
	}

The client requests that the device be switched on manually.

	{
	  "action": "update",
	  "userAgent": "app",
	  "apikey": "ea017bb3-892a-4ce0-8cd6-a4ad5e1b5843",
	  "deviceid": "babecafe11",
	  "params": {
	    "switch": "on",
	    "mainSwitch": "on",
	    "deviceType": "normal"
	  },
	  "sequence": "1519293457086"
	}

The server responds with a simple success message.

	{
	  "error": 0,
	  "deviceid": "babecafe11",
	  "apikey": "ea017bb3-892a-4ce0-8cd6-a4ad5e1b5843",
	  "sequence": "1519293457086"
	}

The server asynchronously sends an update about the device's temp sensor (no humidity).

	{
	  "action": "update",
	  "deviceid": "babecafe11",
	  "apikey": "ea017bb3-892a-4ce0-8cd6-a4ad5e1b5843",
	  "userAgent": "device",
	  "ts": 0,
	  "params": {
	    "currentTemperature": "22",
	    "currentHumidity": "unavailable"
	  },
	  "from": "device"
	}
