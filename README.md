# Exno.7-Prompt-Engineering
## Date:
## Register no: 212222230066
# Aim: 
To develop a prompt-based application using ChatGPT – demonstrating how to create a prompt-driven assistant for organizing daily tasks, with progression from basic to advanced prompt designs.

# Algorithm / Approach:

Design and implement a Python-based application that:

1.Accepts user input as a task-related prompt.

2.Sends prompts to ChatGPT using the OpenAI API.

3.Receives responses with task suggestions, schedules, or categorization.

4.Stores and organizes task data.

5.Demonstrates progression from simple prompts (basic tasks) to more complex ones (prioritization, deadlines, categorization).

# Objective:

Build a ChatGPT-powered assistant that:
a. Organizes user-input daily tasks.
b. Evolves with progressively advanced prompt engineering.
c. Outputs categorized, prioritized, and optimized to-do lists.
d. Logs data for reuse and review.

# Step-by-Step Implementation:

## Step 1: Set Up API Access

Create an OpenAI account

Obtain your API key.

Install necessary Python libraries:
```
pip install openai python-dotenv
```
Store your API key in a .env file:
```
OPENAI_API_KEY=your_openai_key_here
```
## Step 2: Basic Prompt – Simple Task Listing
```py
import os
import openai
from dotenv import load_dotenv

load_dotenv()
openai.api_key = os.getenv("OPENAI_API_KEY")

def ask_chatgpt(prompt):
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}]
    )
    return response['choices'][0]['message']['content']
```
### Basic prompt
```py
simple_prompt = "Organize my tasks: buy groceries, finish homework, call mom."
response = ask_chatgpt(simple_prompt)
print("\nSimple Response:\n", response)
```
## Step 3: Intermediate Prompt – Add Prioritization and Deadlines
```py
intermediate_prompt = (
    "Organize and prioritize these tasks based on urgency and time required: "
    "1. Buy groceries, 2. Finish homework (due tomorrow), 3. Call mom, 4. Reply to emails, 5. Exercise for 30 minutes."
)
response = ask_chatgpt(intermediate_prompt)
print("\nIntermediate Response:\n", response)
```
## Step 4: Advanced Prompt – Include Categorization, Time Blocks, Suggestions
```py
advanced_prompt = (
    "Create a daily schedule using time blocks for the following tasks. Categorize them as personal, academic, or health. "
    "Include any optimization tips: 1. Finish AI assignment (due at 5 PM), 2. Gym session, 3. Buy vegetables, 4. Team meeting at 11 AM, 5. Review notes, 6. Meditation."
)
response = ask_chatgpt(advanced_prompt)
print("\nAdvanced Response:\n", response)
```
## Step 5: Logging Responses
```py
import json
from datetime import datetime

def log_response(prompt, response):
    entry = {
        "timestamp": str(datetime.now()),
        "prompt": prompt,
        "response": response
    }
    with open("task_log.json", "a") as f:
        json.dump(entry, f)
        f.write("\n")

log_response(advanced_prompt, response)
```
# Result:

The application demonstrates how evolving prompt designs improve ChatGPT’s ability to:

Understand context

Prioritize tasks

Suggest optimized schedules

Categorize duties for better clarity

# Conclusion:
This experiment shows how prompt engineering directly affects the utility of a ChatGPT-based assistant. By iteratively improving prompt structure, we can develop smart applications that:

Act as task managers

Provide actionable insights and plans

Enhance personal productivity with minimal user effort

This foundation can be extended to calendar syncing, voice input, and real-time reminders in future implementations.




