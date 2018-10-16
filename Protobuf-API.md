The RDM Protobuf allows Phones to send data in from of base64 encoded protobuf files to RDM.

The Device Controller API bas url is `RDM_IP:9001/raw` and accepts `POST REQUESTS` at that url. The `/raw` Route expects a `JSON` as `POST BODY` and will answer with a `JSON`.


## Example Request: 
**URL:** `http://RDM_IP:9001/raw`<br>
**METHOD:** `POST`<br>
**BODY:** 
```
{
   "gmo": [
      {
         "data": "CsQHCICAgIDkoJnzRxC30PrW5ywaQgojM...."  // GMO Raw Packet with Base64 Encoded
      }, 
      {
         "data": "CsQHCICAgIDkoJnzRxC30PrW5ywaQgojM...."  // GMO Raw Packet with Base64 Encoded
      }, 
   ]
}
```
**RESPONSE:**
```
{
  "status": (The status of the request: "ok" or "error")
  "error": (Only set it status = error, contains error information)
}
```

## Format 

### `gmo`
Should contain an array Base64 encoded GMO Protobuf data like in the example above 
