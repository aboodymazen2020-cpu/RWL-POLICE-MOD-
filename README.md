<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>RWL | POLICE MOD</title>

<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: linear-gradient(180deg, #0a0f1f, #0f1c2e);
    color: white;
    text-align: center;
}

header {
    padding: 30px;
    background: #0d1b2a;
    box-shadow: 0 0 20px #00bfff;
}

.logo {
    width: 180px;
    border-radius: 15px;
    box-shadow: 0 0 20px #00bfff;
}

h1 {
    color: #00bfff;
    font-size: 40px;
}

.ip-box {
    margin-top: 20px;
    background: #001f3f;
    padding: 15px;
    border-radius: 10px;
    display: inline-block;
    box-shadow: 0 0 10px #00bfff;
}

.btn {
    display: inline-block;
    padding: 12px 25px;
    margin: 10px;
    background: #00bfff;
    color: black;
    text-decoration: none;
    border-radius: 8px;
    font-weight: bold;
    cursor: pointer;
}

.section {
    padding: 60px 20px;
}

.card {
    background: rgba(255,255,255,0.05);
    padding: 25px;
    margin: 20px auto;
    width: 85%;
    border-radius: 12px;
    box-shadow: 0 0 15px rgba(0,191,255,0.3);
}

input, textarea, select {
    width: 90%;
    padding: 10px;
    margin: 8px 0;
    border-radius: 6px;
    border: none;
}

footer {
    padding: 20px;
    background: #0d1b2a;
}
</style>
</head>

<body>

<header>
   <img class="logo" src="./logo.gif" alt="لوغو RWL | POLICE MOD">
    <h1>RWL | POLICE MOD</h1>

    <div class="ip-box">
        <p><strong>IP السيرفر:</strong></p>
        <p id="serverIP">connect dag6oj</p>
        <button class="btn" onclick="copyIP()">نسخ IP</button>
    </div>

    <br>
    <a href="#apply" class="btn">التقديم على الشرطة</a>
    <a href="https://discord.gg/rwl" class="btn" target="_blank">دخول الديسكورد</a>
</header>

<div class="section">
    <div class="card">
        <h2>عن السيرفر</h2>
        <p>
        سيرفر RWL | POLICE MOD يقدم تجربة رول بلاي احترافية داخل FiveM
        مع نظام ترقيات، مداهمات، SWAT، تحقيقات، سجن، ونظام مخالفات متكامل.
        </p>
    </div>
</div>

<div class="section">
    <div class="card">
        <h2>📜 القوانين</h2>
        <p>1- احترام الجميع.</p>
        <p>2- يمنع الهاكات.</p>
        <p>3- يمنع RDM و VDM.</p>
        <p>4- الالتزام بالرول بلاي.</p>
        <p>5- يمنع استغلال الثغرات.</p>
        <p>6- يمنع الخروج أثناء المطاردة.</p>
        <p>7- يمنع تقليد الإدارة.</p>
        <p>8- الالتزام بالتعليمات.</p>
    </div>
</div>

<div class="section" id="apply">
    <div class="card">
        <h2>📋 نموذج التقديم</h2>

        <form onsubmit="submitForm(event)">
            <input type="text" placeholder="اسمك داخل اللعبة" required>
            <input type="number" placeholder="عمرك الحقيقي" required>
            <input type="text" placeholder="معرف الديسكورد" required>

            <select required>
                <option value="">هل لديك خبرة رول بلاي؟</option>
                <option>نعم</option>
                <option>لا</option>
            </select>

            <textarea rows="4" placeholder="لماذا تريد الانضمام؟" required></textarea>
            <textarea rows="4" placeholder="ما الذي يميزك؟" required></textarea>

            <button class="btn" type="submit">إرسال الطلب</button>
        </form>
    </div>
</div>

<footer>
    © 2026 RWL | POLICE MOD
</footer>

<script>
const webhookURL = "PUT_NEW_WEBHOOK_HERE";

function copyIP() {
    var ipText = document.getElementById("serverIP").innerText;
    navigator.clipboard.writeText(ipText);
    alert("تم نسخ IP السيرفر ✅");
}

function submitForm(event) {
    event.preventDefault();

    const playerName = document.querySelectorAll("input")[0].value;
    const age = document.querySelectorAll("input")[1].value;
    const discord = document.querySelectorAll("input")[2].value;
    const experience = document.querySelector("select").value;
    const textareas = document.querySelectorAll("textarea");
    const reason = textareas[0].value;
    const skills = textareas[1].value;

    fetch(webhookURL, {
        method: "POST",
        headers: {"Content-Type": "application/json"},
        body: JSON.stringify({
            embeds: [{
                title: "🚓 تقديم جديد - RWL | POLICE MOD",
                color: 3447003,
                fields: [
                    { name: "👤 الاسم", value: playerName },
                    { name: "🎂 العمر", value: age },
                    { name: "💬 الديسكورد", value: discord },
                    { name: "🎮 الخبرة", value: experience },
                    { name: "📌 السبب", value: reason },
                    { name: "⭐ المميزات", value: skills }
                ],
                timestamp: new Date()
            }]
        })
    })
    .then(() => {
        alert("تم إرسال طلبك بنجاح ✅");
        document.querySelector("form").reset();
    })
    .catch(() => {
        alert("خطأ في الإرسال ❌");
    });
}
</script>

</body>
</html>
