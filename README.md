## BOT UNOFFICIAL
SIMPLE GENERATE SECONDARY TOKEN BY IMJUSTGOOD API

```python
import json, requests

host = "https://api.imjustgood.com/lineqr"
headers = {
    "apikey": "your_apikey_here",
    "appName": "CHROMEOS\t2.4.5\tChromeOS\t88",
    "sysName": "JUSTGOOD",
    "cert": None,
    "User-Agent": "Justgood/5.0"
}
main = json.loads(requests.get(host, headers=headers).text)
url = main["result"]["qr"]
print(url)

callback = main["result"]["callback"]["pin"]
data = json.loads(requests.get(callback, headers=headers).text)
if data["status"] == 200:
    pin = data["result"]["pin"]
    print(pin)

callback = main["result"]["callback"]["token"]
data = json.loads(requests.get(callback, headers=headers).text)
certified = data["result"]["cert"]
authtoken = data["result"]["token"]
print(certified)
print(authtoken)
```

Join our forum for more information <a href="https://api.imjustgood.com/custom/forum">here</a>
