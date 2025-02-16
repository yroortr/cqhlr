your-repo/
├── index.html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>可以成为我的恋人吗?</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <img id="mainImage" src="images/heart.png" alt="爱心">
        <h1 id="question">可以成为我的恋人吗?</h1>
        <div class="buttons">
            <button id="yes">可以</button>
            <button id="no">不要</button>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>
├── style.css
body {
    background-color: #f1d5da;
    text-align: center;
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    overflow: hidden;
}

.container {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

#mainImage {
    width: 200px;
    transition: all 0.3s ease;
}

h1 {
    font-size: 28px;
    color: #68495b;
    margin: 20px 0;
}

button {
    font-size: 18px;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin: 10px;
    transition: all 0.3s ease;
}

#yes {
    background-color: #d4818e;
    color: white;
}

#no {
    background-color: #6784b1;
    color: white;
    position: relative;
}

.yes-screen {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: #ffdae0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.yes-text {
    font-size: 40px;
    color: #d4818e;
    animation: pulse 1s infinite;
}

@keyframes pulse {
    0% { transform: scale(1); }
    50% { transform: scale(1.1); }
    100% { transform: scale(1); }
}

.yes-image {
    width: 300px;
    margin-top: 30px;
}
├── script.js
const yesButton = document.getElementById("yes");
const noButton = document.getElementById("no");
const questionText = document.getElementById("question");
const mainImage = document.getElementById("mainImage");

let clickCount = 0;

const noTexts = [
    "？你认真的吗...",
    "要不再想想？",
    "不许选这个！",
    "我会很伤心...",
    "不行！"
];

noButton.addEventListener("click", function() {
    clickCount++;
    
    // Yes按钮放大
    const yesSize = 1 + (clickCount * 1.2);
    yesButton.style.transform = `scale(${yesSize})`;
    
    // No按钮右移
    const noOffset = clickCount * 50;
    noButton.style.transform = `translateX(${noOffset}px)`;
    
    // 元素上移
    const moveUp = clickCount * 25;
    mainImage.style.transform = `translateY(-${moveUp}px)`;
    questionText.style.transform = `translateY(-${moveUp}px)`;
    
    // 文字变化
    if (clickCount <= 5) {
        noButton.innerText = noTexts[clickCount - 1];
    }
    
    // 图片变化
    if (clickCount === 1) mainImage.src = "images/shocked.png";
    if (clickCount === 2) mainImage.src = "images/think.png";
    if (clickCount === 3) mainImage.src = "images/angry.png";
    if (clickCount >= 4) mainImage.src = "images/crying.png";
});

yesButton.addEventListener("click", function() {
    document.body.innerHTML = `
        <div class="yes-screen">
            <h1 class="yes-text">!!!喜欢你!! ( >.<)♡❤</h1>
            <img src="images/hug.png" alt="拥抱" class="yes-image">
        </div>
    `;
    document.body.style.overflow = "hidden";
});
└── images/
    ├── heart.png
    ├── shocked.png
    ├── think.png
    ├── angry.png
    ├── crying.png
    └── hug.png
