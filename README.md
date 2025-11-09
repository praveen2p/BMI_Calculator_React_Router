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
## bmicalclater.jsx:
```
import React, { useState } from 'react';

const BMICalculator = () => {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState('');

  const calculateBMI = () => {
    if (!weight || !height) return;
    const h = height / 100;
    const result = (weight / (h * h)).toFixed(2);
    setBmi(result);

    if (result < 18.5) setCategory('Underweight');
    else if (result < 24.9) setCategory('Normal weight');
    else if (result < 29.9) setCategory('Overweight');
    else setCategory('Obesity');
  };

  return (
    <div className="page">
      <h2>BMI Calculator</h2>
      <input
        type="number"
        placeholder="Weight (kg)"
        value={weight}
        onChange={(e) => setWeight(e.target.value)}
      />
      <input
        type="number"
        placeholder="Height (cm)"
        value={height}
        onChange={(e) => setHeight(e.target.value)}
      />
      <button onClick={calculateBMI}>Calculate</button>

      {bmi && (
        <div className="result">
          <p><strong>BMI:</strong> {bmi}</p>
          <p><strong>Category:</strong> {category}</p>
        </div>
      )}
    </div>
  );
};

export default BMICalculator;
```
### Home.jsx
```
import React from 'react';
import { Link } from 'react-router-dom';

const Home = () => {
  return (
    <div className="page">
      <h1>Welcome to BMI Calculator</h1>
      <Link to="/calculate">
        <button>Go to Calculator</button>
      </Link>
    </div>
  );
};

export default Home;
```
### App.css
```
body {
  background: linear-gradient(to bottom right, #dfe9f3, #ffffff);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.page {
  text-align: center;
  margin-top: 60px;
  padding: 20px;
}

input {
  padding: 12px;
  margin: 12px;
  width: 220px;
  border-radius: 8px;
  border: 1px solid #ccc;
  font-size: 16px;
}

button {
  padding: 12px 25px;
  background: #28a745;
  border: none;
  color: white;
  font-size: 16px;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.3s;
}

button:hover {
  background: #218838;
}

.result {
  margin-top: 25px;
  font-size: 18px;
  color: #333;
}
```



## OUTPUT
![Screenshot 2025-05-31 003846](https://github.com/user-attachments/assets/40399164-6db6-4111-b0ab-b261db7cda41)




## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
