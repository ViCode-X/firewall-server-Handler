import requests

def handle_request(self):
    # Check the incoming request and determine whether it should be blocked
    if should_block_request(self):
        block_request(self)
    else:
        # If the request should not be blocked, send a response
        self.send_response(200)
        self.send_header("content-type", "application/json")
        self.end_headers()

def should_block_request(request_handler):
    # Check if the request method is POST and the path is "/tomcatwar.jsp"
    if request_handler.command == "POST" and request_handler.path == "/tomcatwar.jsp":
        return True

    # Check if any request header contains the specified string
    headers = request_handler.headers
    for header in headers:
        if "suffix=%>//\nc1=Runtime\nc2=<%\nDNT=1\nContent-Type=application/x-www-form-urlencoded\n" in headers[header]:
            return True

    return False

def block_request(request_handler):
    # Log the blocked request in another server
    log_url = "http://my_server/log"
    log_data = {
        "method": request_handler.command,
        "path": request_handler.path,
        "headers": dict(request_handler.headers)
    }

    try:
        response = requests.post(log_url, json=log_data)
        if response.status_code == 200:
            print("Blocked request logged successfully")
        else:
            print("Failed to log blocked request")
    except requests.exceptions.RequestException as e:
        print("Failed to connect to the logging server:", str(e))

    # Send a custom response to indicate that the request was blocked
    request_handler.send_response(403)
    request_handler.send_header("content-type", "text/plain")
    request_handler.end_headers()
    request_handler.wfile.write(b"Access Denied: Request blocked by firewall rule")
