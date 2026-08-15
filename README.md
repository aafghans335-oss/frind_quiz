
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>گفت‌وگوی دوستانه</title>

<style>
    * {
        box-sizing: border-box;
    }

    body {
        margin: 0;
        min-height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        font-family: Tahoma, sans-serif;
        background: linear-gradient(135deg, #16001f, #3b0050, #080808);
        color: white;
        overflow: hidden;
    }

    .box {
        width: 90%;
        max-width: 420px;
        padding: 30px 20px;
        text-align: center;
        background: rgba(255,255,255,0.08);
        border: 1px solid rgba(255,255,255,0.15);
        border-radius: 25px;
        box-shadow: 0 0 35px rgba(255,0,180,0.25);
    }

    h1 {
        font-size: 25px;
        margin-bottom: 25px;
    }

    h2 {
        line-height: 1.8;
        font-size: 21px;
    }

    input {
        width: 90%;
        padding: 14px;
        margin: 15px 0;
        border: none;
        outline: none;
        border-radius: 12px;
        text-align: center;
        font-size: 17px;
    }

    button {
        padding: 13px 25px;
        margin: 6px;
        border: none;
        border-radius: 12px;
        font-size: 17px;
        cursor: pointer;
    }

    button:active {
        transform: scale(0.95);
    }

    #message {
        margin-top: 20px;
        min-height: 30px;
        font-size: 18px;
        line-height: 1.8;
    }

    #final {
        display: none;
    }

    .heart {
        font-size: 60px;
        animation: beat 1s infinite;
    }

    .rainbow-name {
        font-size: 30px;
        font-weight: bold;

        background: linear-gradient(
            90deg,
            red,
            orange,
            yellow,
            lime,
            cyan,
            blue,
            violet,
            red
        );

        background-size: 400%;
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;

        animation: rainbow 4s linear infinite;
    }

    @keyframes rainbow {
        0% {
            background-position: 0%;
        }

        100% {
            background-position: 400%;
        }
    }

    @keyframes beat {
        50% {
            transform: scale(1.25);
        }
    }

    .party {
        position: fixed;
        top: -50px;
        font-size: 28px;
        animation: fall 3s linear forwards;
        pointer-events: none;
    }

    @keyframes fall {
        from {
            transform: translateY(-50px) rotate(0deg);
        }

        to {
            transform: translateY(110vh) rotate(360deg);
        }
    }
</style>
</head>

<body>

<div class="box" id="quiz">

    <h1>✨ یک گفت‌وگوی شیرین ✨</h1>

    <h2 id="question">
        سلام! 😊 اسمت چیه؟
    </h2>

    <div id="area">

        <input
            id="name"
            type="text"
            placeholder="اسمت را بنویس"
        >

        <br>

        <button onclick="nameAnswer()">
            ادامه 🌟
        </button>

    </div>

    <div id="message"></div>

</div>


<div class="box" id="final">

    <div class="heart">❤️</div>

    <h1>🎉 خوشحال شدم! 🎉</h1>

    <h2>
        ممنون که وقتت را برای
    </h2>

    <div class="rainbow-name">
        صالح آراوین نوا
    </div>

    <h2>
        گذاشتی! 🌟
    </h2>

    <p>
        😊 خوشحالم که تا آخر همراه بودی!
    </p>

</div>


<script>

function nameAnswer() {

    const name =
        document.getElementById("name").value.trim();

    if (name === "") {

        document.getElementById("message").innerText =
            "اول اسمت را بنویس 😊";

        return;
    }

    document.getElementById("question").innerText =
        "آیا با من دوست میشی؟ 🤝";

    document.getElementById("message").innerText =
        name + "، چه اسم قشنگی! ✨";

    document.getElementById("area").innerHTML = `

        <button onclick="friendAnswer(true)">
            بلی ❤️
        </button>

        <button onclick="friendAnswer(false)">
            نه 😅
        </button>

    `;
}


function friendAnswer(answer) {

    if (answer) {

        document.getElementById("message").innerText =
            "چه خوب! 😍 یک دوست جدید پیدا کردم!";

    } else {

        document.getElementById("message").innerText =
            "حیف شد 😅";

    }

    document.getElementById("question").innerText =
        "خوب چند سالته؟ 😊";

    document.getElementById("area").innerHTML = `

        <input
            id="age"
            type="number"
            placeholder="سنت را بنویس"
        >

        <br>

        <button onclick="ageAnswer()">
            ادامه 🌟
        </button>

    `;
}


function ageAnswer() {

    const age =
        document.getElementById("age").value;

    if (age === "") {

        document.getElementById("message").innerText =
            "اول سنت را بنویس 😊";

        return;
    }

    document.getElementById("quiz").style.display =
        "none";

    document.getElementById("final").style.display =
        "block";

    partyAnimation();
}


function partyAnimation() {

    const emojis = [
        "🎉",
        "🎊",
        "✨",
        "🎈",
        "🌟",
        "😊",
        "❤️"
    ];

    for (let i = 0; i < 35; i++) {

        const item =
            document.createElement("div");

        item.className = "party";

        item.innerText =
            emojis[
                Math.floor(
                    Math.random() * emojis.length
                )
            ];

        item.style.left =
            Math.random() * 100 + "%";

        item.style.animationDelay =
            Math.random() * 2 + "s";

        document.body.appendChild(item);
    }
}

</script>

</body>
</html># saleh-friend