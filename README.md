<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Tackymeter</title>
  <style>
    body {
      transition: background 0.3s ease, color 0.3s ease;
    }

    .dark-mode {
      background: #000;
      color: #fff;
    }

    .tackymeter-wrapper {
      font-family: 'Arial', sans-serif;
      background: #0e0e11;
      color: #f2f2f2;
      padding: 60px 20px;
      max-width: 1000px;
      margin: 0 auto;
      border-radius: 10px;
    }

    .dark-mode .tackymeter-wrapper {
      background: #111;
      color: #eee;
    }

    h1, h2 {
      color: #00ffc8;
      text-transform: uppercase;
      margin-bottom: 10px;
      letter-spacing: 1px;
    }

    p {
      font-size: 16px;
      color: #ccc;
      line-height: 1.6;
    }

    .section {
      margin-top: 50px;
      border-top: 1px solid #333;
      padding-top: 30px;
    }

    .leaderboard .brand-entry {
      display: flex;
      justify-content: space-between;
      padding: 10px 15px;
      background: #1a1a1f;
      margin-bottom: 8px;
      border-left: 5px solid #00ffc8;
      border-radius: 5px;
      transition: background 0.3s ease;
    }

    .brand-entry:hover {
      background: #2a2a2f;
      cursor: pointer;
    }

    .change.up { color: #00ff88; }
    .change.down { color: #ff0055; }

    .controls {
      margin: 20px 0;
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
    }

    input[type="text"] {
      padding: 8px;
      border-radius: 5px;
      border: none;
      width: 200px;
    }

    button {
      padding: 8px 12px;
      border: none;
      background: #00ffc8;
      color: #000;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background: #00e6b8;
    }
  </style>
</head>
<body>
  <div class="tackymeter-wrapper">
    <div class="hero">
      <h1>Tackymeter</h1>
      <p>Bespoke. Purpose-built. AI-powered horological analytics for a new era of taste.</p>
    </div>

    <div class="controls">
      <input type="text" id="searchInput" placeholder="Search brand..." oninput="filterBrands()" />
      <button onclick="sortBy('position')">Sort by Position</button>
      <button onclick="sortBy('brand')">Sort by Brand</button>
      <button onclick="sortBy('change')">Sort by Change</button>
      <button onclick="filterBy('up')">Show ↑ Only</button>
      <button onclick="filterBy('down')">Show ↓ Only</button>
      <button onclick="resetFilter()">Reset</button>
      <button onclick="toggleDarkMode()">Toggle Dark Mode</button>
    </div>

    <div class="section">
      <h2>GWT Power Rankings</h2>
      <div class="leaderboard" id="leaderboard">
        <div class="brand-entry">
          <span class="position">1.</span>
          <span class="brand-name">Rolex</span>
          <span class="change up">+2</span>
        </div>
        <div class="brand-entry">
          <span class="position">2.</span>
          <span class="brand-name">Patek Philippe</span>
          <span class="change down">-1</span>
        </div>
        <div class="brand-entry">
          <span class="position">3.</span>
          <span class="brand-name">Grand Seiko</span>
          <span class="change up">+4</span>
        </div>
        <div class="brand-entry">
          <span class="position">4.</span>
          <span class="brand-name">Omega</span>
          <span class="change down">-3</span>
        </div>
        <div class="brand-entry">
          <span class="position">5.</span>
          <span class="brand-name">TAG Heuer</span>
          <span class="change up">+1</span>
        </div>
      </div>
    </div>
  </div>

  <script>
    function sortBy(type) {
      const container = document.getElementById('leaderboard');
      const entries = Array.from(container.querySelectorAll('.brand-entry'));

      entries.sort((a, b) => {
        if (type === 'position') {
          return parseInt(a.querySelector('.position').textContent) - parseInt(b.querySelector('.position').textContent);
        } else if (type === 'brand') {
          return a.querySelector('.brand-name').textContent.localeCompare(b.querySelector('.brand-name').textContent);
        } else if (type === 'change') {
          const changeA = parseInt(a.querySelector('.change').textContent);
          const changeB = parseInt(b.querySelector('.change').textContent);
          return changeB - changeA;
        }
      });

      container.innerHTML = '';
      entries.forEach(entry => container.appendChild(entry));
    }

    function filterBy(direction) {
      const entries = document.querySelectorAll('.brand-entry');
      entries.forEach(entry => {
        const change = entry.querySelector('.change');
        if (!change.classList.contains(direction)) {
          entry.style.display = 'none';
        } else {
          entry.style.display = 'flex';
        }
      });
    }

    function resetFilter() {
      document.querySelectorAll('.brand-entry').forEach(entry => {
        entry.style.display = 'flex';
      });
      document.getElementById('searchInput').value = '';
    }

    function filterBrands() {
      const query = document.getElementById('searchInput').value.toLowerCase();
      document.querySelectorAll('.brand-entry').forEach(entry => {
        const brand = entry.querySelector('.brand-name').textContent.toLowerCase();
        entry.style.display = brand.includes(query) ? 'flex' : 'none';
      });
    }

    function toggleDarkMode() {
      document.body.classList.toggle('dark-mode');
      localStorage.setItem('darkMode', document.body.classList.contains('dark-mode'));
    }

    // Load dark mode preference
    window.onload = () => {
      if (localStorage.getItem('darkMode') === 'true') {
        document.body.classList.add('dark-mode');
      }
    };
  </script>
</body>
</html>
