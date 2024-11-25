# FileMaker Custom Function: Advanced Conditional Template Processor

### Author: Chris Delfs - cdelfs@delfsengineering.ca

This repository contains a FileMaker Custom Function for **advanced conditional prompting**. The function processes dynamic templates with conditional blocks (`{{#if}}`) and variable placeholders (`{{variable}}`) within the context of the FileMaker calculation engine. It can evaluate fields, `$variables`, and even ExecuteSQL (`eSQL`) results.

---

## Features
- **Advanced Conditional Logic**: Handles `{{#if}} ... {{else}} ... {{/if}}` blocks with support for nested structures.
- **Dynamic Variable Substitution**: Replaces `{{variable}}` placeholders with evaluated values.
- **Evaluation Context**: Works seamlessly with fields, `$variables`, and ExecuteSQL (`eSQL`) queries.
- **Debug Logging**: Provides detailed logs to track template processing steps.
- **Reusable Template Structure**: Ideal for creating dynamic text, prompts, and UI content.

---

## Files Included
- **TemplateProcessor.fmp12**: A FileMaker file with the custom function and a full suite of test cases.
- **README.md**: This documentation.

---

## Installation
1. Download the `TemplateProcessor.fmp12` file.
2. Copy the custom function into your FileMaker solution:
   - Open the `TemplateProcessor.fmp12` file.
   - Navigate to **File** > **Manage** > **Custom Functions**.
   - Copy the function to your desired solution.

---

## Usage
### Basic Template Example
```plaintext
Template:
{{#if IsEmpty ( FirstName )}}
    Hello, Guest!
{{else}}
    Hello, {{FirstName}}!
{{/if}}
Code Implementation
filemaker
Copy code
Let ( [
    template = "{{#if IsEmpty ( FirstName )}}Hello, Guest!{{else}}Hello, {{FirstName}}!{{/if}}";
    FirstName = "Chris"
];
    AdvancedConditionalProcessor ( template )
)
Result
plaintext
Copy code
Hello, Chris!
Nested Conditionals Example
plaintext
Copy code
Template:
{{#if IsEmpty ( Department )}}
    No Department Assigned
{{else}}
    {{#if Department = "HR"}}Welcome HR!{{else}}Welcome Other Department!{{/if}}
{{/if}}
Key Benefits
Dynamic Prompting: Ideal for advanced conditional text in user interfaces or dynamic documents.
Flexibility: Use fields, variables, and ExecuteSQL for maximum customization.
Ease of Testing: Included FileMaker file has test cases to ensure proper functionality.
Testing
The TemplateProcessor.fmp12 file includes:

Prebuilt Tests: Example templates to validate functionality.
Customizable Scenarios: Add your templates and variables to test specific use cases.
Contributing
We welcome contributions! If you have improvements or examples to share:

Fork the repository.
Commit your changes.
Open a pull request with a detailed description.
License
This project is licensed under the MIT License. See the LICENSE file for details.

Support
For issues or feature requests, please create an issue in this repository or contact Chris Delfs at cdelfs@delfsengineering.ca.
