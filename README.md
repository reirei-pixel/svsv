# <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bank Account Registration</title>
    <style>
        @import url('https://fonts.googleapis.com');

        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: #e2e8f0;
            background-image: 
                radial-gradient(at 0% 0%, hsla(225, 39%, 30%, 1) 0, transparent 50%), 
                radial-gradient(at 50% 0%, hsla(225, 39%, 23%, 1) 0, transparent 50%), 
                radial-gradient(at 100% 0%, hsla(225, 39%, 30%, 1) 0, transparent 50%),
                radial-gradient(at 0% 100%, hsla(225, 39%, 23%, 1) 0, transparent 50%), 
                radial-gradient(at 50% 100%, hsla(225, 39%, 30%, 1) 0, transparent 50%), 
                radial-gradient(at 100% 100%, hsla(225, 39%, 23%, 1) 0, transparent 50%);
            background-attachment: fixed;
            padding: 20px;
        }

        .container {
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            padding: 40px;
            border-radius: 24px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            width: 100%;
            max-width: 600px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-top: 6px solid #2563eb;
        }

        h2 {
            margin: 0 0 32px 0;
            font-size: 1.85rem;
            font-weight: 800;
            color: #0f172a;
            letter-spacing: -0.03em;
            text-align: center;
        }

        h2::after {
            content: "Create your secure banking profile";
            display: block;
            font-size: 0.9rem;
            font-weight: 500;
            color: #64748b;
            margin-top: 8px;
            letter-spacing: normal;
        }

        /* Layout Helpers */
        .form-row {
            display: flex;
            gap: 15px;
            margin-bottom: 5px;
        }

        .form-group {
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        /* UPDATED: Royal Blue Labels & Spacing */
        label {
            display: block;
            font-size: 0.75rem;
            font-weight: 700;
            color: #4169E1; /* Royal Blue */
            text-transform: uppercase;
            letter-spacing: 0.05em;
            margin-bottom: 8px; /* Gap between label and input */
            margin-top: 12px;
        }

        input, select {
            width: 100%;
            padding: 12px 16px;
            border: 1.5px solid #e2e8f0;
            border-radius: 12px;
            font-size: 14px;
            font-family: inherit;
            background-color: #f8fafc;
            box-sizing: border-box;
            transition: all 0.2s ease;
        }

        input:focus, select:focus {
            outline: none;
            border-color: #2563eb;
            background-color: #ffffff;
            box-shadow: 0 0 0 4px rgba(37, 99, 235, 0.1);
        }

        select {
            appearance: none;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org' fill='none' viewBox='0 0 24 24' stroke='%2364748b'%3E%3Cpath stroke-linecap='round' stroke-linejoin='round' stroke-width='2' d='M19 9l-7 7-7-7'%3E%3C/path%3E%3C/svg%3E");
            background-repeat: no-repeat;
            background-position: right 16px center;
            background-size: 18px;
            cursor: pointer;
        }

        button {
            width: 100%;
            padding: 16px;
            margin-top: 25px;
            background: #2563eb;
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 16px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 10px 15px -3px rgba(37, 99, 235, 0.3);
        }

        button:hover {
            background: #1d4ed8;
            transform: translateY(-2px);
        }

        .error {
            color: #e11d48;
            background: rgba(225, 29, 72, 0.08);
            border: 1px solid #e11d48;
            border-radius: 8px;
            font-size: 0.85rem;
            font-weight: 600;
            margin: 6px 0 0 0;
            min-height: 18px;
            padding: 6px 12px;
            box-shadow: 0 2px 8px -2px rgba(225, 29, 72, 0.08);
            transition: all 0.2s;
            letter-spacing: 0.01em;
            display: none;
        }

        .success {
            color: #15803d;
            background: rgba(34, 197, 94, 0.08);
            border: 1px solid #22c55e;
            border-radius: 8px;
            font-size: 0.95rem;
            font-weight: 700;
            margin: 18px 0 0 0;
            padding: 10px 16px;
            box-shadow: 0 2px 8px -2px rgba(34, 197, 94, 0.08);
            letter-spacing: 0.01em;
            text-align: center;
            display: block;
            transition: all 0.2s;
        }

        #successMessage {
            color: #15803d;
            background: rgba(34, 197, 94, 0.08);
            border: 1px solid #22c55e;
            border-radius: 8px;
            font-size: 0.95rem;
            font-weight: 700;
            margin: 18px 0 0 0;
            padding: 10px 16px;
            box-shadow: 0 2px 8px -2px rgba(34, 197, 94, 0.08);
            letter-spacing: 0.01em;
            text-align: center;
            display: none;
            transition: all 0.2s;
        }

        @media (max-width: 480px) {
            .form-row { flex-direction: column; gap: 0; }
            .container { padding: 24px; }
        }
    </style>
</head>

<body>
	<div class="container">
		<h2>Bank Account Registration</h2>
		<form id="registrationForm">
			<!-- Name Row -->
			<div class="form-row">
				<div class="form-group">
					<label>First Name</label>
					<input type="text" id="firstName" placeholder="John">
					<p class="error" id="firstNameError"></p>
				</div>
				<div class="form-group">
					<label>Middle Name</label>
					<input type="text" id="middleName" placeholder="Quincy">
					<p class="error" id="middleNameError"></p>
				</div>
				<div class="form-group">
					<label>Last Name</label>
					<input type="text" id="lastName" placeholder="Doe">
					<p class="error" id="lastNameError"></p>
				</div>
			</div>

			<!-- Contact & Gender Row -->
			<div class="form-row">
				<div class="form-group">
					<label>Contact Number</label>
					<input type="text" id="contactNumber" placeholder="+63 912 345 6789">
					<p class="error" id="contactError"></p>
				</div>
				<div class="form-group">
					<label>Gender</label>
					<select id="gender">
						<option value="" disabled selected>Select Gender</option>
						<option value="male">Male</option>
						<option value="female">Female</option>
						<option value="other">Other</option>
					</select>
					<p class="error" id="genderError"></p>
				</div>
			</div>

			<label>Username</label>
			<input type="text" id="username" placeholder="jdoe24">
			<p class="error" id="usernameError"></p>

			<label>Email Address</label>
			<input type="email" id="email" placeholder="name@bank.com">
			<p class="error" id="emailError"></p>

			<div class="form-row">
				<div class="form-group">
					<label>Password</label>
					<input type="password" id="password" placeholder="••••••••">
					<p class="error" id="passwordError"></p>
				</div>
				<div class="form-group">
					<label>Confirm Password</label>
					<input type="password" id="confirmPassword" placeholder="••••••••">
					<p class="error" id="confirmPasswordError"></p>
				</div>
			</div>

			<button type="submit">Create Secure Account</button>
			<p id="successMessage"></p>
		</form>
	</div>
</body>
<script>
    let firtName = document.querySelector("#firstName");
    let firtNameError = document.querySelector("#firstNameError");

    let middleName = document.querySelector("#middleName");
    let middleNameError = document.querySelector("#middleNameError");

    let lastName = document.querySelector("#lastName");
    let lastNameError = document.querySelector("#lastNameError");

    let contactNumber = document.querySelector("#contactNumber");
    let contactError = document.querySelector("#contactError");

  

    




    firstName.addEventListener('keyup',function(){
        if(firtName.value.trim() === ""){

            firtNameError.textContent = "Error: Input is Empty!";
            firtNameError.style.display = "block";
        } else {
            firtNameError.textContent = "";
            firtNameError.style.display = "none";

        }
    });

    middleName.addEventListener('keyup', function(){
        if(middleName.value.trim() === ""){

            middleNameError.textContent = "Error: Input is Empty!";
            middleNameError.style.display = "block";
        }else{
            middleNameError.textContent = "";
            middleNameError.style.display = "none";
        }
    });

    lastName.addEventListener('keyup', function(){
        if(lastName.value.trim() === ""){

            lastNameError.textContent = "Error: Input is Empty!";
            lastNameError.style.display = "block";
        }else{
            lastNameError.textContent = "";
            lastNameError.style.display = "none";
        }
    });

    contactNumber.addEventListener('keyup', function(){
        if(contactNumber.value.length != 11){

            contactError.textContent = "Error: Number must be greater than 11";
            contactError.style.display = "block";
        }else{
            contactError.textContent = "";
            contactError.style.display = "none";
        }
    });

    let username = document.querySelector("#username");
    let usernameError = document.querySelector("#usernameError");

    username.addEventListener('keyup', function(){
        if(username.value.length < 5){

            usernameError.textContent = "Error: Username must be greater than 5";
            usernameError.style.display = "block";

        }else{
            usernameError.textContent = "";
            usernameError.style.display = "none";
        }
    });

    let email = document.querySelector("#email");
    let emailError = document.querySelector("#emailError");

    email.addEventListener('keyup', function(){
        if(email.value.trim() === ""){
            emailError.textContent = "Error: Email is Empty";
            emailError.style.display = "block";
        }else{
            let emailPattern = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
            if (!emailPattern.test(email.value)) {
                emailError.textContent = "Error: Invalid Email";
                emailError.style.display = "block";
            } else {
                emailError.textContent = "";
                emailError.style.display = "none";
            }
        }
            
    });

    let password = document.querySelector("#password");
    let passwordError = document.querySelector("#passwordError");

    password.addEventListener('keyup', function(){
        if(password.value.length < 8){
            passwordError.textContent = "Error: Password must be greater than 8";
            passwordError.style.display = "block";
        }else{
            passwordError.textContent = "";
            passwordError.style.display = "None";
        }
    })

    let confirmPassword = document.querySelector("#confirmPassword");
    let confirmPasswordError = document.querySelector("#confirmPasswordError");

    confirmPassword.addEventListener('keyup', function(){
        if(confirmPassword.value != password.value){
            confirmPassword.textContent = "Error: Password Incorrect";
            confirmPassword.style.display = "block";
        }else{
            confirmPassword.textContent = "";
            confirmPassword.style.display = "None";
        }
    })
   
    let submit
</script>
</html>
