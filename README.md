# and-they-were-roommates-
school project
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
body {
    margin: 0;
    font-family: "Georgia", serif;
    background: #ffe6ee;
    overflow-x: hidden;
}

header {
    background: #ff9fbd;
    color: white;
    padding: 20px;
    text-align: center;
    box-shadow: 0 3px 10px rgba(255, 150, 180, 0.4);
}

nav button {
    background: #ff77a9;
    color: white;
    border: none;
    padding: 10px 18px;
    margin: 5px;
    cursor: pointer;
    border-radius: 50px;
    font-size: 15px;
    transition: 0.3s;
}

nav button:hover {
    background: #ff4d87;
    transform: scale(1.08);
}

main {
    padding: 25px;
}

.screen {
    display: none;
    opacity: 0;
    animation: fade 0.7s forwards;
    background: white;
    padding: 20px;
    border-radius: 18px;
    box-shadow: 0 0 15px rgba(255, 120, 160, 0.25);
}

.visible {
    display: block !important;
}

@keyframes fade {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
}

.typing {
    width: 100%;
    overflow: hidden;
    white-space: nowrap;
    border-right: 3px solid white;
    animation: typing 3s steps(30), blink .7s infinite;
}

@keyframes typing {
    from { width: 0; }
}

@keyframes blink {
    50% { border-color: transparent; }
}

.blog-create textarea {
    width: 100%;
    height: 70px;
    padding: 10px;
    border-radius: 8px;
    border: 2px solid #ff9fbd;
    background: #fff0f6;
}

.blog-create button {
    margin-top: 10px;
    background: #ff77a9;
    color: white;
    border: none;
    padding: 10px 20px;
    border-radius: 50px;
    cursor: pointer;
}

#blogPosts {
    margin-top: 20px;
}

.post {
    background: #fff1f6;
    padding: 15px;
    border-radius: 12px;
    margin-bottom: 15px;
    box-shadow: 0 0 10px rgba(255, 120, 160, 0.3);
}

.post button {
    background: #ff4d87;
    color: white;
    border: none;
    padding: 6px 10px;
    border-radius: 6px;
    margin-right: 5px;
    cursor: pointer;
}

.heart-cursor span {
    position: fixed;
    pointer-events: none;
    animation: heartFloat 1s ease-out forwards;
    font-size: 20px;
    color: #ff8eb7;
}

@keyframes heartFloat {
    from { transform: translateY(0) scale(1); opacity: 1; }
    to { transform: translateY(-40px) scale(1.6); opacity: 0; }
}
function playBoop() {
    document.getElementById("boopSound").play();
}

function showScreen(name) {
    playBoop();
    document.querySelectorAll(".screen").forEach(s => s.classList.remove("visible"));
    document.getElementById(name).classList.add("visible");
}

function addPost() {
    playBoop();
    let text = document.getElementById("newPostText").value.trim();
    if (text === "") return;

    let post = document.createElement("div");
    post.className = "post";

    post.innerHTML = `
        <p class="content">${text}</p>
        <button onclick="editPost(this)">Edit</button>
        <button onclick="deletePost(this)">Delete</button>
    `;

    document.getElementById("blogPosts").appendChild(post);
    document.getElementById("newPostText").value = "";
}

function deletePost(btn) {
    playBoop();
    btn.parentElement.remove();
}

function editPost(btn) {
    playBoop();
    let post = btn.parentElement;
    let text = post.querySelector(".content").innerText;

    let newText = prompt("Edit your post:", text);
    if (newText !== null) {
        post.querySelector(".content").innerText = newText;
    }
}

document.addEventListener("mousemove", function(e) {
    let heart = document.createElement("span");
    heart.innerText = "❥";
    heart.style.left = e.pageX + "px";
    heart.style.top = e.pageY + "px";
    document.body.appendChild(heart);

    setTimeout(() => {
        heart.remove();
    }, 1000);
});