<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Kalkulator Harga Wajar Saham</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 40px; background: #f9f9f9; }
    h2 { color: #333; }
    label { display: block; margin-top: 10px; }
    input { padding: 5px; width: 200px; }
    button { margin-top: 15px; padding: 10px 20px; cursor: pointer; }
    #result { margin-top: 20px; font-weight: bold; color: #006400; }
    .container { background: #fff; padding: 20px; border-radius: 8px; box-shadow: 0 0 10px rgba(0,0,0,0.1); }
  </style>
</head>
<body>
  <div class="container">
    <h2>Kalkulator Harga Wajar Saham</h2>
    
    <label>Kode Saham:</label>
    <input type="text" id="kode" placeholder="Contoh: MYOR">

    <label>Harga Saham Saat Ini (Rp):</label>
    <input type="number" id="harga">

    <label>Book Value Per Share (BVPS) (Rp):</label>
    <input type="number" id="bvps">

    <label>Earnings Per Share (EPS TTM) (Rp):</label>
    <input type="number" id="eps">

    <button onclick="hitungHargaWajar()">Hitung Harga Wajar</button>
    <button onclick="resetForm()">Reset</button>

    <div id="result"></div>
  </div>

  <script>
    function hitungHargaWajar() {
      const harga = parseFloat(document.getElementById('harga').value);
      const bvps = parseFloat(document.getElementById('bvps').value);
      const eps = parseFloat(document.getElementById('eps').value);

      if (isNaN(harga) || isNaN(bvps) || isNaN(eps)) {
        document.getElementById('result').innerText = "⚠️ Mohon isi semua data terlebih dahulu.";
        return;
      }

      // Metode sederhana: kombinasi PER & PBV
      const fairValuePER = eps * 15;   // asumsi PER wajar = 15x
      const fairValuePBV = bvps * 2;   // asumsi PBV wajar = 2x
      const fairValue = (fairValuePER + fairValuePBV) / 2;

      document.getElementById('result').innerText =
        "Harga Wajar Saham: Rp " + fairValue.toFixed(0);
    }

    function resetForm() {
      document.getElementById('kode').value = "";
      document.getElementById('harga').value = "";
      document.getElementById('bvps').value = "";
      document.getElementById('eps').value = "";
      document.getElementById('result').innerText = "";
    }
  </script>
</body>
</html>
