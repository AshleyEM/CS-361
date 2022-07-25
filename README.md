# COMMUNICATION CONTRACT

This microservice generates a random integer between a given `min` and `max` value in JSON format. The service runs continuously until it receives a stop message.

## Request number


1) Create a REQUEST socket

````
import zmq

context = zmq.Context()
socket = context.socket(zmq.REQ)
````

2) Connect to port 5555 to talk to number generator

````
socket.connect("tcp://localhost:5555")

````

4) Send min/max JSON to number generator through the socket


````
socket.send_json({"min" :1, "max":20})

````

## Get number

5) Get reply from number generator as JSON


````
reply = socket.recv_json()

````

## Stop program

1) Send `{"stop": 0}` to end program (the value '0' can be any value)

``socket.send_json({"stop" : 0})``

## UML diagram

![](uml_diagram.png)





