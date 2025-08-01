<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nex Gen Tech Academy Naukot</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.25/jspdf.plugin.autotable.min.js"></script>
    <style>
        :root {
            --primary: #3498db;
            --secondary: #2c3e50;
            --accent: #e74c3c;
            --light: #ecf0f1;
            --success: #27ae60;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #1a2a6c);
            background-attachment: fixed;
            color: #333;
            min-height: 100vh;
        }
        
        .card {
            border-radius: 15px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
            transition: transform 0.3s, box-shadow 0.3s;
            border: none;
            overflow: hidden;
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.3);
        }
        
        .btn-primary {
            background-color: var(--primary);
            border: none;
            padding: 10px 25px;
            border-radius: 50px;
            font-weight: 600;
            transition: all 0.3s;
        }
        
        .btn-primary:hover {
            background-color: #2980b9;
            transform: scale(1.05);
        }
        
        .btn-accent {
            background-color: var(--accent);
            color: white;
            border: none;
            padding: 10px 25px;
            border-radius: 50px;
            font-weight: 600;
            transition: all 0.3s;
        }
        
        .btn-accent:hover {
            background-color: #c0392b;
            transform: scale(1.05);
        }
        
        .header {
            background: rgba(44, 62, 80, 0.95);
            color: white;
            border-radius: 0 0 20px 20px;
            padding: 20px 0;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .logo {
            font-weight: 800;
            font-size: 1.8rem;
            color: #3498db;
            text-shadow: 0 0 10px rgba(52, 152, 219, 0.5);
        }
        
        .section-title {
            position: relative;
            padding-bottom: 15px;
            margin-bottom: 30px;
            text-align: center;
            color: white;
        }
        
        .section-title:after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: var(--primary);
            border-radius: 2px;
        }
        
        .login-container {
            max-width: 450px;
            margin: 50px auto;
            padding: 30px;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
        }
        
        .form-control {
            border-radius: 50px;
            padding: 12px 20px;
            border: 2px solid #ddd;
            transition: all 0.3s;
        }
        
        .form-control:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 0.25rem rgba(52, 152, 219, 0.25);
        }
        
        .dashboard-card {
            background: linear-gradient(135deg, rgba(255,255,255,0.95), rgba(236, 240, 241,0.95));
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 25px;
            height: 100%;
        }
        
        .course-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            height: 100%;
            position: relative;
        }
        
        .course-card .card-body {
            padding: 25px;
        }
        
        .course-level {
            position: absolute;
            top: 20px;
            right: 20px;
            background: var(--accent);
            color: white;
            border-radius: 50px;
            padding: 5px 15px;
            font-weight: bold;
            font-size: 0.9rem;
        }
        
        .footer {
            background: rgba(44, 62, 80, 0.95);
            color: white;
            padding: 30px 0;
            border-radius: 20px 20px 0 0;
            margin-top: 50px;
        }
        
        .contact-info {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            padding: 20px;
            margin-top: 20px;
        }
        
        .admin-panel {
            background: rgba(44, 62, 80, 0.95);
            color: white;
            min-height: 100vh;
        }
        
        .student-table {
            background: white;
            border-radius: 15px;
            overflow: hidden;
        }
        
        .student-table th {
            background: var(--primary);
            color: white;
        }
        
        .action-buttons .btn {
            margin: 2px;
            padding: 5px 10px;
        }
        
        .view-container {
            display: none;
        }
        
        .active-view {
            display: block;
            animation: fadeIn 0.5s;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .password-toggle {
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            cursor: pointer;
            color: #777;
        }
        
        .password-container {
            position: relative;
        }
        
        .progress-bar {
            height: 8px;
            border-radius: 4px;
            background: #e0e0e0;
            margin-top: 5px;
        }
        
        .progress {
            height: 100%;
            border-radius: 4px;
            transition: width 0.3s;
        }
        
        .password-strength-0 .progress {
            width: 20%;
            background: #e74c3c;
        }
        
        .password-strength-1 .progress {
            width: 40%;
            background: #e67e22;
        }
        
        .password-strength-2 .progress {
            width: 60%;
            background: #f1c40f;
        }
        
        .password-strength-3 .progress {
            width: 80%;
            background: #2ecc71;
        }
        
        .password-strength-4 .progress {
            width: 100%;
            background: #27ae60;
        }
        
        .password-feedback {
            font-size: 0.85rem;
            margin-top: 5px;
            height: 20px;
        }
        
        /* Responsive adjustments */
        @media (max-width: 768px) {
            .login-container {
                margin: 20px auto;
                padding: 20px;
            }
            
            .header h1 {
                font-size: 1.5rem;
            }
            
            .card {
                margin-bottom: 20px;
            }
        }
    </style>
</head>
<body>
    <!-- Home View -->
    <div id="homeView" class="view-container active-view">
        <div class="header">
            <div class="container">
                <div class="row align-items-center">
                    <div class="col-md-6">
                        <h1 class="logo"><i class="fas fa-laptop-code me-2"></i>Nex Gen Tech Academy Naukot</h1>
                    </div>
                    <div class="col-md-6 text-md-end">
                        <button class="btn btn-light me-2" onclick="showView('loginView')">
                            <i class="fas fa-sign-in-alt me-1"></i> Login
                        </button>
                        <button class="btn btn-accent" onclick="showView('applyView')">
                            <i class="fas fa-user-plus me-1"></i> Apply Now
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <div class="container my-5">
            <div class="row">
                <div class="col-12 text-center mb-5">
                    <h2 class="section-title">Welcome to Nex Gen Tech Academy</h2>
                    <p class="lead text-white">Empowering the next generation of technology professionals</p>
                </div>
            </div>
            
            <div class="row g-4">
                <div class="col-md-4">
                    <div class="card">
                        <div class="card-body text-center p-4">
                            <i class="fas fa-graduation-cap display-1 text-primary mb-4"></i>
                            <h3 class="card-title">Quality Education</h3>
                            <p class="card-text">Learn from industry experts with real-world experience and cutting-edge curriculum.</p>
                        </div>
                    </div>
                </div>
                
                <div class="col-md-4">
                    <div class="card">
                        <div class="card-body text-center p-4">
                            <i class="fas fa-laptop-code display-1 text-primary mb-4"></i>
                            <h3 class="card-title">Hands-on Training</h3>
                            <p class="card-text">Gain practical skills through our state-of-the-art computer labs and projects.</p>
                        </div>
                    </div>
                </div>
                
                <div class="col-md-4">
                    <div class="card">
                        <div class="card-body text-center p-4">
                            <i class="fas fa-briefcase display-1 text-primary mb-4"></i>
                            <h3 class="card-title">Career Support</h3>
                            <p class="card-text">Get career guidance, resume building, and job placement assistance.</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="container mt-5">
            <div class="contact-info">
                <div class="row">
                    <div class="col-md-6">
                        <h4><i class="fas fa-user me-2"></i> Academy Director</h4>
                        <p class="ms-4">Muhammad Sadique KK</p>
                    </div>
                    <div class="col-md-6">
                        <h4><i class="fas fa-phone me-2"></i> Contact</h4>
                        <p class="ms-4">0332-2087563, 0335-3321882</p>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="footer">
            <div class="container">
                <div class="row">
                    <div class="col-md-6">
                        <h4><i class="fas fa-map-marker-alt me-2"></i> Location</h4>
                        <p>Naukot, Sindh, Pakistan</p>
                    </div>
                    <div class="col-md-6 text-md-end">
                        <h4>Follow Us</h4>
                        <div class="social-icons mt-2">
                            <a href="#" class="text-white me-3"><i class="fab fa-facebook fa-2x"></i></a>
                            <a href="#" class="text-white me-3"><i class="fab fa-twitter fa-2x"></i></a>
                            <a href="#" class="text-white me-3"><i class="fab fa-instagram fa-2x"></i></a>
                            <a href="#" class="text-white"><i class="fab fa-linkedin fa-2x"></i></a>
                        </div>
                    </div>
                </div>
                <hr class="bg-light">
                <div class="row">
                    <div class="col-12 text-center">
                        <p>&copy; 2023 Nex Gen Tech Academy Naukot. All Rights Reserved.</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Login View -->
    <div id="loginView" class="view-container">
        <div class="header">
            <div class="container">
                <div class="row align-items-center">
                    <div class="col-md-6">
                        <h1 class="logo"><i class="fas fa-laptop-code me-2"></i>Nex Gen Tech Academy</h1>
                    </div>
                    <div class="col-md-6 text-md-end">
                        <button class="btn btn-light" onclick="showView('homeView')">
                            <i class="fas fa-arrow-left me-1"></i> Back to Home
                        </button>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="container">
            <div class="login-container">
                <div class="text-center mb-4">
                    <h3>Student Login</h3>
                    <p class="text-muted">Enter your credentials to access your dashboard</p>
                </div>
                
                <form id="loginForm">
                    <div class="mb-3">
                        <label for="loginPhone" class="form-label">Phone Number</label>
                        <input type="tel" class="form-control" id="loginPhone" placeholder="03XX-XXXXXXX" required>
                    </div>
                    
                    <div class="mb-3 password-container">
                        <label for="loginPassword" class="form-label">Password</label>
                        <input type="password" class="form-control" id="loginPassword" placeholder="Enter your password" required>
                        <span class="password-toggle" onclick="togglePassword('loginPassword')">
                            <i class="fas fa-eye"></i>
                        </span>
                    </div>
                    
                    <div class="d-grid mb-3">
                        <button type="submit" class="btn btn-primary">
                            <i class="fas fa-sign-in-alt me-1"></i> Login
                        </button>
                    </div>
                    
                    <div class="text-center">
                        <p class="mb-0">Admin? <a href="#" onclick="showAdminLogin()">Login here</a></p>
                        <p>Don't have an account? <a href="#" onclick="showView('applyView')">Apply now</a></p>
                    </div>
                </form>
            </div>
        </div>
    </div>
    
    <!-- Apply View -->
    <div id="applyView" class="view-container">
        <div class="header">
            <div class="container">
                <div class="row align-items-center">
                    <div class="col-md-6">
                        <h1 class="logo"><i class="fas fa-laptop-code me-2"></i>Nex Gen Tech Academy</h1>
                    </div>
                    <div class="col-md-6 text-md-end">
                        <button class="btn btn-light" onclick="showView('homeView')">
                            <i class="fas fa-arrow-left me-1"></i> Back to Home
                        </button>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="container my-5">
            <div class="card">
                <div class="card-header bg-primary text-white">
                    <h4 class="mb-0"><i class="fas fa-user-graduate me-2"></i> Student Application Form</h4>
                </div>
                <div class="card-body">
                    <form id="applyForm">
                        <div class="row">
                            <div class="col-md-6 mb-3">
                                <label for="studentName" class="form-label">Student Name</label>
                                <input type="text" class="form-control" id="studentName" placeholder="Enter your full name" required>
                            </div>
                            
                            <div class="col-md-6 mb-3">
                                <label for="fatherName" class="form-label">Father's Name</label>
                                <input type="text" class="form-control" id="fatherName" placeholder="Enter father's name" required>
                            </div>
                        </div>
                        
                        <div class="row">
                            <div class="col-md-6 mb-3">
                                <label for="studentPhone" class="form-label">Student Phone Number</label>
                                <input type="tel" class="form-control" id="studentPhone" placeholder="03XX-XXXXXXX" required>
                            </div>
                            
                            <div class="col-md-6 mb-3">
                                <label for="fatherPhone" class="form-label">Father's Phone Number</label>
                                <input type="tel" class="form-control" id="fatherPhone" placeholder="03XX-XXXXXXX" required>
                            </div>
                        </div>
                        
                        <div class="row">
                            <div class="col-md-6 mb-3">
                                <label for="city" class="form-label">City</label>
                                <input type="text" class="form-control" id="city" value="Naukot" readonly>
                            </div>
                            
                            <div class="col-md-3 mb-3">
                                <label for="age" class="form-label">Age</label>
                                <input type="number" class="form-control" id="age" min="10" max="30" required>
                            </div>
                            
                            <div class="col-md-3 mb-3">
                                <label for="studentClass" class="form-label">Class</label>
                                <select class="form-select" id="studentClass" required>
                                    <option value="">Select Class</option>
                                    <option value="7">Class 7</option>
                                    <option value="8">Class 8</option>
                                    <option value="9">Class 9</option>
                                    <option value="10">Class 10</option>
                                    <option value="11">Class 11</option>
                                    <option value="12">Class 12</option>
                                    <option value="other">Other</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="row">
                            <div class="col-md-6 mb-3 password-container">
                                <label for="password" class="form-label">Password</label>
                                <input type="password" class="form-control" id="password" placeholder="Create a password" required>
                                <span class="password-toggle" onclick="togglePassword('password')">
                                    <i class="fas fa-eye"></i>
                                </span>
                                <div class="progress-bar mt-2">
                                    <div class="progress" id="passwordStrengthBar"></div>
                                </div>
                                <div class="password-feedback" id="passwordFeedback"></div>
                            </div>
                            
                            <div class="col-md-6 mb-3 password-container">
                                <label for="confirmPassword" class="form-label">Confirm Password</label>
                                <input type="password" class="form-control" id="confirmPassword" placeholder="Confirm your password" required>
                                <span class="password-toggle" onclick="togglePassword('confirmPassword')">
                                    <i class="fas fa-eye"></i>
                                </span>
                                <div class="invalid-feedback" id="passwordMatchFeedback">Passwords do not match!</div>
                            </div>
                        </div>
                        
                        <div class="d-grid mt-4">
                            <button type="submit" class="btn btn-primary btn-lg">
                                <i class="fas fa-paper-plane me-2"></i> Submit Application
                            </button>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Student Dashboard View -->
    <div id="studentDashboardView" class="view-container">
        <div class="header">
            <div class="container">
                <div class="row align-items-center">
                    <div class="col-md-6">
                        <h1 class="logo"><i class="fas fa-laptop-code me-2"></i>Student Dashboard</h1>
                    </div>
                    <div class="col-md-6 text-md-end">
                        <button class="btn btn-light me-2" onclick="generateStudentPDF()">
                            <i class="fas fa-download me-1"></i> Download PDF
                        </button>
                        <button class="btn btn-accent" onclick="logout()">
                            <i class="fas fa-sign-out-alt me-1"></i> Logout
                        </button>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="container my-5">
            <div class="row mb-4">
                <div class="col-12">
                    <h3 class="section-title">Welcome, <span id="studentNameDisplay"></span></h3>
                </div>
            </div>
            
            <div class="row">
                <div class="col-md-4 mb-4">
                    <div class="dashboard-card">
                        <div class="d-flex align-items-center mb-3">
                            <div class="bg-primary p-3 rounded-circle me-3">
                                <i class="fas fa-user fa-2x text-white"></i>
                            </div>
                            <div>
                                <h5 class="mb-0">Student Profile</h5>
                                <p class="text-muted mb-0">View your details</p>
                            </div>
                        </div>
                        <div id="studentDetails">
                            <!-- Student details will be populated here -->
                        </div>
                    </div>
                </div>
                
                <div class="col-md-8 mb-4">
                    <div class="dashboard-card">
                        <div class="d-flex align-items-center mb-4">
                            <div class="bg-primary p-3 rounded-circle me-3">
                                <i class="fas fa-book fa-2x text-white"></i>
                            </div>
                            <div>
                                <h5 class="mb-0">Your Courses</h5>
                                <p class="text-muted mb-0">Explore available courses</p>
                            </div>
                        </div>
                        
                        <div class="row g-4">
                            <div class="col-md-4">
                                <div class="course-card">
                                    <span class="course-level">Beginner</span>
                                    <div class="card-body">
                                        <h5 class="card-title">FACE-1</h5>
                                        <p class="card-text">Introduction to Programming, Basic Computer Skills, Office Applications</p>
                                        <button class="btn btn-sm btn-primary">View Details</button>
                                    </div>
                                </div>
                            </div>
                            
                            <div class="col-md-4">
                                <div class="course-card">
                                    <span class="course-level">Intermediate</span>
                                    <div class="card-body">
                                        <h5 class="card-title">FACE-11</h5>
                                        <p class="card-text">Web Development, Database Management, Graphic Design Fundamentals</p>
                                        <button class="btn btn-sm btn-primary">View Details</button>
                                    </div>
                                </div>
                            </div>
                            
                            <div class="col-md-4">
                                <div class="course-card">
                                    <span class="course-level">Advanced</span>
                                    <div class="card-body">
                                        <h5 class="card-title">FACE-111</h5>
                                        <p class="card-text">Advanced Programming, Network Security, AI & Machine Learning</p>
                                        <button class="btn btn-sm btn-primary">View Details</button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="row">
                <div class="col-12">
                    <div class="dashboard-card">
                        <div class="d-flex align-items-center mb-4">
                            <div class="bg-primary p-3 rounded-circle me-3">
                                <i class="fas fa-calendar fa-2x text-white"></i>
                            </div>
                            <div>
                                <h5 class="mb-0">Class Schedule</h5>
                                <p class="text-muted mb-0">Your weekly timetable</p>
                            </div>
                        </div>
                        
                        <div class="table-responsive">
                            <table class="table table-bordered">
                                <thead class="table-primary">
                                    <tr>
                                        <th>Time</th>
                                        <th>Monday</th>
                                        <th>Tuesday</th>
                                        <th>Wednesday</th>
                                        <th>Thursday</th>
                                        <th>Friday</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr>
                                        <td>9:00 - 10:30</td>
                                        <td>Programming Basics</td>
                                        <td>Web Development</td>
                                        <td>Database Management</td>
                                        <td>Programming Basics</td>
                                        <td>Project Work</td>
                                    </tr>
                                    <tr>
                                        <td>10:45 - 12:15</td>
                                        <td>Computer Fundamentals</td>
                                        <td>Graphic Design</td>
                                        <td>Web Development</td>
                                        <td>Computer Fundamentals</td>
                                        <td>Lab Practice</td>
                                    </tr>
                                    <tr>
                                        <td>1:30 - 3:00</td>
                                        <td>Office Applications</td>
                                        <td>Programming Basics</td>
                                        <td>Office Applications</td>
                                        <td>Graphic Design</td>
                                        <td>Lab Practice</td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Admin Login View -->
    <div id="adminLoginView" class="view-container">
        <div class="header">
            <div class="container">
                <div class="row align-items-center">
                    <div class="col-md-6">
                        <h1 class="logo"><i class="fas fa-laptop-code me-2"></i>Admin Portal</h1>
                    </div>
                    <div class="col-md-6 text-md-end">
                        <button class="btn btn-light" onclick="showView('loginView')">
                            <i class="fas fa-arrow-left me-1"></i> Back to Login
                        </button>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="container">
            <div class="login-container">
                <div class="text-center mb-4">
                    <h3>Admin Login</h3>
                    <p class="text-muted">Enter admin credentials to access the dashboard</p>
                </div>
                
                <form id="adminLoginForm">
                    <div class="mb-3">
                        <label for="adminUsername" class="form-label">Username</label>
                        <input type="text" class="form-control" id="adminUsername" placeholder="Enter username" required>
                    </div>
                    
                    <div class="mb-3 password-container">
                        <label for="adminPassword" class="form-label">Password</label>
                        <input type="password" class="form-control" id="adminPassword" placeholder="Enter password" required>
                        <span class="password-toggle" onclick="togglePassword('adminPassword')">
                            <i class="fas fa-eye"></i>
                        </span>
                    </div>
                    
                    <div class="d-grid mb-3">
                        <button type="submit" class="btn btn-primary">
                            <i class="fas fa-sign-in-alt me-1"></i> Login
                        </button>
                    </div>
                </form>
            </div>
        </div>
    </div>
    
    <!-- Admin Dashboard View -->
    <div id="adminDashboardView" class="view-container admin-panel">
        <div class="header">
            <div class="container">
                <div class="row align-items-center">
                    <div class="col-md-6">
                        <h1 class="logo"><i class="fas fa-laptop-code me-2"></i>Admin Dashboard</h1>
                    </div>
                    <div class="col-md-6 text-md-end">
                        <button class="btn btn-light me-2" onclick="showView('adminLoginView')">
                            <i class="fas fa-arrow-left me-1"></i> Back
                        </button>
                        <button class="btn btn-accent" onclick="logout()">
                            <i class="fas fa-sign-out-alt me-1"></i> Logout
                        </button>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="container my-5">
            <div class="row mb-4">
                <div class="col-12">
                    <h3 class="section-title">Student Management</h3>
                </div>
            </div>
            
            <div class="row">
                <div class="col-12">
                    <div class="card">
                        <div class="card-body">
                            <div class="d-flex justify-content-between align-items-center mb-4">
                                <h5 class="card-title mb-0">All Students</h5>
                                <button class="btn btn-sm btn-primary" onclick="addNewStudent()">
                                    <i class="fas fa-plus me-1"></i> Add New Student
                                </button>
                            </div>
                            
                            <div class="table-responsive">
                                <table class="table table-hover student-table">
                                    <thead>
                                        <tr>
                                            <th>ID</th>
                                            <th>Name</th>
                                            <th>Phone</th>
                                            <th>Class</th>
                                            <th>Age</th>
                                            <th>City</th>
                                            <th>Actions</th>
                                        </tr>
                                    </thead>
                                    <tbody id="studentsTableBody">
                                        <!-- Student data will be populated here -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Modals -->
    <div class="modal fade" id="studentModal" tabindex="-1">
        <div class="modal-dialog modal-lg">
            <div class="modal-content">
                <div class="modal-header bg-primary text-white">
                    <h5 class="modal-title" id="modalTitle">Edit Student</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <form id="studentForm">
                        <input type="hidden" id="studentId">
                        <div class="row">
                            <div class="col-md-6 mb-3">
                                <label for="modalStudentName" class="form-label">Student Name</label>
                                <input type="text" class="form-control" id="modalStudentName" required>
                            </div>
                            
                            <div class="col-md-6 mb-3">
                                <label for="modalFatherName" class="form-label">Father's Name</label>
                                <input type="text" class="form-control" id="modalFatherName" required>
                            </div>
                        </div>
                        
                        <div class="row">
                            <div class="col-md-6 mb-3">
                                <label for="modalStudentPhone" class="form-label">Student Phone</label>
                                <input type="tel" class="form-control" id="modalStudentPhone" required>
                            </div>
                            
                            <div class="col-md-6 mb-3">
                                <label for="modalFatherPhone" class="form-label">Father's Phone</label>
                                <input type="tel" class="form-control" id="modalFatherPhone" required>
                            </div>
                        </div>
                        
                        <div class="row">
                            <div class="col-md-6 mb-3">
                                <label for="modalCity" class="form-label">City</label>
                                <input type="text" class="form-control" id="modalCity" value="Naukot" readonly>
                            </div>
                            
                            <div class="col-md-3 mb-3">
                                <label for="modalAge" class="form-label">Age</label>
                                <input type="number" class="form-control" id="modalAge" min="10" max="30" required>
                            </div>
                            
                            <div class="col-md-3 mb-3">
                                <label for="modalClass" class="form-label">Class</label>
                                <select class="form-select" id="modalClass" required>
                                    <option value="7">Class 7</option>
                                    <option value="8">Class 8</option>
                                    <option value="9">Class 9</option>
                                    <option value="10">Class 10</option>
                                    <option value="11">Class 11</option>
                                    <option value="12">Class 12</option>
                                    <option value="other">Other</option>
                                </select>
                            </div>
                        </div>
                    </form>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                    <button type="button" class="btn btn-primary" onclick="saveStudent()">Save Changes</button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Bootstrap & jQuery -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    
    <script>
        // Initialize the app
        document.addEventListener('DOMContentLoaded', function() {
            // Initialize modals
            const studentModal = new bootstrap.Modal(document.getElementById('studentModal'));
            
            // Setup form validation
            setupFormValidation();
            
            // Check if we have a stored student session
            if (localStorage.getItem('currentStudent')) {
                showView('studentDashboardView');
                displayStudentDashboard();
            }
            
            // Check if we have a stored admin session
            if (localStorage.getItem('adminLoggedIn')) {
                showView('adminDashboardView');
                loadStudents();
            }
        });
        
        // View management
        function showView(viewId) {
            // Hide all views
            document.querySelectorAll('.view-container').forEach(view => {
                view.classList.remove('active-view');
            });
            
            // Show the requested view
            document.getElementById(viewId).classList.add('active-view');
            
            // Special actions for specific views
            if (viewId === 'studentDashboardView') {
                displayStudentDashboard();
            } else if (viewId === 'adminDashboardView') {
                loadStudents();
            }
        }
        
        // Password visibility toggle
        function togglePassword(inputId) {
            const input = document.getElementById(inputId);
            const icon = input.nextElementSibling.querySelector('i');
            
            if (input.type === 'password') {
                input.type = 'text';
                icon.classList.remove('fa-eye');
                icon.classList.add('fa-eye-slash');
            } else {
                input.type = 'password';
                icon.classList.remove('fa-eye-slash');
                icon.classList.add('fa-eye');
            }
        }
        
        // Show admin login
        function showAdminLogin() {
            showView('adminLoginView');
        }
        
        // Setup form validation
        function setupFormValidation() {
            // Password strength checker
            document.getElementById('password').addEventListener('input', function() {
                checkPasswordStrength(this.value);
            });
            
            // Password match checker
            document.getElementById('confirmPassword').addEventListener('input', function() {
                const password = document.getElementById('password').value;
                const confirmPassword = this.value;
                
                if (password !== confirmPassword) {
                    this.classList.add('is-invalid');
                    document.getElementById('passwordMatchFeedback').style.display = 'block';
                } else {
                    this.classList.remove('is-invalid');
                    document.getElementById('passwordMatchFeedback').style.display = 'none';
                }
            });
            
            // Login form submission
            document.getElementById('loginForm').addEventListener('submit', function(e) {
                e.preventDefault();
                studentLogin();
            });
            
            // Apply form submission
            document.getElementById('applyForm').addEventListener('submit', function(e) {
                e.preventDefault();
                submitApplication();
            });
            
            // Admin login form submission
            document.getElementById('adminLoginForm').addEventListener('submit', function(e) {
                e.preventDefault();
                adminLogin();
            });
        }
        
        // Password strength indicator
        function checkPasswordStrength(password) {
            let strength = 0;
            const feedback = document.getElementById('passwordFeedback');
            const bar = document.getElementById('passwordStrengthBar');
            const container = document.getElementById('password').parentElement;
            
            // Reset classes
            container.className = 'password-container';
            
            // Check password length
            if (password.length >= 8) strength++;
            if (password.length >= 12) strength++;
            
            // Check for mixed case
            if (/[a-z]/.test(password) && /[A-Z]/.test(password)) strength++;
            
            // Check for numbers
            if (/\d/.test(password)) strength++;
            
            // Check for special characters
            if (/[^A-Za-z0-9]/.test(password)) strength++;
            
            // Update UI based on strength
            container.classList.add(`password-strength-${Math.min(strength, 4)}`);
            
            // Set feedback text
            switch(strength) {
                case 0:
                case 1:
                    feedback.textContent = 'Weak password';
                    feedback.style.color = '#e74c3c';
                    break;
                case 2:
                    feedback.textContent = 'Moderate password';
                    feedback.style.color = '#e67e22';
                    break;
                case 3:
                    feedback.textContent = 'Good password';
                    feedback.style.color = '#f1c40f';
                    break;
                case 4:
                case 5:
                    feedback.textContent = 'Strong password';
                    feedback.style.color = '#27ae60';
                    break;
            }
        }
        
        // Student login function
        function studentLogin() {
            const phone = document.getElementById('loginPhone').value;
            const password = document.getElementById('loginPassword').value;
            
            // Retrieve students from localStorage
            const students = JSON.parse(localStorage.getItem('students') || '[]');
            
            // Find student with matching phone and password
            const student = students.find(s => s.phone === phone && s.password === password);
            
            if (student) {
                // Store current student in session
                localStorage.setItem('currentStudent', JSON.stringify(student));
                showView('studentDashboardView');
            } else {
                alert('Invalid phone number or password. Please try again.');
            }
        }
        
        // Submit application
        function submitApplication() {
            // Get form values
            const student = {
                id: Date.now(), // Unique ID based on timestamp
                name: document.getElementById('studentName').value,
                fatherName: document.getElementById('fatherName').value,
                phone: document.getElementById('studentPhone').value,
                fatherPhone: document.getElementById('fatherPhone').value,
                city: document.getElementById('city').value,
                age: document.getElementById('age').value,
                class: document.getElementById('studentClass').value,
                password: document.getElementById('password').value,
                joined: new Date().toISOString().split('T')[0] // Current date
            };
            
            // Retrieve existing students or initialize empty array
            const students = JSON.parse(localStorage.getItem('students') || '[]');
            
            // Add new student
            students.push(student);
            
            // Save back to localStorage
            localStorage.setItem('students', JSON.stringify(students));
            
            // Store current student in session
            localStorage.setItem('currentStudent', JSON.stringify(student));
            
            // Show success message
            alert('Application submitted successfully! You are now logged in.');
            
            // Redirect to dashboard
            showView('studentDashboardView');
        }
        
        // Display student dashboard
        function displayStudentDashboard() {
            const student = JSON.parse(localStorage.getItem('currentStudent'));
            
            if (!student) {
                showView('loginView');
                return;
            }
            
            // Display student name
            document.getElementById('studentNameDisplay').textContent = student.name;
            
            // Display student details
            const detailsContainer = document.getElementById('studentDetails');
            detailsContainer.innerHTML = `
                <div class="mb-2"><strong>Student ID:</strong> NEX-${student.id.toString().slice(-5)}</div>
                <div class="mb-2"><strong>Name:</strong> ${student.name}</div>
                <div class="mb-2"><strong>Father's Name:</strong> ${student.fatherName}</div>
                <div class="mb-2"><strong>Phone:</strong> ${student.phone}</div>
                <div class="mb-2"><strong>Father's Phone:</strong> ${student.fatherPhone}</div>
                <div class="mb-2"><strong>City:</strong> ${student.city}</div>
                <div class="mb-2"><strong>Age:</strong> ${student.age}</div>
                <div class="mb-2"><strong>Class:</strong> ${student.class}</div>
                <div class="mb-2"><strong>Joined:</strong> ${student.joined}</div>
            `;
        }
        
        // Generate student PDF
        function generateStudentPDF() {
            const student = JSON.parse(localStorage.getItem('currentStudent'));
            
            if (!student) return;
            
            // Use jsPDF to create a PDF
            const { jsPDF } = window.jspdf;
            const doc = new jsPDF();
            
            // Add academy logo and title
            doc.setFontSize(20);
            doc.setTextColor(52, 152, 219);
            doc.text('Nex Gen Tech Academy Naukot', 105, 20, null, null, 'center');
            doc.setFontSize(16);
            doc.setTextColor(44, 62, 80);
            doc.text('Student Details', 105, 30, null, null, 'center');
            
            // Add student information
            doc.setFontSize(12);
            doc.setTextColor(0, 0, 0);
            doc.text(`Student ID: NEX-${student.id.toString().slice(-5)}`, 20, 50);
            doc.text(`Name: ${student.name}`, 20, 60);
            doc.text(`Father's Name: ${student.fatherName}`, 20, 70);
            doc.text(`Phone: ${student.phone}`, 20, 80);
            doc.text(`Father's Phone: ${student.fatherPhone}`, 20, 90);
            doc.text(`City: ${student.city}`, 20, 100);
            doc.text(`Age: ${student.age}`, 20, 110);
            doc.text(`Class: ${student.class}`, 20, 120);
            doc.text(`Joined: ${student.joined}`, 20, 130);
            
            // Add footer
            doc.setFontSize(10);
            doc.setTextColor(100, 100, 100);
            doc.text('Generated by Nex Gen Tech Academy Student Portal', 105, 280, null, null, 'center');
            
            // Save the PDF
            doc.save(`nexgen_student_${student.id}.pdf`);
        }
        
        // Admin login
        function adminLogin() {
            const username = document.getElementById('adminUsername').value;
            const password = document.getElementById('adminPassword').value;
            
            if (username === 'admin' && password === 'admin123') {
                // Set admin session
                localStorage.setItem('adminLoggedIn', 'true');
                showView('adminDashboardView');
            } else {
                alert('Invalid admin credentials. Please try again.');
            }
        }
        
        // Load students for admin
        function loadStudents() {
            const students = JSON.parse(localStorage.getItem('students') || '[]');
            const tableBody = document.getElementById('studentsTableBody');
            
            // Clear existing table rows
            tableBody.innerHTML = '';
            
            // Add each student to the table
            students.forEach(student => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>NEX-${student.id.toString().slice(-5)}</td>
                    <td>${student.name}</td>
                    <td>${student.phone}</td>
                    <td>${student.class}</td>
                    <td>${student.age}</td>
                    <td>${student.city}</td>
                    <td class="action-buttons">
                        <button class="btn btn-sm btn-primary" onclick="viewStudent(${student.id})">
                            <i class="fas fa-eye"></i>
                        </button>
                        <button class="btn btn-sm btn-warning" onclick="editStudent(${student.id})">
                            <i class="fas fa-edit"></i>
                        </button>
                        <button class="btn btn-sm btn-danger" onclick="deleteStudent(${student.id})">
                            <i class="fas fa-trash"></i>
                        </button>
                    </td>
                `;
                tableBody.appendChild(row);
            });
        }
        
        // Add new student from admin panel
        function addNewStudent() {
            // Reset form
            document.getElementById('studentForm').reset();
            document.getElementById('modalTitle').textContent = 'Add New Student';
            document.getElementById('studentId').value = '';
            
            // Show modal
            const studentModal = new bootstrap.Modal(document.getElementById('studentModal'));
            studentModal.show();
        }
        
        // Edit student
        function editStudent(studentId) {
            const students = JSON.parse(localStorage.getItem('students') || '[]');
            const student = students.find(s => s.id === studentId);
            
            if (student) {
                // Populate form
                document.getElementById('studentId').value = student.id;
                document.getElementById('modalStudentName').value = student.name;
                document.getElementById('modalFatherName').value = student.fatherName;
                document.getElementById('modalStudentPhone').value = student.phone;
                document.getElementById('modalFatherPhone').value = student.fatherPhone;
                document.getElementById('modalAge').value = student.age;
                document.getElementById('modalClass').value = student.class;
                
                // Set modal title
                document.getElementById('modalTitle').textContent = 'Edit Student';
                
                // Show modal
                const studentModal = new bootstrap.Modal(document.getElementById('studentModal'));
                studentModal.show();
            }
        }
        
        // View student details
        function viewStudent(studentId) {
            const students = JSON.parse(localStorage.getItem('students') || '[]');
            const student = students.find(s => s.id === studentId);
            
            if (student) {
                // For simplicity, we'll just show an alert with details
                alert(`Student Details:
Name: ${student.name}
Father's Name: ${student.fatherName}
Phone: ${student.phone}
Father's Phone: ${student.fatherPhone}
City: ${student.city}
Age: ${student.age}
Class: ${student.class}
Joined: ${student.joined}`);
            }
        }
        
        // Delete student
        function deleteStudent(studentId) {
            if (confirm('Are you sure you want to delete this student?')) {
                let students = JSON.parse(localStorage.getItem('students') || '[]');
                
                // Filter out the student to delete
                students = students.filter(s => s.id !== studentId);
                
                // Save back to localStorage
                localStorage.setItem('students', JSON.stringify(students));
                
                // Reload the table
                loadStudents();
            }
        }
        
        // Save student (from modal)
        function saveStudent() {
            const studentId = document.getElementById('studentId').value;
            const students = JSON.parse(localStorage.getItem('students') || '[]');
            
            let student;
            if (studentId) {
                // Existing student
                student = students.find(s => s.id === parseInt(studentId));
            } else {
                // New student
                student = {
                    id: Date.now(),
                    password: 'password123', // Default password
                    joined: new Date().toISOString().split('T')[0] // Current date
                };
                students.push(student);
            }
            
            // Update student data
            student.name = document.getElementById('modalStudentName').value;
            student.fatherName = document.getElementById('modalFatherName').value;
            student.phone = document.getElementById('modalStudentPhone').value;
            student.fatherPhone = document.getElementById('modalFatherPhone').value;
            student.age = document.getElementById('modalAge').value;
            student.class = document.getElementById('modalClass').value;
            student.city = 'Naukot';
            
            // Save back to localStorage
            localStorage.setItem('students', JSON.stringify(students));
            
            // Close modal
            const studentModal = bootstrap.Modal.getInstance(document.getElementById('studentModal'));
            studentModal.hide();
            
            // Reload the table
            loadStudents();
        }
        
        // Logout function
        function logout() {
            // Remove session data
            localStorage.removeItem('currentStudent');
            localStorage.removeItem('adminLoggedIn');
            
            // Return to home view
            showView('homeView');
        }
    </script>
</body>
</html>
