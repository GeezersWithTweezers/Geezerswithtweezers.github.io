<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Geezers With Tweezers</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      margin: 0;
      padding: 0;
      background-color: #f4f4f4;
      color: #333;
    }

    header {
      background-color: #222;
      color: #fff;
      padding: 20px;
      text-align: center;
    }

    .section {
      padding: 40px 20px;
      max-width: 900px;
      margin: auto;
    }

    h2 {
      margin-bottom: 20px;
      color: #444;
    }

    label {
      display: block;
      margin: 10px 0;
    }

    input[type="number"] {
      width: 60px;
      padding: 5px;
      margin-left: 10px;
    }

    button {
      margin-top: 15px;
      padding: 10px 20px;
      background-color: #0077cc;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background-color: #005fa3;
    }

    #scoreResult {
      margin-top: 20px;
      font-size: 1.2em;
    }

    .gallery-grid {
      display: flex;
      gap: 20px;
      flex-wrap: wrap;
      justify-content: center;
    }

    .gallery-grid img {
      width: 200px;
      border-radius: 8px;
      cursor: pointer;
      transition: transform 0.3s ease;
    }

    .gallery-grid img:hover {
      transform: scale(1.05);
    }

    .modal {
      display: none;
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(0,0,0,0.8);
      justify-content: center;
      align-items: center;
      z-index: 999;
    }

    .modal img {
      max-width: 80%;
      max-height: 80%;
      border-radius: 10px;
    }

    footer {
      text-align: center;
      padding: 20px;
      background-color: #222;
      color: white;
    }
  </style>
</head>
<body>

  <header>
    <h1>Geezers With Tweezers</h1>
    <p>Celebrating Watchmaking, Taste, and Speed</p>
  </header>

  <div class="section" id="tackymeter-test">
    <h2>Tackymeter Taste Test</h2>
    <p>Rate this watch on style, innovation, and taste. Your score will be calculated instantly.</p>

    <label>Style (1–10): <input type="number" id="style" min="1" max="10" /></label>
    <label>Innovation (1–10): <input type="number" id="innovation" min="1" max="10" /></label>
    <label>Taste (1–10): <input type="number" id="taste" min="1" max="10" /></label>
    <button onclick="calculateTackymeter()">Calculate Score</button>

    <div id="scoreResult"></div>
  </div>

  <div class="section" id="gallery">
    <h2>Watch Gallery</h2>
    <div class="gallery-grid">
      <img src="images/grand-seiko.jpg" alt="Grand Seiko" onclick="openModal(this)" />
      <img src="images/rolex.jpg" alt="Rolex" onclick="openModal(this)" />
      <img src="images/tag-heuer.jpg" alt="TAG Heuer" onclick="openModal(this)" />
    </div>
  </div>

  <div id="modal" class="modal" onclick="closeModal()">
    <img id="modalImg" />
  </div>

  <footer>
    <p>&copy; 2025 Geezers With Tweezers. All rights reserved.</p>
  </footer>

  <script>
    function calculateTackymeter() {
      const style = parseInt(document.getElementById('style').value) || 0;
      const innovation = parseInt(document.getElementById('innovation').value) || 0;
      const taste = parseInt(document.getElementById('taste').value) || 0;

      const score = Math.round((style * 0.4 + innovation * 0.3 + taste * 0.3) * 10);
      const result = document.getElementById('scoreResult');

      result.textContent = `Your Tackymeter Score: ${score}/100`;
      result.style.color = score >= 70 ? '#00cc66' : score >= 40 ? '#ffaa00' : '#ff3333';
    }

    function openModal(img) {
      const modal = document.getElementById('modal');
      const modalImg = document.getElementById('modalImg');
      modalImg.src = img.src;
      modal.style.display = 'flex';
    }

    function closeModal() {
      document.getElementById('modal').style.display = 'none';
    }
  </script>

</body>
</html>
