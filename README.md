<!DOCTYPE html>
<html lang="lv">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HiApp</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>HiApp</h1>
        <p>Sveiki! Iepazīsimies, labi?</p>
        <input type="text" id="nameInput" placeholder="Kā tevi sauc?">
        <button onclick="saveName()">Gatavs!</button>
    </div>

    <script>
        function saveName() {
            const name = document.getElementById("nameInput").value;
            if (name.trim() !== "") {
                localStorage.setItem("username", name);
                window.location.href = "question.html";
            } else {
                alert("Lūdzu, ievadiet savu vārdu!");
            }
        }
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="lv">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HiApp</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1 id="greeting"></h1>
        <p>Kāpēc lejupielādējāt HiApp?</p>

        <label><input type="radio" name="reason" value="public"> Man ir bail no publiskas uzstāšanās</label>
        <label><input type="radio" name="reason" value="strangers"> Man ir bail komunicēt ar svešiniekiem</label>
        <label><input type="radio" name="reason" value="judgment"> Es baidos, ka mani tiesās par manu viedokli</label>
        <label><input type="radio" name="reason" value="confidence"> Es neesmu pārliecināts(-ta) par sevi</label>

        <button onclick="saveReason()">Gatavs!</button>
    </div>

    <script>
        document.addEventListener("DOMContentLoaded", function() {
            const name = localStorage.getItem("username");
            document.getElementById("greeting").innerText = "Sveiki, " + (name || "draugs") + "!";
        });

        function saveReason() {
            const reason = document.querySelector('input[name="reason"]:checked');
            if (reason) {
                localStorage.setItem("reason", reason.value);
                window.location.href = "task.html";
            } else {
                alert("Lūdzu, izvēlieties vienu variantu!");
            }
        }
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="lv">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HiApp</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <header>
            <span>Atliktie uzdevumi: <strong>0</strong></span>
            <span>Lietotāju reitings: <strong>101. vieta</strong></span>
            <span>Pašreizējā sērija: <strong>1</strong></span>
        </header>

        <h2 id="date"></h2>
        <p class="task">Tavs šodienas uzdevums:</p>
        <p class="challenge">Uzdod jautājumu nepazīstamam cilvēkam!</p>
        <p class="example">Piemēram: cik ir pulkstenis?</p>
    </div>

    <script>
        document.addEventListener("DOMContentLoaded", function() {
            const today = new Date();
            const formattedDate = today.toLocaleDateString("lv-LV", { day: '2-digit', month: '2-digit', year: '2-digit', weekday: 'long' });
            document.getElementById("date").innerText = formattedDate.charAt(0).toUpperCase() + formattedDate.slice(1);
        });
    </script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #1e1e3f;
    color: white;
    text-align: center;
    margin: 0;
    padding: 0;
}

.container {
    width: 90%;
    max-width: 400px;
    margin: 50px auto;
    background: #2e2e5e;
    padding: 20px;
    border-radius: 10px;
}

h1 {
    font-size: 24px;
    font-weight: bold;
}

p {
    font-size: 18px;
}

input, button {
    width: 100%;
    padding: 10px;
    margin-top: 10px;
    border: none;
    border-radius: 5px;
}

input {
    background: #6a6aad;
    color: white;
    text-align: center;
    font-size: 16px;
}

button {
    background: #4a4aff;
    color: white;
    cursor: pointer;
    font-size: 18px;
}

button:hover {
    background: #2a2a9f;
}

label {
    display: block;
    background: #6a6aad;
    padding: 10px;
    margin: 5px 0;
    border-radius: 5px;
    cursor: pointer;
}

input[type="radio"] {
    margin-right: 10px;
}

header {
    display: flex;
    justify-content: space-between;
    background: #444466;
    padding: 10px;
    border-radius: 10px;
}

.task {
    font-size: 20px;
    font-weight: bold;
}

.challenge {
    font-size: 22px;
    color: #4a4aff;
}

.example {
    font-size: 16px;
    font-style: italic;
    color: #aaa;
}
