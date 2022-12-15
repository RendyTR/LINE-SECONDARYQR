## BOT UNOFFICIAL
GENERATE LINE SECONDARY TOKEN BY IMJUSTGOOD API

```python
import json, requests

apikey    = "INPUT_YOUR_APIKEY"
host      = "https://api.imjustgood.com/lineqr"
agents    = "Mozilla/5.0 (X11; Linux x86_64) Chrome/51.0.2704.106"
appname   = "DESKTOPMAC\t7.13.2\tMac\t10"
sysname   = "IMJUSTGOOD"
cert      = None

headers   = {
    "User-Agent": agents,
    "apikey": apikey,
    "appName": appname,
    "sysName": sysname,
    "cert": cert,
}

main      = json.loads(requests.get(host, headers=headers).text)
qrlink    = main["result"]["qr"]
barcode   = main["result"]["barcode"]
print(qrlink)
print(barcode)

callback  = main["result"]["callback"]["pin"]
data      = json.loads(requests.get(callback, headers=headers).text)
if data["status"] == 200:
    pincode = data["result"]["pin"]
    print(pincode)

callback  = main["result"]["callback"]["token"]
data      = json.loads(requests.get(callback, headers=headers).text)
certified = data["result"]["cert"]
authtoken = data["result"]["token"]
print(certified)
print(authtoken)
```
