import socket

def Main():
        host = "127.0.0.1" #set host name for client
        port = 5000 #set port for server and client to connect to

        s = socket.socket()#(socket.AF_INET, socket.SOCK_STREAM) #create a new SERVER socket object
        s.bind((host, port)) #Bind socket to host and port using tuple

        s.listen(1) #have socket listen on 1 channel
        c, addr = s.accept() #have socket accept connection from client
        print ("Incoming Connection: " + str(addr))
        while True:
                data = c.recv(2048) #receive 2048 bytes of data
                if not data:
                        break
                print ("Data sent from connected user: " + str(data))
                if 'SECRET' in data: # if the secret word SECRET is in data,
                                     # will strip down str and print all numbers
                                     # within data and count of them
                    digits = ''.join(c for c in data if c.isdigit())
                    digLen = str(len(digits))
                    print("Digits: " + digits, "count: " + digLen)
                    print ("Sending: " + "Digits: " + digits, "Count: " + digLen)
                    c.send("Digits:" + digits + " " + "Count:" + digLen) #send back modified data to client
                else: # if secret word SECRET is not present in data,
                      # send back same str but all caps
                    print("Sending: " + str(data).upper())
                    data = str(data).upper()
                    c.send(data)
        print("Connection closing...")
        c.close() #close the connection between client and server

if __name__ == '__main__':
        Main()
