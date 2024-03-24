<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Grade Generator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <ul>
            <li><a href="#home">HOME</a></li>
            <li><a href="#home">SUBJECTS</a></li>
            <li><a href="#home">CONTACT</a></li>
            <li><a href="#home">HELP</a></li>                       
        </ul>
        <hr>
    </header>
    <div id="about">
        
        <p>This is a student grade generator</p>
        <p>As you can see, the below section prompts you to enter your marks and the program will auto calculate your grade</p>
        <p>Grading ranges from <strong><em>A to E</em></strong></p>
        <p>You are allowed to input marks <strong>from 0 to 100</strong> </em></p>
        
            <div id="inputField">
                <h2>Come On..</h2>
                <h1>Lets Do This!</h1>
                <input id='input' onchange="handleMarksChange()" type="number" placeholder="Enter your marks" />
                <button onclick="displayGrade()">see grade</button> 
                <p id="grade"></p>
            </div>
    </div>

    <script src="index.js"></script>
</body>
</html>

index.js code:

function handleMarksChange(event) {
  //confirm if its a number, if not in a range of 0-9
  if (!/[0-9]/.test(event.key)) {
    event.preventDefault(); //will not pick the value, picking the value is our default
  } else {
    marks.value = Number(event.target.value);
  }
}

function displayGrade() {
  //this checks if there is an input
  if (!isNaN(marks.value)) {
    const grade = getGrade(marks.value);
    document.getElementById("grade").innerText = `Your grade is ${grade}`;
  } else {
    alert("kindly enter a valid number");
  } //this code gets the marks.value inputted, then proceeds to call another function getGrade which converts the value into a grade.
  document.getElementById("input").value = "";
}
function getGrade(marks) {
  switch (true) {
    case marks > 79:
      return "A";
      break;
    case marks >= 60 && marks <= 79:
      return "B";
      break;
    case marks >= 49 && marks <= 59:
      return "C";
      break;
    case marks >= 40 && marks < 50:
      return "D";
      break;
    case marks < 40:
      return "E";
      break;
    default:
      return "E";
  }
}

const marks = document.getElementById("input");
marks.addEventListener("keydown", handleMarksChange);
