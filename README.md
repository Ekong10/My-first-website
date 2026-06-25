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
    </style>
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
    </script><style>
/* Reset */
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    min-height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    padding:20px;
    overflow-x:hidden;
    transition:background 0.8s ease-in-out;
}

/* Animated Particles Background */
body::before{
    content:"";
    position:fixed;
    inset:0;
    background-image:
        radial-gradient(circle, rgba(255,255,255,0.3) 2px, transparent 2px);
    background-size:50px 50px;
    animation:moveParticles 20s linear infinite;
    pointer-events:none;
}

@keyframes moveParticles{
    from{
        transform:translateY(0);
    }
    to{
        transform:translateY(-100px);
    }
}

/* Main Container */
.container{
    max-width:600px;
    width:100%;
    background:rgba(255,255,255,0.15);
    backdrop-filter:blur(15px);
    -webkit-backdrop-filter:blur(15px);
    border:1px solid rgba(255,255,255,0.2);
    border-radius:25px;
    padding:50px 40px;
    box-shadow:0 20px 60px rgba(0,0,0,0.3);
    text-align:center;
    animation:
        slideIn 0.8s ease-out,
        floatCard 5s ease-in-out infinite;
}

@keyframes slideIn{
    from{
        opacity:0;
        transform:translateY(30px);
    }
    to{
        opacity:1;
        transform:translateY(0);
    }
}

@keyframes floatCard{
    0%,100%{
        transform:translateY(0);
    }
    50%{
        transform:translateY(-10px);
    }
}

/* Heading */
h1{
    color:white;
    margin-bottom:30px;
    font-size:2.2em;
    text-shadow:
        0 0 10px rgba(255,255,255,0.7),
        0 0 20px rgba(102,126,234,0.8),
        0 0 40px rgba(118,75,162,0.8);
}

/* Category Badge */
.category{
    display:inline-block;
    background:linear-gradient(135deg,#667eea,#764ba2);
    color:white;
    padding:8px 18px;
    border-radius:30px;
    font-size:0.9em;
    font-weight:600;
    margin-bottom:20px;
    box-shadow:0 5px 15px rgba(0,0,0,0.2);
}

/* Fact Box */
.fact{
    font-size:1.3em;
    line-height:1.8;
    color:white;
    margin-bottom:40px;
    min-height:120px;
    display:flex;
    align-items:center;
    justify-content:center;
    padding:25px;
    border-radius:15px;
    background:rgba(255,255,255,0.1);
    backdrop-filter:blur(10px);
    border:1px solid rgba(255,255,255,0.2);
    animation:fadeIn 0.6s ease-out;
}

@keyframes fadeIn{
    from{
        opacity:0;
    }
    to{
        opacity:1;
    }
}

/* Buttons */
.button-group{
    display:flex;
    gap:15px;
    justify-content:center;
    flex-wrap:wrap;
}

button{
    padding:14px 30px;
    font-size:1em;
    border:none;
    border-radius:12px;
    cursor:pointer;
    font-weight:600;
    text-transform:uppercase;
    letter-spacing:1px;
    transition:all 0.3s ease;
}

/* Next Button */
.btn-next{
    flex:1;
    min-width:150px;
    color:white;
    background:linear-gradient(
        270deg,
        #667eea,
        #764ba2,
        #00c9ff,
        #667eea
    );
    background-size:400% 400%;
    animation:gradientMove 6s ease infinite;
}

@keyframes gradientMove{
    0%{
        background-position:0% 50%;
    }
    50%{
        background-position:100% 50%;
    }
    100%{
        background-position:0% 50%;
    }
}

/* Copy Button */
.btn-copy{
    flex:1;
    min-width:150px;
    background:#f39c12;
    color:white;
}

/* Button Hover Effects */
button:hover{
    transform:translateY(-4px);
    box-shadow:
        0 0 15px rgba(255,255,255,0.4),
        0 0 30px rgba(102,126,234,0.6);
}

button:active{
    transform:translateY(-1px);
}

/* Copy Notification */
.copy-feedback{
    position:fixed;
    bottom:20px;
    right:20px;
    background:#27ae60;
    color:white;
    padding:15px 25px;
    border-radius:10px;
    opacity:0;
    transition:opacity 0.3s ease;
    pointer-events:none;
    z-index:1000;
}

.copy-feedback.show{
    opacity:1;
}

/* Background Themes */
.bg-space{
    background:
        linear-gradient(
            135deg,
            #0f0c29,
            #302b63,
            #24243e
        );
}

.bg-ocean{
    background:
        linear-gradient(
            135deg,
            #0077be,
            #00a8e8,
            #00c9ff
        );
}

.bg-nature{
    background:
        linear-gradient(
            135deg,
            #134e5e,
            #71b280
        );
}

.bg-history{
    background:
        linear-gradient(
            135deg,
            #8b4513,
            #d2691e,
            #cd853f
        );
}

.bg-science{
    background:
        linear-gradient(
            135deg,
            #667eea,
            #764ba2
        );
}

.bg-technology{
    background:
        linear-gradient(
            135deg,
            #0f2027,
            #203a43,
            #2c5364
        );
}

.bg-health{
    background:
        linear-gradient(
            135deg,
            #e74c3c,
            #ecf0f1
        );
}

/* Mobile Responsive */
@media(max-width:600px){

    .container{
        padding:30px 20px;
    }

    h1{
        font-size:1.7em;
    }

    .fact{
        font-size:1.1em;
    }

    .button-group{
        flex-direction:column;
    }

    button{
        width:100%;
    }
}
</style>
</body>
</html><style>

/* ===== PREMIUM RESET ===== */
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

html{
    scroll-behavior:smooth;
}

body{
    font-family:Inter, "Segoe UI", sans-serif;
    min-height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    padding:20px;
    overflow:hidden;
    background:linear-gradient(
        135deg,
        #0f172a 0%,
        #1e293b 50%,
        #312e81 100%
    );
    position:relative;
}

/* ===== ANIMATED AURORA BACKGROUND ===== */
body::before,
body::after{
    content:"";
    position:absolute;
    width:600px;
    height:600px;
    border-radius:50%;
    filter:blur(120px);
    opacity:0.4;
    animation:floatGlow 12s infinite ease-in-out;
}

body::before{
    background:#4f46e5;
    top:-200px;
    left:-100px;
}

body::after{
    background:#06b6d4;
    bottom:-200px;
    right:-100px;
}

@keyframes floatGlow{
    0%,100%{
        transform:translate(0,0);
    }
    50%{
        transform:translate(50px,-50px);
    }
}

/* ===== PREMIUM CARD ===== */
.container{
    position:relative;
    width:100%;
    max-width:720px;
    padding:55px;
    border-radius:30px;

    background:rgba(255,255,255,0.08);
    backdrop-filter:blur(30px);
    -webkit-backdrop-filter:blur(30px);

    border:1px solid rgba(255,255,255,0.15);

    box-shadow:
        0 8px 32px rgba(0,0,0,0.35),
        inset 0 1px 1px rgba(255,255,255,0.1);

    animation:fadeUp .8s ease;
}

.container::before{
    content:"";
    position:absolute;
    inset:0;
    border-radius:30px;
    padding:1px;
    background:linear-gradient(
        135deg,
        rgba(255,255,255,.4),
        rgba(255,255,255,.05)
    );
    -webkit-mask:
        linear-gradient(#fff 0 0) content-box,
        linear-gradient(#fff 0 0);
    -webkit-mask-composite:xor;
    pointer-events:none;
}

@keyframes fadeUp{
    from{
        opacity:0;
        transform:translateY(40px);
    }
    to{
        opacity:1;
        transform:translateY(0);
    }
}

/* ===== LOGO / TITLE ===== */
h1{
    font-size:3rem;
    font-weight:800;
    color:#fff;
    letter-spacing:-1px;
    margin-bottom:20px;
}

.subtitle{
    color:#cbd5e1;
    font-size:1rem;
    margin-bottom:40px;
}

/* ===== CATEGORY BADGE ===== */
.category{
    display:inline-flex;
    align-items:center;
    gap:8px;

    padding:10px 18px;
    border-radius:999px;

    background:rgba(255,255,255,.08);
    border:1px solid rgba(255,255,255,.12);

    color:#f8fafc;
    font-size:.9rem;
    font-weight:600;

    margin-bottom:25px;
}

/* ===== FACT CARD ===== */
.fact{
    background:rgba(255,255,255,.05);
    border:1px solid rgba(255,255,255,.08);
    border-radius:22px;

    padding:35px;
    min-height:180px;

    display:flex;
    align-items:center;
    justify-content:center;

    font-size:1.35rem;
    line-height:1.8;
    color:#fff;

    margin-bottom:35px;

    transition:.3s ease;
}

.fact:hover{
    transform:translateY(-5px);
    border-color:rgba(255,255,255,.2);
}

/* ===== BUTTONS ===== */
.button-group{
    display:flex;
    gap:15px;
}

button{
    border:none;
    cursor:pointer;
    transition:.3s ease;
    font-size:.95rem;
    font-weight:700;
    border-radius:14px;
    padding:16px 26px;
}

/* Primary Button */
.btn-next{
    flex:1;

    color:#fff;

    background:linear-gradient(
        135deg,
        #6366f1,
        #8b5cf6
    );

    box-shadow:
        0 10px 30px rgba(99,102,241,.35);
}

.btn-next:hover{
    transform:translateY(-4px);
    box-shadow:
        0 18px 40px rgba(99,102,241,.45);
}

/* Secondary Button */
.btn-copy{
    flex:1;

    color:#fff;

    background:rgba(255,255,255,.08);
    border:1px solid rgba(255,255,255,.12);
}

.btn-copy:hover{
    background:rgba(255,255,255,.15);
    transform:translateY(-4px);
}

/* ===== NOTIFICATION ===== */
.copy-feedback{
    position:fixed;
    right:25px;
    bottom:25px;

    padding:14px 24px;

    background:#10b981;
    color:white;

    border-radius:12px;

    font-weight:600;

    opacity:0;
    transform:translateY(20px);

    transition:.4s ease;
}

.copy-feedback.show{
    opacity:1;
    transform:translateY(0);
}

/* ===== RESPONSIVE ===== */
@media(max-width:768px){

    .container{
        padding:35px 25px;
    }

    h1{
        font-size:2.2rem;
    }

    .fact{
        font-size:1.1rem;
    }

    .button-group{
        flex-direction:column;
    }

    button{
        width:100%;
    }
}

</style>
<style>

/* =========================
   PREMIUM GLOBAL STYLES
========================= */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    min-height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    font-family:Inter, sans-serif;
    overflow:hidden;
    background:#050816;
    position:relative;
}

/* Animated Gradient Background */
body::before{
    content:"";
    position:absolute;
    inset:-50%;
    background:
        radial-gradient(circle at 20% 20%, #4f46e5 0%, transparent 25%),
        radial-gradient(circle at 80% 30%, #06b6d4 0%, transparent 25%),
        radial-gradient(circle at 50% 80%, #9333ea 0%, transparent 30%);
    animation:rotateBg 25s linear infinite;
    opacity:.8;
}

@keyframes rotateBg{
    from{
        transform:rotate(0deg);
    }
    to{
        transform:rotate(360deg);
    }
}

/* =========================
   GLASS CARD
========================= */

.container{
    position:relative;
    width:100%;
    max-width:750px;

    padding:60px;

    background:rgba(255,255,255,.06);
    backdrop-filter:blur(30px);

    border:1px solid rgba(255,255,255,.12);

    border-radius:32px;

    box-shadow:
        0 25px 80px rgba(0,0,0,.5),
        inset 0 1px 1px rgba(255,255,255,.1);

    z-index:2;

    animation:appear .9s ease;
}

@keyframes appear{
    from{
        opacity:0;
        transform:translateY(40px) scale(.95);
    }
    to{
        opacity:1;
        transform:translateY(0) scale(1);
    }
}

/* Glow Border */

.container::before{
    content:"";
    position:absolute;
    inset:-1px;

    border-radius:32px;

    background:
        linear-gradient(
            135deg,
            rgba(99,102,241,.8),
            rgba(6,182,212,.5),
            rgba(147,51,234,.8)
        );

    z-index:-1;

    filter:blur(15px);
    opacity:.4;
}

/* =========================
   TITLE
========================= */

h1{
    font-size:3.5rem;
    font-weight:900;
    text-align:center;

    background:
        linear-gradient(
            90deg,
            #ffffff,
            #a5b4fc,
            #67e8f9
        );

    -webkit-background-clip:text;
    -webkit-text-fill-color:transparent;

    margin-bottom:15px;
}

.subtitle{
    text-align:center;
    color:#94a3b8;
    font-size:1.05rem;
    margin-bottom:40px;
}

/* =========================
   CATEGORY TAG
========================= */

.category{
    display:inline-block;

    padding:10px 18px;

    border-radius:999px;

    background:
        rgba(255,255,255,.08);

    border:
        1px solid rgba(255,255,255,.15);

    color:#fff;

    font-weight:600;

    margin-bottom:25px;
}

/* =========================
   FACT CARD
========================= */

.fact{
    background:
        rgba(255,255,255,.04);

    border:
        1px solid rgba(255,255,255,.08);

    border-radius:24px;

    padding:35px;

    min-height:180px;

    display:flex;
    justify-content:center;
    align-items:center;

    text-align:center;

    color:white;

    font-size:1.3rem;
    line-height:1.9;

    transition:.4s ease;

    margin-bottom:35px;
}

.fact:hover{
    transform:translateY(-8px);
    box-shadow:
        0 20px 40px rgba(99,102,241,.15);
}

/* =========================
   BUTTONS
========================= */

.button-group{
    display:flex;
    gap:18px;
}

button{
    flex:1;

    padding:18px;

    border:none;

    border-radius:18px;

    cursor:pointer;

    font-weight:700;
    font-size:1rem;

    transition:.35s ease;
}

/* Main Button */

.btn-next{
    background:
        linear-gradient(
            135deg,
            #6366f1,
            #8b5cf6
        );

    color:white;

    box-shadow:
        0 12px 35px rgba(99,102,241,.4);
}

.btn-next:hover{
    transform:
        translateY(-5px)
        scale(1.02);

    box-shadow:
        0 20px 50px rgba(99,102,241,.55);
}

/* Secondary Button */

.btn-copy{
    background:
        rgba(255,255,255,.08);

    color:white;

    border:
        1px solid rgba(255,255,255,.12);
}

.btn-copy:hover{
    transform:
        translateY(-5px);

    background:
        rgba(255,255,255,.15);
}

/* =========================
   TOAST
========================= */

.copy-feedback{
    position:fixed;
    right:25px;
    bottom:25px;

    background:#10b981;

    color:white;

    padding:15px 22px;

    border-radius:14px;

    font-weight:600;

    opacity:0;
    transition:.4s;
}

.copy-feedback.show{
    opacity:1;
}

/* =========================
   MOBILE
========================= */

@media(max-width:768px){

    .container{
        padding:35px 25px;
    }

    h1{
        font-size:2.4rem;
    }

    .fact{
        font-size:1.05rem;
    }

    .button-group{
        flex-direction:column;
    }
}

</style>
/* RESET */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', sans-serif;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #f4f6f9;
    padding: 20px;
}

/* CONTAINER */
.container {
    max-width: 600px;
    width: 100%;
    background: white;
    padding: 40px;
    border-radius: 15px;
    box-shadow: 0 5px 20px rgba(0,0,0,0.1);
    text-align: center;
}

/* TITLE */
h1 {
    color: #333;
    font-size: 2rem;
    margin-bottom: 20px;
}

/* CATEGORY */
.category {
    display: inline-block;
    background: #667eea;
    color: white;
    padding: 8px 16px;
    border-radius: 20px;
    margin-bottom: 20px;
    font-size: 0.9rem;
}

/* FACT */
.fact {
    font-size: 1.2rem;
    color: #444;
    line-height: 1.7;
    margin-bottom: 30px;
}

/* BUTTONS */
.button-group {
    display: flex;
    gap: 10px;
}

button {
    flex: 1;
    padding: 12px;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    font-size: 1rem;
    transition: 0.3s;
}

.btn-next {
    background: #667eea;
    color: white;
}

.btn-next:hover {
    background: #5563d6;
}

.btn-copy {
    background: #f39c12;
    color: white;
}

.btn-copy:hover {
    background: #e67e22;
}

/* COPY MESSAGE */
.copy-feedback {
    position: fixed;
    bottom: 20px;
    right: 20px;
    background: #27ae60;
    color: white;
    padding: 12px 20px;
    border-radius: 6px;
    display: none;
}

.copy-feedback.show {
    display: block;
}

/* MOBILE */
@media (max-width: 600px) {
    .container {
        padding: 25px;
    }

    .button-group {
        flex-direction: column;
    }
}
