<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fun English Quiz for Kids! 🎉</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: #f0f8ff; /* Light sky blue */
            margin: 0;
            padding: 20px;
            box-sizing: border-box;
        }

        .quiz-container {
            background-color: #fff;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            text-align: center;
            max-width: 650px; /* Slightly wider for Arabic meanings */
            width: 100%;
            border: 2px solid #aaddff; /* Light blue border */
        }

        h1 {
            color: #333;
            margin-bottom: 25px;
            font-size: 2.2em;
        }

        .input-group {
            margin-bottom: 20px;
        }

        .input-group label {
            font-size: 1.2em;
            color: #555;
            margin-right: 10px;
        }

        .input-group input[type="text"] {
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 1em;
            width: calc(100% - 100px); /* Adjust width */
            max-width: 250px;
        }

        .question {
            font-size: 1.5em;
            margin-bottom: 20px;
            color: #555;
            min-height: 60px; /* To prevent layout shift */
            display: flex;
            align-items: center;
            justify-content: center;
            flex-wrap: wrap;
            flex-direction: column; /* To stack question and image if any */
        }

        .question img {
            max-width: 100%;
            height: auto;
            border-radius: 8px;
            margin-top: 15px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }

        .options button {
            display: block;
            width: calc(100% - 20px); /* Adjust for padding */
            padding: 15px;
            margin: 10px auto;
            border: 2px solid #66b2ff; /* Medium blue */
            border-radius: 8px;
            background-color: #e0f2ff; /* Lighter blue */
            color: #333;
            font-size: 1.2em;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.2s, border-color 0.3s;
            text-align: left;
            box-sizing: border-box; /* Include padding and border in the element's total width and height */
        }

        .options button:hover {
            background-color: #cce7ff; /* Even lighter blue */
            transform: translateY(-2px);
            border-color: #4da6ff;
        }

        .options button:active {
            transform: translateY(0);
        }

        .feedback {
            margin-top: 20px;
            font-size: 1.3em;
            font-weight: bold;
            min-height: 30px; /* To prevent layout shift */
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
        }

        .feedback.correct {
            color: #28a745; /* Green */
        }

        .feedback.incorrect {
            color: #dc3545; /* Red */
        }

        .arabic-meaning {
            font-size: 1em;
            color: #666;
            margin-top: 5px;
            font-style: italic;
        }

        .controls button {
            background-color: #007bff; /* Blue */
            color: white;
            padding: 12px 25px;
            border: none;
            border-radius: 8px;
            font-size: 1.1em;
            cursor: pointer;
            margin-top: 25px;
            transition: background-color 0.3s, transform 0.2s;
        }

        .controls button:hover {
            background-color: #0056b3;
            transform: translateY(-2px);
        }

        .controls button:disabled {
            background-color: #cccccc;
            cursor: not-allowed;
        }

        #score-display {
            font-size: 1.4em;
            margin-top: 20px;
            font-weight: bold;
            color: #444;
        }

        .start-screen, .results-screen {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
        }

        .start-screen button, .results-screen button {
            margin-top: 20px;
            background-color: #28a745; /* Green for start/restart */
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 8px;
            font-size: 1.2em;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.2s;
        }

        .start-screen button:hover, .results-screen button:hover {
            background-color: #218838;
            transform: translateY(-2px);
        }

        #results-content {
            margin-top: 20px;
            font-size: 1.3em;
            color: #333;
        }

        .whatsapp-button {
            background-color: #25D366 !important; /* WhatsApp green */
            margin-top: 15px !important;
            padding: 12px 25px !important;
            font-size: 1.1em !important;
        }
        .whatsapp-button:hover {
            background-color: #1DA851 !important;
        }

        /* Responsive adjustments */
        @media (max-width: 768px) {
            .quiz-container {
                padding: 20px;
                border-radius: 10px;
            }
            h1 {
                font-size: 1.8em;
            }
            .input-group label, .input-group input {
                font-size: 1em;
            }
            .question {
                font-size: 1.3em;
                min-height: 80px;
            }
            .options button {
                font-size: 1em;
                padding: 12px;
            }
            .feedback {
                font-size: 1.1em;
            }
            .controls button {
                padding: 10px 20px;
                font-size: 1em;
            }
            #score-display {
                font-size: 1.2em;
            }
            .arabic-meaning {
                font-size: 0.9em;
            }
            .start-screen button, .results-screen button {
                padding: 12px 25px;
                font-size: 1.1em;
            }
            .whatsapp-button {
                padding: 10px 20px !important;
                font-size: 1em !important;
            }
        }

        @media (max-width: 480px) {
            .quiz-container {
                padding: 15px;
            }
            h1 {
                font-size: 1.5em;
            }
            .input-group input {
                width: calc(100% - 20px);
                max-width: none;
            }
            .question {
                font-size: 1.1em;
                min-height: 100px;
            }
            .options button {
                font-size: 0.9em;
                padding: 10px;
            }
            .feedback {
                font-size: 1em;
            }
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <div id="start-screen" class="start-screen">
            <h1>Welcome to the English Quiz! 🎉</h1>
            <div class="input-group">
                <label for="student-name">Enter your name:</label>
                <input type="text" id="student-name" placeholder="Your Name">
            </div>
            <button id="start-quiz-button">Start Quiz!</button>
        </div>

        <div id="quiz-screen" style="display: none;">
            <h1>Fun English Quiz! 🎉</h1>
            <div class="question" id="question"></div>
            <div class="options" id="options"></div>
            <div class="feedback" id="feedback"></div>
            <div class="controls">
                <button id="next-button">Next Question</button>
            </div>
            <div id="score-display"></div>
        </div>

        <div id="results-screen" class="results-screen" style="display: none;">
            <h1>Quiz Results! 🥳</h1>
            <p id="results-content"></p>
            <button id="restart-quiz-button">Play Again!</button>
            <button id="whatsapp-share-button" class="whatsapp-button">Share Results on WhatsApp</button>
        </div>
    </div>

    <script>
        const allQuestions = [
            // Multiple Choice Questions (Type: 'mcq')
            { type: 'mcq', question: "What color is a sunny sky?", options: ["Red", "Green", "Blue", "Yellow"], answer: "Blue", meaning: "السماء الزرقاء" },
            { type: 'mcq', question: "How many legs does a cat have?", options: ["Two", "Four", "Six", "Eight"], answer: "Four", meaning: "أربعة أرجل" },
            { type: 'mcq', question: "Which animal says 'Moo'?", options: ["Dog", "Cow", "Cat", "Duck"], answer: "Cow", meaning: "البقرة" },
            { type: 'mcq', question: "What do you use to eat soup?", options: ["Fork", "Spoon", "Knife", "Chopsticks"], answer: "Spoon", meaning: "ملعقة" },
            { type: 'mcq', question: "Which fruit is red and round?", options: ["Banana", "Orange", "Apple", "Grape"], answer: "Apple", meaning: "تفاحة" },
            { type: 'mcq', question: "What is the opposite of 'hot'?", options: ["Warm", "Cold", "Big", "Fast"], answer: "Cold", meaning: "بارد" },
            { type: 'mcq', question: "Which shape has four equal sides?", options: ["Circle", "Triangle", "Square", "Oval"], answer: "Square", meaning: "مربع" },
            { type: 'mcq', question: "What is a baby chicken called?", options: ["Calf", "Lamb", "Chick", "Puppy"], answer: "Chick", meaning: "كتكوت" },
            { type: 'mcq', question: "What do birds use to fly?", options: ["Legs", "Wings", "Fins", "Paws"], answer: "Wings", meaning: "أجنحة" },
            { type: 'mcq', question: "Which day comes before Friday?", options: ["Saturday", "Wednesday", "Thursday", "Sunday"], answer: "Thursday", meaning: "الخميس" },
            { type: 'mcq', question: "What do you wear on your head?", options: ["Shoes", "Gloves", "Hat", "Socks"], answer: "Hat", meaning: "قبعة" },
            { type: 'mcq', question: "Which one is a musical instrument?", options: ["Chair", "Table", "Guitar", "Book"], answer: "Guitar", meaning: "جيتار" },

            // True/False Questions (Type: 'tf')
            { type: 'tf', question: "The sun is green.", options: ["True", "False"], answer: "False", meaning: "الشمس ليست خضراء" },
            { type: 'tf', question: "A fish can fly.", options: ["True", "False"], answer: "False", meaning: "السمكة لا تستطيع الطيران" },
            { type: 'tf', question: "Winter is a cold season.", options: ["True", "False"], answer: "True", meaning: "الشتاء فصل بارد" },
            { type: 'tf', question: "You use your nose to smell.", options: ["True", "False"], answer: "True", meaning: "تستخدم أنفك للشم" },
            { type: 'tf', question: "A car has two wheels.", options: ["True", "False"], answer: "False", meaning: "السيارة لديها أربع عجلات" },
            { type: 'tf', question: "An elephant is a small animal.", options: ["True", "False"], answer: "False", meaning: "الفيل حيوان ضخم" },
            { type: 'tf', question: "You drink water with your ears.", options: ["True", "False"], answer: "False", meaning: "تشرب الماء بفمك" },
            { type: 'tf', question: "A triangle has three sides.", options: ["True", "False"], answer: "True", meaning: "المثلث له ثلاثة أضلاع" },
            { type: 'tf', question: "Blue and yellow make green.", options: ["True", "False"], answer: "True", meaning: "الأزرق والأصفر يصنعان الأخضر" },
            { type: 'tf', question: "Books are for reading.", options: ["True", "False"], answer: "True", meaning: "الكتب للقراءة" },
            { type: 'tf', question: "A mouse is bigger than an elephant.", options: ["True", "False"], answer: "False", meaning: "الفأر أصغر من الفيل" },
            { type: 'tf', question: "You eat breakfast in the evening.", options: ["True", "False"], answer: "False", meaning: "تأكل الإفطار في الصباح" },
            { type: 'tf', question: "A bird can swim underwater.", options: ["True", "False"], answer: "False", meaning: "الطيور لا تستطيع السباحة تحت الماء (معظمها)" },
            { type: 'tf', question: "The number 5 is an even number.", options: ["True", "False"], answer: "False", meaning: "الرقم 5 هو رقم فردي" }
        ];

        const QUIZ_LENGTH = 20; // Number of questions per quiz session (can be up to allQuestions.length)
        let currentQuestions = []; // Questions for the current quiz session
        let currentQuestionIndex = 0;
        let score = 0;
        let answeredThisQuestion = false;
        let studentName = "";

        // DOM Elements
        const startScreen = document.getElementById('start-screen');
        const quizScreen = document.getElementById('quiz-screen');
        const resultsScreen = document.getElementById('results-screen');
        const studentNameInput = document.getElementById('student-name');
        const startQuizButton = document.getElementById('start-quiz-button');
        const restartQuizButton = document.getElementById('restart-quiz-button');
        const whatsappShareButton = document.getElementById('whatsapp-share-button'); // New button

        const questionElement = document.getElementById('question');
        const optionsElement = document.getElementById('options');
        const feedbackElement = document.getElementById('feedback');
        const nextButton = document.getElementById('next-button');
        const scoreDisplay = document.getElementById('score-display');
        const resultsContent = document.getElementById('results-content');

        // Function to shuffle an array (Fisher-Yates algorithm)
        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]]; // Swap elements
            }
            return array;
        }

        function startQuiz() {
            studentName = studentNameInput.value.trim();
            if (studentName === "") {
                alert("Please enter your name to start the quiz!");
                return;
            }

            startScreen.style.display = 'none';
            quizScreen.style.display = 'block';
            resultsScreen.style.display = 'none';

            // Shuffle all questions and pick the first QUIZ_LENGTH questions
            // Ensure we don't pick more questions than available
            const questionsToPick = Math.min(QUIZ_LENGTH, allQuestions.length);
            currentQuestions = shuffleArray([...allQuestions]).slice(0, questionsToPick);
            currentQuestionIndex = 0;
            score = 0;
            nextButton.style.display = 'block';
            nextButton.textContent = 'Next Question'; // Reset button text
            loadQuestion();
        }

        function loadQuestion() {
            answeredThisQuestion = false;
            feedbackElement.innerHTML = ''; // Clear previous feedback and meaning
            feedbackElement.className = 'feedback'; // Reset feedback class
            nextButton.disabled = true; // Disable next button until an answer is selected
            optionsElement.innerHTML = ''; // Clear previous options

            if (currentQuestionIndex < currentQuestions.length) {
                const currentQ = currentQuestions[currentQuestionIndex];
                questionElement.textContent = currentQ.question;
                scoreDisplay.textContent = `Score: ${score}/${currentQuestions.length} | Question ${currentQuestionIndex + 1} of ${currentQuestions.length}`;

                // Shuffle options for the current question
                const shuffledOptions = shuffleArray([...currentQ.options]);

                shuffledOptions.forEach(option => {
                    const button = document.createElement('button');
                    button.textContent = option;
                    button.onclick = () => selectOption(option, currentQ.answer, currentQ.meaning);
                    optionsElement.appendChild(button);
                });
            } else {
                showResults();
            }
        }

        function selectOption(selectedOption, correctAnswer, arabicMeaning) {
            if (answeredThisQuestion) return; // Prevent multiple clicks

            answeredThisQuestion = true;
            nextButton.disabled = false; // Enable next button after an answer is selected

            const buttons = optionsElement.querySelectorAll('button');
            buttons.forEach(button => {
                button.disabled = true; // Disable all buttons after selection
                if (button.textContent === correctAnswer) {
                    button.style.backgroundColor = '#d4edda'; // Light green for correct
                    button.style.borderColor = '#28a745';
                }
            });

            const meaningSpan = document.createElement('span');
            meaningSpan.className = 'arabic-meaning';
            meaningSpan.textContent = `Meaning: ${arabicMeaning}`;

            if (selectedOption === correctAnswer) {
                feedbackElement.textContent = "Correct! ✨";
                feedbackElement.classList.add('correct');
                score++;
            } else {
                feedbackElement.textContent = `Oops! The correct answer was: ${correctAnswer}`;
                feedbackElement.classList.add('incorrect');
                // Highlight incorrect choice
                buttons.forEach(button => {
                    if (button.textContent === selectedOption) {
                        button.style.backgroundColor = '#f8d7da'; // Light red for incorrect
                        button.style.borderColor = '#dc3545';
                    }
                });
            }
            feedbackElement.appendChild(meaningSpan); // Add meaning after feedback text
            scoreDisplay.textContent = `Score: ${score}/${currentQuestions.length} | Question ${currentQuestionIndex + 1} of ${currentQuestions.length}`;
        }

        function nextQuestion() {
            currentQuestionIndex++;
            loadQuestion();
        }

        function showResults() {
            quizScreen.style.display = 'none';
            resultsScreen.style.display = 'block';

            let resultMessage = `Dear ${studentName}, your final score is: ${score} out of ${currentQuestions.length}!`;

            if (score === currentQuestions.length) {
                resultMessage += "<br>Amazing job! You got all of them right! 🏆 Perfect score!";
            } else if (score >= currentQuestions.length * 0.8) { // 80% or more
                resultMessage += "<br>Excellent work! You did great! Keep up the good learning! 👍";
            } else if (score >= currentQuestions.length * 0.5) { // 50% or more
                resultMessage += "<br>Good effort! You're getting there! A little more practice will make you even better! 😊";
            } else {
                resultMessage += "<br>You can do it! Don't worry, keep practicing and try again to get a better score! 💪";
            }
            resultsContent.innerHTML = resultMessage;

            // Prepare WhatsApp message
            const whatsappText = `Hello! 👋\n\nQuiz Results for ${studentName}:\nScore: ${score} out of ${currentQuestions.length} questions.\n\nGreat job! 🎉`;
            // Encode the message for URL
            const encodedWhatsappText = encodeURIComponent(whatsappText);
            // Set the href for the WhatsApp share button
            whatsappShareButton.href = `https://wa.me/201117112423?text=${encodedWhatsappText}`;
        }

        // Event Listeners
        startQuizButton.addEventListener('click', startQuiz);
        nextButton.addEventListener('click', nextQuestion);
        restartQuizButton.addEventListener('click', () => {
            studentNameInput.value = ""; // Clear name input for next round
            startScreen.style.display = 'block';
            quizScreen.style.display = 'none';
            resultsScreen.style.display = 'none';
        });

        // WhatsApp Share Button Listener (will open the link)
        whatsappShareButton.addEventListener('click', (event) => {
            // This prevents the default link behavior if you want to add more JS logic,
            // but for a simple wa.me link, it's not strictly necessary.
            // event.preventDefault();
            // window.open(whatsappShareButton.href, '_blank'); // Opens in a new tab
        });


        // Initial setup: show start screen
        startScreen.style.display = 'block';
        quizScreen.style.display = 'none';
        resultsScreen.style.display = 'none';
    </script>
</body>
</html>
