# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program 
```
Name:MOHAMMED JASITH J
Reg no:212225230180
```
ex5.py
```
import socket

def start_server():
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind(("127.0.0.1", 8080))
    server_socket.listen(1)

    print("Server running at http://127.0.0.1:8080")

    conn, addr = server_socket.accept()
    print("Connected by:", addr)

    request = conn.recv(1024).decode()
    print("Request:\n", request)

    # Read HTML file
    with open("index.html", "r") as f:
        html_content = f.read()

    # HTTP response
    response = "HTTP/1.1 200 OK\r\nContent-Type: text/html\r\n\r\n" + html_content

    conn.sendall(response.encode())

    conn.close()
    server_socket.close()

start_server()
```
index.html
```
<!DOCTYPE html>
<html>
<head>
    <title>Book Cover</title>
<style>
body, html {
    margin: 0;
    padding: 0;
    height: 100%;
    font-family: 'Georgia', serif;
}

.cover {
    position: relative;
    width: 100%;
    height: 100vh;
    background-color:black;
    overflow: hidden;
}

.bg-img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    opacity: 0.7;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 0;
}

.content {
    position: relative;
    z-index: 1;
    color: white;
    text-align: center;
    padding-top: 15%;
}

.title {
    font-size: 3.5em;
    margin-bottom: 10px;
    color: #fff;
    text-shadow: 2px 2px 8px #000;
}

.subtitle {
    font-size: 1.8em;
    margin-bottom: 30px;
    color: #ccc;
}

.author {
    font-size: 1.2em;
    font-style: italic;
    color: #ab7676;
}

</style>
</head>
<body>
    <div class="cover">
        <img src="nothing.jpg" class="bg-img" alt="Background">
        <div class="content">
            <h1 class="title">The Art of Django</h1>
            <h3 class="subtitle">Mastering Web Development</h3>
            <div class="author">by Jane Doe</div>
        </div>
    </div>
</body>
</html>
```
## OUTPUT
<img width="1920" height="1080" alt="Screenshot (45)" src="https://github.com/user-attachments/assets/bb15b91b-a32d-48d8-b122-4a5d1bd310a9" />

## Result
Thus the socket for HTTP for web page upload and download created and Executed
