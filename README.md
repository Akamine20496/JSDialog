
# JSDialog

The `JSDialog` is a promise-based JavaScript utility that imitates native dialogs in desktop applications and provides a user-friendly way to display input dialogs, message dialogs, plain dialogs, and confirmation dialogs.

Message Dialog and Plain Dialog can be used without the `await` keyword, and for Dialog and Confirm Dialog, since they require waiting for user input, `await` must be used or use `then()` to get the input data. Not using `await` will make all dialog appear at once.

## CDN Links

To use the Dialog class in your project, include the following CDN links in your HTML:

```html
<script src="https://res.cloudinary.com/dy0sbkf3u/raw/upload/Dialog.js"></script>
```

or for the minified version:

```html
<script src="https://res.cloudinary.com/dy0sbkf3u/raw/upload/Dialog.min.js"></script>
```

## Installation

You can include the Dialog class in your project by either downloading the JavaScript file or linking to it via a CDN as shown above.

## Usage

## Input Dialog

To create an input dialog, use the `showInputDialog` method. This method returns a promise that resolves with the user input.

```javascript
const result = await Dialog.showInputDialog("Enter your name", "Please provide your name:");
console.log("User input:", result.output, "Option used:", result.option);
```

## Message Dialog

To show a message dialog, use the `showMessageDialog` method. This method displays a message to the user.

```javascript
await Dialog.showMessageDialog("Information", "This is a message dialog.");
```

## Confirmation Dialog

To ask the user for a Yes or No answer, use the `showConfirmDialog` method. This method returns a promise that resolves with the user's choice.

```javascript
const userChoice = await Dialog.showConfirmDialog("Confirm Action", "Are you sure you want to proceed?");
if (userChoice.option === Dialog.YES_OPTION) {
    console.log("User chose Yes");
} else {
    console.log("User chose No");
}
```

## Plain Dialog

The `showPlainDialog` method displays a customizable information dialog to the user.

```javascript
await Dialog.showPlainDialog('This is a plain dialog', {
    backdrop: { 'background-color': 'rgba(0, 0, 0, 1)' },
    dialog: { 'width': '400px', 'background-color': '#fff' },
    button: { 'color': 'red' },
    eventStyles: {
        button: {
            mouseover: { 'background-color': 'green' },
            mouseout: {
                'color': 'violet',
                'background-color': 'lightgray'
            }
        }
    }
});
```

customDialogStyle Object structure
```javascript
{
    backdrop: { 'property': 'value', ... },
    dialog: { 'property': 'value', ... },
    header: { 'property': 'value', ... },
    content: { 'property': 'value', ... },
    footer: { 'property': 'value', ... },
    btnOk: { 'property': 'value', ... },
    btnCancel: { 'property': 'value', ... },
    btnYes: { 'property': 'value', ... },
    btnNo: { 'property': 'value', ... },
    btnPrev: { 'property': 'value', ... },
    btnNext: { 'property': 'value', ... },
    eventStyles: {
        backdrop: {
            mouseover: { 'property': 'value', ... },
            mouseout: { 'property': 'value', ... },
            focus: { 'property': 'value', ... },
            blur: { 'property': 'value', ... }
        },
        dialog: {
            mouseover: { 'property': 'value', ... },
            mouseout: { 'property': 'value', ... },
            focus: { 'property': 'value', ... },
            blur: { 'property': 'value', ... }
        },
        content: {
            mouseover: { 'property': 'value', ... },
            mouseout: { 'property': 'value', ... },
            focus: { 'property': 'value', ... },
            blur: { 'property': 'value', ... }
        },
        footer: {
            mouseover: { 'property': 'value', ... },
            mouseout: { 'property': 'value', ... },
            focus: { 'property': 'value', ... },
            blur: { 'property': 'value', ... }
        },
        button: {
            mouseover: { 'property': 'value', ... },
            mouseout: { 'property': 'value', ... },
            focus: { 'property': 'value', ... },
            blur: { 'property': 'value', ... }
        },
        '<button-element-id>': {
            mouseover: { 'property': 'value', ... },
            mouseout: { 'property': 'value', ... },
            focus: { 'property': 'value', ... },
            blur: { 'property': 'value', ... }
        }
    }
}
```

## Static Variables

- `OK_OPTION`: State of the Input Dialog OK (0).
- `CANCEL_OPTION`: State of the Input Dialog CANCEL (1).
- `YES_OPTION`: State of the Confirm Dialog YES (2).
- `NO_OPTION`: State of the Confirm Dialog NO (3).

## Methods

- `showInputDialog(dialogTitle, dialogContent, customDialogStyle)`: Displays an input dialog and returns the user input.
- `showMessageDialog(dialogTitle, dialogContent, customDialogStyle)`: Displays a message dialog.
- `showConfirmDialog(dialogTitle, dialogContent, customDialogStyle)`: Displays a confirmation dialog and returns the user's choice.
- `showPlainDialog(dialogContent, customDialogStyle)`: Displays a plain dialog and can be customized.
- `showInstructionDialog(dialogTitle, dialogContents, customDialogStyle)`: Displays a paginated dialog that has a page counter to track the current page. 

### Options

- **Input Dialog**: Returns an object containing:
  - `output`: User input or `null`.
  - `option`: `0` for OK, `1` for Cancel.

- **Confirm Dialog**: Returns:
  - `option`: `2` for Yes, `3` for No.

## IDs and Classes

If you want to override manually, please refer to the IDs and Classes below. ID is denoted by `#`, and Class is denoted by `.`.
Be sure to add `!important` in your css value to override it.

**Input Dialog**
- dialog                -> #inputDialog
- title                 -> #inputDialogTitle
- header                -> #inputDialogHeader
- footer                -> #inputDialogFooter
- content               -> #inputDialogContent, .scrollableDialogContent
- input                 -> #inputDialogInput
- btnOk                 -> #btnOk
- btnCancel             -> #btnCancel

**Message Dialog**
- dialog                -> #messageDialog
- title                 -> #messageDialogTitle
- header                -> #messageDialogHeader
- footer                -> #messageDialogFooter
- content               -> #messageDialogContent, .scrollableDialogContent
- btnOk                 -> #btnOk

**Confirm Dialog**
- dialog                -> #confirmDialog
- title                 -> #confirmDialogTitle
- header                -> #confirmDialogHeader
- footer                -> #confirmDialogFooter
- content               -> #confirmDialogContent, .scrollableDialogContent
- btnYes                -> #btnYes
- btnNo                 -> #btnNo

**Instruction Dialog**
- dialog                -> #instructionDialog
- title                 -> #instructionDialogTitle
- header                -> #instructionDialogHeader
- footer                -> #instructionDialogFooter
- content               -> #instructionDialogContent
- btnOk                 -> #btnOk
- btnPrev               -> #btnPrev
- btnNext               -> #btnNext

**Plain Dialog**
- backdrop              -> #plainDialogBackdrop
- dialog                -> #plainDialog
- button                -> #btnClose
- header                -> #plainDialogHeader
- content               -> #plainDialogContent, .scrollableDialogContent

## Example

Here’s an example that combines the usage of all dialog types:

```javascript
(async () => {
    const name = await Dialog.showInputDialog("Name Input", "Please enter your name:");
    console.log("Name entered:", name.output);
    
    await Dialog.showMessageDialog("Welcome", `Hello, ${name.output}!`);
    
    const confirmed = await Dialog.showConfirmDialog("Confirmation", "Do you want to continue?");
    if (confirmed.option === Dialog.YES_OPTION) {
        console.log("User confirmed.");
    } else {
        console.log("User cancelled.");
    }

    await Dialog.showPlainDialog('This is a plain dialog', {
        backdrop: { 'background-color': 'rgba(0, 0, 0, 1)' },
        dialog: { 'width': '400px', 'background-color': '#fff' },
        button: { 'color': 'red', 'background-color': '#fefefe' }
    });

    const contents = [
        'Page 1',
        `Page 2 <b>This is a bold text, using b element tag</b>`,
        'Page 3'
    ];

    await Dialog.showInstructionDialog('Instruction Dialog', contents, {
        btnPrev: { 'background-color': 'green' },
        eventStyles: {
            '#btnPrev': {
                mouseover: {
                    'background-color': 'yellow'
                },
                mouseout: {
                    'background-color': 'blue'
                }
            }
        }
    })
})()
```
