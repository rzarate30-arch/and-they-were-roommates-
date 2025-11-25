<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>and he was my roommate.</title>
    <link rel="stylesheet" href="style.css" />
</head>
<body>

    <audio id="boopSound" src="https://cdn.pixabay.com/download/audio/2021/08/04/audio_7e78090cdf.mp3?filename=click-124467.mp3"></audio>

    <div class="heart-cursor"></div>

    <header>
        <h1 class="typing">💗 and he was my roommate. 💗</h1>

        <nav>
            <button onclick="showScreen('me')">Me</button>
            <button onclick="showScreen('blog')">Blog</button>
            <button onclick="showScreen('updates')">Updates</button>
            <button onclick="showScreen('diary')">Diary</button>
            <button onclick="showScreen('twitter')">Twitter</button>
        </nav>
    </header>

    <main>
        <section id="me" class="screen visible">
            <h2>About Me</h2>
            <p>Welcome to my soft, dreamy, love-themed corner of the internet. 💕</p>
        </section>

        <section id="blog" class="screen">
            <h2>Blog</h2>

            <div class="blog-create">
                <textarea id="newPostText" placeholder="Write something..."></textarea>
                <button onclick="addPost()">Post</button>
            </div>

            <div id="blogPosts"></div>
        </section>

        <section id="updates" class="screen">
            <h2>Updates</h2>
            <p>Recent news or cute life updates go here. 🌸</p>
        </section>

        <section id="diary" class="screen">
            <h2>Diary</h2>
            <p>Your deepest thoughts live here. 🌙</p>
        </section>

        <section id="twitter" class="screen">
            <h2>Twitter</h2>
            <p>Link or embed tweets here. 💌</p>
        </section>
    </main>

    <script src="script.js"></script>
</body>
</html>