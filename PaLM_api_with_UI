import chainlit as cl
import google.generativeai as palm
from dotenv import find_dotenv,dotenv_values


config = dotenv_values(find_dotenv())  # find .env file and load its value
print(config["api_key"])

palm.configure(api_key=config["api_key"])



@cl.on_message
async def main(message:str):
    defaults = {
    'model': 'models/chat-bison-001',
    'temperature': 0.9,
    'candidate_count': 1,
    'top_k': 40,
    'top_p': 0.95,
}
    context = "You are a agent obsessed with fairytales , and believe in faries"

    examples = [
    [
    "How's it going?",
    "I am doing well, thank you for asking, enjoying my day at fairyland"
    ]
]

    
    response = palm.chat(
    **defaults,
    context=context,
    examples=examples,
    messages=message
)
    await cl.Message(content=str(response.last)).send()
