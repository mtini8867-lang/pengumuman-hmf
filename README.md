# pengumuman-hmf
[Uploading pengumuman_hmf.html…]()

<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Pengumuman Kelulusan HMF</title>
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #1e3c72, #2a5298);
      color: #fff;
      text-align: center;
      padding: 50px 20px;
    }

    h1 {
      font-size: 2.5em;
      margin-bottom: 10px;
      text-shadow: 2px 2px 5px rgba(0,0,0,0.3);
    }

    .card {
      background: rgba(255, 255, 255, 0.1);
      border-radius: 20px;
      padding: 30px;
      margin: 20px auto;
      max-width: 500px;
      box-shadow: 0 0 15px rgba(255, 255, 255, 0.2);
      backdrop-filter: blur(10px);
    }

    input {
      padding: 10px;
      border-radius: 10px;
      border: none;
      width: 80%;
      margin: 15px 0;
      font-size: 1em;
    }

    button {
      background: #00b4d8;
      border: none;
      padding: 10px 20px;
      color: white;
      border-radius: 10px;
      cursor: pointer;
      transition: 0.3s;
      font-size: 1em;
    }

    button:hover {
      background: #0077b6;
    }

    .result {
      margin-top: 20px;
      font-size: 1.2em;
      font-weight: 500;
    }

    .status {
      font-size: 1.4em;
      margin-top: 10px;
      color: #90ee90;
      font-weight: bold;
    }

    .not-found {
      color: #ffcccc;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h1>🎓 Pengumuman Kelulusan Seleksi Wawancara</h1>
  <h2>Himpunan Mahasiswa Farmasi</h2>

  <div class="card">
    <p>Masukkan nama lengkap Anda untuk melihat hasil:</p>
    <input type="text" id="namaInput" placeholder="Contoh: INDAH NIRMALA SARI" />
    <br />
    <button onclick="cekKelulusan()">Cek Hasil</button>

    <div class="result" id="hasil"></div>
  </div>

  <script>
    const dataKelulusan = [
      { nama: "INDAH NIRMALA SARI", divisi: "Internal", status: "LULUS (KADIV)" },
      { nama: "RAHIL LUBNA", divisi: "Internal", status: "LULUS" },
      { nama: "NOVIA RAMADHANI", divisi: "Internal", status: "LULUS" },
      { nama: "DINA APRILIA", divisi: "Internal", status: "LULUS" },
      { nama: "BQ. UMIE HAFILDA", divisi: "Internal", status: "LULUS" },
      { nama: "SUCI HAWALIA PUTRI", divisi: "Internal", status: "LULUS" },
      { nama: "MUHAMAD LUTFI", divisi: "Eksternal", status: "LULUS (KADIV)" },
      { nama: "M. DEDE IRDAYANTO", divisi: "Eksternal", status: "LULUS" },
      { nama: "IDA SOLEHA", divisi: "Eksternal", status: "LULUS" },
      { nama: "ZALIYANA KHAIRATI", divisi: "Eksternal", status: "LULUS" },
      { nama: "LELY INDRI YENI", divisi: "Eksternal", status: "LULUS" },
      { nama: "DASA MUTIARA RATMANINGSIH", divisi: "RaSa", status: "LULUS (KADIV)" },
      { nama: "YOLANDA ELSIAN TIRA ILODRA", divisi: "RaSa", status: "LULUS" },
      { nama: "SITI NUR HINAYAH", divisi: "RaSa", status: "LULUS" },
      { nama: "HUSNUL KHOTIMAH", divisi: "RaSa", status: "LULUS" },
      { nama: "M. WYAN DESKA WAHID", divisi: "RaSa", status: "LULUS" },
      { nama: "NOVIA ZALIYANTY ATMY", divisi: "Minat Bakat", status: "LULUS (KADIV)" },
      { nama: "AULIA KHAERANI", divisi: "Minat Bakat", status: "LULUS" },
      { nama: "DEVA ANGGARINI", divisi: "Minat Bakat", status: "LULUS" },
      { nama: "INTAN APRILIA PUTRI", divisi: "Minat Bakat", status: "LULUS" },
      { nama: "BAIQ. TIRTA PUTRI RINJANI B.K", divisi: "Minat Bakat", status: "LULUS" },
      { nama: "LULU HAULIA", divisi: "Keagamaan", status: "LULUS (KADIV)" },
      { nama: "HELMALIA PUTRI", divisi: "Keagamaan", status: "LULUS" },
      { nama: "DESI", divisi: "Keagamaan", status: "LULUS" },
      { nama: "BAIQ. HIMAYA ASFIA", divisi: "Keagamaan", status: "LULUS" },
      { nama: "SITI MARYAM", divisi: "Pengabdian Masyarakat", status: "LULUS (KADIV)" },
      { nama: "WIRA YUDA", divisi: "Pengabdian Masyarakat", status: "LULUS" },
      { nama: "SITI AULIA SYAKBANI", divisi: "Pengabdian Masyarakat", status: "LULUS" },
      { nama: "PALZA ALIM SAPUTRA", divisi: "Pengabdian Masyarakat", status: "LULUS" },
      { nama: "LISDA AULIA RERANI", divisi: "Pengabdian Masyarakat", status: "LULUS" },
      { nama: "MEZA ALPIRA LARASATI", divisi: "Pengabdian Masyarakat", status: "LULUS" },
      { nama: "MARTINI", divisi: "Media & Komunikasi", status: "LULUS (KADIV)" },
      { nama: "ALOFIA ADNI AK", divisi: "Media & Komunikasi", status: "LULUS" },
      { nama: "JUNITA AULIA", divisi: "Media & Komunikasi", status: "LULUS" },
      { nama: "MAYGOZA SUPANI", divisi: "Media & Komunikasi", status: "LULUS" },
      { nama: "HUSNUL KHARNINGSIH", divisi: "Media & Komunikasi", status: "LULUS" },
      { nama: "HAMZAN MUZADI", divisi: "Asisten Laboratorium Farmasi (ALFA)", status: "LULUS (KADIV)" },
      { nama: "ADITYA KUSUMA PUTRA", divisi: "Asisten Laboratorium Farmasi (ALFA)", status: "LULUS" },
      { nama: "PINA ASTUTI", divisi: "Asisten Laboratorium Farmasi (ALFA)", status: "LULUS" },
    ];

    function cekKelulusan() {
      const inputNama = document.getElementById("namaInput").value.trim().toUpperCase();
      const hasilDiv = document.getElementById("hasil");

      const hasil = dataKelulusan.find(item => item.nama === inputNama);

      if (hasil) {
        hasilDiv.innerHTML = `
          <p>Nama: <b>${hasil.nama}</b></p>
          <p>Divisi: <b>${hasil.divisi}</b></p>
          <p class="status">${hasil.status}</p>
        `;
      } else {
        hasilDiv.innerHTML = `<p class="not-found">❌ Nama tidak ditemukan. Pastikan penulisan sesuai daftar peserta.</p>`;
      }
    }
  </script>
</body>
</html>
