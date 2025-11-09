# Ex06 BMI Calculator
## Date: 05-11-2025

## AIM
To develop a responsive and interactive Body Mass Index (BMI) Calculator using React that allows users to input their height and weight, and calculates their BMI to categorize their health status (e.g., Underweight, Normal, Overweight, Obese).

## DESIGN STEPS

### STEP 1: Initialize React Project

<li>Create a new React app using create-react-app.</li>
<li>Install React Router using:</li>
npm install react-router-dom

### STEP 2: Set Up Routing

Create routing structure with react-router-dom:

<li>Home route (/) – Intro or Navigation</li>

<li>BMI Calculator route (/bmi)</li>

<li>Result route (/result)</li>

### STEP 3: Design the BMI Form Page

<li>Create a form to accept Height (in cm or m) and Weight (in kg).</li>

<li>On form submit, navigate to the result page with entered values via URL query params or context/state.</li>

## STEP 4: Handle Input Validation

<li>Check if height and weight are valid numbers.</li>

<li>Optionally, show error messages for invalid inputs.</li>

### STEP 5: Perform BMI Calculation

<li>In the result component:

<li>Extract height and weight from the route (URL or passed state).</li>

<li>Apply the BMI formula:</li>

![image](https://github.com/user-attachments/assets/ec785506-c96b-489e-8783-fb1a5d36101a)
​
 
<li>Convert height from cm to m if needed.</li></li>

### STEP 6: Display Result

<li>Show calculated BMI.</li>

<li>Show category based on BMI range:

<li>Underweight, Normal, Overweight, Obese, etc.</li></li>

### STEP 7: Navigation Options

<li>Provide a button to go back to the BMI form to calculate again.</li>

### STEP 8: Enhancements

<li>Add styling using CSS or Tailwind.</li>

## PROGRAM

app.js
```

import React, { useState } from "react";
import "./App.css";

function App() {
  const [weight, setWeight] = useState("");
  const [height, setHeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState("");

  const calculateBMI = () => {
    if (weight && height) {
      const heightInMeters = height / 100;
      const bmiValue = (weight / (heightInMeters * heightInMeters)).toFixed(2);
      setBmi(bmiValue);

      if (bmiValue < 18.5) setCategory("Underweight");
      else if (bmiValue < 25) setCategory("Normal weight");
      else if (bmiValue < 30) setCategory("Overweight");
      else setCategory("Obesity");
    }
  };

  const reset = () => {
    setWeight("");
    setHeight("");
    setBmi(null);
    setCategory("");
  };

  return (
    <div className="container">
      <h1>BMI Calculator</h1>
      <div className="card">
        <div className="input-group">
          <label>Weight (kg):</label>
          <input
            type="number"
            value={weight}
            onChange={(e) => setWeight(e.target.value)}
          />
        </div>
        <div className="input-group">
          <label>Height (cm):</label>
          <input
            type="number"
            value={height}
            onChange={(e) => setHeight(e.target.value)}
          />
        </div>
        <div className="buttons">
          <button className="btn calculate" onClick={calculateBMI}>Calculate</button>
          <button className="btn reset" onClick={reset}>Reset</button>
        </div>
        {bmi && (
          <div className="result">
            <h2>Your BMI: {bmi}</h2>
            <p className={`category ${category.toLowerCase().replace(" ", "-")}`}>
              Category: {category}
            </p>
          </div>
        )}
      </div>
      <div>
        <footer>@copyrigth from santhosh d</footer>
      </div>
    </div>
  );
}

export default App;
```

app.css
```
body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: linear-gradient(135deg, #e0f7fa, #ffffff);
  margin: 0;
  padding: 0;
}

.container {
  max-width: 420px;
  margin: 80px auto;
  padding: 35px 25px;
  background-color: #ffffff;
  border-radius: 16px;
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
  text-align: center;
  transition: transform 0.2s ease-in-out;
}

.container:hover {
  transform: translateY(-5px);
}

h1 {
  margin-bottom: 25px;
  font-size: 28px;
  color: #2c3e50;
}

.input-group {
  margin-bottom: 20px;
  text-align: left;
}

.input-group label {
  display: block;
  margin-bottom: 6px;
  font-weight: 600;
  color: #34495e;
}

.input-group input {
  width: 100%;
  padding: 12px;
  font-size: 16px;
  border: 2px solid #dfe6e9;
  border-radius: 10px;
  background-color: #f9f9f9;
  outline: none;
  transition: border-color 0.3s;
}

.input-group input:focus {
  border-color: #00bcd4;
}

button {
  padding: 12px 24px;
  font-size: 16px;
  margin: 12px 6px;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  background-color: #00bcd4;
  color: white;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

button:hover {
  background-color: #0097a7;
  transform: scale(1.05);
}

button.reset {
  background-color: #95a5a6;
}

button.reset:hover {
  background-color: #7f8c8d;
}

.result {
  margin-top: 30px;
  padding: 20px;
  border-radius: 10px;
  background-color: #ecf0f1;
  border-left: 5px solid #00bcd4;
  text-align: center;
}

.result h2 {
  margin-bottom: 10px;
  color: #2c3e50;
}
.message {
  font-size: 18px;
  font-weight: bold;
  color: #2c3e50;
}

footer {
  margin-top: 40px;
  font-size: 14px;
  color: #7f8c8d;
  font-weight: 500;
}


```



## OUTPUT

![web](https://github.com/user-attachments/assets/fb455d06-20f6-4763-9503-702a5f35489e)



## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
