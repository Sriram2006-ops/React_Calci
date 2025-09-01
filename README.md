# Ex04 Simple Calculator - React Project
## Date:01-09-2025
SRIRAM.E
212224220106

## AIM
To  develop a Simple Calculator using React.js with clean and responsive design, ensuring a smooth user experience across different screen sizes.

## ALGORITHM
### STEP 1
Create a React App.

### STEP 2
Open a terminal and run:
  <ul><li>npx create-react-app simple-calculator</li>
  <li>cd simple-calculator</li>
  <li>npm start</li></ul>

### STEP 3
Inside the src/ folder, create a new file Calculator.js and define the basic structure.

### STEP 4
Plan the UI: Display screen, number buttons (0-9), operators (+, -, *, /), clear (C), and equal (=).

### STEP 5
Create a new file Calculator.css in src/ and add the styling.

### STEP 6
Open src/App.js and modify it.

### STEP 7
Start the development server.
  npm start

### STEP 8
Open http://localhost:3000/ in the browser.

### STEP 9
Test the calculator by entering numbers and operations.

### STEP 10
Fix styling issues and refine content placement.

### STEP 11
Deploy the website.

### STEP 12
Upload to GitHub Pages for free hosting.

## PROGRAM

App.js
```
import { useState } from "react";
import "./App.css";

function App() {
  const [input, setInput] = useState("0");
  const [lastResult, setLastResult] = useState("");

  const handleClick = (value) => {
    setInput((prev) => (prev === "0" ? value : prev + value));
  };

  const handleClear = () => {
    setInput("0");
    setLastResult("");
  };

  const handleBackspace = () => {
    setInput((prev) => (prev.length > 1 ? prev.slice(0, -1) : "0"));
  };

  const handleCalculate = () => {
    try {
      const result = eval(input).toString();
      setLastResult(input + " = " + result);
      setInput(result);
    } catch {
      setInput("Error");
    }
  };

  return (
    <div className="app-container">
      <div className="calculator-container">
        <div className="calculator">
          <div className="last-result">{lastResult}</div>
          <div className="display">{input}</div>
          <div className="buttons">
            <button className="button number" onClick={() => handleClick("7")}>7</button>
            <button className="button number" onClick={() => handleClick("8")}>8</button>
            <button className="button number" onClick={() => handleClick("9")}>9</button>
            <button className="button operator" onClick={() => handleClick("/")}>÷</button>
            <button className="button number" onClick={() => handleClick("4")}>4</button>
            <button className="button number" onClick={() => handleClick("5")}>5</button>
            <button className="button number" onClick={() => handleClick("6")}>6</button>
            <button className="button operator" onClick={() => handleClick("*")}>×</button>
            <button className="button number" onClick={() => handleClick("1")}>1</button>
            <button className="button number" onClick={() => handleClick("2")}>2</button>
            <button className="button number" onClick={() => handleClick("3")}>3</button>
            <button className="button operator" onClick={() => handleClick("-")}>−</button>
            <button className="button number" onClick={() => handleClick("00")}>00</button>
            <button className="button number" onClick={() => handleClick("0")}>0</button>
            <button className="button number" onClick={() => handleClick(".")}>.</button>
            <button className="button operator" onClick={() => handleClick("+")}>+</button>
            <button className="button backspace" onClick={handleBackspace}>⌫</button>
            <button className="button equals" onClick={handleCalculate}>=</button>
            <button className="button clear" onClick={handleClear}>Clear</button>
          </div>
        </div>
      </div>
      
      {/* Footer is outside the calculator box */}
      <footer className="footer">
        &copy; 2025 sriram.e 212224220106. All Rights Reserved.
      </footer>
    </div>
  );
}

export default App;
```

App.css
```
.App {
    text-align: center;
  }
  
  .App-logo {
    height: 40vmin;
    pointer-events: none;
  }
  
  @media (prefers-reduced-motion: no-preference) {
    .App-logo {
      animation: App-logo-spin infinite 20s linear;
    }
  }
  
  .App-header {
    background-color: #f5f5f5;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-size: calc(10px + 2vmin);
    color: #333;
  }
  
  .App-link {
    color: #ff6f61;
  }
  
  @keyframes App-logo-spin {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(360deg);
    }
  }
  
  .calculator-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color:  #b2e5f4; /* Light mode background */
  }
  
  .calculator {
    width: 280px;
    height: 400px;
    background: #f9f9f9; /* Soft white for calculator */
    padding: 20px;
    border-radius: 15px;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
    text-align: center;
  }
  
  .display {
    font-size: 2rem;
    background: #e1e6e3be; /* Light gray display */
    color: #003366; /* Dark blue text */
    padding: 15px;
    border-radius: 10px;
    margin-bottom: 15px;
    text-align: right;
  }
  
  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 8px;
  }
  
  .button {
    padding: 12px;
    font-size: 1.2rem;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: 0.3s ease;
    background-color:  #b2e5f4;
  }
  
  .number-7 { background-color: #ffb3b3; }
  .number-8 { background-color: #ffcf94; }
  .number-9 { background-color: #ffee99; }
  .operator-divide { background-color: #7ed6df; }
  
  .number-4 { background-color: #f3b8f3; }
  .number-5 { background-color: #a6b1e1; }
  .number-6 { background-color: #91c1ff; }
  .operator-multiply { background-color: #ff6b81; }
  
  .number-1 { background-color: #ffae42; }
  .number-2 { background-color: #c2f7c2; }
  .number-3 { background-color: #f8c3c3; }
  .operator-subtract { background-color: #008ecc; }
  
  .number-0 { background-color: #b3e6b3; }
  .number-dot { background-color: #ffda77; }
  .equals { background-color: #28a745; color: white; }
  .operator-add { background-color: #ff3366; }
  
  .clear {
    grid-column: span 2;
    background-color: #ff4444;
    color: white;
    font-size: 1.4rem;
    border-radius: 10px;
    padding: 10px;
  }
  
  .number {
    background-color: #add8e6;
    color: black;
  }
  
  .operator {
    background-color: #ff9800;
    color: white;
  }
  
  .clear {
    background-color: #ff5555;
    color: white;
  }
  
  .equals {
    background-color: #00c853;
    color: white;
  }
  
  .footer {
    text-align: center;
    padding: 10px;
    background-color: #b2e5f4;
    color: #333;
    font-size: 14px;
    width: 100%;
    position: fixed;
    bottom: 0;
  }
  ```


## OUTPUT
<img width="1023" height="509" alt="Screenshot 2025-09-01 112038" src="https://github.com/user-attachments/assets/0e104896-6da4-4cac-a4c4-cd79d9eef1d8" />


## RESULT
The program for developing a simple calculator in React.js is executed successfully.
