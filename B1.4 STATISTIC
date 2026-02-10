<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>B1.4 Statistics – Exam Simulation</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body{
    margin:0;
    font-family:Arial, Helvetica, sans-serif;
    background:#f4f6f8;
    color:#333;
}
.container{
    max-width:900px;
    margin:auto;
    padding:20px;
}
h1,h2{
    text-align:center;
}
.card{
    background:#ffffff;
    padding:20px;
    border-radius:8px;
    margin-bottom:20px;
    box-shadow:0 2px 6px rgba(0,0,0,0.08);
}
.question{
    margin-bottom:20px;
}
.options label{
    display:block;
    padding:6px;
    cursor:pointer;
}
.correct{
    background:#d1fae5;
}
.wrong{
    background:#fee2e2;
}
button{
    padding:10px 18px;
    border:none;
    border-radius:5px;
    background:#2563eb;
    color:white;
    cursor:pointer;
    font-size:14px;
}
button:disabled{
    background:#9ca3af;
}
input[type="text"]{
    width:100%;
    padding:8px;
    margin-top:8px;
    margin-bottom:10px;
}
table{
    width:100%;
    border-collapse:collapse;
}
th,td{
    border:1px solid #ddd;
    padding:8px;
    text-align:center;
}
th{
    background:#e5e7eb;
}
</style>
</head>

<body>
<div class="container">

<h1>B1.4 Statistics</h1>
<h2>Interactive Exam Simulation</h2>

<div class="card">
<label><strong>Candidate Name (Required)</strong></label>
<input type="text" id="studentName" placeholder="Enter your full name">
<button onclick="startExam()">Start Exam</button>
</div>

<form id="exam" style="display:none">

<div class="card" id="questions"></div>

<div class="card" style="text-align:center">
<button type="button" onclick="submitExam()">Submit Exam</button>
</div>

</form>

<div class="card" id="result" style="display:none"></div>

<div class="card" id="history">
<h2>Score History (Local Storage)</h2>
<table>
<thead>
<tr>
<th>Name</th>
<th>Score</th>
<th>Date</th>
</tr>
</thead>
<tbody id="historyBody"></tbody>
</table>
</div>

</div>

<script>
const questions = [
{
q:"Which statement best describes a deterministic phenomenon?",
o:["Outcome cannot be predicted","Outcome shows long-term regularity","Outcome can be perfectly predicted using a mathematical model","Outcome depends on probability theory"],
a:2,
e:"Deterministic phenomena allow perfect prediction if initial conditions are known."
},
{
q:"A random phenomenon is characterized by:",
o:["Predictable outcome","No long-run regularity","Unpredictable outcome with long-run statistical regularity","Only one possible outcome"],
a:2,
e:"Random phenomena are unpredictable per trial but show statistical regularity over many trials."
},
{
q:"Which of the following is a haphazard phenomenon?",
o:["Coin toss","Rolling a fair die","Phenomenon with no statistical regularity","Normal distribution"],
a:2,
e:"Haphazard phenomena do not exhibit long-run statistical regularity."
},
{
q:"The sample space S is defined as:",
o:["Any event","A subset of outcomes","All possible outcomes of an experiment","Only successful outcomes"],
a:2,
e:"Sample space contains all possible outcomes."
},
{
q:"An event E occurs when:",
o:["The experiment ends","Outcome lies outside S","Outcome lies in E","Probability equals 1"],
a:2,
e:"An event occurs if the observed outcome belongs to that event."
},
{
q:"Which event never occurs?",
o:["Entire event","Sample space","Null event","Union event"],
a:2,
e:"The null (empty) event contains no outcomes."
},
{
q:"If A and B are mutually exclusive, then:",
o:["A ∩ B ≠ ∅","They can occur together","A ∩ B = ∅","P(A∪B)=P(A)−P(B)"],
a:2,
e:"Mutually exclusive events have no common outcomes."
},
{
q:"Which operation corresponds to the word 'AND'?",
o:["Union","Intersection","Complement","Sample space"],
a:1,
e:"'And' implies intersection of events."
},
{
q:"Which operation corresponds to the word 'OR'?",
o:["Complement","Intersection","Union","Null event"],
a:2,
e:"'Or' implies union of events."
},
{
q:"Classical probability applies only when:",
o:["Outcomes are infinite","Outcomes are equally likely and finite","Events overlap","Distribution is normal"],
a:1,
e:"Classical probability requires finite and equiprobable outcomes."
},
{
q:"The probability of the complement of A is:",
o:["P(A)","1 + P(A)","1 − P(A)","P(A∪B)"],
a:2,
e:"Complement rule: P(Ā)=1−P(A)."
},
{
q:"A random variable is:",
o:["An event","A probability","A function assigning numbers to outcomes","A sample space"],
a:2,
e:"Random variables map outcomes to numerical values."
},
{
q:"Which is a discrete random variable?",
o:["Depth","Time","Number of errors","Length"],
a:2,
e:"Discrete variables are countable."
},
{
q:"Which is a continuous random variable?",
o:["Number of calls","People in line","Time","Mistakes per page"],
a:2,
e:"Continuous variables vary on a continuous scale."
},
{
q:"The arithmetic mean is defined as:",
o:["Middle value","Most frequent value","Sum of values divided by number of values","Maximum minus minimum"],
a:2,
e:"Mean = Σx / n."
},
{
q:"Variance measures:",
o:["Central tendency","Spread of data","Correlation strength","Probability"],
a:1,
e:"Variance measures dispersion around the mean."
},
{
q:"Standard deviation is:",
o:["Variance squared","Square root of variance","Mean deviation","Range"],
a:1,
e:"Standard deviation is the square root of variance."
},
{
q:"Skewness measures:",
o:["Spread","Symmetry of distribution","Central value","Sample size"],
a:1,
e:"Skewness measures asymmetry of data."
},
{
q:"Covariance indicates:",
o:["Strength only","Direction only","Direction of relationship","Exact correlation"],
a:2,
e:"Covariance shows whether variables move together or inversely."
},
{
q:"A negative covariance means:",
o:["No relationship","Direct relationship","Inverse relationship","Perfect correlation"],
a:2,
e:"Negative covariance indicates inverse relationship."
},
{
q:"Correlation differs from covariance because it:",
o:["Has units","Is unbounded","Is normalized","Cannot be negative"],
a:2,
e:"Correlation is standardized and unitless."
},
{
q:"Correlation coefficient range is:",
o:["0 to 1","−∞ to +∞","−1 to +1","0 to 100"],
a:2,
e:"Correlation ranges from −1 to +1."
},
{
q:"Normal distribution is defined by:",
o:["Mode and range","Mean and variance","Mean and standard deviation","Median and skewness"],
a:2,
e:"Normal distribution depends on μ and σ."
},
{
q:"Changing σ in a normal distribution affects:",
o:["Center position","Skewness","Spread of curve","Total probability"],
a:2,
e:"Standard deviation controls spread."
},
{
q:"Z-score is calculated as:",
o:["X/σ","(X−μ)/σ","μ/σ","σ/(X−μ)"],
a:1,
e:"Z = (X − μ) / σ."
},
{
q:"Approximately what percentage of data lies within ±2σ?",
o:["68%","95%","99.7%","50%"],
a:1,
e:"Empirical rule: ±2σ ≈ 95%."
}
];

function startExam(){
    const name=document.getElementById("studentName").value.trim();
    if(name===""){alert("Name is required.");return;}
    document.getElementById("exam").style.display="block";
    loadQuestions();
}

function loadQuestions(){
    const qDiv=document.getElementById("questions");
    qDiv.innerHTML="";
    questions.forEach((q,i)=>{
        let html=`<div class="question"><p><strong>${i+1}. ${q.q}</strong></p><div class="options">`;
        q.o.forEach((opt,j)=>{
            html+=`
            <label>
            <input type="radio" name="q${i}" value="${j}"> ${String.fromCharCode(65+j)}. ${opt}
            </label>`;
        });
        html+=`</div></div>`;
        qDiv.innerHTML+=html;
    });
}

function submitExam(){
    let score=0;
    const total=questions.length;
    questions.forEach((q,i)=>{
        const radios=document.getElementsByName(`q${i}`);
        radios.forEach(r=>{
            if(r.checked){
                if(parseInt(r.value)===q.a){
                    score++;
                    r.parentElement.classList.add("correct");
                }else{
                    r.parentElement.classList.add("wrong");
                }
            }
            if(parseInt(r.value)===q.a){
                r.parentElement.classList.add("correct");
            }
        });
    });
    const finalScore=Math.round((score/total)*100);
    const resultDiv=document.getElementById("result");
    resultDiv.style.display="block";
    resultDiv.innerHTML=`<h2>Result</h2>
    <p><strong>Score:</strong> ${finalScore}/100</p>
    <p><strong>Explanation:</strong></p>
    <ul>${questions.map(q=>`<li>${q.e}</li>`).join("")}</ul>
    <button onclick="saveScore(${finalScore})">Save Score</button>`;
}

function saveScore(score){
    const name=document.getElementById("studentName").value;
    const data=JSON.parse(localStorage.getItem("stats_scores")||"[]");
    data.push({name,score,date:new Date().toLocaleString()});
    localStorage.setItem("stats_scores",JSON.stringify(data));
    loadHistory();
}

function loadHistory(){
    const body=document.getElementById("historyBody");
    body.innerHTML="";
    const data=JSON.parse(localStorage.getItem("stats_scores")||"[]");
    data.forEach(d=>{
        body.innerHTML+=`<tr><td>${d.name}</td><td>${d.score}</td><td>${d.date}</td></tr>`;
    });
}
loadHistory();
</script>

</body>
</html>
