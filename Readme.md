# Ex06 BMI Calculator
## Date:

## AIM
To create a BMI calculator using React Router 

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM
App.jsx
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
    </div>
  );
}

export default App;
```
App.css
```
body {
  margin: 0;
  font-family: "Segoe UI", sans-serif;
  background: #f2f7ff;
  color: #222;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}

h1 {
  margin-bottom: 20px;
  color: #2e3c88;
}

.card {
  background: #ffffff;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
  width: 350px;
}

.input-group {
  margin-bottom: 20px;
}

.input-group label {
  display: block;
  margin-bottom: 8px;
  font-weight: bold;
}

.input-group input {
  width: 100%;
  padding: 10px;
  border: 2px solid #ccc;
  border-radius: 10px;
  font-size: 1em;
}

.buttons {
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
}

.btn {
  flex: 1;
  padding: 10px;
  border: none;
  font-size: 1em;
  cursor: pointer;
  border-radius: 10px;
  margin: 0 5px;
}

.calculate {
  background-color: #2e8b57;
  color: white;
}

.reset {
  background-color: #ff4c4c;
  color: white;
}

.result {
  margin-top: 30px;
  text-align: center;
}

.result h2 {
  margin-bottom: 10px;
  color: #2e3c88;
}

.category {
  padding: 8px 12px;
  border-radius: 10px;
  display: inline-block;
  font-weight: bold;
  background-color: #e0e0e0;
}

.category.normal-weight {
  background-color: #a6f0c6;
  color: #006400;
}

.category.underweight {
  background-color: #ffe0b3;
  color: #cc7a00;
}

.category.overweight {
  background-color: #ffd6cc;
  color: #b30000;
}

.category.obesity {
  background-color: #ff9999;
  color: #990000;
}

```




## OUTPUT
![image](https://github.com/user-attachments/assets/f9d52db0-4f0f-4cb0-921e-bcd6771a68cd)



## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
