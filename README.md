<html lang="id">
<head>
<meta charset="utf-8">
<title>Kalkulator Redaman ODP</title>
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>

<body class="bg-light">
<div class="container my-4">
<div class="row justify-content-center">
<div class="col-12 col-md-10 col-lg-8">

<h4 class="text-center mb-3">
Kalkulator Redaman ODP<br>
<small class="text-muted">Fiber Optic Calculator</small>
</h4>

<div class="card shadow-sm">
<div class="card-body">

<div class="mb-3">
<label class="form-label fw-bold">Input Laser (dBm)</label>
<input type="number" id="laser" class="form-control" step="0.01" value="-5.84">
</div>

<div class="mb-3">
<label class="form-label fw-bold">Persen Besar (Splitter Ratio)</label>
<select id="ratio" class="form-select">
<option value="0">0:0</option>
<option value="0.24">1:99</option>
<option value="0.29">2:98</option>
<option value="0.33">3:97</option>
<option value="0.38">4:96</option>
<option value="0.42">5:95</option>
<option value="0.47">6:94</option>
<option value="0.52">7:93</option>
<option value="0.56">8:92</option>
<option value="0.61">9:91</option>
<option value="0.66">10:90</option>
<option value="0.76">12:88</option>
<option value="0.91">15:85</option>
<option value="1.06">18:82</option>
<option value="1.17">20:80</option>
<option value="1.28">22:78</option>
<option value="1.45">25:75</option>
<option value="1.63">28:72</option>
<option value="1.75">30:70</option>
<option value="2.07">35:65</option>
<option value="2.42">40:60</option>
<option value="2.80">45:55</option>
<option value="3.21">50:50</option>
</select>
</div>

<div class="mb-3">
<label class="form-label fw-bold">Splitter ODP (PLC)</label>
<select id="plc" class="form-select">
<option value="0">0:0</option>
<option value="3.25">1:2</option>
<option value="7">1:4</option>
<option value="10">1:8</option>
<option value="13.5">1:16</option>
<option value="17">1:32</option>
<option value="20">1:64</option>
</select>
</div>

<button class="btn btn-primary w-100" onclick="hitung()">HITUNG</button>

</div>
</div>

<div class="card mt-4 shadow-sm d-none" id="hasil">
<div class="card-body">
<div class="mb-2">
<b>REDAMAN ODP</b><br>
<span class="text-danger fw-bold" id="redamanOdp"></span>
<span class="text-muted">(Redaman Optimal)</span>
</div>
<div>
<b>SISA LASER</b><br>
<span class="text-success fw-bold" id="sisaLaser"></span>
<button class="btn btn-sm btn-outline-secondary ms-2" onclick="pakaiUlang()">⬆️</button>
</div>
</div>
</div>

<div class="text-center text-muted small mt-3">
by <b>WIFI KOIN AKHFI</b>
</div>

</div>
</div>
</div>

<script>
const faktorBilhanet = 0.94;
let lastRedaman = 0;

function hitung(){
let inputLaser = parseFloat(document.getElementById("laser").value);
let lossRatio = parseFloat(document.getElementById("ratio").value);
let lossPLC = parseFloat(document.getElementById("plc").value);

let totalRedaman = (lossRatio + lossPLC) * faktorBilhanet;
let redamanOdp = inputLaser - totalRedaman;

lastRedaman = totalRedaman;

document.getElementById("redamanOdp").innerText =
redamanOdp.toFixed(2) + " dBm";

document.getElementById("sisaLaser").innerText =
totalRedaman.toFixed(2);

document.getElementById("hasil").classList.remove("d-none");
}

function pakaiUlang(){
document.getElementById("laser").value =
(document.getElementById("laser").value - lastRedaman).toFixed(2);
window.scrollTo({top:0, behavior:"smooth"});
}
</script>

</body>
</html>
