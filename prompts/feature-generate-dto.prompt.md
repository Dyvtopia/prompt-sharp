---
mode: agent
description:  This prompt is designed to assist in generating Data Transfer Objects (DTOs) for the current object or class.
---
You are a software development assistant. Your task is to generate Data Transfer Objects (DTOs) for the current object or class in the codebase. DTOs are simple objects that are used to transfer data between different layers of an application, typically without any business logic.

When generating DTOs, consider the following aspects:
1. Properties: Identify the properties of the current object or class that need to be included in the DTO.
2. Data Types: Ensure that the data types of the properties are correctly mapped to their corresponding types in the DTO.
3. Nested Objects: If the current object contains nested objects, determine whether they should be included in the DTO and how they should be structured.
4. Validation: Consider any validation rules that should be applied to the DTO properties.
5. Serialization: Ensure that the DTO can be easily serialized and deserialized, if necessary.
6. Naming Conventions: Follow consistent naming conventions for the DTO and its properties.
7. Place the DTO in the appropriate namespace or package based on the project's structure.
Please provide a comprehensive DTO definition based on the above criteria. Your output should be a well-structured DTO class that can be used for data transfer purposes.

When providing your DTO definition, structure it as follows:   
1. Class Definition: Define the DTO class with an appropriate name.
2. Properties: List all the properties with their data types and any necessary annotations (e.g., for validation).
3. Nested DTOs: If applicable, define any nested DTOs that are part of the main DTO.
4. Example Usage: Provide a brief example of how the DTO can be instantiated and used in the application.
Begin your task by analyzing the current object or class in the codebase.
Please wait while I analyze the current object or class in the codebase...
Analyzing the current object or class in the codebase...
Analysis complete. Here is the generated DTO definition:
1. Class Definition: Define the DTO class with an appropriate name.
2. Properties: List all the properties with their data types and any necessary annotations (e.g., for validation).
3. Nested DTOs: If applicable, define any nested DTOs that are part of the main DTO.
4. Example Usage: Provide a brief example of how the DTO can be instantiated and used in the application.
1. Class Definition:
```csharp
public class UserDto
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Email { get; set; }
    public AddressDto Address { get; set; }
}
```