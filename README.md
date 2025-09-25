# wiser-poets
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>𝗐𝗂𝗌𝖾𝗋 𝖯𝗈𝖾𝗍𝗌 - Inspiring Words for Every Mood</title>
    <style>
        body {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Georgia', serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            padding: 40px 20px;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }

        .header h1 {
            font-size: 3rem;
            margin: 0;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .header p {
            font-size: 1.2rem;
            color: #666;
            margin: 10px 0 0 0;
        }

        .category-tabs {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .tab-button {
            padding: 12px 24px;
            border: none;
            border-radius: 25px;
            background: rgba(255, 255, 255, 0.2);
            color: white;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }

        .tab-button:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-2px);
        }

        .tab-button.active {
            background: rgba(255, 255, 255, 0.9);
            color: #333;
        }

        .quotes-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }

        .quote-card {
            background: rgba(255, 255, 255, 0.95);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .quote-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.15);
        }

        .quote-card::before {
            content: '"';
            position: absolute;
            top: -10px;
            left: 20px;
            font-size: 6rem;
            color: rgba(102, 126, 234, 0.1);
            font-family: serif;
        }

        .quote-text {
            font-size: 1.1rem;
            line-height: 1.6;
            margin-bottom: 15px;
            font-style: italic;
            position: relative;
            z-index: 1;
        }

        .quote-author {
            font-weight: 600;
            color: #667eea;
            text-align: right;
            font-size: 0.95rem;
        }

        .quote-category {
            position: absolute;
            top: 15px;
            right: 15px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            padding: 5px 12px;
            border-radius: 15px;
            font-size: 0.8rem;
            font-weight: 600;
        }

        .load-more {
            display: block;
            margin: 0 auto;
            padding: 15px 30px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            border-radius: 25px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .load-more:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(102, 126, 234, 0.3);
        }

        .hidden {
            display: none;
        }

        @media (max-width: 768px) {
            .header h1 {
                font-size: 2rem;
            }
            
            .quotes-grid {
                grid-template-columns: 1fr;
            }
            
            .quote-card {
                padding: 20px;
            }
            
            .category-tabs {
                gap: 5px;
            }
            
            .tab-button {
                padding: 10px 16px;
                font-size: 0.9rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>QuoteVerse</h1>
            <p>Inspiring words for every mood and moment</p>
        </div>

        <div class="category-tabs">
            <button class="tab-button active" data-category="all">All Quotes</button>
            <button class="tab-button" data-category="motivation">Motivation</button>
            <button class="tab-button" data-category="love">Love</button>
            <button class="tab-button" data-category="sad">Sad</button>
            <button class="tab-button" data-category="attitude">Attitude</button>
        </div>

        <div class="quotes-grid" id="quotesGrid">
            <!-- Quotes will be populated by JavaScript -->
        </div>

        <button class="load-more" id="loadMoreBtn">Load More Quotes</button>
    </div>

    <script>
        const quotes = [
            // Motivation Quotes
            { text: "The only way to do great work is to love what you do.", author: "Steve Jobs", category: "motivation" },
            { text: "Success is not final, failure is not fatal: it is the courage to continue that counts.", author: "Winston Churchill", category: "motivation" },
            { text: "Believe you can and you're halfway there.", author: "Theodore Roosevelt", category: "motivation" },
            { text: "The future belongs to those who believe in the beauty of their dreams.", author: "Eleanor Roosevelt", category: "motivation" },
            { text: "It is during our darkest moments that we must focus to see the light.", author: "Aristotle", category: "motivation" },
            { text: "Don't watch the clock; do what it does. Keep going.", author: "Sam Levenson", category: "motivation" },
            
            // Love Quotes
            { text: "Being deeply loved by someone gives you strength, while loving someone deeply gives you courage.", author: "Lao Tzu", category: "love" },
            { text: "The best thing to hold onto in life is each other.", author: "Audrey Hepburn", category: "love" },
            { text: "Love is not about how many days, months, or years you have been together. It's about how much you love each other every single day.", author: "Unknown", category: "love" },
            { text: "In all the world, there is no heart for me like yours. In all the world, there is no love for you like mine.", author: "Maya Angelou", category: "love" },
            { text: "Love is composed of a single soul inhabiting two bodies.", author: "Aristotle", category: "love" },
            { text: "You know you're in love when you can't fall asleep because reality is finally better than your dreams.", author: "Dr. Seuss", category: "love" },
            
            // Sad Quotes
            { text: "The word 'happy' would lose its meaning if it were not balanced by sadness.", author: "Carl Jung", category: "sad" },
            { text: "Tears are words that need to be written.", author: "Paulo Coelho", category: "sad" },
            { text: "Sometimes you need to sit lonely on the floor in a quiet room in order to hear your own voice and not let it drown in the noise of others.", author: "Charlotte Eriksson", category: "sad" },
            { text: "The walls we build around us to keep sadness out also keeps out the joy.", author: "Jim Rohn", category: "sad" },
            { text: "Heavy hearts, like heavy clouds in the sky, are best relieved by the letting of a little water.", author: "Christopher Morley", category: "sad" },
            { text: "Don't cry because it's over, smile because it happened.", author: "Dr. Seuss", category: "sad" },
            
            // Attitude Quotes
            { text: "Your attitude, not your aptitude, will determine your altitude.", author: "Zig Ziglar", category: "attitude" },
            { text: "I don't have an attitude problem. You have a perception problem.", author: "Unknown", category: "attitude" },
            { text: "Life is 10% what happens to you and 90% how you react to it.", author: "Charles R. Swindoll", category: "attitude" },
            { text: "A positive attitude causes a chain reaction of positive thoughts, events and outcomes.", author: "Wade Boggs", category: "attitude" },
            { text: "Excellence is not a skill, it's an attitude.", author: "Ralph Marston", category: "attitude" },
            { text: "The only disability in life is a bad attitude.", author: "Scott Hamilton", category: "attitude" },
            
            // Additional quotes for variety
            { text: "The greatest glory in living lies not in never falling, but in rising every time we fall.", author: "Nelson Mandela", category: "motivation" },
            { text: "Love recognizes no barriers. It jumps hurdles, leaps fences, penetrates walls to arrive at its destination full of hope.", author: "Maya Angelou", category: "love" },
            { text: "Sadness flies away on the wings of time.", author: "Jean de La Fontaine", category: "sad" },
            { text: "Keep your face always toward the sunshine—and shadows will fall behind you.", author: "Walt Whitman", category: "attitude" }
        ];

        let currentCategory = 'all';
        let displayedQuotes = 0;
        const quotesPerLoad = 6;

        function shuffleArray(array) {
            const shuffled = [...array];
            for (let i = shuffled.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [shuffled[i], shuffled[j]] = [shuffled[j], shuffled[i]];
            }
            return shuffled;
        }

        function getFilteredQuotes() {
            if (currentCategory === 'all') {
                return shuffleArray(quotes);
            }
            return shuffleArray(quotes.filter(quote => quote.category === currentCategory));
        }

        function createQuoteCard(quote) {
            return `
                <div class="quote-card">
                    <div class="quote-category">${quote.category.charAt(0).toUpperCase() + quote.category.slice(1)}</div>
                    <div class="quote-text">${quote.text}</div>
                    <div class="quote-author">— ${quote.author}</div>
                </div>
            `;
        }

        function loadQuotes(reset = false) {
            const quotesGrid = document.getElementById('quotesGrid');
            const filteredQuotes = getFilteredQuotes();
            
            if (reset) {
                quotesGrid.innerHTML = '';
                displayedQuotes = 0;
            }
            
            const quotesToShow = filteredQuotes.slice(displayedQuotes, displayedQuotes + quotesPerLoad);
            
            quotesToShow.forEach(quote => {
                quotesGrid.innerHTML += createQuoteCard(quote);
            });
            
            displayedQuotes += quotesToShow.length;
            
            // Hide load more button if all quotes are displayed
            const loadMoreBtn = document.getElementById('loadMoreBtn');
            if (displayedQuotes >= filteredQuotes.length) {
                loadMoreBtn.style.display = 'none';
            } else {
                loadMoreBtn.style.display = 'block';
            }
        }

        // Tab functionality
        document.querySelectorAll('.tab-button').forEach(button => {
            button.addEventListener('click', () => {
                // Remove active class from all buttons
                document.querySelectorAll('.tab-button').forEach(btn => btn.classList.remove('active'));
                // Add active class to clicked button
                button.classList.add('active');
                
                // Update current category
                currentCategory = button.dataset.category;
                
                // Load quotes for new category
                loadQuotes(true);
            });
        });

        // Load more functionality
        document.getElementById('loadMoreBtn').addEventListener('click', () => {
            loadQuotes();
        });

        // Initial load
        loadQuotes();
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'984b2b8f02f69cbf',t:'MTc1ODgxMDEwOS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>

