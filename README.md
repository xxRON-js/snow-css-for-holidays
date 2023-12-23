# Snowfall Effect for Your Website

Add a delightful snowfall effect to your website with this simple HTML, CSS, and JavaScript code. Copy the code below and paste it into your HTML file to create a festive atmosphere on your web pages during the holiday season.

## Example

![Snowfall Example](https://github.com/xxRON-js/snow-css-for-holidays/blob/main/example.png)


## How to Use

Enjoy the snowfall effect on your website!

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Holidays</title>
  <style>
    /* Paste the provided CSS code here */
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      overflow: hidden; /* Add this line to prevent scrolling */
    }

    main {
      background: linear-gradient(to bottom, #2d91c2 0%, #1e528e 100%);
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: "Pacifico", cursive;
      height: 100vh;
      padding: 20px;
      text-align: center;
    }

    h1 {
      color: white;
    }

    #snow-container {
      height: 100vh;
      overflow: hidden;
      position: absolute;
      top: 0;
      transition: opacity 500ms;
      width: 100%;
    }

    .snow {
      animation: fall ease-in infinite, sway ease-in-out infinite;
      color: skyblue;
      position: absolute;
    }

    footer {
      background-color: #ffdfb9;
      bottom: 0;
      font-family: sans-serif;
      padding: 1rem;
      text-align: center;
      width: 100%;
    }

    footer a {
      color: inherit;
      text-decoration: none;
    }

    footer .heart {
      color: #dc143c;
    }

    @keyframes fall {
      0% {
        opacity: 0;
      }
      50% {
        opacity: 1;
      }
      100% {
        top: 100vh;
        opacity: 1;
      }
    }

    @keyframes sway {
      0% {
        margin-left: 0;
      }
      25% {
        margin-left: 50px;
      }
      50% {
        margin-left: -50px;
      }
      75% {
        margin-left: 50px;
      }
      100% {
        margin-left: 0;
      }
    }
  </style>
</head>

<body>
  <!-- Main Content -->
  <main>
    <h1>Happy Holidays!</h1>
  </main>

  <!-- Snowfall Container -->
  <div id="snow-container" title="Click anywhere to remove snow">
  </div>

  <!-- Footer -->
  <footer>
  </footer>

  <script>
    const snowContainer = document.getElementById("snow-container");
    const snowContent = ['&#10052', '&#10053', '&#10054']

    const random = (num) => {
      return Math.floor(Math.random() * num);
    }

    const getRandomStyles = () => {
      const top = random(100);
      const left = random(100);
      const dur = random(10) + 10;
      const size = random(25) + 25;
      return `
        top: -${top}%;
        left: ${left}%;
        font-size: ${size}px;
        animation-duration: ${dur}s;
      `;
    }

    const createSnow = (num) => {
      for (var i = num; i > 0; i--) {
        var snow = document.createElement("div");
        snow.className = "snow";
        snow.style.cssText = getRandomStyles();
        snow.innerHTML = snowContent[random(3)]
        snowContainer.append(snow);
      }
    }

    const removeSnow = () => {
      snowContainer.style.opacity = "0";
      setTimeout(() => {
        snowContainer.remove()
      }, 500)
    }

    window.addEventListener("load", () => {
      createSnow(30)
      setTimeout(removeSnow, (1000 * 60))
    });

    window.addEventListener("click", () => {
      removeSnow()
    });
  </script>
</body>

</html>
