# Design of a Standard Calculator

## AIM:

To design a web application for a standard calculator.

## DESIGN STEPS:

### Step 1:Clone the github repository and create Django admin interface.

### Step 2:Change settings.py file to allow request from all hosts.

### Step 3:Use CSS for creating attractive colors.

### Step 4:Write JavaScript program for implementing five different operations.

### Step 5:Validate the HTML and CSS code.

### Step 6:Publish the website in the given URL.

### Step 7: Validate the HTML and CSS code.

### Step 8: Publish the website in the given URL. PROGRAM :
<title>Calculator</title> <script src="script.js" defer></script>
AC DEL ÷ 1 2 3 * 4 5 6 + 7 8 9 - . 0 =
<script> class Calculator { constructor(previousOperandTextElement, currentOperandTextElement) { this.previousOperandTextElement = previousOperandTextElement this.currentOperandTextElement = currentOperandTextElement this.clear() } clear() { this.currentOperand = '' this.previousOperand = '' this.operation = undefined } delete() { this.currentOperand = this.currentOperand.toString().slice(0, -1) } appendNumber(number) { if (number === '.' && this.currentOperand.includes('.')) return this.currentOperand = this.currentOperand.toString() + number.toString() } chooseOperation(operation) { if (this.currentOperand === '') return if (this.previousOperand !== '') { this.compute() } this.operation = operation this.previousOperand = this.currentOperand this.currentOperand = '' } compute() { let computation const prev = parseFloat(this.previousOperand) const current = parseFloat(this.currentOperand) if (isNaN(prev) || isNaN(current)) return switch (this.operation) { case '+': computation = prev + current break case '-': computation = prev - current break case '*': computation = prev * current break case '÷': computation = prev / current break default: return } this.currentOperand = computation this.operation = undefined this.previousOperand = '' } getDisplayNumber(number) { const stringNumber = number.toString() const integerDigits = parseFloat(stringNumber.split('.')[0]) const decimalDigits = stringNumber.split('.')[1] let integerDisplay if (isNaN(integerDigits)) { integerDisplay = '' } else { integerDisplay = integerDigits.toLocaleString('en', { maximumFractionDigits: 0 }) } if (decimalDigits != null) { return `${integerDisplay}.${decimalDigits}` } else { return integerDisplay } } updateDisplay() { this.currentOperandTextElement.innerText = this.getDisplayNumber(this.currentOperand) if (this.operation != null) { this.previousOperandTextElement.innerText = `${this.getDisplayNumber(this.previousOperand)} ${this.operation}` } else { this.previousOperandTextElement.innerText = '' } } } const numberButtons = document.querySelectorAll('[data-number]') const operationButtons = document.querySelectorAll('[data-operation]') const equalsButton = document.querySelector('[data-equals]') const deleteButton = document.querySelector('[data-delete]') const allClearButton = document.querySelector('[data-all-clear]') const previousOperandTextElement = document.querySelector('[data-previous-operand]') const currentOperandTextElement = document.querySelector('[data-current-operand]') const calculator = new Calculator(previousOperandTextElement, currentOperandTextElement) numberButtons.forEach(button => { button.addEventListener('click', () => { calculator.appendNumber(button.innerText) calculator.updateDisplay() }) }) operationButtons.forEach(button => { button.addEventListener('click', () => { calculator.chooseOperation(button.innerText) calculator.updateDisplay() }) }) equalsButton.addEventListener('click', button => { calculator.compute() calculator.updateDisplay() }) allClearButton.addEventListener('click', button => { calculator.clear() calculator.updateDisplay() }) deleteButton.addEventListener('click', button => { calculator.delete() calculator.updateDisplay() }) </script> <style> *, *::before, *::after { box-sizing: border-box; font-family: Gotham Rounded, sans-serif; font-weight: normal; } body { padding: 0; margin: 0; background:(to right,lightsteelblue,lemonchiffon); } .calculator-grid { display: grid; justify-content: center; align-content: center; min-height: 100vh; grid-template-columns: repeat(4, 100px); grid-template-rows: minmax(120px, auto) repeat(5, 100px); } .calculator-grid > button { cursor: pointer; font-size: 2rem; border: 1px solid white; outline: none; background-color: lightgrey; } .calculator-grid > button:hover { background-color:lightyellow; } .span-two { grid-column: span 2; } .output { grid-column: 1 / -1; background-color: rgba(0, 0, 0, .75); display: flex; align-items: flex-end; justify-content: space-around; flex-direction: column; padding: 10px; word-wrap: break-word; word-break: break-all; } .output .previous-operand { color:royalblue; font-size: 1.5rem; } .output .current-operand { color: white; font-size: 2.5rem; } </style>

## PROGRAM :
```
JavaScript program to implement a simple calculator.

<!DOCTYPE html>
<html>
    <head>
        <title>SEC Demo on Calculator</title>
        <style type="text/css">
        table{
            border: 1px solid black;
            margin-left: auto;
            margin-right: auto;
        }
        input[type="text"]{
            border: 1px solid black;
            padding: 20px 30px;
            font-size: 24px;
            font-weight: bold;
            border-radius: 2px;
        }


        input[type="button"]{
            width: 100%;
            padding: 20px 40px;
            background-color:greenyellow;
            border-radius: 2px;
        }
        </style>
    </head>
    <body>
        <form name="form1" onload="result.value=''">
            <h1 style="text-align: center;color:blue;">Simple Calculator</h1>
        <table id="calc">
            <tr>
                <td colspan="4">
                    <input type="text" id="result">
                </td>
            </tr>
            <tr>
                <td><input type="button" value="1" onclick="result.value+='1'"/></td>
                <td><input type="button" value="2" onclick="result.value+='2'"/></td>
                <td><input type="button" value="3" onclick="result.value+='3'"/></td>
                <td><input type="button" value="+" onclick="result.value+='+'"/></td>
            </tr>
            <tr>
                <td><input type="button" value="4" onclick="result.value+='4'"/></td>
                <td><input type="button" value="5" onclick="result.value+='5'"/></td>
                <td><input type="button" value="6" onclick="result.value+='6'"/></td>
                <td><input type="button" value="-" onclick="result.value+='-'"/></td>
            </tr>
            <tr>
                <td><input type="button" value="7" onclick="result.value+='7'"/></td>
                <td><input type="button" value="8" onclick="result.value+='8'"/></td>
                <td><input type="button" value="9" onclick="result.value+='9'"/></td>
                <td><input type="button" value="*" onclick="result.value+='*'"/></td>
            </tr>
            <tr>
                <td><input type="button" value="/" onclick="result.value+='/'"/></td>
                <td><input type="button" value="0" onclick="result.value+='0'"/></td>
                <td><input type="button" value="." onclick="result.value+='.'"/></td>
                <td><input type="button" value="=" onclick="result.value=eval(result.value)"/></td>
            </tr>
            <tr>
                <td colspan="4">
                    <input type="button" value="clear all" id="clear" onclick="result.value=''">
                </td>
            </tr>
        </table>
        </form>
    </body>
</html>
```
```
Java script coding :

let screen = document.getElementById('screen');
buttons = document.querySelectorAll('button');
let screenValue = '';
for (item of buttons) {
    item.addEventListener('click', (e) => {
        buttonText = e.target.innerText;
        console.log('Button text is ', buttonText);
        if (buttonText == 'X') {
            buttonText = '*';
            screenValue += buttonText;
            screen.value = screenValue;
        }
        else if (buttonText == 'C') {
            screenValue = "";
            screen.value = screenValue;
        }
        else if (buttonText == '=') {
            screen.value = eval(screenValue);
        }
        else {
            screenValue += buttonText;
            screen.value = screenValue;
        }

    })
}
```

## OUTPUT:


![image](https://github.com/prabhjot-singh18/standard-calculator/assets/121215854/c792dd09-d401-4785-ae50-2ce8e3d409c9)

## Result:
    The Program has been Executed Successfully.

