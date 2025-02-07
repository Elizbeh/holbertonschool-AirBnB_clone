##

<img src=":image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAkGBwgHBgkIBwgKCgkLDRYPDQwMDRsUFRAWIB0iIiAdHx8kKDQsJCYxJx8fLT0tMTU3Ojo6Iys/RD84QzQ5Ojf/2wBDAQoKCg0MDRoPDxo3JR8lNzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzf/wAARCAAbAEADASIAAhEBAxEB/8QAGwAAAgMBAQEAAAAAAAAAAAAABAUAAQYDAgf/xAArEAACAQMDAwMDBQEAAAAAAAABAgMABBEFEjETIVEUQWFxgbEGIiMkcpH/xAAXAQEBAQEAAAAAAAAAAAAAAAAAAgEE/8QAHREAAgIBBQAAAAAAAAAAAAAAAAECEQQDEjFxkf/aAAwDAQACEQMRAD8A+HUySxt02Q3DzLOyhmZQNkW7jd7+M/WuGmxI0zTTDMMC9Rx58L9zitdpSWkP6efUdSbMd6zdUdPeGOSF3EDIAIyPBPJ7ConPYrOjGx3ryaukldmJljeGV45Bh0JUj5qlR3DFFZgoycDOBRl7/ZtYrwd3H8U3+gOx+4/FE6Ds6d/1Swj9Od23nHvirOcUgE8AnFVWjtLS1gillikl9PcWjk7wCy4Izx9aGh0m1uAk8M8vpmRydyjcpX80AmAJ4GaqtDp1pbx7riCSX081tKDvUblwRnill5aQC0S7s5JGhL9NlkADK2M+3xQHq1ja402SC2AM3WDugOCy47Y84Of+0bAzRaRPpVzchZZmDxQl/wBqEHJ3EcZ8ce/akVSsaT5KhOULrr0ZJby2VpdesXYkiBUQkZZsggj4HfvQtrdyWyTpGFImQo24cD4oepWkjCHV54Yo4hFCyJG0eHUnIJBOe/xVnWLjcNkcMcYRkWNFwo3cnnml1SgD7XVZ7aGOJEiZUVlG9Schjk57/Fc7y/kuo0i6cUUSHIjiXAz5oSpQH//Z">

## Introduction

## Creation Of The Console
- The first step is in python. We will begin with the implementation of the parent class called BaseModel.
- This class do the initialization, serialization and deserialization of the future instances : Instance <-> Dictionary <-> JSON string <-> file
- During this project, we created some classes that inherit from BaseModel such as : User, State, City, Place, review, state, amenity...
- Create the first abstracted storage engine of the project: File storage.
- And to finish create the unittest to validate all the classes and storage processes

<img src="https://raw.githubusercontent.com/ChongLeangUENG/holbertonschool-AirBnB_clone/main/images/0.png">

## Definition
First lets have some few definitions to help understand the project :

- What is a Python package ?
A Python package is a folder containing modules and maybe other folders that themselves may contain more folders and modules. A package folder usually contains one file named init.py that basically tells Python: “Hey, this directory is a package!” The init file may be empty, or it may contain code to be executed upon package initialization

- Why use the command interpreter in Python ?
The Cmd instance or subclass instance is a line-oriented interpreter framework. There is no good reason to instantiate Cmd itself; rather, it’s useful as a superclass of an interpreter class you define yourself in order to inherit Cmd’s methods and encapsulate action methods.

- How to manage datetime ?
To manage datetime in python, you have to import the module named datetime. This module allow you to deal with the hours or the dates

- What is a UUID what can it be used for?
UUIDs are generally used for identifying information that needs to be unique within a system or a network.

- What is *args and how to use it ?
The special syntax *args in function definitions in python is used to pass a variable number of arguments to a function. But we won't use *args in this project.

- What is **kwargs and how to use it ?
Kwargs allow you to pass keyword arguments to a function. They are used when you are not sure of the number of keyword arguments that will be passed in the function. Kwargs can be used for unpacking dictionary key, value pairs. This is done using the double asterisk notation ( ** ).

- How to handle named arguments in a function ?
Keyword arguments (or named arguments) are values that, when passed into a function, are identifiable by specific parameter names. A keyword argument is preceded by a parameter and the assignment operator = . Keyword arguments can be likened to dictionaries in that they map a value to a keyword.

## Use the console
The (hbnb) Airbnb Clone can be run both in interactive and non-interactive mode. To run the console in non-interactive mode, you can use the following command :

'''sh
$ echo "help" | ./console.py
(hbnb)

Documented commands (type help <topic>):
========================================
EOF  help  quit
(hbnb) 
$
$ cat test_help
help
$
$ cat test_help | ./console.py
(hbnb)

Documented commands (type help <topic>):
========================================
EOF  help  quit
(hbnb) 
$
'''

You can use the interactive mode with the following command :

'''sh
$ ./console.py
(hbnb) help

Documented commands (type help <topic>):
========================================
EOF  help  quit

(hbnb) 
(hbnb) 
(hbnb) quit
$
'''

## Main Commands

| COMMAND after the (hbnb) | DESCRIPTION |
| ----------------------- | ------------ |
| quit |	To quit the console |
| EOF |	To quit the console by EOF |
| help + command | Display the help for the command ask |
| create + class | Creates an object and print the ID |
| show + class + id | To show the informations of the object |
| destroy + class + id | To remove an object |
| all + class | To show all the instances of a class
| update + class + id + attribute name + "attribute value" | To create or update the attribute of a class |
| count + class	To count | the number of instance by class |

## BaseModel
The BaseModel class is the parent of all the classes :

- The init method defines the common attributes for all the class that inrherite from that one. We call that the constructor method.

- The str method is the method that defines the good output format as a string.

- The save method is useful to updates the public instance attribute 'updated_at' with the current datetime.

- The to_dict method returns a dictionary containing all the keys and values of the instance.

## Other classes
All the classes listed bellow inherits from BaseModel :

| class | Attributes | Description |
| ----- | ---------- | ----------- |
| User | email + password + first_name + last_name | This class is about user information, it retrieve main information about the future user |
| State | name | This class retrieve information about for the future state of the future location |
| City | state_id + name | This class retrieve more precise information about the geographic position of future location |
| Place | city_id + user_id + name + description number_rooms + number_bathrooms + max_guest price_by_night + latitude + longitude + amenity_ids | This class retrieve all information about the future location, all important information like the number of room and the equipment inside the location |
| Review | place_id + user_id + text | This class retrieve a review of the future place with information of the user that post the review |
| Amenity | name | This class retrieve information about the future amenity |

## Filestorage
- This file is composed of methods that are used by the console :

- The all method display the dictionary view of objects.

- The new method sets a new instance with the class name and a new id for the object.

- The save method serialize the object in dictionary format to the JSON file.

- The reload method deserialize the JSON file to object. In other words, bring the data in the file.json and change it to object.

- The HBNBCommand class is created to implement the prompt. The option do at the beginning of the method define the action. So do_quit defined the command to quit the prompt, the EOF command does the same with the signal.

- The command do_create is to create a new instance and tell the user if there is a missing argument or if the class called doesn't exist. If the argument are passed on the good way, the instance is created and saved.

'''sh
Usage: create <class name> OR <class name>.create()
'''

The command do_show is to show a string representation of an instance. This mean that when you type : "show User id" on the good way it will display the information of this user. If a argument is missing it will display an error message.

'''sh
Usage: show <class name> <id> OR <class name>.show(<id>)
'''

The command do_destroy works on the same way as "show" but the objective is to remove an instance.

'''sh
Usage: destroy <class name> OR <class name>.destroy(<id>)
'''

The command do_all displays in the prompt the string representation of all the instance saved.

'''sh
Usage: all OR all <class name> OR <class name>.all()
'''

- The command do_update is useful to update an instance. If the instance already exist, it updates the instance and the datetime. If the instance doesn't exist, it creates it.

'''sh
Usage: update <class name> <id> <attribute name> "<attribute value>" 
Usage: <class name>.update(<id>, <attribute name>, <attribute value>)
'''

- The command do_count counts the number of instance for each class.

'''sh
Usage: count <class name> OR <class name>.count()
'''

- The method default is called when the command is not recognized. If the input line cannot be overrided, an error message is printed and returns.

'''sh
$ input
(hbnb) User.count()

$ method default switch by
(hbnb) count User
'''

## Python Unit Tests
We have done some tests for our classes and methods. Tests are made to make sure our code display the result and the outputs expected.

The command to display the results of the tests in interactive mode is :

'''sh
$ python3 -m unittest discover tests
'''

And the command in non-interactive mode is :

'''sh
echo "python3 -m unittest discover tests" | bash
'''
