<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Login - Brand In Hand</title>
  <script src="https://www.gstatic.com/firebasejs/9.6.10/firebase-app-compat.js"></script>
  <script src="https://www.gstatic.com/firebasejs/9.6.10/firebase-auth-compat.js"></script>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin-top: 50px;
    }
    input {
      padding: 10px;
      margin: 8px;
      width: 250px;
    }
    button {
      padding: 10px 20px;
      margin: 8px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h2>Login or Signup</h2>

  <input type="email" id="email" placeholder="Email" /><br>
  <input type="password" id="password" placeholder="Password" /><br>

  <button onclick="login()">Login</button>
  <button onclick="signup()">Signup</button><br>
  <a href="#" onclick="resetPassword()">Forgot Password?</a>

  <script>
    // Initialize Firebase
    const firebaseConfig = {
      apiKey: "AIzaSyCmGXM8qEa-5c6xtByCwr_NsO4lKPOhAFQ",
      authDomain: "brandinhandlogin.firebaseapp.com",
      projectId: "brandinhandlogin",
      storageBucket: "brandinhandlogin.appspot.com",
      messagingSenderId: "536075142608",
      appId: "1:536075142608:web:299aa19512a07d2e8725d5"
    };
    firebase.initializeApp(firebaseConfig);

    const auth = firebase.auth();

    function login() {
      const email = document.getElementById("email").value;
      const password = document.getElementById("password").value;
      auth.signInWithEmailAndPassword(email, password)
        .then(() => alert("Login successful!"))
        .catch((err) => alert("Login failed: " + err.message));
    }

    function signup() {
      const email = document.getElementById("email").value;
      const password = document.getElementById("password").value;
      auth.createUserWithEmailAndPassword(email, password)
        .then(() => alert("Signup successful!"))
        .catch((err) => alert("Signup failed: " + err.message));
    }

    function resetPassword() {
      const email = document.getElementById("email").value;
      auth.sendPasswordResetEmail(email)
        .then(() => alert("Reset email sent!"))
        .catch((err) => alert("Reset failed: " + err.message));
    }
  </script>
</body>
</html>
