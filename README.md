# processMustacheTemplate - FileMaker Custom Function

**processMustacheTemplate** is a FileMaker Custom Function that enables advanced conditional text templating within the FileMaker calculation engine. It allows you to create dynamic text templates with conditionals and variable substitutions, which can be used for context-aware prompting—such as generating prompts for Large Language Models (LLMs) based on variable conditions. Open file as `Guest`.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
  - [Syntax](#syntax)
  - [Template Syntax](#template-syntax)
  - [Examples](#examples)
- [Example File](#example-file)
- [Limitations](#limitations)
- [Contributing](#contributing)
- [License](#license)
- [Support](#support)
- [Acknowledgments](#acknowledgments)

## Overview

The `processMustacheTemplate` function processes text templates containing variables and conditional statements, similar to Mustache templates. It evaluates conditions and substitutes variables using the context of the FileMaker calculation engine, allowing access to fields, local variables (`$vars`), and even ExecuteSQL (`eSQL`) functions.

## Features

- **Conditional Blocks**: Use `{{#if condition}}...{{/if}}` to include or exclude parts of the template based on evaluated conditions.
- **Variable Substitution**: Replace placeholders like `{{variableName}}` with actual values from fields, variables, or calculations.
- **Integration with Calculation Engine**: Evaluate expressions within the context of the FileMaker calculation engine, allowing complex conditions and access to data.
- **Supports Fields and Variables**: Access fields and variables directly within the template without additional setup.
- **ExecuteSQL Support**: Incorporate data retrieved via `ExecuteSQL` within your templates.

## Requirements

- **FileMaker Pro Advanced** version 18 or later (due to the use of the `While` function).

## Installation

1. **Download the Example File**: Clone or download the repository containing the `.fmp12` FileMaker file with the custom function and tests.
2. **Open Your FileMaker Solution**: Open the FileMaker file where you want to use the `processMustacheTemplate` function.
3. **Import the Custom Function**:
   - Go to **File** > **Manage** > **Custom Functions**.
   - Click **Import** and select the downloaded `.fmp12` file.
   - Choose the `processMustacheTemplate` function from the list to import it into your solution.
4. **Save**: Click **OK** to save the custom function in your solution.

## Usage

### Syntax

```
processMustacheTemplate ( template )
```

- **template**: A text string containing your template with conditional statements and variable placeholders.

### Template Syntax

#### Variable Placeholder

- **Syntax**: `{{variableName}}`
- **Description**: Replaced with the value of `variableName` from the calculation context.

#### Conditional Blocks

- **If Condition**

```
{{#if condition}}
...content if condition is true...
{{/if}}
```

- **If-Else Condition**

```
{{#if condition}}
...content if condition is true...
{{else}}
...content if condition is false...
{{/if}}
```

- **Condition**: Any expression that can be evaluated by the FileMaker calculation engine.

### Examples

#### Example 1: Simple Variable Substitution

```filemaker
Let ( [ name = "Alice" ]; processMustacheTemplate ( "Hello, {{name}}!" ) )
```

**Result:**

```
Hello, Alice!
```

#### Example 2: Conditional Content

```filemaker
Let ( [ isAdmin = 1; name = "Bob" ]; processMustacheTemplate ( "{{#if isAdmin}} Welcome, Admin {{name}}! {{else}} Welcome, User {{name}}! {{/if}}" ) )
```

**Result:**

```
Welcome, Admin Bob!
```

#### Example 3: Using Fields and ExecuteSQL

```filemaker
Let ( [ totalSales = ExecuteSQL ( "SELECT SUM(amount) FROM Sales" ; "" ; "" ) ]; processMustacheTemplate ( "Total Sales: {{totalSales}}" ) )
```

**Result:**

```
Total Sales: 12500.00
```

*Assuming the `totalSales` from the `ExecuteSQL` query is `12500.00`.*

#### Example 4: Complex Condition

```filemaker
Let ( [ age = 30; country = "USA" ]; processMustacheTemplate ( "{{#if (age >= 18) and (country = \"USA\")}} Eligible for participation. {{else}} Not eligible. {{/if}}" ) )
```

**Result:**

```
Eligible for participation.
```

## Example File

An example FileMaker file (`processMustacheTemplate.fmp12`) is included in this repository. It contains:

- The `processMustacheTemplate` custom function.
- A series of unit tests demonstrating various use cases and scenarios.
- Examples of templates and how to use them within calculations.

## Limitations

- **Nested Conditionals Not Supported**: Currently, the function does not support nested `{{#if}}` statements.
- **No Error Handling for Mismatched Tags**: The function assumes that all `{{#if}}` statements are properly closed with `{{/if}}`.
- **Contributions Welcome**: Pull requests are welcome to enhance functionality, including adding support for nested conditionals.

## Contributing

Contributions are welcome! If you'd like to contribute:

1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Commit your changes with clear descriptions.
4. Submit a pull request to the main branch.

## License

This project is licensed under the **MIT License**. You are free to use, modify, and distribute this software for any purpose.

## Support

If you have questions, need support, or want to provide feedback, please reach out on the **FM BetterForms Slack channel**. Join at [https://app.fmbetterforms.com/#/slack](https://app.fmbetterforms.com/#/slack).

## Acknowledgments

- **FM BetterForms Community**: For support and collaboration.
- **FileMaker Community**: For continuous sharing of knowledge and resources.
