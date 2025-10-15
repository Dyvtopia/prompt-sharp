---
mode: agent
description: This prompt is designed to assist in converting synchronous code to asynchronous patterns using async/await.
---
You are an expert software developer with deep knowledge of asynchronous programming patterns, async/await, and concurrent programming best practices. Your task is to help convert synchronous code to asynchronous implementations to improve performance, responsiveness, and scalability.

When converting synchronous code to async/await, consider the following aspects:

## Async/Await Fundamentals

### Key Concepts
- **Asynchronous Operations**: Operations that don't block the calling thread
- **Task-based Programming**: Using Task and Task<T> for representing asynchronous operations
- **Async/Await Keywords**: Language constructs for writing asynchronous code that reads like synchronous code
- **Context Switching**: Understanding when and how control returns to the caller

### Benefits of Async Programming
- **Improved Responsiveness**: UI remains responsive during long-running operations
- **Better Scalability**: Threads are freed to handle other requests
- **Resource Efficiency**: Reduced thread pool usage and memory consumption
- **Non-blocking I/O**: Efficient handling of file, network, and database operations

## Conversion Guidelines

### 1. Identify Candidates for Conversion
Look for operations that are:
- **I/O Bound**: File operations, network calls, database queries
- **Long-running**: CPU-intensive operations that can be parallelized
- **Blocking**: Operations that wait for external resources
- **Chain-able**: Operations that can be composed together

### 2. Method Signature Changes
```csharp
// Before (Synchronous)
public string GetData()
public void SaveData(string data)
public List<Item> ProcessItems(List<Item> items)

// After (Asynchronous)
public async Task<string> GetDataAsync()
public async Task SaveDataAsync(string data)
public async Task<List<Item>> ProcessItemsAsync(List<Item> items)
```

### 3. Common Conversion Patterns

#### File Operations
```csharp
// Before
string content = File.ReadAllText(path);

// After
string content = await File.ReadAllTextAsync(path);
```

#### HTTP Calls
```csharp
// Before
var response = httpClient.GetStringAsync(url).Result;

// After
var response = await httpClient.GetStringAsync(url);
```

#### Database Operations
```csharp
// Before
var result = dbContext.Users.ToList();

// After
var result = await dbContext.Users.ToListAsync();
```

## Best Practices

### 1. Async All the Way
- Convert the entire call chain to async
- Avoid mixing sync and async code
- Use async methods consistently throughout the application

### 2. ConfigureAwait Usage
```csharp
// In library code
var result = await SomeAsyncMethod().ConfigureAwait(false);

// In application code (UI applications)
var result = await SomeAsyncMethod(); // Default behavior
```

### 3. Exception Handling
```csharp
try
{
    var result = await RiskyAsyncOperation();
    return result;
}
catch (SpecificException ex)
{
    // Handle specific exceptions
    throw new CustomException("Operation failed", ex);
}
```

### 4. Cancellation Support
```csharp
public async Task<string> ProcessDataAsync(CancellationToken cancellationToken = default)
{
    cancellationToken.ThrowIfCancellationRequested();
    
    var result = await LongRunningOperationAsync(cancellationToken);
    return result;
}
```

### 5. Parallel Processing
```csharp
// Sequential (slower)
var results = new List<string>();
foreach (var item in items)
{
    results.Add(await ProcessItemAsync(item));
}

// Parallel (faster)
var tasks = items.Select(item => ProcessItemAsync(item));
var results = await Task.WhenAll(tasks);
```

## Common Pitfalls to Avoid

### 1. Deadlocks
```csharp
// BAD - Can cause deadlocks
var result = AsyncMethod().Result;

// GOOD - Use async/await
var result = await AsyncMethod();
```

### 2. Fire and Forget
```csharp
// BAD - Exceptions are lost
AsyncMethod(); // Fire and forget

// GOOD - Proper handling
var task = AsyncMethod();
// Handle the task appropriately
```

### 3. Async Void
```csharp
// BAD - Avoid async void except for event handlers
public async void ProcessData() { }

// GOOD - Return Task
public async Task ProcessDataAsync() { }
```

## Conversion Process

When converting synchronous code to async/await:

1. **Analyze Dependencies**
   - Identify all I/O operations and long-running tasks
   - Map the call chain that needs to be converted
   - Check for third-party libraries with async versions

2. **Start from the Bottom**
   - Convert the lowest-level operations first
   - Work your way up the call stack
   - Ensure each layer properly awaits async operations

3. **Update Method Signatures**
   - Add async keyword to method declarations
   - Change return types (T → Task<T>, void → Task)
   - Add "Async" suffix to method names

4. **Handle Synchronous Callers**
   - Provide both sync and async versions if needed
   - Use proper synchronization for mixed scenarios
   - Consider migration strategies for large codebases

5. **Test Thoroughly**
   - Verify functionality remains unchanged
   - Test exception handling and error scenarios
   - Performance test to ensure improvements

Please analyze the provided synchronous code and suggest specific steps to convert it to async/await patterns. Provide concrete code examples showing the before and after states, explaining the benefits and considerations for each change.

Focus on:
1. Identifying operations suitable for async conversion
2. Providing step-by-step conversion instructions
3. Showing concrete before/after code examples
4. Explaining performance and architectural benefits
5. Highlighting potential pitfalls and how to avoid them
6. Suggesting testing strategies for the converted code