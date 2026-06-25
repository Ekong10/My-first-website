# My-first-website
Great fact you should know 
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Interesting Facts</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: background 0.8s ease-in-out, background-color 0.8s ease-in-out;
            padding: 20px;
        }

        .container {
            max-width: 600px;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 50px 40px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            text-align: center;
            animation: slideIn 0.6s ease-out;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        h1 {
            color: #333;
            margin-bottom: 30px;
            font-size: 2em;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }

        .fact {
            font-size: 1.3em;
            line-height: 1.8;
            color: #2c3e50;
            margin-bottom: 40px;
            min-height: 120px;
            display: flex;
            align-items: center;
            justify-content: center;
            animation: fadeIn 0.6s ease-out;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        .category {
            display: inline-block;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 0.9em;
            margin-bottom: 20px;
            font-weight: 600;
        }

        .button-group {
            display: flex;
            gap: 15px;
            justify-content: center;
            flex-wrap: wrap;
        }

        button {
            padding: 12px 30px;
            font-size: 1em;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .btn-next {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            flex: 1;
            min-width: 150px;
        }

        .btn-next:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(102, 126, 234, 0.4);
        }

        .btn-next:active {
            transform: translateY(-1px);
        }

        .btn-copy {
            background: #f39c12;
            color: white;
            flex: 1;
            min-width: 150px;
        }

        .btn-copy:hover {
            background: #e67e22;
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(243, 156, 18, 0.4);
        }

        .copy-feedback {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #27ae60;
            color: white;
            padding: 15px 25px;
            border-radius: 8px;
            opacity: 0;
            transition: opacity 0.3s ease;
            pointer-events: none;
            z-index: 1000;
        }

        .copy-feedback.show {
            opacity: 1;
        }

        /* Background styles for different categories */
        .bg-space {
            background: linear-gradient(135deg, #1a0033 0%, #330066 50%, #003366 100%);
            background-attachment: fixed;
            color: white;
        }

        .bg-ocean {
            background: linear-gradient(135deg, #0077be 0%, #00a8e8 50%, #00c9ff 100%);
            background-attachment: fixed;
        }

        .bg-nature {
            background: linear-gradient(135deg, #134e5e 0%, #71b280 100%);
            background-attachment: fixed;
        }

        .bg-history {
            background: linear-gradient(135deg, #8b4513 0%, #d2691e 50%, #cd853f 100%);
            background-attachment: fixed;
        }

        .bg-science {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            background-attachment: fixed;
        }

        .bg-technology {
            background: linear-gradient(135deg, #0f2027 0%, #203a43 50%, #2c5364 100%);
            background-attachment: fixed;
        }

        .bg-health {
            background: linear-gradient(135deg, #e74c3c 0%, #ecf0f1 100%);
            background-attachment: fixed;
        }

        @media (max-width: 600px) {
            .container {
                padding: 30px 20px;
            }

            h1 {
                font-size: 1.5em;
            }

            .fact {
                font-size: 1.1em;
            }

            .button-group {
                flex-direction: column;
            }

            button {
                width: 100%;
            }
        }
    </style/>
</head>
<body>
    <div class="container">
        <h1>🌟 Random Interesting Facts</h1>
        <div class="category" id="category"></div>
        <div class="fact" id="fact"></div>
        <div class="button-group">
            <button class="btn-next" onclick="nextFact()">Get Next Fact</button>
            <button class="btn-copy" onclick="copyFact()">Copy Fact</button>
        </div>
    </div>

    <div class="copy-feedback" id="feedback">Fact copied to clipboard!</div>

    <script>
        const facts = [
            {
                category: "🌌 Space",
                fact: "A day on Venus is longer than its year. Venus takes 243 Earth days to complete one rotation, but only 225 Earth days to orbit the sun!",
                bg: "bg-space"
            },
            {
                category: "🌊 Ocean",
                fact: "Octopuses have three hearts. Two pump blood to the gills, while the third pumps blood to the rest of the body.",
                bg: "bg-ocean"
            },
            {
                category: "🌿 Nature",
                fact: "Trees can 'talk' to each other through an underground network called the 'Wood Wide Web' using fungi.",
                bg: "bg-nature"
            },
            {
                category: "📚 History",
                fact: "Cleopatra lived closer to the invention of the iPhone than to the construction of the Great Pyramid of Giza.",
                bg: "bg-history"
            },
            {
                category: "🔬 Science",
                fact: "Honey never spoils. Archaeologists have found 3000-year-old honey in Egyptian tombs that was still perfectly edible.",
                bg: "bg-science"
            },
            {
                category: "💻 Technology",
                fact: "The first webcam was created at Cambridge University to monitor a coffee pot, so scientists could see if there was coffee before going downstairs.",
                bg: "bg-technology"
            },
            {
                category: "❤️ Health",
                fact: "Your nose can remember over 1 trillion different scents, making it more powerful than your eyes and ears combined.",
                bg: "bg-health"
            },
            {
                category: "🌌 Space",
                fact: "Light from the sun takes about 8 minutes and 20 seconds to reach Earth. We literally see the sun as it was 8 minutes ago!",
                bg: "bg-space"
            },
            {
                category: "🌊 Ocean",
                fact: "The ocean produces at least 50% of the world's oxygen, and most of it comes from ocean plants, not trees.",
                bg: "bg-ocean"
            },
            {
                category: "🌿 Nature",
                fact: "Bananas are berries, but strawberries aren't! Botanically speaking, bananas fit the definition of berries while strawberries don't.",
                bg: "bg-nature"
            },
            {
                category: "📚 History",
                fact: "Oxford University is older than the Aztec Empire. Oxford was founded around 1096, while the Aztec Empire was founded in 1428.",
                bg: "bg-history"
            },
            {
                category: "🔬 Science",
                fact: "Diamonds rain on Jupiter and Saturn. The extreme pressure and heat in their atmospheres convert carbon into diamonds.",
                bg: "bg-science"
            },
            {
                category: "💻 Technology",
                fact: "The '@' symbol is called 'at sign' in English, but different countries have creative names like 'little duck' in Greece and 'elephant's trunk' in Denmark.",
                bg: "bg-technology"
            },
            {
                category: "❤️ Health",
                fact: "Your body replaces approximately 330 billion cells per day. You are literally a different person at the cellular level every few years!",
                bg: "bg-health"
            },
            {
                category: "🌌 Space",
                fact: "A year on Neptune is 165 Earth years. A Neptunian child would need to wait 165 years to celebrate their first birthday!",
                bg: "bg-space"
            }
        ];

        let currentIndex = 0;

        function displayFact(index) {
            const fact = facts[index];
            document.getElementById('fact').textContent = fact.fact;
            document.getElementById('category').textContent = fact.category;
            document.body.className = fact.bg;
        }

        function nextFact() {
            currentIndex = (currentIndex + 1) % facts.length;
            displayFact(currentIndex);
        }

        function copyFact() {
            const fact = facts[currentIndex];
            const textToCopy = `${fact.category}\n${fact.fact}`;
            navigator.clipboard.writeText(textToCopy).then(() => {
                const feedback = document.getElementById('feedback');
                feedback.classList.add('show');
                setTimeout(() => {
                    feedback.classList.remove('show');
                }, 2000);
            });
        }

        // Initialize with a random fact
        window.addEventListener('load', () => {
            currentIndex = Math.floor(Math.random() * facts.length);
            displayFact(currentIndex);
        });

        // Keyboard navigation
        document.addEventListener('keydown', (e) => {
            if (e.key === 'ArrowRight' || e.key === ' ') {
                nextFact();
            }
        });
    </script/>
