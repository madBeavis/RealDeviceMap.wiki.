The RDM Device Controller API allows Phones (Device Controllers) to interact with RDM.
This allows RDM to control the phones.

The Device Controller API bas url is `RDM_IP:9001/controler` and accepts `POST REQUESTS` at that url.
The `/controler` Route expects a `JSON` as `POST BODY` and will answer with a `JSON`.

## Example Request: 
**URL:** `http://RDM_IP:9001/controler`<br>
**METHOD:** `POST`<br>
**BODY:** 
```
{
  "uuid": "The Phones UUID",
  "type": "The Correct Action"
}
```
**RESPONSE:**
```
{
  "status": (The status of the request: "ok" or "error")
  "error": (Only set it status = error, contains error information)
  "data": (Only set if status = ok, contains data)
}
```


## Actions

### Type `init`
**Info**: Initializes the device on RDM. Should be called once on each App start.<br>
**Data:**<br>
`assigned`: Bool (returns weather or not the device is assigned to any instance, only continue if this is true)

### Type `heartbeat`
**Info**: Should be send every 5 seconds while running.<br>
**Data:** none

### Type `get_job`
**Info**: Gets a task that the devices should do next.<br>
**Data:**<br>
`action`: String ("scan_pokemon" or "scan_raid", should wait until Pokemon or Raids are loaded before contonuing)
`lat`: Double (The Latitude of the scan)
`lon`: Double (The Longitude of the scan)