# sahil
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Netflix Clone</title>
    <style>
        body {
            background-color: black;
            color: white;
            font-family: Arial, sans-serif;
            text-align: center;
        }
        .movie-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 50px;
        }
        .movie-card {
            background-color: #333;
            padding: 20px;
            border-radius: 10px;
            width: 200px;
        }
        .movie-card img {
            width: 100%;
            border-radius: 10px;
        }
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            display: none;
        }
        .modal-content {
            background-color: #222;
            padding: 20px;
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <h1>Netflix Clone</h1>
    <div class="movie-container" id="movieContainer"></div>
    <div class="modal" id="movieModal">
        <div class="modal-content">
            <h2 id="modalTitle"></h2>
            <p id="modalDescription"></p>
            <button onclick="closeModal()">Close</button>
        </div>
    </div>
    <script>
        const movies = [
            { title: "Inception", description: "A mind-bending thriller.", image: "https://image.tmdb.org/t/p/w500/qmDpIHrmpJINaRKAfWQfftjCdyi.jpg" },
            { title: "Breaking Bad", description: "A high school teacher turns into a drug lord.", image: "https://image.tmdb.org/t/p/w500/eSzpy96DwBujGFj0xMbXBcGcfxX.jpg" },
            { title: "Interstellar", description: "A journey beyond the stars.", image: "https://image.tmdb.org/t/p/w500/rAiYTfKGqDCRIIqo664sY9XZIvQ.jpg" }
        ];

        function loadMovies() {
            const container = document.getElementById('movieContainer');
            movies.forEach(movie => {
                const movieCard = document.createElement('div');
                movieCard.classList.add('movie-card');
                movieCard.innerHTML = `
                    <img src="${movie.image}" alt="${movie.title}">
                    <h3>${movie.title}</h3>
                `;
                movieCard.onclick = () => showModal(movie.title, movie.description);
                container.appendChild(movieCard);
            });
        }

        function showModal(title, description) {
            document.getElementById('modalTitle').innerText = title;
            document.getElementById('modalDescription').innerText = description;
            document.getElementById('movieModal').style.display = 'flex';
        }

        function closeModal() {
            document.getElementById('movieModal').style.display = 'none';
        }

        window.onload = loadMovies;
    </script>
</body>
</html>

