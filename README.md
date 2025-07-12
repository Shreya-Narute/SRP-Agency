<!DOCTYPE html>
<html lang="mr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>GreenRoots Agro - SRP Agency</title>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #f2fff4;
      margin: 0;
      padding: 0;
    }
    .navbar { background-color: #2e7d32; }
    .navbar-brand, .nav-link { color: white !important; font-weight: bold; }
    header {
      background: url('https://source.unsplash.com/1200x300/?market') no-repeat center center/cover;
      height: 300px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      text-shadow: 2px 2px 4px #000;
    }
    header h1 { font-size: 3rem; }
    section { padding: 40px 20px; }
    .gallery img { max-width: 100%; height: auto; margin-bottom: 15px; border-radius: 10px; }
    footer { background: #2e7d32; color: white; padding: 20px; text-align: center; }
    form input, form button {
      width: 100%;
      margin-bottom: 10px;
      padding: 10px;
    }
    table {
      width: 100%;
      margin-top: 20px;
    }
    th, td {
      padding: 8px;
      border: 1px solid #ccc;
    }
    .card {
      border: 1px solid #ccc;
      border-radius: 10px;
      padding: 15px;
      margin: 10px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    .partner-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-around;
    }
  </style>
</head>
<body>
  <nav class="navbar navbar-expand-lg">
    <a class="navbar-brand" href="#">GreenRoots Agro</a>
    <ul class="navbar-nav ml-auto">
      <li class="nav-item"><a class="nav-link" href="#about">आमच्याबद्दल</a></li>
      <li class="nav-item"><a class="nav-link" href="#services">सेवा</a></li>
      <li class="nav-item"><a class="nav-link" href="#gallery">गॅलरी</a></li>
      <li class="nav-item"><a class="nav-link" href="#partners">भागीदार</a></li>
      <li class="nav-item"><a class="nav-link" href="#seeds">बीज वितरण</a></li>
    </ul>
  </nav>

  <header>
    <h1>आपल्या शेतकऱ्यांचा विश्वास</h1>
  </header>

  <section id="about" class="container">
    <h2>आमच्याबद्दल</h2>
    <p>GreenRoots Agro ही आपल्या शेतकऱ्यांकडून भाजीपाला खरेदी करून पुणे-मुंबई मार्केटमध्ये पोचवणारी संस्था आहे. आम्ही बियाण्यांचं वाटप करून त्यांना योग्य दरामध्ये खरेदी करत असतो.</p>
  </section>

  <section id="services" class="bg-light container">
    <h2>आमच्या सेवा</h2>
    <ul>
      <li>शेतकऱ्यांकडून भाजीपाला खरेदी</li>
      <li>बियाण्यांचे वितरण</li>
      <li>पुणे व मुंबई मार्केटमध्ये विक्री</li>
      <li>वेळेवर पेमेंट</li>
    </ul>
  </section>

  <section id="gallery" class="container">
    <h2>गॅलरी</h2>
    <div class="row gallery">
      <div class="col-md-4"><img src="https://source.unsplash.com/400x300/?farmer" alt="Farm"></div>
      <div class="col-md-4"><img src="https://source.unsplash.com/400x300/?market" alt="Market"></div>
      <div class="col-md-4"><img src="https://source.unsplash.com/400x300/?truck" alt="Transport"></div>
    </div>
  </section>

  <section id="partners" class="container">
    <h2>भागीदार माहिती</h2>
    <div class="partner-row">
      <div class="card">
        <h5>श्री. सुरेश नरुटे</h5>
        <p><strong>गाव:</strong> अंदोरी<br>मोबाइल: 7387057752</p>
      </div>
      <div class="card">
        <h5>श्री. राहुल कोकरे</h5>
        <p><strong>गाव:</strong> रुई<br>मोबाइल: 7709192226</p>
      </div>
      <div class="card">
        <h5>श्री. प्रकाश नरुटे</h5>
        <p><strong>गाव:</strong> अंदोरी<br>मोबाइल: 7709181501</p>
      </div>
    </div>
  </section>

  <section id="seeds" class="container bg-light">
    <h2>बियाणे वितरण फॉर्म</h2>
    <form id="seedForm">
      <input type="text" id="name" class="form-control" placeholder="पूर्ण नाव" required>
      <input type="text" id="village" class="form-control" placeholder="गाव" required>
      <input type="text" id="crop" class="form-control" placeholder="पीक" required>
      <input type="text" id="seedType" class="form-control" placeholder="बियाण्याचा प्रकार" required>
      <input type="number" id="quantity" class="form-control" placeholder="किती किलो" required>
      <input type="date" id="date" class="form-control" required>
      <button type="submit" class="btn btn-success">सबमिट करा</button>
    </form>

    <table id="sheetData">
      <thead>
        <tr>
          <th>नाव</th>
          <th>गाव</th>
          <th>पीक</th>
          <th>बियाण्याचा प्रकार</th>
          <th>प्रमाण</th>
          <th>दिनांक</th>
        </tr>
      </thead>
      <tbody></tbody>
    </table>
  </section>

  <footer>
    &copy; 2025 GreenRoots Agro. सर्व हक्क राखीव.
  </footer>

  <script>
    document.getElementById("seedForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const formData = {
        name: document.getElementById("name").value,
        village: document.getElementById("village").value,
        crop: document.getElementById("crop").value,
        seedType: document.getElementById("seedType").value,
        quantity: document.getElementById("quantity").value,
        date: document.getElementById("date").value
      };

      fetch("https://script.google.com/macros/s/AKfycbwy4oAshPfoQYbLjUofjPqJ9GHbX072Hr_Qc-rsTeQynIwDVVkShyVYTVJfxDJLlePP/exec", {
        method: "POST",
        body: JSON.stringify(formData),
        headers: { "Content-Type": "application/json" }
      })
      .then(res => res.text())
      .then(data => {
        alert("बियाण्याची माहिती यशस्वीरित्या सबमिट झाली!");
        document.getElementById("seedForm").reset();
      })
      .catch(err => alert("डेटा सबमिट करताना त्रुटी आली!"));
    });

    fetch("https://opensheet.elk.sh/1eNBlxdGZxX4ViZBGCplrXFYDNdETEp7ZgYBaNFjTzo8/Sheet1")
      .then(res => res.json())
      .then(data => {
        const table = document.querySelector("#sheetData tbody");
        data.forEach(row => {
          const tr = document.createElement("tr");
          tr.innerHTML = `
            <td>${row.name || ''}</td>
            <td>${row.village || ''}</td>
            <td>${row.crop || ''}</td>
            <td>${row.seedType || ''}</td>
            <td>${row.quantity || ''}</td>
            <td>${row.date || ''}</td>
          `;
          table.appendChild(tr);
        });
      });
  </script>
</body>
</html>

