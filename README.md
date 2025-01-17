<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Training and Placement Registration</title>
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(to right, #f8f9fa, #e9ecef);
            color: #333;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .form-container {
            background: #fff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 800px;
        }

        .form-container h2 {
            text-align: center;
            margin-bottom: 20px;
            font-size: 24px;
            color: #495057;
        }

        .form-row {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
        }

        .form-group {
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        .form-group label {
            margin-bottom: 5px;
            font-weight: bold;
        }

        .form-group input, .form-group select {
            padding: 10px;
            border: 1px solid #ced4da;
            border-radius: 5px;
            font-size: 14px;
        }

        .form-group input:focus, .form-group select:focus {
            border-color: #6c757d;
            outline: none;
        }

        .table-container {
            margin-bottom: 20px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 10px;
        }

        table th, table td {
            border: 1px solid #dee2e6;
            padding: 10px;
            text-align: left;
        }

        table th {
            background-color: #f1f1f1;
            font-weight: bold;
        }

        .submit-btn {
            display: block;
            width: 100%;
            padding: 12px;
            background-color: #6c757d;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }

        .submit-btn:hover {
            background-color: #5a6268;
        }

        .form-footer {
            text-align: center;
            margin-top: 20px;
            font-size: 14px;
            color: #495057;
        }
    </style>
</head>
<body>
    <div class="form-container">
        <h2>Training and Placement Registration</h2>
        <form id="registrationForm">
            <div class="form-row">
                <div class="form-group">
                    <label for="name">Full Name</label>
                    <input type="text" id="name" name="name" placeholder="Enter your full name">
                </div>
                <div class="form-group">
                    <label for="dob">Date of Birth</label>
                    <input type="date" id="dob" name="dob">
                </div>
            </div>

            <div class="form-row">
                <div class="form-group">
                    <label for="email">Email</label>
                    <input type="email" id="email" name="email" placeholder="Enter your email">
                </div>
                <div class="form-group">
                    <label for="phone">Mobile Number</label>
                    <input type="text" id="phone" name="phone" placeholder="Enter your mobile number">
                </div>
            </div>

            <div class="form-row">
                <div class="form-group">
                    <label for="branch">Branch</label>
                    <select id="branch" name="branch">
                        <option value="">Select your branch</option>
                        <option value="CSE">CSE</option>
                        <option value="IT">IT</option>
                        <option value="ECE">ECE</option>
                        <option value="ECS">ECS</option>
                        <option value="AIML">AIML</option>
                        <option value="DS">DS</option>
                        <option value="CS">CS</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="cgpa">Current CGPA</label>
                    <input type="number" id="cgpa" name="cgpa" step="0.01" placeholder="Enter your CGPA">
                </div>
            </div>

            <div class="form-row">
                <div class="form-group">
                    <label for="motherName">Mother's Name</label>
                    <input type="text" id="motherName" name="motherName" placeholder="Enter your mother's name">
                </div>
                <div class="form-group">
                    <label for="fatherName">Father's Name</label>
                    <input type="text" id="fatherName" name="fatherName" placeholder="Enter your father's name">
                </div>
            </div>

            <div class="form-group">
                <label for="photo">Upload Photo (JPEG/JPG only, max 100MB)</label>
                <input type="file" id="photo" name="photo" accept="image/jpeg,image/jpg" onchange="validatePhoto()">
            </div>

            <div class="form-group">
                <label for="resume">Upload Resume (PDF only)</label>
                <input type="file" id="resume" name="resume" accept=".pdf" onchange="validateResume()">
            </div>

            <div class="form-group">
                <label>Academic Details</label>
                <table>
                    <thead>
                        <tr>
                            <th>Class</th>
                            <th>Year of Passing</th>
                            <th>Percentage</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>10th</td>
                            <td><input type="number" id="tenthYear" name="tenthYear" placeholder="Enter year"></td>
                            <td><input type="number" id="tenthPercentage" name="tenthPercentage" step="0.01" placeholder="Enter percentage"></td>
                        </tr>
                        <tr>
                            <td>12th</td>
                            <td><input type="number" id="twelfthYear" name="twelfthYear" placeholder="Enter year"></td>
                            <td><input type="number" id="twelfthPercentage" name="twelfthPercentage" step="0.01" placeholder="Enter percentage"></td>
                        </tr>
                    </tbody>
                </table>
            </div>

            <div class="form-group">
                <label for="backlog">Number of Active Backlogs</label>
                <input type="number" id="backlog" name="backlog" placeholder="Enter number of active backlogs">
            </div>

            <button type="button" class="submit-btn" onclick="validateForm()">Register</button>
        </form>
        <div class="form-footer">We wish you a successful registration!</div>
    </div>

    <script>
        function validateResume() {
            const resume = document.getElementById('resume').files[0];
            if (resume && resume.type !== 'application/pdf') {
                alert('Please upload your resume in PDF format.');
                document.getElementById('resume').value = ''; // Clear file input
            }
        }

        function validatePhoto() {
            const photo = document.getElementById('photo').files[0];
            if (photo && (photo.type !== 'image/jpeg' && photo.type !== 'image/jpg')) {
                alert('Please upload your photo in JPEG/JPG format.');
                document.getElementById('photo').value = ''; // Clear file input
            }
        }

        function validateForm() {
            let isValid = true;

            // Clear all error messages
            document.querySelectorAll('.error').forEach(error => error.textContent = '');

            // Name validation
            const name = document.getElementById('name').value.trim();
            if (name === '') {
                alert('Name is required');
                isValid = false;
            }

            // Date of Birth validation
            const dob = document.getElementById('dob').value.trim();
            if (dob === '') {
                alert('Date of birth is required');
                isValid = false;
            }

            // Email validation
            const email = document.getElementById('email').value.trim();
            const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (email === '' || !emailRegex.test(email)) {
                alert('Enter a valid email address');
                isValid = false;
            }

            // Phone validation
            const phone = document.getElementById('phone').value.trim();
            const phoneRegex = /^\d{10}$/;
            if (phone === '' || !phoneRegex.test(phone)) {
                alert('Enter a valid 10-digit mobile number');
                isValid = false;
            }

            if (isValid) {
                alert('Form submitted successfully!');
            }
        }
    </script>
</body>
</html>
