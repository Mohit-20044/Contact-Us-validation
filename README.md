# Contact-Us-validation
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contact Form</title>
    <style>
        <style>
    body {
      font-family: Arial, sans-serif;
      background: #f9f9f9;
      padding: 20px;
    }
    form {
      background: white;
      padding: 20px;
      border-radius: 10px;
      max-width: 400px;
      margin: auto;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }
     label {
      font-weight: bold;
      display: block;
      margin: 10px 0 5px;
    }
    input, textarea {
      width: 100%;
      padding: 8px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
           background: #28a745;
      color: white;
      padding: 10px 15px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover {
      background: #218838;
    }
    .error {
      color: red;
      font-size: 0.9em;
    }
    </style>
</head>
<body>
    <h2>Contact Us</h2>
    <form id="ContactForm" onsubmit="return validateForm()">
        <label for="name">Name:</label>
        <input type="text" id="name" placeholder="Your Name">
        <div id="nameError" class="error"></div>

        <label for="email">Email:</label>
        <input type="email" id="email" placeholder="Your Email">
        <div id="emailError" class="error"></div>

         <label for="message">Message:</label>
        <textarea id="message" rows="4" placeholder="Your Message"></textarea>
        <div id="messageError" class="error"></div>

        <button type="submit">Submit</button>
<script>
    function validateForm() {
  let isValid = true;

  // Get field values
  let name = document.getElementById("name").value.trim();
  let email = document.getElementById("email").value.trim();
  let message = document.getElementById("message").value.trim();

  // Error fields
  let nameError = document.getElementById("nameError");
  let emailError = document.getElementById("emailError");
  let messageError = document.getElementById("messageError");

  // Clear previous errors
  nameError.textContent = "";
  emailError.textContent = "";
  messageError.textContent = "";

  // Name validation
  if (name === "") {
    nameError.textContent = "Name is required.";
    isValid = false;
  }

  // Email validation (simple regex)
  let emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,6}$/;
  if (email === "") {
    emailError.textContent = "Email is required.";
    isValid = false;
  } else if (!emailPattern.test(email)) {
    emailError.textContent = "Enter a valid email.";
    isValid = false;
  }
 // Message validation
  if (message === "") {
    messageError.textContent = "Message is required.";
    isValid = false;
  } else if (message.length < 10) {
    messageError.textContent = "Message must be at least 10 characters.";
    isValid = false;
  }

  return isValid; // Prevent submission if false
}
</script>        
</body>
</html>
