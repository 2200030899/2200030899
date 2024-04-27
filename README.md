<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Student Grievance System</title>
<style>
  body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f2f2f2;
  }
  .container {
    max-width: 600px;
    margin: 50px auto;
    text-align: center;
    background-color: #ffffff;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
  }
  h2 {
    font-size: 36px;
    color: #333333;
    margin-bottom: 30px;
  }
  input[type="text"],
  input[type="password"],
  textarea {
    width: calc(100% - 20px);
    padding: 12px;
    margin: 10px 0;
    border: 1px solid #cccccc;
    border-radius: 5px;
    box-sizing: border-box;
    font-size: 18px;
  }
  button {
    padding: 12px 24px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 18px;
    transition: background-color 0.3s;
  }
  button:hover {
    background-color: #45a049;
  }
  #successMessage {
    background-color: #4CAF50;
    color: white;
    padding: 20px;
    border-radius: 10px;
    margin-top: 20px;
    font-size: 24px;
  }
</style>
</head>
<body>

<div class="container" id="loginContainer">
  <h2>Login Page</h2>
  <form id="loginForm">
    <input type="text" placeholder="Username" id="username">
    <br>
    <input type="password" placeholder="Password" id="password">
    <br>
    <button type="submit">Login</button>
  </form>
</div>

<div class="container options" id="grievanceOptions" style="display: none;">
  <h2>Select Option</h2>
  <button onclick="showGrievanceOptions('cc')">Submit Grievance to CC</button>
  <button onclick="showGrievanceOptions('hod')">Submit Grievance to HOD</button>
  <button onclick="showGrievanceOptions('dean')">Submit Grievance to Dean</button>
</div>

<div class="container options" id="ccGrievance" style="display: none;">
  <h2>Grievance to CC</h2>
  <form id="ccGrievanceForm" onsubmit="submitGrievance('cc'); return false;">
    <input type="text" placeholder="Subject" id="ccSubject">
    <br>
    <textarea placeholder="Explanation" id="ccExplanation"></textarea>
    <br>
    <button type="submit">Submit Grievance</button>
  </form>
</div>

<div class="container options" id="hodGrievance" style="display: none;">
  <h2>Grievance to HOD</h2>
  <form id="hodGrievanceForm" onsubmit="submitGrievance('hod'); return false;">
    <input type="text" placeholder="Subject" id="hodSubject">
    <br>
    <textarea placeholder="Explanation" id="hodExplanation"></textarea>
    <br>
    <button type="submit">Submit Grievance</button>
  </form>
</div>

<div class="container options" id="deanGrievance" style="display: none;">
  <h2>Grievance to Dean</h2>
  <form id="deanGrievanceForm" onsubmit="submitGrievance('dean'); return false;">
    <input type="text" placeholder="Subject" id="deanSubject">
    <br>
    <textarea placeholder="Explanation" id="deanExplanation"></textarea>
    <br>
    <button type="submit">Submit Grievance</button>
  </form>
</div>

<div class="container" id="successMessage" style="display: none;">
  <h2>Grievance Successfully Submitted</h2>
</div>

<script>
  document.getElementById("loginForm").addEventListener("submit", function(event) {
    event.preventDefault();
    document.getElementById("loginContainer").style.display = "none";
    document.getElementById("grievanceOptions").style.display = "block";
  });

  function showGrievanceOptions(option) {
    document.getElementById("grievanceOptions").style.display = "none";
    if (option === 'cc') {
      document.getElementById("ccGrievance").style.display = "block";
    } else if (option === 'hod') {
      document.getElementById("hodGrievance").style.display = "block";
    } else if (option === 'dean') {
      document.getElementById("deanGrievance").style.display = "block";
    }
  }

  function submitGrievance(option) {
    var successMessage = document.getElementById("successMessage");
    if (option === 'cc') {
      var ccSubject = document.getElementById("ccSubject").value;
      var ccExplanation = document.getElementById("ccExplanation").value;
      if (ccSubject && ccExplanation) {
        successMessage.style.display = "block";
        document.getElementById("ccGrievance").style.display = "none";
      } else {
        alert("Please fill in all fields");
      }
    } else if (option === 'hod') {
      var hodSubject = document.getElementById("hodSubject").value;
      var hodExplanation = document.getElementById("hodExplanation").value;
      if (hodSubject && hodExplanation) {
        successMessage.style.display = "block";
        document.getElementById("hodGrievance").style.display = "none";
      } else {
        alert("Please fill in all fields");
      }
    } else if (option === 'dean') {
      var deanSubject = document.getElementById("deanSubject").value;
      var deanExplanation = document.getElementById("deanExplanation").value;
      if (deanSubject && deanExplanation) {
        successMessage.style.display = "block";
        document.getElementById("deanGrievance").style.display = "none";
      } else {
        alert("Please fill in all fields");
      }
    }
  }
</script>

</body>
</html>
