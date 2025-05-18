# JavaScript-
Interactive elements 

<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS Event Handling & Interactivity</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>JS Event Handling & Interactive Elements</h1>
    <div id="event-handling">
        <button id="clickBtn">Click Me</button>
        <button id="hoverBtn">Hover Over Me</button>
        <input type="text" id="keypressInput" placeholder="Type something...">
        <button id="secretBtn">Secret Action</button>
    </div>

    <div id="interactive-elements">
        <button id="colorChangeBtn">Change Color</button>
        <div id="gallery">
            <img src="image1.jpg" alt="Image 1">
            <img src="image2.jpg" alt="Image 2">
            <img src="image3.jpg" alt="Image 3">
        </div>
        <div id="tabs">
            <button class="tab" data-content="content1">Tab 1</button>
            <button class="tab" data-content="content2">Tab 2</button>
            <button class="tab" data-content="content3">Tab 3</button>
        </div>
        <div id="tab-content">
            <div id="content1" class="content">Content for Tab 1</div>
            <div id="content2" class="content hidden">Content for Tab 2</div>
            <div id="content3" class="content hidden">Content for Tab 3</div>
        </div>
    </div>

    <div id="form-validation">
        <form id="myForm">
            <input type="text" id="name" placeholder="Name" required>
            <input type="email" id="email" placeholder="Email" required>
            <input type="password" id="password" placeholder="Password (min 8 chars)" required>
            <button type="submit">Submit</button>
            <div id="feedback"></div>
        </form>
    </div>

    <script src="script.js"></script>
</body>
</html>

/* style.css */
body {
    font-family: Arial, sans-serif;
}
button {
    margin: 5px;
    padding: 10px;
}
.hidden {
    display: none;
}

/* script.js */
document.addEventListener("DOMContentLoaded", () => {
    const clickBtn = document.getElementById("clickBtn");
    const hoverBtn = document.getElementById("hoverBtn");
    const keypressInput = document.getElementById("keypressInput");
    const secretBtn = document.getElementById("secretBtn");
    const colorChangeBtn = document.getElementById("colorChangeBtn");
    const tabs = document.querySelectorAll(".tab");
    const tabContents = document.querySelectorAll(".content");

    clickBtn.addEventListener("click", () => alert("Button clicked!"));

    hoverBtn.addEventListener("mouseover", () => hoverBtn.style.backgroundColor = "lightblue");
    hoverBtn.addEventListener("mouseout", () => hoverBtn.style.backgroundColor = "");

    keypressInput.addEventListener("keypress", (e) => console.log("Key pressed: ", e.key));

    secretBtn.addEventListener("dblclick", () => alert("Secret Action!"));

    colorChangeBtn.addEventListener("click", () => {
        colorChangeBtn.style.backgroundColor = colorChangeBtn.style.backgroundColor === "lightgreen" ? "" : "lightgreen";
    });

    tabs.forEach(tab => {
        tab.addEventListener("click", () => {
            tabContents.forEach(content => content.classList.add("hidden"));
            document.getElementById(tab.dataset.content).classList.remove("hidden");
        });
    });
});
