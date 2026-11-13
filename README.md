# Exp-6-React-Lab-Exercise-Form-Validation
## NAME : Paladugu Venkata Balaji
## REG NO : 2305001024
## Aim
To create a React form with validation for required fields, email, and password, and display appropriate error messages.

## Objectives
1. To create a form using React.
2. To manage form data using useState().
3. To validate required fields.
4. To validate an email address.
5. To validate password length.
6. To display error messages dynamically.
# Program
## Step 1 – Create React Project
~~~
npm create vite@latest form-validation
cd form-validation
npm install
npm run dev
~~~
Select React as the framework and JavaScript as the variant.

## Step 2 – App.jsx
~~~
import { useState } from "react";
import "./App.css";

function App() {
  const [formData, setFormData] = useState({
    name: "",
    email: "",
    password: ""
  });

  const [errors, setErrors] = useState({});

  const handleChange = (e) => {
    setFormData({
      ...formData,
      [e.target.name]: e.target.value
    });
  };

  const validate = () => {
    let newErrors = {};

    // Required field validation
    if (formData.name.trim() === "") {
      newErrors.name = "Name is required";
    }

    // Email validation
    if (formData.email.trim() === "") {
      newErrors.email = "Email is required";
    } else if (!formData.email.includes("@")) {
      newErrors.email = "Enter a valid email";
    }

    // Password validation
    if (formData.password === "") {
      newErrors.password = "Password is required";
    } else if (formData.password.length < 6) {
      newErrors.password =
        "Password must contain at least 6 characters";
    }

    return newErrors;
  };

  const handleSubmit = (e) => {
    e.preventDefault();

    const validationErrors = validate();
    setErrors(validationErrors);

    if (Object.keys(validationErrors).length === 0) {
      alert("Form submitted successfully!");
    }
  };

  return (
    <div className="container">
      <h1>Registration Form</h1>

      <form onSubmit={handleSubmit} noValidate>
        <label>Name:</label>
        <input
          type="text"
          name="name"
          value={formData.name}
          onChange={handleChange}
          placeholder="Enter your name"
        />
        {errors.name && <p>{errors.name}</p>}

        <label>Email:</label>
        <input
          type="text"
          name="email"
          value={formData.email}
          onChange={handleChange}
          placeholder="Enter your email"
        />
        {errors.email && <p>{errors.email}</p>}

        <label>Password:</label>
        <input
          type="password"
          name="password"
          value={formData.password}
          onChange={handleChange}
          placeholder="Enter your password"
        />
        {errors.password && <p>{errors.password}</p>}

        <button type="submit">Register</button>
      </form>
    </div>
  );
}

export default App;

~~~

## Step 3 – App.css
~~~ 
.container {
  width: 350px;
  margin: 30px auto;
  padding: 20px;
  border: 1px solid gray;
  border-radius: 10px;
}

h1 {
  text-align: center;
  color: blue;
}

label {
  display: block;
  margin-top: 15px;
  font-weight: bold;
}

input {
  width: 100%;
  padding: 8px;
  margin-top: 5px;
  box-sizing: border-box;
}

p {
  color: red;
  margin: 5px 0;
}

button {
  margin-top: 20px;
  padding: 10px 20px;
  cursor: pointer;
}
~~~ 
## Output
1. Invalid Form – Error Messages
<img width="1406" height="717" alt="image" src="https://github.com/user-attachments/assets/75b39e6f-d819-4df2-bd22-7738a4849cbb" />
2. Correct Form – Valid Input Details
<img width="1470" height="702" alt="image" src="https://github.com/user-attachments/assets/8a609bec-4fe0-4971-93ff-6b3f79461b45" />
3. Successful Form Submission – Alert Pop-up
<img width="1472" height="711" alt="image" src="https://github.com/user-attachments/assets/d0479d00-e443-4f9d-9a6f-692b55ea054e" />

## Result
Thus, a React Registration Form was successfully created with form validation using the useState() Hook. Required fields, email format, and password length were validated, and appropriate error messages were displayed dynamically. The form was successfully submitted when all the entered details were valid.
