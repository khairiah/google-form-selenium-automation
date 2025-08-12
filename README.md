# Google Form Automation with Selenium

This project demonstrates how to automate form submissions on Google Forms using Selenium WebDriver with a label-driven XPath approach.

## Features

- Automates form submission for multiple records
- Handles both single-line input fields and multi-line textareas
- Order-independent field identification using label text
- Robust waiting mechanisms for reliable execution
- Handles form submission confirmation

## Approach

For this form, labels are unique and appear before their corresponding input field. Utilized label-based XPath with `following::` axis to find the correct input regardless of the form's order. Even if the questions are rearranged, it will still find the correct field as long as the label text remains the same.

It tackles both single input fields and multi-line text areas at one go. Explicit wait is utilized as a best practice. 

## When to consider using XPaths

- When there are no meaningful IDs or classes
- When the HTML is deeply nested or poorly structured (XPath is great for traversing through deep hierarchies)
- When you need to match elements based on position, relationship, or text

## Prerequisites

- Python 3.x
- Selenium WebDriver
- ChromeDriver (matching your Chrome browser version)

## Installation

1. Clone this repository
2. Install required packages:
   ```bash
   pip install selenium
3. Download ChromeDriver and ensure it's in your PATH

## Usage

1. Update the labels list with your form's field labels
2. Update the classList with your form data (each sub-list represents one form submission)
3. Run the script: ```python label_driven_xpath.py```


## Code Structure

- get_field_by_label(): Finds input fields by their label text using XPath

- main(): Handles the form submission process including:
  - Navigation to the form
  - Field population
  - Form submission
  - Success verification

## Best Practices Implemented

- Explicit waits instead of static sleeps
- Label-based element location (more maintainable than positional selectors)
- Clean resource management (browser quits properly)
- Flexible field handling (works with both inputs and textareas)

## Limitations

- Requires consistent label text
- Form structure must have labels preceding inputs
- Google Forms structure changes may require XPath adjustments (rare)

## Future Improvements
- Add error handling for failed submissions
- Implement retry mechanism for flaky connections
- Add support for other form elements (radio buttons, checkboxes)
- Make the script configurable via external files
