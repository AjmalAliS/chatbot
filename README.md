# chatbot
## AIM
To develop a simple chatbot using Python that can interact with users through text-based conversation.


## SOFTWARE USED
Python 3.12.1

## ALGORITHM
1. Start the program.

2. Initialize a knowledge base to store predefined keywords and responses in a Python dictionary.

3. Take user input from the terminal.

4. Convert input to lowercase to make matching easier.

5. Search for keywords in the user’s message that match entries in the knowledge base.

6. If a match is found, display a random response from the related list.

7. If no match is found, return a default message such as “I’m not sure about that. Please rephrase your question.”

8. Repeat until the user types 'exit' or 'quit'.

9. End the program.

## Program
```
import random
import datetime
import re

class ChatBot:
    def __init__(self):
        self.responses = {
            'greeting': [
                "Hello! How can I assist you?",
                "Hi there! What’s up?",
                "Hey! How can I help?"
            ],
            'goodbye': [
                "Goodbye! Have a nice day!",
                "See you soon!",
                "Take care!"
            ],
            'thanks': [
                "You're welcome!",
                "Anytime!",
                "Glad to help!"
            ],
            'time': [
                "The current time is: {time}",
                "Right now it's {time}",
                "{time}"
            ],
            'default': [
                "I didn't quite get that.",
                "Can you rephrase it?",
                "Interesting... tell me more!"
            ]
        }

        self.patterns = {
            'greeting': r'\b(hello|hi|hey|sup|yo)\b',
            'goodbye': r'\b(bye|goodbye|see you|later)\b',
            'thanks': r'\b(thanks|thank you)\b',
            'time': r'\b(time|current time|what time)\b'
        }

    def get_response(self, message):
        message = message.lower().strip()

        for intent, pattern in self.patterns.items():
            if re.search(pattern, message):
                if intent == "time":
                    now = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
                    return random.choice(self.responses[intent]).format(time=now)
                return random.choice(self.responses[intent])

        return random.choice(self.responses['default'])


bot = ChatBot()

print("\n============================")
print("🤖 INTERACTIVE CHATBOT ACTIVE")
print("============================")
print("Type 'bye' to exit.\n")

while True:
    user = input("You: ")

    if user.lower() in ["bye", "exit", "quit"]:
        print("Bot:", random.choice(bot.responses["goodbye"]))
        break

    reply = bot.get_response(user)
    print("Bot:", reply)
```

## OUTPUT :

## RESULT
Thus the chatbot is created and executed successfully.
