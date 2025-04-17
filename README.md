# feb-2025-avasjcript-events-and-basic-interactivity

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Interactive JavaScript</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
    }
    .input-group {
      margin-bottom: 15px;
    }
    .error {
      color: red;
      font-size: 0.9em;
    }
    #colorBox {
      width: 100px;
      height: 100px;
      background-color: coral;
      margin-top: 20px;
      border-radius: 8px;
      transition: background-color 0.3s ease;
    }
  </style>
</head>
<body>

  <h2>Interactive Form with Validation</h2>

  <form id="demoForm">
    <div class="input-group">
      <label for="username">Username:</label><br>
      <input type="text" id="username">
      <div id="usernameError" class="error"></div>
    </div>

    <div class="input-group">
      <label for="password">Password:</label><br>
      <input type="password" id="password">
      <button type="button" id="togglePwd">Show/Hide</button>
      <div id="passwordError" class="error"></div>
    </div>

    <button type="submit">Submit</button>
  </form>

  <div id="colorBox"></div>
  <button id="changeColorBtn">Change Box Color</button>

  <script>
    // Grab elements
    const form = document.getElementById("demoForm");
    const usernameInput = document.getElementById("username");
    const passwordInput = document.getElementById("password");
    const usernameError = document.getElementById("usernameError");
    const passwordError = document.getElementById("passwordError");
    const togglePwdBtn = document.getElementById("togglePwd");
    const colorBox = document.getElementById("colorBox");
    const changeColorBtn = document.getElementById("changeColorBtn");

    // Validate form
    form.addEventListener("submit", function(event) {
      event.preventDefault();

      let valid = true;
      usernameError.textContent = "";
      passwordError.textContent = "";

      if (usernameInput.value.trim() === "") {
        usernameError.textContent = "Username is required.";
        valid = false;
      }

      if (passwordInput.value.trim().length < 6) {
        passwordError.textContent = "Password must be at least 6 characters.";
        valid = false;
      }

      if (valid) {
        alert("Form submitted successfully!");
        form.reset();
      }
    });

    // Toggle password
