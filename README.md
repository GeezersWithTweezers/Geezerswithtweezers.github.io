<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Tackymeter Dashboard</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #1a1a1a;
      color: #f0f0f0;
      margin: 0;
      padding: 0;
    }

    header {
      background: #111;
      padding: 30px;
      text-align: center;
      border-bottom: 4px solid #00ffc8;
    }

    h1 {
      margin: 0;
      font-size: 2em;
      color: #00ffc8;
    }

    .section {
      padding: 40px 20px;
      max-width: 1000px;
      margin: auto;
    }

    h2 {
      color: #ffcc00;
      margin-bottom: 20px;
    }

    .table {
      width: 100%;
      border-collapse: collapse;
      margin-bottom: 40px;
    }

    .table th, .table td {
      padding: 12px;
      border-bottom: 1px solid #444;
      text-align: left;
    }

    .table th {
      background-color: #333;
      color: #00ffc8;
    }

    .table tr:hover {
      background-color: #2a2a2a;
    }

    footer {
      text-align: center;
      padding: 20px;
      background-color: #111;
      color: white;
      border-top: 4px solid #00ffc8;
    }
  </style>
</head>
<body>

  <header>
    <h1>Tackymeter Analytics</h1>
    <p>Live data from Google Sheets via OpenSheet</p>
  </header>

  <div class="section" id="tackymeter-q1">
    <h2>🏁 Tackymeter Wall – Q1</h2>
    <table class="table" id="table-q1">
      <thead>
        <tr>
          <th>Position</th>
          <th>Brand</th>
          <th>Model</th>
          <th>Score</th>
        </tr>
      </thead>
      <tbody></tbody>
    </table>
  </div>

  <div class="section" id="tackymeter-q2">
    <h2>🏁 Tackymeter Wall – Q2</h2>
    <table class="table" id="table-q2">
      <thead>
        <tr>
          <th>Position</th>
          <th>Brand</th>
          <th>Model</th>
          <th>Score</th>
        </tr>
      </thead>
      <tbody></tbody>
    </table>
  </div>

  <div class="section" id="power-rankings-q1">
    <h2>📊 Power Rankings – Q1</h2>
    <table class="table" id="table-pr-q1">
      <thead>
        <tr>
          <th>Rank</th>
          <th>Brand</th>
          <th>Change</th>
          <th>Insight</th>
        </tr>
      </thead>
      <tbody></tbody>
    </table>
  </div>

  <footer>
    <p>&copy; 2025 Geezers With Tweezers. Powered by OpenSheet + Google Sheets</p>
  </footer>

  <script>
    // Replace with your actual Google Sheet ID
    const SHEET_ID = 'YOUR_SHEET_ID_HERE';

    const endpoints = {
      q1: `https://opensheet.elk.sh/${SHEET_ID}/tackymeter-q1`,
      q2: `https://opensheet.elk.sh/${SHEET_ID}/tackymeter-q2`,
      prq1: `https://opensheet.elk.sh/${SHEET_ID}/power-rankings-q1`
    };

    function loadTable(endpoint, tableId, columns) {
      fetch(endpoint)
        .then(res => res.json())
        .then(data => {
          const tbody = document.querySelector(`#${tableId} tbody`);
          data.forEach(row => {
            const tr = document.createElement('tr');
            columns.forEach(col => {
              const td = document.createElement('td');
              td.textContent = row[col] || '';
              tr.appendChild(td);
            });
            tbody.appendChild(tr);
          });
        });
    }

    // Load each table
    loadTable(endpoints.q1, 'table-q1', ['Position', 'Brand', 'Model', 'Score']);
    loadTable(endpoints.q2, 'table-q2', ['Position', 'Brand', 'Model', 'Score']);
    loadTable(endpoints.prq1, 'table-pr-q1', ['Rank', 'Brand', 'Change', 'Insight']);
  </script>

</body>
</html>
