<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>İngilizce-Türkçe Kelime Kartları</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Nunito', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }
        
        .perspective-1000 {
            perspective: 1000px;
        }
        
        .card-inner {
            position: relative;
            width: 100%;
            height: 100%;
            text-align: center;
            transition: transform 0.6s;
            transform-style: preserve-3d;
            cursor: pointer;
        }
        
        .card-inner.flipped {
            transform: rotateY(180deg);
        }
        
        .card-front, .card-back {
            position: absolute;
            width: 100%;
            height: 100%;
            -webkit-backface-visibility: hidden;
            backface-visibility: hidden;
            border-radius: 1.5rem;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
        }
        
        .card-back {
            transform: rotateY(180deg);
            background: white;
        }
        
        .category-btn {
            transition: all 0.3s ease;
        }
        
        .category-btn.active {
            background: white;
            color: #667eea;
            transform: scale(1.05);
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }
        
        .floating {
            animation: float 3s ease-in-out infinite;
        }
        
        .progress-bar {
            transition: width 0.3s ease;
        }
    </style>
</head>
<body class="p-4 md:p-8">
    <div class="max-w-4xl mx-auto">
        <!-- Header -->
        <div class="text-center mb-8 text-white">
            <h1 class="text-4xl md:text-5xl font-extrabold mb-2 floating">🎓 Kelime Kartları</h1>
            <p class="text-lg opacity-90">İngilizce öğrenmenin en eğlenceli yolu</p>
        </div>

        <!-- Category Filter -->
        <div class="flex flex-wrap justify-center gap-2 mb-8">
            <button onclick="filterCategory('all')" class="category-btn active px-4 py-2 rounded-full bg-white/20 text-white font-semibold backdrop-blur-sm border border-white/30 hover:bg-white/30" data-category="all">
                Tümü
            </button>
            <button onclick="filterCategory('objects')" class="category-btn px-4 py-2 rounded-full bg-white/20 text-white font-semibold backdrop-blur-sm border border-white/30 hover:bg-white/30" data-category="objects">
                📚 Nesneler
            </button>
            <button onclick="filterCategory('emotions')" class="category-btn px-4 py-2 rounded-full bg-white/20 text-white font-semibold backdrop-blur-sm border border-white/30 hover:bg-white/30" data-category="emotions">
                😊 Duygular
            </button>
            <button onclick="filterCategory('actions')" class="category-btn px-4 py-2 rounded-full bg-white/20 text-white font-semibold backdrop-blur-sm border border-white/30 hover:bg-white/30" data-category="actions">
                🏃 Eylemler
            </button>
            <button onclick="filterCategory('colors')" class="category-btn px-4 py-2 rounded-full bg-white/20 text-white font-semibold backdrop-blur-sm border border-white/30 hover:bg-white/30" data-category="colors">
                🎨 Renkler
            </button>
            <button onclick="filterCategory('animals')" class="category-btn px-4 py-2 rounded-full bg-white/20 text-white font-semibold backdrop-blur-sm border border-white/30 hover:bg-white/30" data-category="animals">
                🦁 Hayvanlar
            </button>
            <button onclick="filterCategory('family')" class="category-btn px-4 py-2 rounded-full bg-white/20 text-white font-semibold backdrop-blur-sm border border-white/30 hover:bg-white/30" data-category="family">
                👨‍👩‍👧 Aile
            </button>
        </div>

        <!-- Progress Bar -->
        <div class="bg-white/20 backdrop-blur-sm rounded-full h-2 mb-6 overflow-hidden">
            <div id="progressBar" class="progress-bar bg-white h-full rounded-full" style="width: 0%"></div>
        </div>
        <div class="text-center text-white mb-6 font-semibold">
            <span id="currentIndex">1</span> / <span id="totalCount">0</span>
        </div>

        <!-- Card Container -->
        <div class="perspective-1000 w-full max-w-md mx-auto h-96 mb-8">
            <div id="card" class="card-inner" onclick="flipCard()">
                <!-- Front -->
                <div class="card-front bg-white flex flex-col items-center justify-center p-8 border-4 border-white">
                    <div class="text-6xl mb-4" id="frontEmoji">📚</div>
                    <h2 id="englishWord" class="text-4xl font-bold text-gray-800 mb-2">Pen</h2>
                    <p class="text-gray-500 text-sm mt-4">Çevirmek için tıkla</p>
                </div>
                
                <!-- Back -->
                <div class="card-back flex flex-col items-center justify-center p-8 border-4 border-white overflow-hidden">
                    <div id="turkishImage" class="w-full h-48 mb-4 rounded-lg overflow-hidden bg-gray-100 flex items-center justify-center">
                        <img id="wordImage" src="" alt="" class="w-full h-full object-cover hidden">
                        <div id="imagePlaceholder" class="text-6xl">🖼️</div>
                    </div>
                    <h2 id="turkishWord" class="text-3xl font-bold text-purple-600 mb-2">Tükenmez Kalem</h2>
                    <p id="phonetic" class="text-gray-500 text-sm italic"></p>
                </div>
            </div>
        </div>

        <!-- Controls -->
        <div class="flex justify-center gap-4 mb-8">
            <button onclick="previousCard()" class="bg-white text-purple-600 w-14 h-14 rounded-full shadow-lg hover:shadow-xl hover:scale-110 transition-all flex items-center justify-center text-2xl font-bold">
                ←
            </button>
            <button onclick="flipCard()" class="bg-yellow-400 text-yellow-900 w-14 h-14 rounded-full shadow-lg hover:shadow-xl hover:scale-110 transition-all flex items-center justify-center text-2xl font-bold" title="Çevir">
                ↻
            </button>
            <button onclick="nextCard()" class="bg-white text-purple-600 w-14 h-14 rounded-full shadow-lg hover:shadow-xl hover:scale-110 transition-all flex items-center justify-center text-2xl font-bold">
                →
            </button>
        </div>

        <!-- Keyboard Shortcuts Info -->
        <div class="text-center text-white/80 text-sm bg-white/10 backdrop-blur-sm rounded-lg p-4 max-w-md mx-auto">
            <p class="font-semibold mb-2">Klavye Kısayolları:</p>
            <div class="flex justify-center gap-4 flex-wrap">
                <span class="bg-white/20 px-2 py-1 rounded">← Önceki</span>
                <span class="bg-white/20 px-2 py-1 rounded">Space / Enter Çevir</span>
                <span class="bg-white/20 px-2 py-1 rounded">→ Sonraki</span>
            </div>
        </div>
    </div>

    <script>
        // Kelime veritabanı - kategorilere ayrılmış
        const words = [
            // Nesneler
            { en: "Pen", tr: "Tükenmez Kalem", category: "objects", emoji: "🖊️", image: "pen" },
            { en: "Pencil", tr: "Kurşun Kalem", category: "objects", emoji: "✏️", image: "pencil" },
            { en: "Eraser", tr: "Silgi", category: "objects", emoji: "🧼", image: "eraser" },
            { en: "Book", tr: "Kitap", category: "objects", emoji: "📖", image: "book" },
            { en: "Notebook", tr: "Defter", category: "objects", emoji: "📓", image: "notebook" },
            { en: "Chair", tr: "Sandalye", category: "objects", emoji: "🪑", image: "chair" },
            { en: "Table", tr: "Masa", category: "objects", emoji: "🪑", image: "table" },
            { en: "Crayon", tr: "Pastel Boya", category: "objects", emoji: "🖍️", image: "crayon" },
            { en: "Paper", tr: "Kağıt", category: "objects", emoji: "📄", image: "paper" },
            { en: "Paintbrush", tr: "Boya Fırçası", category: "objects", emoji: "🖌️", image: "paintbrush" },
            { en: "Paint", tr: "Boya", category: "objects", emoji: "🎨", image: "paint" },
            { en: "Scissors", tr: "Makas", category: "objects", emoji: "✂️", image: "scissors" },
            { en: "Cup of water", tr: "Bir bardak su", category: "objects", emoji: "🥤", image: "water cup" },
            { en: "Watercolors", tr: "Sulu boyalar", category: "objects", emoji: "🎨", image: "watercolors" },
            { en: "Glue", tr: "Yapıştırıcı", category: "objects", emoji: "🧴", image: "glue" },
            { en: "Cake", tr: "Pasta / Kek", category: "objects", emoji: "🎂", image: "cake" },
            { en: "Motorcycle", tr: "Motosiklet", category: "objects", emoji: "🏍️", image: "motorcycle" },
            { en: "Candy", tr: "Şekerleme", category: "objects", emoji: "🍬", image: "candy" },
            { en: "Candle", tr: "Mum", category: "objects", emoji: "🕯️", image: "candle" },
            { en: "Balloon", tr: "Balon", category: "objects", emoji: "🎈", image: "balloon" },
            { en: "Present", tr: "Hediye", category: "objects", emoji: "🎁", image: "gift" },
            { en: "Party hat", tr: "Parti şapkası", category: "objects", emoji: "🎉", image: "party hat" },
            { en: "Towel", tr: "Havlu", category: "objects", emoji: "🧺", image: "towel" },
            { en: "Backpack", tr: "Sırt çantası", category: "objects", emoji: "🎒", image: "backpack" },
            { en: "Flashlight", tr: "El feneri", category: "objects", emoji: "🔦", image: "flashlight" },
            { en: "Sleeping bag", tr: "Uyku tulumu", category: "objects", emoji: "🛏️", image: "sleeping bag" },
            { en: "Sunglasses", tr: "Güneş gözlüğü", category: "objects", emoji: "🕶️", image: "sunglasses" },
            { en: "Bottle of water", tr: "Bir şişe su", category: "objects", emoji: "💧", image: "water bottle" },
            { en: "Bicycle", tr: "Bisiklet", category: "objects", emoji: "🚲", image: "bicycle" },
            { en: "Tablet", tr: "Tablet", category: "objects", emoji: "📱", image: "tablet" },
            { en: "Colored pencils", tr: "Boya kalemleri", category: "objects", emoji: "✏️", image: "colored pencils" },
            { en: "Puzzle", tr: "Yapboz", category: "objects", emoji: "🧩", image: "puzzle" },
            { en: "Coloring book", tr: "Boyama kitabı", category: "objects", emoji: "📒", image: "coloring book" },
            { en: "Ball", tr: "Top", category: "objects", emoji: "⚽", image: "ball" },
            { en: "Board game", tr: "Masa oyunu", category: "objects", emoji: "🎲", image: "board game" },
            { en: "Dice", tr: "Zar", category: "objects", emoji: "🎲", image: "dice" },
            { en: "Game piece", tr: "Oyun taşı / piyon", category: "objects", emoji: "♟️", image: "game piece" },
            { en: "Screen", tr: "Ekran", category: "objects", emoji: "🖥️", image: "screen" },
            { en: "Stove", tr: "Ocak / Soba", category: "objects", emoji: "🔥", image: "stove" },
            { en: "Bed", tr: "Yatak", category: "objects", emoji: "🛏️", image: "bed" },
            { en: "Roof", tr: "Çatı", category: "objects", emoji: "🏠", image: "roof" },
            { en: "Stairs", tr: "Merdivenler", category: "objects", emoji: "🪜", image: "stairs" },
            { en: "Wig", tr: "Peruk", category: "objects", emoji: "👩‍🦰", image: "wig" },
            { en: "Socks", tr: "Çorap", category: "objects", emoji: "🧦", image: "socks" },
            { en: "T-shirt", tr: "Tişört", category: "objects", emoji: "👕", image: "tshirt" },
            { en: "Hat", tr: "Şapka", category: "objects", emoji: "🧢", image: "hat" },
            { en: "Jacket", tr: "Ceket / Mont", category: "objects", emoji: "🧥", image: "jacket" },
            { en: "Skirt", tr: "Etek", category: "objects", emoji: "👗", image: "skirt" },
            { en: "Glasses", tr: "Gözlük", category: "objects", emoji: "👓", image: "glasses" },

            // Duygular
            { en: "Scared", tr: "Korkmuş", category: "emotions", emoji: "😱", image: "scared" },
            { en: "Hungry", tr: "Aç", category: "emotions", emoji: "🤤", image: "hungry" },
            { en: "Sad", tr: "Üzgün", category: "emotions", emoji: "😢", image: "sad" },
            { en: "Happy", tr: "Mutlu", category: "emotions", emoji: "😊", image: "happy" },
            { en: "Mad", tr: "Kızgın", category: "emotions", emoji: "😠", image: "angry" },
            { en: "Tired", tr: "Yorgun", category: "emotions", emoji: "😴", image: "tired" },
            { en: "Excited", tr: "Heyecanlı", category: "emotions", emoji: "🤩", image: "excited" },
            { en: "Worried", tr: "Endişeli", category: "emotions", emoji: "😰", image: "worried" },

            // Eylemler
            { en: "See", tr: "Görmek", category: "actions", emoji: "👀", image: "see" },
            { en: "Hang up a coat", tr: "Mont asmak", category: "actions", emoji: "🧥", image: "hang coat" },
            { en: "Color", tr: "Boyamak", category: "actions", emoji: "🎨", image: "color" },
            { en: "Sit", tr: "Oturmak", category: "actions", emoji: "🪑", image: "sit" },
            { en: "Use a computer", tr: "Bilgisayar kullanmak", category: "actions", emoji: "💻", image: "use computer" },
            { en: "Say hello", tr: "Merhaba demek", category: "actions", emoji: "👋", image: "say hello" },
            { en: "Wave goodbye", tr: "El sallayarak veda etmek", category: "actions", emoji: "👋", image: "wave goodbye" },
            { en: "Watch videos", tr: "Video izlemek", category: "actions", emoji: "📺", image: "watch videos" },
            { en: "Learn music", tr: "Müzik öğrenmek", category: "actions", emoji: "🎵", image: "learn music" },
            { en: "Speak English", tr: "İngilizce konuşmak", category: "actions", emoji: "🗣️", image: "speak english" },
            { en: "Paint with watercolors", tr: "Sulu boya ile boyamak", category: "actions", emoji: "🎨", image: "paint watercolors" },
            { en: "Read a book", tr: "Kitap okumak", category: "actions", emoji: "📖", image: "read book" },
            { en: "Play on the playground", tr: "Oyun parkında oynamak", category: "actions", emoji: "🎪", image: "playground" },
            { en: "Wait", tr: "Beklemek", category: "actions", emoji: "⏰", image: "wait" },
            { en: "Make", tr: "Yapmak", category: "actions", emoji: "🔨", image: "make" },
            { en: "Bake", tr: "Fırında pişirmek", category: "actions", emoji: "🥧", image: "bake" },
            { en: "Scream", tr: "Çığlık atmak", category: "actions", emoji: "😱", image: "scream" },
            { en: "Frown", tr: "Kaş çatmak", category: "actions", emoji: "😠", image: "frown" },
            { en: "Shout hooray", tr: "Yaşasın diye bağırmak", category: "actions", emoji: "🎉", image: "shout hooray" },
            { en: "Yawn", tr: "Esnemek", category: "actions", emoji: "😮‍💨", image: "yawn" },
            { en: "Cry", tr: "Ağlamak", category: "actions", emoji: "😭", image: "cry" },
            { en: "Laugh", tr: "Gülmek", category: "actions", emoji: "😂", image: "laugh" },
            { en: "Agree", tr: "Katılmak / Aynı fikirde olmak", category: "actions", emoji: "👍", image: "agree" },
            { en: "Disagree", tr: "Katılmamak / Aynı fikirde olmamak", category: "actions", emoji: "👎", image: "disagree" },
            { en: "Make a campfire", tr: "Kamp ateşi yakmak", category: "actions", emoji: "🔥", image: "campfire" },
            { en: "Sing", tr: "Şarkı söylemek", category: "actions", emoji: "🎤", image: "sing" },
            { en: "Hike", tr: "Doğa yürüyüşü yapmak", category: "actions", emoji: "🥾", image: "hike" },
            { en: "Climb", tr: "Tırmanmak", category: "actions", emoji: "🧗", image: "climb" },
            { en: "Read a map", tr: "Harita okumak", category: "actions", emoji: "🗺️", image: "read map" },
            { en: "Go on rides", tr: "Oyuncaklara binmek", category: "actions", emoji: "🎢", image: "rides" },
            { en: "Row a boat", tr: "Sandal çekmek", category: "actions", emoji: "🚣", image: "row boat" },
            { en: "Ride a horse", tr: "Ata binmek", category: "actions", emoji: "🐴", image: "ride horse" },
            { en: "Swim", tr: "Yüzmek", category: "actions", emoji: "🏊", image: "swim" },
            { en: "Go on a hike", tr: "Doğa yürüyüşüne çıkmak", category: "actions", emoji: "🥾", image: "go hike" },
            { en: "Cut", tr: "Kesmek", category: "actions", emoji: "✂️", image: "cut" },
            { en: "Ride bikes", tr: "Bisiklete binmek", category: "actions", emoji: "🚴", image: "ride bikes" },
            { en: "Play soccer", tr: "Futbol oynamak", category: "actions", emoji: "⚽", image: "play soccer" },
            { en: "Play with marbles", tr: "Misketlerle oynamak", category: "actions", emoji: "🔮", image: "play marbles" },
            { en: "Jump rope", tr: "İp atlamak", category: "actions", emoji: "🪢", image: "jump rope" },
            { en: "Draw pictures", tr: "Resim çizmek", category: "actions", emoji: "🎨", image: "draw" },
            { en: "Play with dolls", tr: "Bebeklerle oynamak", category: "actions", emoji: "🪆", image: "play dolls" },
            { en: "Play charades", tr: "Sessiz sinema oynamak", category: "actions", emoji: "🎭", image: "charades" },
            { en: "Win", tr: "Kazanmak", category: "actions", emoji: "🏆", image: "win" },
            { en: "Lose", tr: "Kaybetmek", category: "actions", emoji: "😞", image: "lose" },

            // Renkler
            { en: "Green", tr: "Yeşil", category: "colors", emoji: "🟢", image: "green color" },
            { en: "Blue", tr: "Mavi", category: "colors", emoji: "🔵", image: "blue color" },
            { en: "Orange", tr: "Turuncu", category: "colors", emoji: "🟠", image: "orange color" },
            { en: "Yellow", tr: "Sarı", category: "colors", emoji: "🟡", image: "yellow color" },
            { en: "Purple", tr: "Mor", category: "colors", emoji: "🟣", image: "purple color" },
            { en: "Red", tr: "Kırmızı", category: "colors", emoji: "🔴", image: "red color" },
            { en: "Pink", tr: "Pembe", category: "colors", emoji: "🩷", image: "pink color" },
            { en: "Brown", tr: "Kahverengi", category: "colors", emoji: "🟤", image: "brown color" },
            { en: "White", tr: "Beyaz", category: "colors", emoji: "⚪", image: "white color" },
            { en: "Black", tr: "Siyah", category: "colors", emoji: "⚫", image: "black color" },

            // Sayılar
            { en: "One", tr: "Bir", category: "numbers", emoji: "1️⃣", image: "number one" },
            { en: "Two", tr: "İki", category: "numbers", emoji: "2️⃣", image: "number two" },
            { en: "Three", tr: "Üç", category: "numbers", emoji: "3️⃣", image: "number three" },
            { en: "Four", tr: "Dört", category: "numbers", emoji: "4️⃣", image: "number four" },
            { en: "Five", tr: "Beş", category: "numbers", emoji: "5️⃣", image: "number five" },
            { en: "Six", tr: "Altı", category: "numbers", emoji: "6️⃣", image: "number six" },
            { en: "Seven", tr: "Yedi", category: "numbers", emoji: "7️⃣", image: "number seven" },
            { en: "Eight", tr: "Sekiz", category: "numbers", emoji: "8️⃣", image: "number eight" },
            { en: "Nine", tr: "Dokuz", category: "numbers", emoji: "9️⃣", image: "number nine" },
            { en: "Ten", tr: "On", category: "numbers", emoji: "🔟", image: "number ten" },

            // Vücut
            { en: "Eyes", tr: "Gözler", category: "body", emoji: "👀", image: "eyes" },
            { en: "Nose", tr: "Burun", category: "body", emoji: "👃", image: "nose" },
            { en: "Mouth", tr: "Ağız", category: "body", emoji: "👄", image: "mouth" },
            { en: "Head", tr: "Baş / Kafa", category: "body", emoji: "👤", image: "head" },
            { en: "Ears", tr: "Kulaklar", category: "body", emoji: "👂", image: "ears" },
            { en: "Arms", tr: "Kollar", category: "body", emoji: "💪", image: "arms" },
            { en: "Hands", tr: "Eller", category: "body", emoji: "👐", image: "hands" },
            { en: "Legs", tr: "Bacaklar", category: "body", emoji: "🦵", image: "legs" },
            { en: "Feet", tr: "Ayaklar", category: "body", emoji: "🦶", image: "feet" },
            { en: "Hair", tr: "Saç", category: "body", emoji: "💇", image: "hair" },
            { en: "Teeth", tr: "Dişler", category: "body", emoji: "🦷", image: "teeth" },
            { en: "Tongue", tr: "Dil", category: "body", emoji: "👅", image: "tongue" },
            { en: "Tail", tr: "Kuyruk", category: "body", emoji: "🦨", image: "tail" },
            { en: "Beak", tr: "Gaga", category: "body", emoji: "🐦", image: "beak" },
            { en: "Claw", tr: "Pençe", category: "body", emoji: "🐾", image: "claw" },
            { en: "Fur", tr: "Kürk / Tüy", category: "body", emoji: "🧸", image: "fur" },
            { en: "Wings", tr: "Kanatlar", category: "body", emoji: "🦋", image: "wings" },

            // Aile
            { en: "Mom", tr: "Anne", category: "family", emoji: "👩", image: "mom" },
            { en: "Dad", tr: "Baba", category: "family", emoji: "👨", image: "dad" },
            { en: "Sister", tr: "Kız kardeş", category: "family", emoji: "👧", image: "sister" },
            { en: "Brother", tr: "Erkek kardeş", category: "family", emoji: "👦", image: "brother" },
            { en: "Family", tr: "Aile", category: "family", emoji: "👨‍👩‍👧‍👦", image: "family" },
            { en: "Home", tr: "Ev", category: "family", emoji: "🏠", image: "home" },
            { en: "Friend", tr: "Arkadaş", category: "family", emoji: "🤝", image: "friend" },
            { en: "Girl", tr: "Kız çocuk", category: "family", emoji: "👧", image: "girl" },
            { en: "Boy", tr: "Erkek çocuk", category: "family", emoji: "👦", image: "boy" },
            { en: "Baby", tr: "Bebek", category: "family", emoji: "👶", image: "baby" },

            // Yerler
            { en: "Tree", tr: "Ağaç", category: "places", emoji: "🌳", image: "tree" },
            { en: "Fun park", tr: "Lunapark", category: "places", emoji: "🎡", image: "fun park" },
            { en: "Beach", tr: "Plaj / Sahil", category: "places", emoji: "🏖️", image: "beach" },
            { en: "Mountain", tr: "Dağ", category: "places", emoji: "⛰️", image: "mountain" },
            { en: "Lake", tr: "Göl", category: "places", emoji: "🏞️", image: "lake" },
            { en: "Forest", tr: "Orman", category: "places", emoji: "🌲", image: "forest" },
            { en: "Jungle", tr: "Orman (Balta girmemiş)", category: "places", emoji: "🌴", image: "jungle" },
            { en: "Ocean", tr: "Okyanus", category: "places", emoji: "🌊", image: "ocean" },
            { en: "Land", tr: "Kara / Toprak", category: "places", emoji: "🌍", image: "land" },
            { en: "Dining room", tr: "Yemek odası", category: "places", emoji: "🍽️", image: "dining room" },
            { en: "Living room", tr: "Oturma odası", category: "places", emoji: "🛋️", image: "living room" },
            { en: "Bedroom", tr: "Yatak odası", category: "places", emoji: "🛏️", image: "bedroom" },
            { en: "Kitchen", tr: "Mutfak", category: "places", emoji: "🍳", image: "kitchen" },
            { en: "Apartment", tr: "Apartman dairesi", category: "places", emoji: "🏢", image: "apartment" },
            { en: "Room", tr: "Oda", category: "places", emoji: "🚪", image: "room" },
            { en: "Garden", tr: "Bahçe", category: "places", emoji: "🌻", image: "garden" },
            { en: "Houseboat", tr: "Ev tekne", category: "places", emoji: "🚢", image: "houseboat" },
            { en: "Tree house", tr: "Ağaç ev", category: "places", emoji: "🏕️", image: "tree house" },
            { en: "Igloo", tr: "İglo (Buz ev)", category: "places", emoji: "🧊", image: "igloo" },
            { en: "Hut", tr: "Kulübe", category: "places", emoji: "🏚️", image: "hut" },
            { en: "Country", tr: "Ülke", category: "places", emoji: "🗺️", image: "country" },

            // Hayvanlar
            { en: "Bee", tr: "Arı", category: "animals", emoji: "🐝", image: "bee" },
            { en: "Zebra", tr: "Zebra", category: "animals", emoji: "🦓", image: "zebra" },
            { en: "Elephant", tr: "Fil", category: "animals", emoji: "🐘", image: "elephant" },
            { en: "Octopus", tr: "Ahtapot", category: "animals", emoji: "🐙", image: "octopus" },
            { en: "Dolphin", tr: "Yunus", category: "animals", emoji: "🐬", image: "dolphin" },
            { en: "Crocodile", tr: "Timsah", category: "animals", emoji: "🐊", image: "crocodile" },
            { en: "Parrot", tr: "Papağan", category: "animals", emoji: "🦜", image: "parrot" },
            { en: "Brown bear", tr: "Boz ayı", category: "animals", emoji: "🐻", image: "brown bear" },
            { en: "Blue whale", tr: "Mavi balina", category: "animals", emoji: "🐋", image: "blue whale" },
            { en: "Panda", tr: "Panda", category: "animals", emoji: "🐼", image: "panda" },
            { en: "Penguin", tr: "Penguen", category: "animals", emoji: "🐧", image: "penguin" },
            { en: "Rabbit", tr: "Tavşan", category: "animals", emoji: "🐰", image: "rabbit" },
            { en: "Snake", tr: "Yılan", category: "animals", emoji: "🐍", image: "snake" },
            { en: "Dinosaur", tr: "Dinozor", category: "animals", emoji: "🦕", image: "dinosaur" },

            // Diğer
            { en: "Birthday", tr: "Doğum günü", category: "other", emoji: "🎂", image: "birthday" },
            { en: "Day", tr: "Gün", category: "other", emoji: "📅", image: "day" },
            { en: "May", tr: "Mayıs", category: "other", emoji: "🌸", image: "may" },
            { en: "Flag", tr: "Bayrak", category: "other", emoji: "🚩", image: "flag" },
            { en: "Age", tr: "Yaş", category: "other", emoji: "🎂", image: "age" },
            { en: "Different", tr: "Farklı", category: "other", emoji: "⚖️", image: "different" },
            { en: "Similar", tr: "Benzer", category: "other", emoji: "🤝", image: "similar" },
            { en: "Short", tr: "Kısa", category: "other", emoji: "📏", image: "short" },
            { en: "Long", tr: "Uzun", category: "other", emoji: "📏", image: "long" },
            { en: "Tall", tr: "Uzun (Boy)", category: "other", emoji: "📏", image: "tall" },
            { en: "Curly", tr: "Kıvırcık", category: "other", emoji: "🦱", image: "curly" },
            { en: "Straight", tr: "Düz", category: "other", emoji: "🧑", image: "straight" },
            { en: "Blond", tr: "Sarışın", category: "other", emoji: "👱", image: "blond" },
            { en: "Similarities", tr: "Benzerlikler", category: "other", emoji: "🤝", image: "similarities" },
            { en: "Differences", tr: "Farklılıklar", category: "other", emoji: "⚖️", image: "differences" },
            { en: "Old", tr: "Yaşlı / Eski", category: "other", emoji: "👴", image: "old" },
            { en: "Young", tr: "Genç", category: "other", emoji: "🧒", image: "young" },
            { en: "Fast", tr: "Hızlı", category: "other", emoji: "💨", image: "fast" },
            { en: "Slow", tr: "Yavaş", category: "other", emoji: "🐌", image: "slow" },
            { en: "Real", tr: "Gerçek", category: "other", emoji: "✅", image: "real" },
            { en: "Fantasy", tr: "Hayal ürünü / Fantastik", category: "other", emoji: "🦄", image: "fantasy" },
            { en: "Special", tr: "Özel", category: "other", emoji: "⭐", image: "special" },
            { en: "Favorite", tr: "Favori / En sevilen", category: "other", emoji: "❤️", image: "favorite" },
            { en: "Color", tr: "Renk", category: "other", emoji: "🎨", image: "color" },
            { en: "Family tree", tr: "Soy ağacı", category: "other", emoji: "🌳", image: "family tree" },
            { en: "Square", tr: "Kare", category: "other", emoji: "⬜", image: "square" },
            { en: "Question mark", tr: "Soru işareti", category: "other", emoji: "❓", image: "question mark" },
            { en: "Exclamation point", tr: "Ünlem işareti", category: "other", emoji: "❗", image: "exclamation point" },
            { en: "Moon", tr: "Ay", category: "other", emoji: "🌙", image: "moon" },
            { en: "Sun", tr: "Güneş", category: "other", emoji: "☀️", image: "sun" },
            { en: "Stars", tr: "Yıldızlar", category: "other", emoji: "⭐", image: "stars" },
            { en: "Yes", tr: "Evet", category: "other", emoji: "✅", image: "yes" },
            { en: "No", tr: "Hayır", category: "other", emoji: "❌", image: "no" },
            { en: "Water", tr: "Su", category: "other", emoji: "💧", image: "water" },
            { en: "Big", tr: "Büyük", category: "other", emoji: "⬆️", image: "big" },
            { en: "But", tr: "Ama / Fakat", category: "other", emoji: "⚡", image: "but" },
            { en: "Nut", tr: "Fındık / Kuruyemiş", category: "other", emoji: "🥜", image: "nut" },
            { en: "Fig", tr: "İncir", category: "other", emoji: "🌰", image: "fig" },
            { en: "In", tr: "İçinde", category: "other", emoji: "📦", image: "in" },
            { en: "On", tr: "Üzerinde", category: "other", emoji: "⬆️", image: "on" },
            { en: "Under", tr: "Altında", category: "other", emoji: "⬇️", image: "under" },
            { en: "Action figure", tr: "Aksiyon figürü", category: "other", emoji: "🦸", image: "action figure" },
            { en: "Spaceship", tr: "Uzay gemisi", category: "other", emoji: "🚀", image: "spaceship" },
            { en: "Monkey bars", tr: "Maymun parmaklıkları", category: "other", emoji: "🐒", image: "monkey bars" },
            { en: "Bike", tr: "Bisiklet", category: "other", emoji: "🚲", image: "bike" },
            { en: "Car", tr: "Araba", category: "other", emoji: "🚗", image: "car" },
            { en: "Don't touch", tr: "Dokunma", category: "other", emoji: "🚫", image: "dont touch" },
            { en: "Don't run", tr: "Koşma", category: "other", emoji: "🚫", image: "dont run" },
            { en: "Don't jump", tr: "Zıplama", category: "other", emoji: "🚫", image: "dont jump" },
            { en: "I agree", tr: "Katılıyorum", category: "other", emoji: "👍", image: "i agree" },
            { en: "I disagree", tr: "Katılmıyorum", category: "other", emoji: "👎", image: "i disagree" },
            { en: "You are right", tr: "Haklısın", category: "other", emoji: "✅", image: "you are right" },
            { en: "I think so", tr: "Öyle düşünüyorum", category: "other", emoji: "🤔", image: "i think so" },
            { en: "I don't think so", tr: "Öyle düşünmüyorum", category: "other", emoji: "🤷", image: "i dont think so" },
            { en: "Exactly", tr: "Kesinlikle / Aynen", category: "other", emoji: "🎯", image: "exactly" },
            { en: "Absolutely", tr: "Kesinlikle", category: "other", emoji: "💯", image: "absolutely" },
            { en: "No way", tr: "Asla / Hiç yolu yok", category: "other", emoji: "🚫", image: "no way" },
            { en: "I'm not sure", tr: "Emin değilim", category: "other", emoji: "🤔", image: "not sure" },
            { en: "Me too", tr: "Ben de", category: "other", emoji: "✋", image: "me too" },
            { en: "Me neither", tr: "Ben de (olumsuz)", category: "other", emoji: "✋", image: "me neither" },
            { en: "That's true", tr: "Bu doğru", category: "other", emoji: "✅", image: "thats true" }
        ];

        let currentCategory = 'all';
        let currentIndex = 0;
        let filteredWords = [...words];

        function filterCategory(category) {
            currentCategory = category;
            currentIndex = 0;
            
            // Update buttons
            document.querySelectorAll('.category-btn').forEach(btn => {
                btn.classList.remove('active');
                if(btn.dataset.category === category) {
                    btn.classList.add('active');
                }
            });
            
            // Filter words
            if(category === 'all') {
                filteredWords = [...words];
            } else {
                filteredWords = words.filter(w => w.category === category);
            }
            
            // Shuffle for random order
            filteredWords.sort(() => Math.random() - 0.5);
            
            updateCard();
            updateProgress();
        }

        function updateCard() {
            const word = filteredWords[currentIndex];
            const card = document.getElementById('card');
            
            // Remove flip class to show front
            card.classList.remove('flipped');
            
            setTimeout(() => {
                document.getElementById('englishWord').textContent = word.en;
                document.getElementById('frontEmoji').textContent = word.emoji;
                document.getElementById('turkishWord').textContent = word.tr;
                
                // Set image using Unsplash source
                const imgElement = document.getElementById('wordImage');
                const placeholder = document.getElementById('imagePlaceholder');
                
                // Use specific image search query
                const searchQuery = encodeURIComponent(word.image + ' ' + word.en);
                imgElement.src = `https://source.unsplash.com/400x300/?${searchQuery}`;
                imgElement.classList.remove('hidden');
                placeholder.classList.add('hidden');
                
                // Fallback if image fails
                imgElement.onerror = function() {
                    this.classList.add('hidden');
                    placeholder.classList.remove('hidden');
                    placeholder.textContent = word.emoji;
                };
            }, 200);
        }

        function flipCard() {
            document.getElementById('card').classList.toggle('flipped');
        }

        function nextCard() {
            if(currentIndex < filteredWords.length - 1) {
                currentIndex++;
                updateCard();
                updateProgress();
            } else {
                // Loop back to start
                currentIndex = 0;
                updateCard();
                updateProgress();
            }
        }

        function previousCard() {
            if(currentIndex > 0) {
                currentIndex--;
                updateCard();
                updateProgress();
            } else {
                // Loop to end
                currentIndex = filteredWords.length - 1;
                updateCard();
                updateProgress();
            }
        }

        function updateProgress() {
            document.getElementById('currentIndex').textContent = currentIndex + 1;
            document.getElementById('totalCount').textContent = filteredWords.length;
            const progress = ((currentIndex + 1) / filteredWords.length) * 100;
            document.getElementById('progressBar').style.width = progress + '%';
        }

        // Keyboard navigation
        document.addEventListener('keydown', (e) => {
            if(e.key === 'ArrowRight') nextCard();
            if(e.key === 'ArrowLeft') previousCard();
            if(e.key === ' ' || e.key === 'Enter') {
                e.preventDefault();
                flipCard();
            }
        });

        // Initialize
        filterCategory('all');
    </script>
</body>
</html>
