const calculator = document.createElement('div');
calculator.className='calculator';
document.body.appendChild(calculator);

const display = document.createElement('input');
display.type ='text';
display.className ='calculator-display';
display.disabled ='true';
calculator.appendChild(display);

const buttonsContainer = document.createElement('div');
buttonsContainer.className ='calculator-buttons';
calculator.appendChild(buttonsContainer);
const buttons = [
    '7', '8', '9', '/',
    '4', '5', '6', '*',
    '1', '2', '3', '-',
    '0', '.', '=', '+',
    'C'
];
buttons.forEach((btn) => {
const button = document.createElement('button');
button.innerText = btn;
button.className = 'calculator-button';
button.addEventListener('click', () => onButtonclick(btn));
buttonsContainer.appendChild(button);
});
let currentInput ='';
function onButtonclick(value) {
    if(value === 'C') {
        currentInput = '';
        display.value = '';
    } else if (value ==='=') {
        try {
            currentInput = eval(currentInput).toStrong();
            display.value = currentInput;

        } catch(error) {
            display.value = 'Error';
            currentInput ='';
        }
    } else {
        currentInput += value;
        display.value = currentInput;

    }
}
const style = document.createElement('style');
style.innerHTML = `
.calculator {
    width: 300px;
    margin:50px auto;
    padding:10px;
    border: 1px solid #ccc;
    border-radius:10px;
    border:1px solid #ccc:
    box-shadow:0 4px 8px rgba(0,0,0,0,1);
    text-align:center;
    background-color:#f9f9f9;
}
    .calculator-display {
    width:100%;
    height:50px;
    font-size:2rem;
    margin-bottom:10px;
    text-align:right;
    padding:5px;
}
    .calculator-buttons {
    display:grid;
    grid-template-columns:repeat((4,1fr);
    gap:10px;
    }

    .calculator-button {
    padding:15px;
    font-size:1.5rem;
    border:none;
    border-radius:5px;
    cursor:pointer;
    transition:background-color 0.2s;
}
    .calculator-button:hover {
    background-color:#ddd;
    }
.calculator-button:active {
background-color:#bbb;
}
    
`;
document.head.appendChild(style);
