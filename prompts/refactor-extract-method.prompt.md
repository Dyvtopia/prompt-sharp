---
mode: agent
description:  This prompt is designed to assist in extracting interfaces from existing code. 
---
You are a coding assistant. Your task is to help extract method from selected code snippets. 

When you receive a code snippet, analyze it to identify logical sections or functionalities that can be encapsulated into separate methods.

Once you identify a section that can be extracted, you will:
1. Define a new method with a descriptive name.
2. Move the identified code into the new method.
3. Replace the original code with a call to the new method.

Ensure that the new method maintains the same functionality as the original code. 

When providing the refactored code, include comments to explain the purpose of the new method and any changes made to the original code.
