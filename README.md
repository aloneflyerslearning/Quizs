<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>गणित प्रश्नोत्तरी (कक्षा 10)</title>
    <style>
         body {
            font-family: 'Arial', sans-serif;
            text-align: center;
            margin: 40px;
            background-color: #f9f9f9;
            color: #333;
            line-height: 1.6; /* Improved line spacing */
        }

        .container {
            background-color: white;
            border-radius: 12px;
            padding: 30px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.15); /* More prominent shadow */
            max-width: 700px;
            margin: 0 auto;
            border: 1px solid #e1e1e1; /* Light border */
        }

        h1, h2 {
            color: #2c3e50;
            margin-bottom: 20px; /* Spacing below headings */
        }

        #name-form, #quiz-container, #results-container {
            margin-top: 25px;
            padding: 15px;
            border-radius: 8px;
            border: 1px solid #ddd;
            background-color: #fefefe; /* Light background */
        }

       label {
           display: block;
           margin-bottom: 8px;
           font-weight: bold;
           color: #555; /* Darker label color */
        }

        input[type="text"] {
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 6px;
            width: calc(100% - 22px); /* Adjusted width */
            box-sizing: border-box;
        }

        button {
            padding: 12px 25px;
             background-color: #3498db; /* A nicer blue */
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            transition: background-color 0.3s;
            font-size: 1rem;
        }

        button:hover {
            background-color: #2980b9; /* Darker hover blue */
        }

        #options button {
             margin: 8px 0;
           display: block;
             width: calc(100% - 22px);
        }
           #scoreDisplay{
          margin-top:20px;
          font-weight:bold;
           font-size: 1.2rem;
         }
        #all-results h3 {
          color: #2c3e50; /* Consistent heading color */
          margin-bottom: 15px;
          border-bottom: 1px solid #eee; /* Underline effect */
          padding-bottom: 5px;
      }
       #all-results p{
         background-color: #f0f0f0;
         padding:10px;
          margin-bottom:5px;
         border-radius: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>कक्षा 10 गणित प्रश्नोत्तरी</h1>
        <div id="name-form">
            <label for="userName">अपना नाम दर्ज करें:</label>
            <input type="text" id="userName" required placeholder="यहाँ अपना नाम लिखें">
            <button onclick="startQuiz()">प्रारंभ करें</button>
        </div>
        <div id="quiz-container" style="display:none;">
            <h2 id="question-number"></h2>
            <p id="question-text"></p>
            <div id="options"></div>
             <button onclick="nextQuestion()">अगला प्रश्न</button>
            <p id = "scoreDisplay"></p>
        </div>
        <div id="results-container" style="display:none;">
            <h2>परिणाम</h2>
            <p id="user-result"></p>
            <div id="all-results"></div>

        </div>
    </div>

    <script>
         const questions = [
    {
        question: "1. वास्तविक संख्याएँ क्या होती हैं?",
        options: ["केवल परिमेय संख्याएँ", "केवल अपरिमेय संख्याएँ", "परिमेय और अपरिमेय दोनों संख्याएँ", "कोई नहीं"],
        answer: 2
    },
    {
        question: "2. यदि दो बहुपद p(x) और q(x) में q(x) का घात p(x) के घात से अधिक हो, तो p(x)/q(x) क्या होगा?",
        options: ["एक बहुपद", "एक अचर", "एक भिन्नात्मक बहुपद", "परिभाषित नहीं"],
        answer: 3
    },
    {
        question: "3. एक द्विघात समीकरण ax² + bx + c = 0 में विविक्तकर का सूत्र क्या है?",
        options: ["b² - 4ac", "b² + 4ac", "a² - 4bc", "a² + 4bc"],
        answer: 0
    },
      {
        question: "4. यदि एक समांतर श्रेणी का पहला पद 'a' और सार्व अंतर 'd' हो, तो nवां पद ज्ञात करने का सूत्र क्या है?",
        options: ["an = a + (n - 1)d", "an = a + nd", "an = a + (n + 1)d", "an = a + (n - 2)d"],
        answer: 0
    },
    {
        question: "5. दो समरूप त्रिभुजों की संगत भुजाएँ किस अनुपात में होती हैं?",
        options: ["बराबर", "अनुपातिक", "लंबवत", "समकोणीय"],
        answer: 1
    },
    {
         question: "6. एक वृत्त की परिधि और व्यास का अनुपात क्या है?",
        options: ["π/2", "π", "2π", "3π"],
        answer: 1
    },
    {
        question: "7. एक बेलन का आयतन क्या होता है?",
        options: ["πr²h", "2πrh", "πr²", "2πr"],
        answer: 0
    },
    {
        question: "8. त्रिकोणमिति में, sin θ का मान क्या होता है?",
       options: ["कर्ण/लंब", "आधार/कर्ण", "लंब/कर्ण", "आधार/लंब"],
        answer: 2
    },
    {
         question: "9. प्रायिकता का अधिकतम मान कितना होता है?",
        options: ["0", "0.5", "1", "अनंत"],
        answer: 2
    },
      {
        question: "10. दो बिंदुओं (x1, y1) और (x2, y2) के बीच की दूरी का सूत्र क्या है?",
        options: ["√(x1-x2)² + (y1-y2)²", "(x1-x2)² + (y1-y2)²", "√(x1+x2)² + (y1+y2)²", "x1-x2 + y1-y2"],
        answer: 0
    },
    {
        question: "11. यदि किसी वृत्त की त्रिज्या 7 सेमी हो, तो उसका क्षेत्रफल क्या होगा?",
        options: ["154 वर्ग सेमी", "44 वर्ग सेमी", "22 वर्ग सेमी", "49 वर्ग सेमी"],
         answer: 0
    },
     {
        question: "12. यदि एक शंकु की त्रिज्या 3 सेमी और ऊँचाई 4 सेमी है, तो उसकी तिरछी ऊँचाई कितनी होगी?",
        options: ["7 सेमी", "5 सेमी", "12 सेमी", "4 सेमी"],
        answer: 1
    },
    {
        question: "13. समीकरण x + y = 5 में कितने हल संभव हैं?",
        options: ["कोई हल नहीं", "एक हल", "दो हल", "अनंत हल"],
         answer: 3
    },
     {
        question: "14. दो रेखाएँ जो एक-दूसरे को कभी नहीं काटतीं, क्या कहलाती हैं?",
         options: ["प्रतिच्छेदी रेखाएँ", "लंब रेखाएँ", "समांतर रेखाएँ", "तिर्यक रेखाएँ"],
        answer: 2
    },
    {
        question: "15. एक समांतर चतुर्भुज में, सम्मुख कोण कैसे होते हैं?",
         options: ["बराबर", "अनुपूरक", "पूरक", "लंबवत"],
        answer: 0
    },
    {
      question: "16. यदि tan θ = 1, तो θ का मान क्या है?",
        options: ["30°", "45°", "60°", "90°"],
        answer: 1
    },
    {
         question: "17. cos 90° का मान क्या होता है?",
        options: ["0", "1", "-1", "√3/2"],
        answer: 0
    },
    {
         question: "18. यदि किसी घटना के घटित होने की प्रायिकता 0.3 है, तो उसके न घटित होने की प्रायिकता क्या है?",
        options: ["0.3", "0.7", "0", "1"],
         answer: 1
    },
    {
         question: "19. एक पासे को एक बार फेंकने पर 5 आने की प्रायिकता क्या है?",
         options: ["1/6", "1/3", "1/2", "1/4"],
        answer: 0
    },
    {
        question: "20. एक गोले का पृष्ठीय क्षेत्रफल क्या होता है?",
        options: ["4πr²", "2πr²", "πr²", "πr³"],
         answer: 0
    },
    {
      question:"21. यदि दो संख्याओं का योग 10 और अंतर 2 है, तो संख्याएँ क्या हैं?",
        options: ["5 और 5", "6 और 4", "7 और 3", "8 और 2"],
        answer: 1
    },
   {
        question: "22. निम्नलिखित में से कौन सा समीकरण द्विघात समीकरण है?",
        options: ["x + 2 = 0", "x² + 3x - 4 = 0", "x³ + 1 = 0", "2x - 5 = 0"],
        answer: 1
    },
   {
        question:"23. समांतर श्रेणी 2, 4, 6, ... का 10वां पद क्या है?",
        options: ["18", "20", "22", "24"],
       answer: 1
   },
    {
        question: "24. सभी समबाहु त्रिभुज होते हैं:",
        options: ["असमरूप", "समरूप", "सर्वांगसम", "कोई नहीं"],
        answer: 1
    },
    {
        question: "25. 10 सेमी त्रिज्या वाले वृत्त का क्षेत्रफल क्या है?",
         options: ["100 वर्ग सेमी", "100π वर्ग सेमी", "200π वर्ग सेमी", "50π वर्ग सेमी"],
        answer: 1
    },
    {
       question: "26. एक घन का कुल पृष्ठीय क्षेत्रफल क्या होता है, यदि एक भुजा a है?",
        options: ["a²", "4a²", "6a²", "a³"],
       answer: 2
    },
     {
      question: "27. यदि sin θ = 3/5 है, तो cos θ का मान क्या होगा?",
      options: ["4/5", "5/3", "3/4", "5/4"],
      answer: 0
    },
    {
       question: "28. केंद्रीय प्रवृत्ति की माप क्या नहीं है?",
        options: ["माध्य", "माध्यिका", "बहुलक", "विचरण"],
        answer: 3
    },
    {
      question: "29. दो पासे को एक साथ फेंकने पर दोनों पर समान अंक आने की प्रायिकता क्या है?",
        options: ["1/6", "1/3", "1/2", "1/12"],
        answer: 0
    },
    {
        question: "30. मूल बिंदु के निर्देशांक क्या होते हैं?",
        options: ["(1, 1)", "(0, 1)", "(1, 0)", "(0, 0)"],
        answer: 3
    }

];


        let currentQuestion = 0;
        let score = 0;
        let userName = "";
        let userResults = JSON.parse(localStorage.getItem('userResults') || '[]');
        const nameForm = document.getElementById('name-form');
        const quizContainer = document.getElementById('quiz-container');
        const questionNumberElement = document.getElementById('question-number');
        const questionTextElement = document.getElementById('question-text');
        const optionsContainer = document.getElementById('options');
        const resultsContainer = document.getElementById('results-container');
        const userResultDisplay = document.getElementById('user-result');
        const allResultsDisplay = document.getElementById('all-results');
        const scoreDisplay = document.getElementById('scoreDisplay');


        function startQuiz() {
            userName = document.getElementById('userName').value.trim();
            if (userName === "") {
                alert("कृपया अपना नाम दर्ज करें!");
                return;
            }
            nameForm.style.display = 'none';
            quizContainer.style.display = 'block';
            loadQuestion();
        }


        function loadQuestion() {
            questionNumberElement.textContent = `प्रश्न ${currentQuestion + 1} / ${questions.length}`;
            questionTextElement.textContent = questions[currentQuestion].question;
            optionsContainer.innerHTML = "";
            questions[currentQuestion].options.forEach((option, index) => {
                const button = document.createElement('button');
                button.textContent = option;
                button.onclick = () => checkAnswer(index);
                optionsContainer.appendChild(button);
            });
        }

        function checkAnswer(selectedOption) {
            if (selectedOption === questions[currentQuestion].answer) {
                score++;
            }
             currentQuestion++;
            scoreDisplay.textContent = `अंक: ${score}`;
            if (currentQuestion < questions.length) {
                loadQuestion();
            } else {
                endQuiz();
            }
        }
          function nextQuestion(){
           checkAnswer(-1);
        }

        function endQuiz() {
            quizContainer.style.display = 'none';
            resultsContainer.style.display = 'block';
            userResultDisplay.textContent = `${userName}, आपका स्कोर है: ${score} / ${questions.length}`;

            userResults.push({ name: userName, score: score });
            localStorage.setItem('userResults', JSON.stringify(userResults));
            displayAllResults();
        }

        function displayAllResults() {
            allResultsDisplay.innerHTML = "<h3>सभी प्रतिभागियों के परिणाम</h3>";
            if (userResults.length === 0) {
                allResultsDisplay.innerHTML = "<p>अभी कोई परिणाम उपलब्ध नहीं है.</p>";
                return;
            }
            userResults.forEach(result => {
                allResultsDisplay.innerHTML += `<p>${result.name}: ${result.score} / ${questions.length}</p>`;
            });
        }
        window.onload = displayAllResults;

    </script>
</body>
</html>