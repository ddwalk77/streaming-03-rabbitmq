## Before You Begin

1. Fork this starter repo into your GitHub.
1. Clone your repo down to your machine.
1. In VS Code with Python extension, click on emit_message_v1.py to get VS Code in Python mode.
1. View / Command Palette - then Python: Select Interpreter
1. Select your conda environment. See the references below for more.
1. Use the terminal to install pika into your active environment. 

`conda install -c conda-forge pika`

## Read

1. Read the [RabbitMQ Tutorial - Hello, World!](https://www.rabbitmq.com/tutorials/tutorial-one-python.html)
1. Read the code and comments in this repo.

## Execute about,py

1. Run about.py.
1. Read about.txt. 
1. Verfiy you have exactly one active, one None env.

## Version 1 - Execute the Producer/Sender

1. Read v1_emit_message.py (and the tutorial)
1. Run the file. 

You'll need to fix an error in the program to get it to run.
Once it runs and finishes, we can reuse the terminal.

- Note: I did not have to fix an error. It appears to run without an issue, showing 'Hello World' as sent.

## Version 1 - Execute the Consumer/Listener

1. Read v1_listen_for_messages.py (and the tutorial)
1. Run the file.

You'll need to fix an error in the program to get it to run.
 - Note: Made correction and the program ran successfully

Once it runs successfully, will it terminate on its own? How do you know? 
 - Note: The program continues to run and listen until you abort in the terminal. You know this because the drive prompt never appears.
As long as the process is running, we cannot use this terminal for other commands. 

## Version 1 - Open a New Terminal / Emit More Messages

1. Open a new terminal window.
1. Use this new window to emit more messages
1. In v1_emit_message.py, modify the message. 
1. Execute the script. 
1. Watch what happens in the listening window.
1. Do this several times to emit at least 3 different messages.

## Version 1: Don't Repeat Yourself (DRY)

1. Did you notice you had to change the message in two places?
    1. You update the actual message sent. 
    1. You also update what is displayed to the user.
    - Note: I did not catch this at first and thought the first message was still being picked up. Once I read this, I updated both places.
1. Fix this by introducting a variable to hold the message. 
    1. Use your variable when sending. 
    1. Use the variable again when displaying to the user.
    - Note: Code was updated to add variable 'Message' and changed code to pick up the variable, allowing for update in one location

To send a new message, you'll only make one change.
Updating and improving code is called 'refactoring'. 
Use your skills to keep coding enjoyable. 

Notes:
- The queue name where both processes on both terminals are listening and emitting is called 'Hello'
- Emitting:
![Emitting terminal script](https://github.com/ddwalk77/streaming-03-rabbitmq/blob/main/Screenshot-2023-01-22-095930-emitting.png "Emitting terminal script")
- Listening:
![Listening terminal script](https://github.com/ddwalk77/streaming-03-rabbitmq/blob/main/Screenshot-2023-01-22-095844-listening.png "Listening terminal script")

## Version 2

Now look at the second version of each file.
These include more graceful error handling,
and a consistent, reusable approach to building code.

Each of the version 2 programs include an error as well. 

1. Find the error and fix it. 
1. Compare the structure of the version 2 files. 
1. Modify the docstrings on all your files.
1. Include your name and the date.
1. Imports always go at the top, just after the file docstring.
1. Imports should be one per line - why? This makes the code easier to read. It is clear what is being imported
1. Then, define your functions.
1. Functions are reuable logic blocks.
1. Everything the function needs comes in through the arguments.
1. A function may - or may not - return a value. 
1. When we open a connection, we should close the connection. 
1. Which of the 4 files will always close() the connection? All close the connection, but two require an interruption to abort, the listening files.
1. Search GitHub for if __name__ == "__main__":
1. How many hits did you get? 531,000
1. Learn and understand this common Python idiom.
    - https://realpython.com/if-name-main-python/#:~:text=Nesting%20code%20under%20if%20__,defined%2C%20but%20no%20code%20executes
    - This link has lots of information (honestly, more than I understand at this time)
    - Allows you to execute code when the file is run as a script, but not when imported as a module
    - Why use it? The primary reason to use the idiom is to collect user input, either through standard input or the command line; Also used for testing, but this should be in a separate file as best practice. Best at end of code, but there are other instances where this is not the case.

## Reference

- [RabbitMQ Tutorial - Hello, World!](https://www.rabbitmq.com/tutorials/tutorial-one-python.html)
- [Using Python environments in VS Code](https://code.visualstudio.com/docs/python/environments)

## Multiple Terminals

Notes:
- Emitting:
![Emitting terminal script](https://github.com/ddwalk77/streaming-03-rabbitmq/blob/main/Screenshot-2023-01-22-110134-v2-emitting.png "Emitting v2terminal script")
- Listening:
![Listening terminal script](https://github.com/ddwalk77/streaming-03-rabbitmq/blob/main/Screenshot-2023-01-22-110215-v2_listening.png "Listening v2terminal script")
- Multiples Screens:
![Listening terminal script](https://github.com/ddwalk77/streaming-03-rabbitmq/blob/main/multiple.png "Multiple Terminals")

## Reflection (additional information)

Think of examples where a message broker like RabbitMQ or a more advanced system like Kafka could be helpful.
- I read this and asked myself, 'What is a message broker?'. This article has LOTS of great information: https://www.g2.com/articles/message-broker. It helped me grasp what we are doing and why.

Explore Kafka (compare and contrast), and take a look at Apache Beam to see where steaming technologies are going.
- RabbitMQ - Best suited for environments with low throughput
- Amazon MQ - Part of AWS, cloud-based, reduces routine business tasks
- Apache Kafka - Originally tracked website activity which required large data storage for an extended period. Excels in this area, especially for real-time data storage. Described as “distributed event streaming platform.”
- Redis - Fast but has data loss
- If you search, there are many other platforms...

- Apache Beam - Unified batch and stream processing system. Basically multiple systems in one. Focused on real-time data.
