<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1" />
<title>Registration Form</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');

  * {
    box-sizing: border-box;
  }

  body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background: linear-gradient(135deg, #6b73ff 0%, #000dff 100%);
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 15px;
  }

  .container {
    background: #fff;
    border-radius: 15px;
    box-shadow: 0 0 25px rgba(0,0,0,0.15);
    max-width: 350px;
    width: 100%;
    padding: 30px 25px;
  }

  h2 {
    margin: 0 0 20px;
    font-weight: 600;
    font-size: 1.8rem;
    color: #202020;
    text-align: center;
  }

  form {
    display: flex;
    flex-direction: column;
  }

  label {
    font-weight: 600;
    font-size: 0.9rem;
    margin-bottom: 6px;
    color: #444;
  }

  input[type="text"],
  input[type="email"],
  input[type="password"] {
    padding: 12px 14px;
    margin-bottom: 18px;
    font-size: 1rem;
    border: 1.8px solid #ccc;
    border-radius: 8px;
    transition: border-color 0.3s ease;
  }

  input[type="text"]:focus,
  input[type="email"]:focus,
  input[type="password"]:focus {
    border-color: #000dff;
    outline: none;
  }

  button {
    padding: 14px;
    background-color: #000dff;
    border: none;
    border-radius: 10px;
    color: white;
    font-size: 1.1rem;
    font-weight: 600;
    cursor: pointer;
    transition: background-color 0.3s ease;
    margin-top: 8px;
  }

  button:hover,
  button:focus {
    background-color: #6b73ff;
  }

  .note {
    font-size: 0.8rem;
    color: #666;
    text-align: center;
    margin-top: 15px;
  }

  @media (max-width: 400px) {
    .container {
      max-width: 100%;
      padding: 25px 20px;
    }
  }
</style>
</head>
<body>
  <div class="container" role="main">
    <h2>Register</h2>
    <form id="registrationForm" novalidate>
      <label for="fullname">Full Name</label>
      <input type="text" id="fullname" name="fullname" placeholder="Your full name" required autocomplete="name" />

      <label for="email">Email Address</label>
      <input type="email" id="email" name="email" placeholder="example@mail.com" required autocomplete="email" />

      <label for="password">Password</label>
      <input type="password" id="password" name="password" placeholder="Enter password" required autocomplete="new-password" minlength="6" />

      <label for="confirmPassword">Confirm Password</label>
      <input type="password" id="confirmPassword" name="confirmPassword" placeholder="Confirm password" required autocomplete="new-password" minlength="6" />

      <button type="submit">Register</button>
      <p class="note">* Password must be at least 6 characters</p>
    </form>
  </div>

<script>
  const form = document.getElementById('registrationForm');

  form.addEventListener('submit', function (e) {
    e.preventDefault();

    const fullname = form.fullname.value.trim();
    const email = form.email.value.trim();
    const password = form.password.value;
    const confirmPassword = form.confirmPassword.value;

    if (!fullname) {
      alert('Please enter your full name.');
      form.fullname.focus();
      return;
    }

    if (!email || !validateEmail(email)) {
      alert('Please enter a valid email address.');
      form.email.focus();
      return;
    }

    if (password.length < 6) {
      alert('Password must be at least 6 characters.');
      form.password.focus();
      return;
    }

    if (password !== confirmPassword) {
      alert('Passwords do not match.');
      form.confirmPassword.focus();
      return;
    }

    alert('Registration successful!');

    form.reset();
  });

  function validateEmail(email) {
    // Simple email regex for validation
    const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return re.test(email);
  }
</script>
</body>
</html>


