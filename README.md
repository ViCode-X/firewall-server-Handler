# Firewall-Server-Handler
The purpose of this repo is to simulate a firewall server handling a malicious event

## Introduction


The purpose of this repo is to simulate a firewall server handling a malicious event for a Cyber virtual experience program.


## Requirements


* Python 3+


## Get Started


The base HTTPServer is available in `firewall_server.py`. To start the server:


```python
python firewall_server.py
```


You can visit http://localhost:8000 in your browser and assert the console output for the server displays the response.


After you have written your firewall rule, you can test your code by running:


```python
python test_requests.py
```


This will make 5 test requests to `localhost:8000`, simulating the malware attack.


## Resources


HTTPServer: https://docs.python.org/3/library/http.server.html
