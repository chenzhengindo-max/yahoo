<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jadwal Vaksinasi Lengkap</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            max-width: 1000px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f5f9ff;
            color: #333;
        }
        
        h1 {
            color: #2c3e50;
            text-align: center;
            margin-bottom: 30px;
        }
        
        .container {
            background-color: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .input-section {
            margin-bottom: 25px;
            padding: 15px;
            background-color: #e8f4ff;
            border-radius: 8px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #2c3e50;
        }
        
        input[type="date"] {
            padding: 10px;
            border: 1px solid #bdc3c7;
            border-radius: 4px;
            width: 200px;
            font-size: 16px;
        }
        
        button {
            background-color: #3498db;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            margin-left: 10px;
            transition: background-color 0.3s;
        }
        
        button:hover {
            background-color: #2980b9;
        }
        
        .result {
            margin-top: 20px;
        }
        
        .vaccine-box {
            background-color: #e1f5fe;
            border-left: 5px solid #0288d1;
            padding: 15px;
            margin-bottom: 15px;
            border-radius: 4px;
            display: none;
        }
        
        .vaccine-title {
            font-weight: bold;
            color: #01579b;
            margin-bottom: 5px;
            font-size: 18px;
        }
        
        .vaccine-detail {
            margin-bottom: 8px;
        }
        
        .info {
            background-color: #fff8e1;
            border-left: 5px solid #ffa000;
            padding: 15px;
            margin-bottom: 15px;
            border-radius: 4px;
        }
        
        .highlight {
            background-color: #fffacd;
            padding: 3px 5px;
            border-radius: 3px;
            font-weight: bold;
        }
        
        .no-vaccine {
            color: #7f8c8d;
            font-style: italic;
            text-align: center;
            padding: 20px;
        }
        
        .vaccine-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }
        
        .vaccine-card {
            background-color: #e8f5e9;
            border-radius: 8px;
            padding: 15px;
            border-left: 5px solid #4caf50;
        }
        
        .vaccine-card.mr {
            background-color: #e1f5fe;
            border-left-color: #0288d1;
        }
        
        .vaccine-card.dpt {
            background-color: #fff8e1;
            border-left-color: #ffa000;
        }
        
        .age-indicator {
            display: inline-block;
            background-color: #3498db;
            color: white;
            padding: 3px 8px;
            border-radius: 12px;
            font-size: 12px;
            margin-left: 10px;
        }
        
        .vaccine-schedule {
            margin-top: 30px;
            overflow-x: auto;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }
        
        th, td {
            border: 1px solid #ddd;
            padding: 10px;
            text-align: left;
        }
        
        th {
            background-color: #f2f2f2;
            font-weight: bold;
        }
        
        tr:nth-child(even) {
            background-color: #f9f9f9;
        }
        
        .current-age {
            font-weight: bold;
            color: #e74c3c;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Jadwal Vaksinasi Lengkap Berdasarkan Umur</h1>
        
        <div class="input-section">
            <label for="birthdate">Masukkan Tanggal Lahir:</label>
            <input type="date" id="birthdate">
            <button onclick="checkVaccine()">Periksa Vaksin</button>
        </div>
        
        <div class="info">
            <p>Sistem akan menampilkan vaksin yang diperlukan berdasarkan umur saat ini, dengan penekanan khusus pada vaksin <span class="highlight">MR</span> dan <span class="highlight">DPT Lanjutan</span> untuk usia 9 bulan.</p>
        </div>
        
        <div class="result" id="result">
            <!-- Hasil akan ditampilkan di sini -->
        </div>
        
        <div class="vaccine-schedule">
            <h2>Jadwal Vaksinasi Lengkap</h2>
            <table>
                <thead>
                    <tr>
                        <th>Vaksin</th>
                        <th>Usia Pemberian</th>
                        <th>Keterangan</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>BCG</td>
                        <td>0-2 bulan</td>
                        <td>Vaksin untuk mencegah tuberkulosis</td>
                    </tr>
                    <tr>
                        <td>HB-0</td>
                        <td>0-7 hari</td>
                        <td>Vaksin hepatitis B pertama</td>
                    </tr>
                    <tr>
                        <td>Polio-0</td>
                        <td>0-1 bulan</td>
                        <td>Vaksin polio pertama</td>
                    </tr>
                    <tr>
                        <td>DPT-HB-Hib 1</td>
                        <td>2 bulan</td>
                        <td>Vaksin kombinasi difteri, pertusis, tetanus, hepatitis B, dan Hib</td>
                    </tr>
                    <tr>
                        <td>Polio-1</td>
                        <td>2 bulan</td>
                        <td>Vaksin polio kedua</td>
                    </tr>
                    <tr>
                        <td>PCV 1</td>
                        <td>2 bulan</td>
                        <td>Vaksin pneumokokus pertama</td>
                    </tr>
                    <tr>
                        <td>Rotavirus 1</td>
                        <td>2 bulan</td>
                        <td>Vaksin rotavirus pertama</td>
                    </tr>
                    <tr>
                        <td>DPT-HB-Hib 2</td>
                        <td>3 bulan</td>
                        <td>Vaksin kombinasi kedua</td>
                    </tr>
                    <tr>
                        <td>Polio-2</td>
                        <td>3 bulan</td>
                        <td>Vaksin polio ketiga</td>
                    </tr>
                    <tr>
                        <td>Rotavirus 2</td>
                        <td>3 bulan</td>
                        <td>Vaksin rotavirus kedua (tergantung jenis vaksin)</td>
                    </tr>
                    <tr>
                        <td>DPT-HB-Hib 3</td>
                        <td>4 bulan</td>
                        <td>Vaksin kombinasi ketiga</td>
                    </tr>
                    <tr>
                        <td>Polio-3</td>
                        <td>4 bulan</td>
                        <td>Vaksin polio keempat</td>
                    </tr>
                    <tr>
                        <td>PCV 2</td>
                        <td>4 bulan</td>
                        <td>Vaksin pneumokokus kedua</td>
                    </tr>
                    <tr>
                        <td>Rotavirus 3</td>
                        <td>4 bulan</td>
                        <td>Vaksin rotavirus ketiga (tergantung jenis vaksin)</td>
                    </tr>
                    <tr>
                        <td>PCV 3</td>
                        <td>6 bulan</td>
                        <td>Vaksin pneumokokus ketiga</td>
                    </tr>
                    <tr>
                        <td class="current-age">MR</td>
                        <td class="current-age">9 bulan</td>
                        <td class="current-age">Vaksin campak dan rubella</td>
                    </tr>
                    <tr>
                        <td>DPT-HB-Hib Lanjutan</td>
                        <td>12-18 bulan</td>
                        <td>Vaksin kombinasi lanjutan</td>
                    </tr>
                    <tr>
                        <td>MR Lanjutan</td>
                        <td>18 bulan</td>
                        <td>Vaksin campak dan rubella lanjutan</td>
                    </tr>
                    <tr>
                        <td>Polio-4</td>
                        <td>18 bulan</td>
                        <td>Vaksin polio kelima</td>
                    </tr>
                    <tr>
                        <td>DPT Lanjutan</td>
                        <td>5-7 tahun</td>
                        <td>Vaksin difteri, pertusis, tetanus lanjutan</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>

    <script>
        function checkVaccine() {
            const birthdateInput = document.getElementById('birthdate').value;
            const resultDiv = document.getElementById('result');
            
            if (!birthdateInput) {
                alert('Silakan masukkan tanggal lahir terlebih dahulu.');
                return;
            }
            
            const birthdate = new Date(birthdateInput);
            const today = new Date();
            
            // Hitung umur dalam bulan
            let ageInMonths = (today.getFullYear() - birthdate.getFullYear()) * 12;
            ageInMonths += today.getMonth() - birthdate.getMonth();
            
            // Koreksi jika hari ini belum mencapai tanggal lahir di bulan ini
            if (today.getDate() < birthdate.getDate()) {
                ageInMonths--;
            }
            
            // Format tanggal untuk ditampilkan
            const options = { day: 'numeric', month: 'long', year: 'numeric' };
            const formattedBirthdate = birthdate.toLocaleDateString('id-ID', options);
            const formattedToday = today.toLocaleDateString('id-ID', options);
            
            // Tampilkan hasil
            let resultHTML = `
                <div class="info">
                    <p>Tanggal lahir: <span class="highlight">${formattedBirthdate}</span></p>
                    <p>Hari ini: <span class="highlight">${formattedToday}</span></p>
                    <p>Umur saat ini: <span class="highlight">${ageInMonths} bulan</span></p>
                </div>
            `;
            
            // Vaksin berdasarkan usia
            let vaccines = [];
            
            if (ageInMonths >= 0 && ageInMonths <= 2) {
                vaccines.push({
                    name: "BCG",
                    description: "Vaksin untuk mencegah tuberkulosis. Diberikan sekali seumur hidup.",
                    age: "0-2 bulan",
                    type: "basic"
                });
            }
            
            if (ageInMonths >= 0 && ageInMonths <= 1) {
                vaccines.push({
                    name: "Polio-0",
                    description: "Vaksin polio pertama yang diberikan sesegera mungkin setelah lahir.",
                    age: "0-1 bulan",
                    type: "basic"
                });
                
                vaccines.push({
                    name: "HB-0",
                    description: "Vaksin hepatitis B pertama yang diberikan dalam waktu 12 jam setelah lahir.",
                    age: "0-7 hari",
                    type: "basic"
                });
            }
            
            if (ageInMonths >= 2 && ageInMonths <= 3) {
                vaccines.push({
                    name: "DPT-HB-Hib 1",
                    description: "Vaksin kombinasi pertama untuk mencegah difteri, pertusis, tetanus, hepatitis B, dan infeksi Haemophilus influenzae tipe B.",
                    age: "2 bulan",
                    type: "basic"
                });
                
                vaccines.push({
                    name: "Polio-1",
                    description: "Vaksin polio kedua yang diberikan bersamaan dengan DPT-HB-Hib 1.",
                    age: "2 bulan",
                    type: "basic"
                });
                
                vaccines.push({
                    name: "PCV 1",
                    description: "Vaksin pneumokokus pertama untuk mencegah infeksi pneumokokus seperti pneumonia dan meningitis.",
                    age: "2 bulan",
                    type: "optional"
                });
                
                vaccines.push({
                    name: "Rotavirus 1",
                    description: "Vaksin rotavirus pertama untuk mencegah diare akibat rotavirus.",
                    age: "2 bulan",
                    type: "optional"
                });
            }
            
            if (ageInMonths >= 3 && ageInMonths <= 4) {
                vaccines.push({
                    name: "DPT-HB-Hib 2",
                    description: "Vaksin kombinasi kedua untuk mencegah difteri, pertusis, tetanus, hepatitis B, dan infeksi Haemophilus influenzae tipe B.",
                    age: "3 bulan",
                    type: "basic"
                });
                
                vaccines.push({
                    name: "Polio-2",
                    description: "Vaksin polio ketiga yang diberikan bersamaan dengan DPT-HB-Hib 2.",
                    age: "3 bulan",
                    type: "basic"
                });
                
                vaccines.push({
                    name: "Rotavirus 2",
                    description: "Vaksin rotavirus kedua (tergantung jenis vaksin yang digunakan).",
                    age: "3 bulan",
                    type: "optional"
                });
            }
            
            if (ageInMonths >= 4 && ageInMonths <= 5) {
                vaccines.push({
                    name: "DPT-HB-Hib 3",
                    description: "Vaksin kombinasi ketiga untuk mencegah difteri, pertusis, tetanus, hepatitis B, dan infeksi Haemophilus influenzae tipe B.",
                    age: "4 bulan",
                    type: "basic"
                });
                
                vaccines.push({
                    name: "Polio-3",
                    description: "Vaksin polio keempat yang diberikan bersamaan dengan DPT-HB-Hib 3.",
                    age: "4 bulan",
                    type: "basic"
                });
                
                vaccines.push({
                    name: "PCV 2",
                    description: "Vaksin pneumokokus kedua.",
                    age: "4 bulan",
                    type: "optional"
                });
                
                vaccines.push({
                    name: "Rotavirus 3",
                    description: "Vaksin rotavirus ketiga (tergantung jenis vaksin yang digunakan).",
                    age: "4 bulan",
                    type: "optional"
                });
            }
            
            if (ageInMonths >= 6 && ageInMonths <= 7) {
                vaccines.push({
                    name: "PCV 3",
                    description: "Vaksin pneumokokus ketiga.",
                    age: "6 bulan",
                    type: "optional"
                });
            }
            
            // Vaksin khusus untuk usia 9 bulan
            if (ageInMonths === 9) {
                vaccines.push({
                    name: "MR (Campak dan Rubella)",
                    description: "Vaksin MR diberikan untuk melindungi anak dari penyakit campak dan rubella. Vaksin ini penting untuk mencegah komplikasi serius dari kedua penyakit tersebut.",
                    age: "9 bulan",
                    type: "mr",
                    priority: true
                });
                
                vaccines.push({
                    name: "DPT Lanjutan",
                    description: "Vaksin DPT (Difteri, Pertusis, Tetanus) lanjutan diberikan untuk memperkuat kekebalan tubuh anak terhadap ketiga penyakit tersebut.",
                    age: "9 bulan",
                    type: "dpt",
                    priority: true
                });
            }
            
            if (ageInMonths >= 12 && ageInMonths <= 18) {
                vaccines.push({
                    name: "DPT-HB-Hib Lanjutan",
                    description: "Vaksin kombinasi lanjutan untuk memperkuat kekebalan.",
                    age: "12-18 bulan",
                    type: "basic"
                });
            }
            
            if (ageInMonths >= 18 && ageInMonths <= 24) {
                vaccines.push({
                    name: "MR Lanjutan",
                    description: "Vaksin MR lanjutan untuk memperkuat kekebalan terhadap campak dan rubella.",
                    age: "18 bulan",
                    type: "mr"
                });
                
                vaccines.push({
                    name: "Polio-4",
                    description: "Vaksin polio kelima yang diberikan bersamaan dengan MR lanjutan.",
                    age: "18 bulan",
                    type: "basic"
                });
            }
            
            if (vaccines.length > 0) {
                resultHTML += `<div class="vaccine-grid">`;
                
                vaccines.forEach(vaccine => {
                    let cardClass = "vaccine-card";
                    if (vaccine.type === "mr") cardClass += " mr";
                    if (vaccine.type === "dpt") cardClass += " dpt";
                    
                    resultHTML += `
                        <div class="${cardClass}">
                            <div class="vaccine-title">${vaccine.name} <span class="age-indicator">${vaccine.age}</span></div>
                            <div class="vaccine-detail">${vaccine.description}</div>
                            ${vaccine.priority ? '<div class="vaccine-detail"><strong>Prioritas tinggi untuk usia saat ini!</strong></div>' : ''}
                        </div>
                    `;
                });
                
                resultHTML += `</div>`;
                
                if (ageInMonths === 9) {
                    resultHTML += `
                        <div class="info">
                            <p><strong>Segera kunjungi fasilitas kesehatan terdekat untuk mendapatkan vaksinasi MR dan DPT lanjutan!</strong></p>
                        </div>
                    `;
                }
            } else {
                resultHTML += `
                    <div class="no-vaccine">
                        <p>Saat ini tidak ada vaksin yang perlu diberikan untuk usia ${ageInMonths} bulan.</p>
                        <p>Lihat tabel jadwal vaksinasi lengkap di bawah untuk informasi lebih lanjut.</p>
                    </div>
                `;
            }
            
            resultDiv.innerHTML = resultHTML;
        }
        
        // Set tanggal default untuk contoh (9 bulan yang lalu)
        window.onload = function() {
            const today = new Date();
            const nineMonthsAgo = new Date(today.getFullYear(), today.getMonth() - 9, today.getDate());
            document.getElementById('birthdate').valueAsDate = nineMonthsAgo;
        };
    </script>
</body>
</html>
