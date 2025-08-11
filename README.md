<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Tackymeter</title>
  <style>
    .tackymeter-wrapper {
      font-family: 'Arial', sans-serif;
      background: #0e0e11;
      color: #f2f2f2;
      padding: 60px 20px;
      max-width: 1000px;
      margin: 0 auto;
      border-radius: 10px;
    }

    .tackymeter-wrapper h1,
    .tackymeter-wrapper h2 {
      color: #00ffc8;
      text-transform: uppercase;
      margin-bottom: 10px;
      letter-spacing: 1px;
    }

    .tackymeter-wrapper p {
      font-size: 16px;
      color: #ccc;
      line-height: 1.6;
    }

    .section {
      margin-top: 50px;
      border-top: 1px solid #333;
      padding-top: 30px;
    }

    .walls ul,
    .awards ul,
    .leaderboard {
      margin-top: 20px;
      padding-left: 0;
      list-style: none;
    }

    .walls li,
    .awards li {
      margin-bottom: 10px;
      font-weight: bold;
    }

    .walls a {
      color: #00ffc8;
      text-decoration: none;
    }

    .walls a:hover {
      text-decoration: underline;
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

    .leaderboard .brand-entry:hover {
      background: #2a2a2f;
      cursor: pointer;
    }

    .leaderboard .change {
      font-weight: bold;
    }

    .leaderboard .up {
      color: #00ff88;
    }

    .leaderboard .down {
      color: #ff0055;
    }

    .awards li.winner {
      color: #00ff88;
    }

    .awards li.loser {
      color: #ff0055;
    }

    .hero {
      text-align: center;
      margin-bottom: 50px;
    }

    .hero p {
      font-style: italic;
      font-size: 18px;
      color: #aaa;
      margin-top: 10px;
    }

    @media (max-width: 600px) {
      .leaderboard .brand-entry {
        flex-direction: column;
        align-items: flex-start;
      }
    }
  </style>
</head>
<body>
  <div class="tackymeter-wrapper">
    <div class="hero">
      <h1>Tackymeter</h1>
      <p>Bespoke. Purpose-built. AI-powered horological analytics for a new era of taste.</p>
    </div>

    <div class="section walls">
      <h2>The Tackymeter Walls</h2>
      <p>Each quarter, we analyze watch releases and rank them on the Tackymeter — a 100-point scale of stylistic precision. Our extra wall focuses exclusively on the spectacle of Watches & Wonders.</p>
      <ul>
        <li><a href="#wall-q1">Q1 Tackymeter Wall</a></li>
        <li><a href="#wall-q2">Q2 Tackymeter Wall</a></li>
        <li><a href="#wall-q3">Q3 Tackymeter Wall</a></li>
        <li><a href="#wall-q4">Q4 Tackymeter Wall</a></li>
        <li><a href="#wall-wonders">Watches & Wonders Tackymeter</a></li>
      </ul>
    </div>

    <div class="section">
      <h2>GWT Power Rankings</h2>
      <p>The quarterly league table of the top 50 watch brands — ranked using data, sentiment, and taste dynamics. Updated in real-time, this is your compass in the horological noise.</p>
      <div class="leaderboard">
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
      </div>
    </div>

    <div class="section awards">
      <h2>The GWT Awards</h2>
      <p>At year’s end, we honor the most iconic — and the most infamous. Five winners, five losers. All powered by Tackymeter’s end-of-year metrics.</p>
      <ul>
        <li class="winner">🏆 Best Overall Brand – Grand Seiko</li>
        <li class="winner">🚀 Breakout Brand – Nomos Glashütte</li>
        <li class="winner">🧠 Best Innovation – Zenith Defy Extreme</li>
        <li class="loser">📉 Biggest Disappointment – Hublot Classic Fusion Remix</li>
        <li class="loser">💀 Most Overhyped – Brand X “Limited Edition”</li>
      </ul>
    </div>
  </div>
</body>
</html>
