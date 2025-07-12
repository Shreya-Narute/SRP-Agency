<!DOCTYPE html>
<html lang="mr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>SRP Agency</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f3fff3;
      margin: 0;
      padding: 20px;
    }
    h2 {
      text-align: center;
      margin-top: 40px;
    }
    #toggleLang {
      background: #007bff;
      color: white;
      padding: 10px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin: 0 auto 20px auto;
      display: block;
    }
    form {
      background: #fff;
      padding: 20px;
      border-radius: 12px;
      max-width: 500px;
      margin: 20px auto;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    }
    input, button {
      display: block;
      width: 100%;
      margin-bottom: 15px;
      padding: 10px;
      font-size: 16px;
    }
    button {
      background-color: #4CAF50;
      color: white;
      border: none;
      border-radius: 6px;
      cursor: pointer;
    }
    button:hover {
      background-color: #45a049;
    }
    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 15px;
      max-width: 800px;
      margin: 20px auto;
    }
    .gallery img {
      width: 100%;
      border-radius: 10px;
    }
    table {
      border-collapse: collapse;
      width: 100%;
      max-width: 1000px;
      margin: 30px auto;
    }
    th, td {
      padding: 10px;
      border: 1px solid #ccc;
      text-align: left;
    }
    @media (max-width: 600px) {
      input, button {
        font-size: 14px;
      }
      h2 {
        font-size: 18px;
      }
    }
  </style>
</head>
<body>

  <button id="toggleLang">Switch to English</button>
  <h2 id="formTitle">बीज वाटप फॉर्म</h2>

  <form id="seedForm">
    <input type="text" id="name" placeholder="नाव" required>
    <input type="text" id="village" placeholder="गाव" required>
    <input type="text" id="crop" placeholder="पीक" required>
    <input type="text" id="seedType" placeholder="बीज प्रकार" required>
    <input type="number" id="quantity" placeholder="प्रमाण (kg)" required>
    <input type="date" id="date" required>
    <button type="submit" id="submitBtn">सबमिट करा</button>
  </form>

  <h2>📷 आमचे काम - गॅलरी</h2>
  <div class="gallery">
    <img src="https://source.unsplash.com/200x150/?farmer" alt="Farmer">
    <img src="https://source.unsplash.com/200x150/?vegetables" alt="Vegetables">
    <img src="https://source.unsplash.com/200x150/?farming" alt="Farming">
    <img src="https://source.unsplash.com/200x150/?truck" alt="Truck">
    <img src="https://source.unsplash.com/200x150/?market" alt="Market">
    <img src="https://source.unsplash.com/200x150/?seeds" alt="Seeds">
  </div>

  <h2>📋 शेतकऱ्यांची नोंद</h2>
  <div style="overflow-x:auto; max-width: 1000px; margin: auto;">
    <table id="sheetData">
      <thead>
        <tr>
          <th>नाव</th>
          <th>गाव</th>
          <th>पीक</th>
          <th>बीज प्रकार</th>
          <th>प्रमाण</th>
          <th>दिनांक</th>
        </tr>
      </thead>
      <tbody></tbody>
    </table>
  </div>

  <script>
    const translations = {
      mr: {
        title: "बीज वाटप फॉर्म",
        placeholders: ["नाव", "गाव", "पीक", "बीज प्रकार", "प्रमाण (kg)"],
        submit: "सबमिट करा",
        toggle: "Switch to English",
        success: "✅ तुमचा फॉर्म यशस्वीरित्या सबमिट झाला आहे!",
        error: "❌ त्रुटी: फॉर्म सबमिट होऊ शकला नाही."
      },
      en: {
        title: "Seed Distribution Form",
        placeholders: ["Name", "Village", "Crop", "Seed Type", "Quantity (kg)"],
        submit: "Submit",
        toggle: "भाषा बदला (मराठी)",
        success: "✅ Your form has been submitted successfully!",
        error: "❌ Error: Could not submit the form."
      }
    };

    let currentLang = "mr";

    document.getElementById("toggleLang").addEventListener("click", () => {
      currentLang = currentLang === "mr" ? "en" : "mr";
      const t = translations[currentLang];
      document.getElementById("formTitle").innerText = t.title;
      document.getElementById("name").placeholder = t.placeholders[0];
      document.getElementById("village").placeholder = t.placeholders[1];
      document.getElementById("crop").placeholder = t.placeholders[2];
      document.getElementById("seedType").placeholder = t.placeholders[3];
      document.getElementById("quantity").placeholder = t.placeholders[4];
      document.getElementById("submitBtn").innerText = t.submit;
      document.getElementById("toggleLang").innerText = t.toggle;
    });

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

      fetch("https://script.google.com/macros/s/AKfycbyIJwwct0J8hNNyhyfyfaZGfsztpi5Czf_xK6NpHMRi3jeq7ioWvvgEHXhyAHA4icY/exec", {
        method: "POST",
        body: JSON.stringify(formData),
        headers: { "Content-Type": "application/json" }
      })
      .then(res => res.text())
      .then(data => {
        alert(translations[currentLang].success);
        document.getElementById("seedForm").reset();
      })
      .catch(error => {
        alert(translations[currentLang].error + "\n" + error);
      });
    });

    // Google Sheet Data Display
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
      })
      .catch(err => {
        console.error("Sheet data load error", err);
      });
  </script>

</body>
</html>
