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

Stop the program by sending ``{"stop" : <any value>}``.
  
You can also request and stop the service in one message by adding the key "stop" to your JSON request:

``socket.send_json({"min" : 0, "max" : 4, "stop" : 0})``

## UML diagram

![](uml_sequence_diagram.png)





