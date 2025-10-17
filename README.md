
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FLIX MOVIES - Movies</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1a1a2e, #16213e);
            color: white;
            min-height: 100vh;
        }

        .header {
            background: rgba(0, 0, 0, 0.95);
            padding: 1rem 2rem;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 20px rgba(229, 9, 20, 0.3);
        }

        .nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 2rem;
            font-weight: bold;
            color: #e50914;
            text-decoration: none;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            align-items: center;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            transition: color 0.3s;
            font-weight: 500;
        }

        .nav-links a:hover {
            color: #e50914;
        }

        .language-switcher {
            background: #007bff;
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 5px;
            cursor: pointer;
            font-size: 0.9rem;
        }

        .main-content {
            margin-top: 80px;
            padding: 2rem;
        }

        .section-title {
            font-size: 1.8rem;
            margin-bottom: 1.5rem;
            color: #e50914;
            border-left: 4px solid #e50914;
            padding-left: 1rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .movies-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
            margin-bottom: 3rem;
        }

        .movie-card {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            overflow: hidden;
            transition: all 0.3s ease;
            cursor: pointer;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .movie-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 35px rgba(229, 9, 20, 0.4);
        }

        .movie-thumbnail {
            width: 100%;
            height: 400px;
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            position: relative;
        }

        .movie-play-btn {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(229, 9, 20, 0.9);
            color: white;
            border: none;
            border-radius: 50%;
            width: 60px;
            height: 60px;
            font-size: 1.5rem;
            cursor: pointer;
            opacity: 0;
            transition: opacity 0.3s;
        }

        .movie-card:hover .movie-play-btn {
            opacity: 1;
        }

        .movie-info {
            padding: 1.2rem;
        }

        .movie-title {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
            color: white;
        }

        .movie-year {
            color: #ccc;
            font-size: 0.9rem;
            margin-bottom: 0.3rem;
        }

        .movie-quality {
            background: #e50914;
            color: white;
            padding: 0.2rem 0.6rem;
            border-radius: 4px;
            font-size: 0.8rem;
            font-weight: bold;
        }

        .video-player {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.98);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 2000;
        }

        .video-container {
            width: 90%;
            max-width: 1100px;
            position: relative;
        }

        .close-btn {
            position: absolute;
            top: -50px;
            right: 0;
            background: #e50914;
            color: white;
            border: none;
            padding: 0.7rem 1.2rem;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: bold;
        }

        video {
            width: 100%;
            height: auto;
            border-radius: 10px;
        }

        .no-movies {
            text-align: center;
            padding: 3rem;
            color: #ccc;
            grid-column: 1 / -1;
        }

        .admin-section {
            background: rgba(255, 255, 255, 0.1);
            padding: 2rem;
            border-radius: 15px;
            margin-bottom: 2rem;
            display: none;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: bold;
        }

        .form-group input, .form-group select {
            width: 100%;
            padding: 0.8rem;
            border: none;
            border-radius: 8px;
            background: rgba(255, 255, 255, 0.9);
            font-size: 1rem;
        }

        .upload-btn {
            background: #e50914;
            color: white;
            border: none;
            padding: 1rem 2rem;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: bold;
            width: 100%;
        }

        .jm4-admin-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #007bff;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 8px;
            cursor: pointer;
            z-index: 3000;
            font-weight: bold;
            font-size: 14px;
            box-shadow: 0 4px 12px rgba(0, 123, 255, 0.3);
            transition: all 0.3s ease;
        }

        .jm4-admin-btn:hover {
            background: #0056b3;
            transform: translateY(-2px);
            box-shadow: 0 6px 16px rgba(0, 123, 255, 0.4);
        }

        .login-form {
            max-width: 400px;
            margin: 2rem auto;
            background: rgba(255, 255, 255, 0.1);
            padding: 2rem;
            border-radius: 15px;
            display: none;
        }

        @media (max-width: 768px) {
            .movies-grid {
                grid-template-columns: 1fr;
            }
            .movie-thumbnail {
                height: 300px;
            }
            .jm4-admin-btn {
                bottom: 15px;
                right: 15px;
                font-size: 12px;
                padding: 8px 12px;
            }
        }
    </style>
</head>
<body>
    <header class="header">
        <nav class="nav">
            <a href="#" class="logo">FLIX MOVIES</a>
            <div class="nav-links">
                <a href="#movies" data-en="All Movies" data-sw="Filamu Zote">All Movies</a>
                <button class="language-switcher" id="languageSwitcher">SW</button>
            </div>
        </nav>
    </header>

    <main class="main-content">
        <!-- Secret Admin Login -->
        <div id="adminLogin" class="login-form">
            <h2 class="section-title" data-en="Admin Login" data-sw="Admin Login">Admin Login</h2>
            <form id="loginForm">
                <div class="form-group">
                    <label for="password" data-en="Password:" data-sw="Password:">Password:</label>
                    <input type="password" id="password" required>
                </div>
                <button type="submit" class="upload-btn" data-en="Login" data-sw="Ingia">Login</button>
            </form>
        </div>

        <!-- Secret Admin Section -->
        <div id="adminSection" class="admin-section">
            <h2 class="section-title" data-en="Add New Movie" data-sw="Ongeza Filamu Mpya">Add New Movie</h2>
            <form id="movieForm">
                <div class="form-group">
                    <label for="title" data-en="Movie Title:" data-sw="Jina la Filamu:">Movie Title:</label>
                    <input type="text" id="title" required>
                </div>
                
                <div class="form-group">
                    <label for="year" data-en="Year:" data-sw="Mwaka:">Year:</label>
                    <input type="text" id="year" required>
                </div>
                
                <div class="form-group">
                    <label for="category" data-en="Category:" data-sw="Aina ya Filamu:">Category:</label>
                    <select id="category" required>
                        <option value="" data-en="Select Category" data-sw="Chagua Aina">Select Category</option>
                        <option value="Action">Action</option>
                        <option value="Drama">Drama</option>
                        <option value="Comedy">Comedy</option>
                        <option value="Romance">Romance</option>
                        <option value="Adventure">Adventure</option>
                        <option value="Mystery">Mystery</option>
                        <option value="Horror">Horror</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="quality" data-en="Video Quality:" data-sw="Ubora wa Video:">Video Quality:</label>
                    <select id="quality" required>
                        <option value="" data-en="Select Quality" data-sw="Chagua Ubora">Select Quality</option>
                        <option value="HD">HD</option>
                        <option value="FHD">FHD</option>
                        <option value="4K">4K</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="coverUrl" data-en="Cover Image URL:" data-sw="URL ya Picha ya Cover:">Cover Image URL:</label>
                    <input type="url" id="coverUrl" required>
                </div>
                
                <div class="form-group">
                    <label for="videoUrl" data-en="Video URL:" data-sw="URL ya Video:">Video URL:</label>
                    <input type="url" id="videoUrl" required>
                </div>
                
                <button type="submit" class="upload-btn" data-en="Add Movie" data-sw="Ongeza Filamu">Add Movie</button>
            </form>

            <div style="margin-top: 2rem;">
                <h3 class="section-title" data-en="Existing Movies" data-sw="Filamu Zilizopo">Existing Movies</h3>
                <div id="moviesList">
                    <!-- Movies list will appear here -->
                </div>
            </div>
        </div>

        <!-- Movies Section -->
        <section id="movies">
            <h2 class="section-title" data-en="All Movies" data-sw="Filamu Zote">All Movies</h2>
            <div class="movies-grid" id="moviesGrid">
                <!-- Movies will load here -->
            </div>
        </section>
    </main>

    <!-- JM4 Admin Button (blue button) -->
    <button class="jm4-admin-btn" id="jm4AdminBtn" title="Admin Panel">JM4</button>

    <div class="video-player" id="videoPlayer">
        <div class="video-container">
            <button class="close-btn" onclick="closeVideo()" data-en="Close ✕" data-sw="Funga ✕">Close ✕</button>
            <video id="movieVideo" controls>
                Your browser doesn't support video.
            </video>
        </div>
    </div>

    <script>
        const ADMIN_PASSWORD = "usenge6014";
        let isAdminLoggedIn = false;
        let currentLanguage = 'en'; // Default language is English

        // Language translations
        const translations = {
            en: {
                noMoviesTitle: "No Movies Available",
                noMoviesText: "Movies will be added soon",
                deleteConfirm: "Are you sure you want to delete this movie?",
                movieDeleted: "Movie deleted!",
                loginSuccess: "Successfully logged in as Admin!",
                wrongPassword: "Wrong password!",
                loginFirst: "Please login first as admin!",
                movieAdded: "Movie added successfully!",
                appTitle: "FLIX MOVIES - Movies"
            },
            sw: {
                noMoviesTitle: "Hakuna Filamu Zilizopakuliwa Bado",
                noMoviesText: "Filamu zitaongezwa hivi karibuni",
                deleteConfirm: "Una uhakika unataka kufuta filamu hii?",
                movieDeleted: "Filamu imefutwa!",
                loginSuccess: "Umelingia kikamilifu kama Admin!",
                wrongPassword: "Password si sahihi!",
                loginFirst: "Tafuta lingia kwanza kama admin!",
                movieAdded: "Filamu imeongezwa kikamilifu!",
                appTitle: "FLIX MOVIS - Filamu"
            }
        };

        // Load movies from localStorage
        let movies = JSON.parse(localStorage.getItem('flixmovis_movies')) || [];

        const moviesGrid = document.getElementById('moviesGrid');
        const adminSection = document.getElementById('adminSection');
        const adminLogin = document.getElementById('adminLogin');
        const jm4AdminBtn = document.getElementById('jm4AdminBtn');
        const languageSwitcher = document.getElementById('languageSwitcher');

        // Language switching function
        function switchLanguage(lang) {
            currentLanguage = lang;
            
            // Update all elements with data attributes
            document.querySelectorAll('[data-en]').forEach(element => {
                element.textContent = element.getAttribute(`data-${lang}`);
            });
            
            // Update page title
            document.title = translations[lang].appTitle;
            
            // Update language switcher button
            languageSwitcher.textContent = lang === 'en' ? 'SW' : 'EN';
            
            // Reload movies to update any dynamic text
            loadMovies();
            if (isAdminLoggedIn) {
                loadMoviesList();
            }
        }

        // Language switcher event
        languageSwitcher.addEventListener('click', function() {
            const newLang = currentLanguage === 'en' ? 'sw' : 'en';
            switchLanguage(newLang);
        });

        // JM4 admin button click
        jm4AdminBtn.addEventListener('click', function() {
            if (!isAdminLoggedIn) {
                adminLogin.style.display = 'block';
                adminSection.style.display = 'none';
            } else {
                adminSection.style.display = 'block';
                adminLogin.style.display = 'none';
            }
        });

        // Login form handler
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const password = document.getElementById('password').value;
            
            if (password === ADMIN_PASSWORD) {
                isAdminLoggedIn = true;
                adminLogin.style.display = 'none';
                adminSection.style.display = 'block';
                loadMoviesList();
                alert(translations[currentLanguage].loginSuccess);
            } else {
                alert(translations[currentLanguage].wrongPassword);
            }
        });

        // Movie form handler
        document.getElementById('movieForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!isAdminLoggedIn) {
                alert(translations[currentLanguage].loginFirst);
                return;
            }

            const newMovie = {
                id: Date.now(),
                title: document.getElementById('title').value,
                year: document.getElementById('year').value,
                category: document.getElementById('category').value,
                quality: document.getElementById('quality').value,
                coverUrl: document.getElementById('coverUrl').value,
                videoUrl: document.getElementById('videoUrl').value
            };

            movies.push(newMovie);
            localStorage.setItem('flixmovis_movies', JSON.stringify(movies));
            
            alert(translations[currentLanguage].movieAdded);
            this.reset();
            loadMovies();
            loadMoviesList();
        });

        function loadMovies() {
            moviesGrid.innerHTML = '';

            if (movies.length === 0) {
                moviesGrid.innerHTML = `
                    <div class="no-movies">
                        <h3>${translations[currentLanguage].noMoviesTitle}</h3>
                        <p>${translations[currentLanguage].noMoviesText}</p>
                    </div>
                `;
                return;
            }

            movies.forEach(movie => {
                const movieCard = document.createElement('div');
                movieCard.className = 'movie-card';
                movieCard.innerHTML = `
                    <div class="movie-thumbnail" style="background-image: url('${movie.coverUrl}')">
                        <button class="movie-play-btn">▶</button>
                    </div>
                    <div class="movie-info">
                        <div class="movie-title">${movie.title}</div>
                        <div class="movie-year">${movie.year} • ${movie.category}</div>
                        <div class="movie-quality">${movie.quality}</div>
                    </div>
                `;
                
                // Add click event for play button
                const playBtn = movieCard.querySelector('.movie-play-btn');
                playBtn.addEventListener('click', () => playVideo(movie.videoUrl, movie.title));
                
                moviesGrid.appendChild(movieCard);
            });
        }

        function loadMoviesList() {
            const moviesList = document.getElementById('moviesList');
            moviesList.innerHTML = '';

            movies.forEach((movie, index) => {
                const movieItem = document.createElement('div');
                movieItem.className = 'movie-item';
                movieItem.style.cssText = 'background: rgba(255,255,255,0.05); padding: 1rem; margin-bottom: 0.5rem; border-radius: 8px; display: flex; justify-content: space-between; align-items: center;';
                movieItem.innerHTML = `
                    <div>
                        <strong>${movie.title}</strong> (${movie.year}) - ${movie.category}
                    </div>
                    <button onclick="deleteMovie(${index})" style="background: #ff4444; color: white; border: none; padding: 0.5rem 1rem; border-radius: 5px; cursor: pointer;">
                        ${currentLanguage === 'en' ? 'Delete' : 'Futa'}
                    </button>
                `;
                moviesList.appendChild(movieItem);
            });
        }

        function deleteMovie(index) {
            if (confirm(translations[currentLanguage].deleteConfirm)) {
                movies.splice(index, 1);
                localStorage.setItem('flixmovis_movies', JSON.stringify(movies));
                loadMovies();
                loadMoviesList();
                alert(translations[currentLanguage].movieDeleted);
            }
        }

        function playVideo(videoUrl, title) {
            const player = document.getElementById('videoPlayer');
            const video = document.getElementById('movieVideo');
            
            video.src = videoUrl;
            document.title = title + ' - FLIX MOVIES';
            player.style.display = 'flex';
            video.play();
        }

        function closeVideo() {
            const player = document.getElementById('videoPlayer');
            const video = document.getElementById('movieVideo');
            
            video.pause();
            video.src = '';
            player.style.display = 'none';
            document.title = translations[currentLanguage].appTitle;
        }

        // Close video when clicking outside
        document.getElementById('videoPlayer').addEventListener('click', function(e) {
            if (e.target === this) closeVideo();
        });

        // Initialize the app
        loadMovies();
        
        // Set initial language to English
        switchLanguage('en');
    </script>
</body>
</html>
