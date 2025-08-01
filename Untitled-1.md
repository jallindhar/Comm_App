<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Register</title>
    <style>
        body {
            background: rgba(0,0,0,0.2);
            font-family: Arial, sans-serif;
        }
        .register-box {
            background: #fff;
            width: 450px;
            margin: 30px auto;
            padding: 32px 32px 24px 32px;
            border-radius: 2px;
            box-shadow: 0 4px 16px rgba(0,0,0,0.2);
        }
        h2 {
            text-align: center;
            margin-bottom: 30px;
        }
        form {
            display: flex;
            flex-direction: column;
            gap: 18px;
        }
        .form-row {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        .form-row label {
            width: 140px;
            font-weight: bold;
            text-align: right;
            margin-right: 10px;
        }
        .form-row input {
            width: 220px;
            padding: 8px;
            border: 2px solid #222;
            border-radius: 6px;
            font-size: 16px;
        }
        .register-btn {
            width: 180px;
            padding: 10px;
            background: #7ffcff;
            border: 2px solid #222;
            border-radius: 8px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            margin: 20px auto 0 auto;
            display: block;
        }
        .error {
            color: #d00;
            font-size: 14px;
            text-align: center;
            margin-top: -10px;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <div class="register-box">
        <h2>Register</h2>
        <form id="registerForm" autocomplete="off">
            <div class="form-row">
                <label for="fullname">Full Name</label>
                <input type="text" id="fullname" name="fullname" value="Anne Hunter">
            </div>
            <div class="form-row">
                <label for="email">Email</label>
                <input type="email" id="email" name="email" value="anne.hunter@mail.com">
            </div>
            <div class="form-row">
                <label for="password">Password</label>
                <input type="password" id="password" name="password" value="******">
            </div>
            <div class="form-row">
                <label for="confirmpassword">Confirm Password</label>
                <input type="password" id="confirmpassword" name="confirmpassword" value="******">
            </div>
            <div id="errorMsg" class="error"></div>
            <button type="submit" class="register-btn">Register</button>
        </form>
    </div>
    <script>
        document.getElementById('registerForm').onsubmit = function(e) {
            e.preventDefault();
            var fullname = document.getElementById('fullname').value.trim();
            var email = document.getElementById('email').value.trim();
            var password = document.getElementById('password').value;
            var confirmpassword = document.getElementById('confirmpassword').value;
            var errorMsg = document.getElementById('errorMsg');
            errorMsg.textContent = "";

            // Simple email regex
            var emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

            if (!fullname) {
                errorMsg.textContent = "Please enter your full name.";
                return false;
            }
            if (!email || !emailPattern.test(email)) {
                errorMsg.textContent = "Please enter a valid email address.";
                return false;
            }
            if (!password) {
                errorMsg.textContent = "Please enter a password.";
                return false;
            }
            if (!confirmpassword) {
                errorMsg.textContent = "Please confirm your password.";
                return false;
            }
            if (password !== confirmpassword) {
                errorMsg.textContent = "Passwords do not match.";
                return false;
            }
            // If all validations pass, go to success page
            window.location.href = "Login successful.html";
        };
    </script>
</body>
</html>