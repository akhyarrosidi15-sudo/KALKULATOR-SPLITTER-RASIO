<html lang="id">
<head>
<meta charset="utf-8">
<title>Kalkulator Splitter Rasio | Fiber Optic</title>
<meta name="viewport" content="width=device-width, initial-scale=1">

<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>

<body class="bg-light">

<div class="container my-4">
    <div class="row justify-content-center">
        <div class="col-12 col-md-10 col-lg-8">

            <h4 class="mb-3 text-center">
                Kalkulator Splitter Rasio<br>
                <small class="text-muted">Fiber Optic Power Calculator</small>
            </h4>

            <!-- FORM -->
            <div class="card shadow-sm">
                <div class="card-body">

                    <div class="mb-3">
                        <label class="form-label fw-bold">Input Laser Power (dB)</label>
                        <input type="number" id="laser" class="form-control" min="0" max="12" step="0.01" value="9">
                        <div class="form-text">Maksimal 12 dB</div>
                    </div>

                    <div class="mb-3">
                        <label class="form-label fw-bold">Persen Rasio (Splitter Ratio)</label>
                        <select id="ratio" class="form-select">
                            <option value="0">0:0 (Tanpa Rasio)</option>
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
                        <label class="form-label fw-bold">Varian ODP (Pasif Splitter)</label>
                        <select id="plc" class="form-select">
                            <option value="0">0:0 (Tanpa PLC)</option>
                            <option value="3.25">1:2</option>
                            <option value="7">1:4</option>
                            <option value="10">1:8</option>
                            <option value="13.5">1:16</option>
                        </select>
                    </div>

                    <div class="d-grid">
                        <button class="btn btn-primary" onclick="hitung()">HITUNG</button>
                    </div>

                </div>
            </div>

            <!-- HASIL -->
            <div class="card mt-4 shadow-sm d-none" id="hasilBox">
                <div class="card-body">

                    <div class="mb-3">
                        <b>REDAMAN ODP</b><br>
                        <span class="text-danger fw-bold fs-5" id="redaman"></span>
                    </div>

                    <div>
                        <b>SISA LASER</b><br>
                        <span class="text-success fw-bold fs-5" id="sisa"></span>
                        <div class="mt-2">
                            <button class="btn btn-outline-secondary btn-sm" onclick="gunakanSisa()">
                                ⬆️ Gunakan sebagai Input Laser
                            </button>
                        </div>
                    </div>

                </div>
            </div>

            <div class="text-center mt-4 text-muted small">
                by <b>WIFI KOIN AKHFI</b>
            </div>

        </div>
    </div>
</div>

<script>
let sisaLaserGlobal = 0;

function hitung(){
    let laser = parseFloat(document.getElementById("laser").value);
    let ratioLoss = parseFloat(document.getElementById("ratio").value);
    let plcLoss = parseFloat(document.getElementById("plc").value);

    if(isNaN(laser) || laser > 12){
        alert("Input Laser Power tidak valid (maks 12 dB)");
        return;
    }

    let totalLoss = ratioLoss + plcLoss;
    let sisa = laser - totalLoss;

    sisaLaserGlobal = sisa;

    document.getElementById("redaman").innerText =
        totalLoss.toFixed(2) + " dB";

    document.getElementById("sisa").innerText =
        sisa.toFixed(2) + " dB";

    document.getElementById("hasilBox").classList.remove("d-none");
}

function gunakanSisa(){
    if(sisaLaserGlobal <= 0){
        alert("Sisa laser tidak valid");
        return;
    }
    document.getElementById("laser").value = sisaLaserGlobal.toFixed(2);
    window.scrollTo({top:0, behavior:"smooth"});
}
</script>

</body>
</html>
