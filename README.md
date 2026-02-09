<html lang="id">
<head>
<meta charset="UTF-8">
<title>Kalkulator Splitter Rasio Style</title>
<style>
body { font-family: Arial; background:#f5f5f5; padding:20px; }
.box { background:#fff; padding:20px; border-radius:8px; max-width:400px; }
label { font-weight:bold; }
input, select, button {
  width:100%;
  padding:8px;
  margin-top:5px;
  margin-bottom:15px;
}
button {
  background:#007bff;
  color:#fff;
  border:none;
  cursor:pointer;
}
.result {
  margin-top:15px;
  padding:15px;
  background:#eee;
  border-radius:6px;
}
.red { color:#d600d6; font-weight:bold; }
.green { color:green; font-weight:bold; }
</style>
</head>

<body>
<div class="box">
  <label>Input Laser Power (dB)</label>
  <input type="number" id="laser" value="9">

  <label>Persen Rasio (Splitter Ratio)</label>
  <select id="rasio">
    <option value="99">1:99</option>
    <option value="63">1:63</option>
    <option value="31">1:31</option>
  </select>

  <label>Varian ODP (Pasif Splitter)</label>
  <select disabled>
    <option>1:2</option>
  </select>

  <button onclick="hitung()">HITUNG</button>

  <div class="result">
    <div class="red">
      REDAMAN ODP<br>
      <span id="redaman">-</span> dBm (Redaman Optimal)
    </div>
    <br>
    <div class="green">
      SISA LASER (Persen Besar)<br>
      <span id="sisa">-</span>
    </div>
  </div>
</div>

<script>
function hitung() {
  let laser = parseFloat(document.getElementById("laser").value);
  let rasio = parseFloat(document.getElementById("rasio").value);

  // Rumus BILHANET
  let redaman = - (10 * Math.log10(rasio));
  redaman = redaman.toFixed(2);

  let sisa = (laser + parseFloat(redaman));
  sisa = sisa.toFixed(2);

  document.getElementById("redaman").innerText = redaman;
  document.getElementById("sisa").innerText = sisa;
}
</script>
</body>
</html>
