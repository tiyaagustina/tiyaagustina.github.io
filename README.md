<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Aplikasi Acak</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      background-color: #272a2c;
    }

    #container {
      text-align: center;
      background: #edf0f1;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
      width: 300px;
    }

    h1 {
      font-size: 18px;
      color: #000000;
    }

    #hasilAcak {
      margin: 10px 0;
      font-size: 35px;
      font-weight: bold;
      color: #000000;
      text-transform:uppercase;
    }

    input {
      width: calc(100% - 20px);
      height: 40px;
      margin-bottom: 10px;
      padding: 0 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      font-size: 16px;
    }

    button {
      width: 100%;
      height: 40px;
      margin: 5px 0;
      background: #011852;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 16px;
      transition: background 0.3s;
    }

    button:hover {
        background: #272a2c;
    }

    .btn-tambah {
      width: 100%;
      height: 40px;
      margin: 5px 0;
      background: #000000;
      color: rgb(255, 255, 255);
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 16px;
      transition: background 0.3s;
    }

    .btn-tambah:hover {
        background: #272a2c;
    }

    ul {
      list-style-type: none;
      padding: 0;
      margin: 15px 0;
      max-height: 150px;
      overflow-y: auto;
    }

    li {
      margin: 5px 0;
      font-size: 16px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .btn-remove {
      color: red;
      cursor: pointer;
      font-weight: bold;
    }

    .btn-secondary {
      background: #790000;
      color: white;
    }

    .btn-secondary:hover {
      background: #272a2c;
    }
  </style>
</head>
<body>
  <div id="container">
    <h1>=== Aplikasi PickMe ===</h1>
    <div id="hasilAcak"></div>
    <div>
        <button onclick="acakDaftar()">Acak</button>
    </div>
    <input type="text" id="inputPilihan" placeholder="masukkan pilihan">
    <button class="btn-tambah" onclick="tambahPilihan()">Tambah</button>
    <ul id="daftarPilihan"></ul>
    <div>
        <button class="btn-secondary" onclick="bersihkanDaftar()">Bersih</button>
    </div>
  </div>

  <script>
    const daftarPilihan = document.getElementById("daftarPilihan");
    const inputPilihan = document.getElementById("inputPilihan");
    const hasilAcak = document.getElementById("hasilAcak");

    // Fungsi untuk menambahkan Pilihan ke daftar
    function tambahPilihan() {
      const Pilihan = inputPilihan.value.trim();

      if (Pilihan) {
        const li = document.createElement("li");
        li.textContent = Pilihan;

        const btnRemove = document.createElement("span");
        btnRemove.textContent = " x";
        btnRemove.className = "btn-remove";
        btnRemove.onclick = () => li.remove();

        li.appendChild(btnRemove);
        daftarPilihan.appendChild(li);
        inputPilihan.value = "";
      }
    }

    // Fungsi untuk menampilkan hasil acak
    function acakDaftar() {
      const items = Array.from(daftarPilihan.children);
      if (items.length > 0) {
        const randomIndex = Math.floor(Math.random() * items.length);
        const randomItem = items[randomIndex].textContent.replace(" x", "");
        hasilAcak.textContent = `${randomItem}`;
      } else {
        hasilAcak.textContent = "Daftar kosong! Tambahkan item terlebih dahulu.";
      }
    }

    // Fungsi untuk membersihkan daftar
    function bersihkanDaftar() {
      daftarPilihan.innerHTML = "";
      hasilAcak.textContent = "";
    }

    // Event listener untuk menambahkan dengan tombol Enter
    inputPilihan.addEventListener("keydown", (e) => {
      if (e.key === "Enter") {
        tambahPilihan();
      }
    });
  </script>
</body>
</html>
