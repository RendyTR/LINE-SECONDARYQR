## BOT UNOFFICIAL
SIMPLE GENERATE SECONDARY TOKEN BY IMJUSTGOOD API

```python
import json, requests

host      = "https://api.imjustgood.com/lineqr"
headers   = {
    "User-Agent": "Justgood/5.0"
    "apikey": "YOUR APIKEY HERE",
    "appName": "CHROMEOS\t2.4.7\tChromeOS\t96",
    "sysName": "IMJUSTGOOD",
    "cert": None,
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

Join our forum for more information <a href="https://api.imjustgood.com/custom/forum">here</a>
