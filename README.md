# PI VIDEO RECORDING & LIVE
Raspbian with raspivid

## Enable camera on raspberry
`sudo raspi-config`

Then -> Interface options -> Camera -> Enabled ? Yes

## VLC Installation
`sudo apt-get install vlc`

## avconv to convert from h264 to mp4
`sudo apt-get install libav-tools`

## Conf
In config.json, you can specify :
```json
{
  "allowedOrigins": [
    "*"
  ],
  "port": 5000,
  "livePort": 5002,
  "recordTimeout": 610000,
  "writePath": "/tmp",
  "size": {
    "width": 900,
    "height": 1600
  }
}
```

    
## Launch server
`npm start`

## Requests
- **GET** : `/api/`
	
	To check if the server is running.
- **GET** : `/api/state`
	
	To know the current state of the server.
- **POST** : `/api/live/start`
	
	To start the live streaming
- **POST** : `/api/live/stop`
	
	To stop the live streaming
- **POST** : `/api/record/start filename`
  
	- `filename`: name of your recording file
	
  To start the recording.
- **POST** : `/api/record/stop filename`
	
	- `filename`: name of your recording file
	
	To stop the recording -> also encoding from h264 to mp4 (can take some time)
