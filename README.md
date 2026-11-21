<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>LandHub TH - ตลาดซื้อขายที่ดิน</title>
  <style>
    :root {
      --primary: #059669;
      --primary-hover: #047857;
      --secondary: #0f172a;
      --bg: #f8fafc;
      --card-bg: #ffffff;
      --text: #1e293b;
      --text-muted: #64748b;
      --border: #e2e8f0;
      --danger: #ef4444;
      --radius: 12px;
      --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.05);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    }

    body {
      background-color: var(--bg);
      color: var(--text);
      line-height: 1.5;
      padding-bottom: 60px;
    }

    header {
      background-color: var(--card-bg);
      border-bottom: 1px solid var(--border);
      position: sticky;
      top: 0;
      z-index: 50;
      box-shadow: 0 1px 3px rgba(0,0,0,0.05);
    }

    .nav-container {
      max-width: 1100px;
      margin: 0 auto;
      padding: 12px 16px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 10px;
    }

    .logo {
      font-size: 1.35rem;
      font-weight: 800;
      color: var(--primary);
      text-decoration: none;
      display: flex;
      align-items: center;
      gap: 8px;
      cursor: pointer;
    }

    .nav-actions {
      display: flex;
      align-items: center;
      gap: 8px;
      flex-wrap: wrap;
    }

    .btn {
      padding: 8px 16px;
      border-radius: 8px;
      font-size: 0.9rem;
      font-weight: 600;
      cursor: pointer;
      border: 1px solid transparent;
      transition: all 0.2s;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
      text-decoration: none;
    }

    .btn-primary {
      background-color: var(--primary);
      color: white;
    }

    .btn-primary:hover {
      background-color: var(--primary-hover);
    }

    .btn-outline {
      background-color: transparent;
      border-color: var(--border);
      color: var(--text);
    }

    .btn-outline:hover {
      background-color: #f1f5f9;
    }

    .btn-danger {
      background-color: #fee2e2;
      color: var(--danger);
    }

    .btn-danger:hover {
      background-color: #fecaca;
    }

    .container {
      max-width: 1100px;
      margin: 24px auto;
      padding: 0 16px;
    }

    .hidden {
      display: none !important;
    }

    .filter-card {
      background: var(--card-bg);
      padding: 16px;
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      margin-bottom: 24px;
      border: 1px solid var(--border);
    }

    .filter-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 12px;
    }

    input, select, textarea {
      width: 100%;
      padding: 10px 12px;
      border: 1px solid var(--border);
      border-radius: 8px;
      font-size: 0.95rem;
      background-color: #fff;
      color: var(--text);
      outline: none;
      transition: border-color 0.2s;
    }

    input:focus, select:focus, textarea:focus {
      border-color: var(--primary);
    }

    select:disabled {
      background-color: #f1f5f9;
      color: var(--text-muted);
      cursor: not-allowed;
    }

    .land-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 20px;
    }

    .card {
      background: var(--card-bg);
      border-radius: var(--radius);
      overflow: hidden;
      box-shadow: var(--shadow);
      border: 1px solid var(--border);
      display: flex;
      flex-direction: column;
      transition: transform 0.2s;
    }

    .card:hover {
      transform: translateY(-3px);
    }

    .card-img-wrap {
      position: relative;
      height: 200px;
      background-color: #0f172a;
    }

    .card-img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .badge {
      position: absolute;
      top: 12px;
      left: 12px;
      background: rgba(15, 23, 42, 0.8);
      color: #fff;
      padding: 4px 10px;
      border-radius: 20px;
      font-size: 0.75rem;
      font-weight: 600;
      z-index: 2;
    }

    .media-count-badge {
      position: absolute;
      bottom: 10px;
      right: 10px;
      background: rgba(0, 0, 0, 0.75);
      color: #fff;
      padding: 3px 8px;
      border-radius: 6px;
      font-size: 0.75rem;
    }

    .card-body {
      padding: 16px;
      flex: 1;
      display: flex;
      flex-direction: column;
    }

    .card-title {
      font-size: 1.1rem;
      font-weight: 700;
      margin-bottom: 6px;
      color: var(--secondary);
    }

    .card-location {
      font-size: 0.85rem;
      color: var(--text-muted);
      margin-bottom: 10px;
    }

    .card-meta {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: auto;
      padding-top: 12px;
      border-top: 1px solid var(--border);
    }

    .card-price {
      font-size: 1.2rem;
      font-weight: 800;
      color: var(--primary);
    }

    .card-area {
      font-size: 0.85rem;
      font-weight: 600;
      background: #f1f5f9;
      padding: 4px 8px;
      border-radius: 6px;
    }

    .card-footer {
      padding: 12px 16px;
      background: #f8fafc;
      border-top: 1px solid var(--border);
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 0.85rem;
    }

    .form-box {
      max-width: 650px;
      margin: 20px auto;
      background: var(--card-bg);
      padding: 24px;
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      border: 1px solid var(--border);
    }

    .form-title {
      font-size: 1.4rem;
      font-weight: 700;
      margin-bottom: 20px;
      text-align: center;
      color: var(--secondary);
    }

    .form-group {
      margin-bottom: 16px;
    }

    .form-group label {
      display: block;
      font-size: 0.9rem;
      font-weight: 600;
      margin-bottom: 6px;
    }

    .preview-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
      gap: 10px;
      margin-top: 10px;
      border: 2px dashed var(--border);
      border-radius: 8px;
      padding: 10px;
      min-height: 140px;
      background: #f8fafc;
    }

    .preview-item {
      position: relative;
      height: 100px;
      border-radius: 6px;
      overflow: hidden;
      background: #000;
    }

    .preview-item img, .preview-item video {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .modal-backdrop {
      position: fixed;
      inset: 0;
      background: rgba(15, 23, 42, 0.6);
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 16px;
      z-index: 100;
    }

    .modal-content {
      background: var(--card-bg);
      border-radius: var(--radius);
      max-width: 700px;
      width: 100%;
      max-height: 90vh;
      overflow-y: auto;
      padding: 24px;
      position: relative;
      box-shadow: 0 20px 25px -5px rgba(0,0,0,0.1);
    }

    .modal-close {
      position: absolute;
      top: 16px;
      right: 16px;
      background: #f1f5f9;
      border: none;
      width: 32px;
      height: 32px;
      border-radius: 50%;
      font-size: 1.2rem;
      cursor: pointer;
    }

    .media-gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 10px;
      margin-top: 15px;
    }

    .gallery-item {
      border-radius: 6px;
      overflow: hidden;
      background: #000;
      min-height: 180px;
      display: flex;
      align-items: center;
    }
  </style>
</head>
<body>

  <header>
    <div class="nav-container">
      <div class="logo" onclick="showSection('marketplace')">
        <span>🏞️</span> LandHub TH
      </div>
      
      <div id="nav-guest" class="nav-actions">
        <a href="login.html" class="btn btn-outline">เข้าสู่ระบบ</a>
        <a href="register.html" class="btn btn-primary">สมัครสมาชิก</a>
      </div>

      <div id="nav-user" class="nav-actions hidden">
        <span id="user-greeting" style="font-size: 0.95rem; font-weight: 700; color: var(--primary); margin-right: 6px;"></span>
        <button class="btn btn-primary" onclick="showSection('post-land')">+ ลงประกาศขาย</button>
        <button class="btn btn-outline" onclick="showSection('marketplace')">ตลาดที่ดิน</button>
        <button class="btn btn-danger" onclick="logout()">ออก</button>
      </div>
    </div>
  </header>

  <main class="container">
    <section id="sec-marketplace">
      <div class="filter-card">
        <div class="filter-grid">
          <input type="text" id="filter-search" placeholder="ค้นหาจังหวัด, อำเภอ, ชื่อประกาศ..." oninput="renderLands()">
          <select id="filter-type" onchange="renderLands()">
            <option value="">ประเภทที่ดินทั้งหมด</option>
            <option value="ที่ดินเปล่า">ที่ดินเปล่า</option>
            <option value="ที่ดินการเกษตร / สวน">ที่ดินการเกษตร / สวน</option>
            <option value="ที่ดินพร้อมสิ่งปลูกสร้าง">ที่ดินพร้อมสิ่งปลูกสร้าง</option>
            <option value="ที่ดินติดแม่น้ำ / ทะเล">ที่ดินติดแม่น้ำ / ทะเล</option>
          </select>
          <select id="filter-price" onchange="renderLands()">
            <option value="">ช่วงราคาทั้งหมด</option>
            <option value="0-1000000">ไม่เกิน 1 ล้านบาท</option>
            <option value="1000000-5000000">1 - 5 ล้านบาท</option>
            <option value="5000000-999999999">มากกว่า 5 ล้านบาท</option>
          </select>
          <button class="btn btn-outline" onclick="resetFilters()">ล้างตัวกรอง</button>
        </div>
      </div>

      <div id="land-list" class="land-grid"></div>
    </section>

    <section id="sec-post-land" class="hidden">
      <div class="form-box">
        <h2 id="form-action-title" class="form-title">ลงประกาศขายที่ดิน</h2>
        <form id="postLandForm">
          <input type="hidden" id="edit-id">
          <div class="form-group">
            <label>หัวข้อประกาศ</label>
            <input type="text" id="land-title" required placeholder="เช่น ขายที่ดินติดถนนสาย 41 ทำเลทอง">
          </div>

          <div class="filter-grid" style="margin-bottom: 16px;">
            <div>
              <label style="display:block; font-size:0.9rem; font-weight:600; margin-bottom:6px;">ประเภทที่ดิน</label>
              <select id="land-type" required>
                <option value="ที่ดินเปล่า">ที่ดินเปล่า</option>
                <option value="ที่ดินการเกษตร / สวน">ที่ดินการเกษตร / สวน</option>
                <option value="ที่ดินพร้อมสิ่งปลูกสร้าง">ที่ดินพร้อมสิ่งปลูกสร้าง</option>
                <option value="ที่ดินติดแม่น้ำ / ทะเล">ที่ดินติดแม่น้ำ / ทะเล</option>
              </select>
            </div>
            <div>
              <label style="display:block; font-size:0.9rem; font-weight:600; margin-bottom:6px;">ราคาขายรวม (บาท)</label>
              <input type="number" id="land-price" required min="1" placeholder="เช่น 1500000">
            </div>
          </div>

          <label style="display:block; font-size:0.9rem; font-weight:600; margin-bottom:6px;">ขนาดพื้นที่</label>
          <div class="filter-grid" style="margin-bottom: 16px; grid-template-columns: 1fr 1fr 1fr;">
            <input type="number" id="land-rai" placeholder="ไร่" min="0">
            <input type="number" id="land-ngan" placeholder="งาน" min="0" max="3">
            <input type="number" id="land-wah" placeholder="ตารางวา" min="0" max="99">
          </div>

          <label style="display:block; font-size:0.9rem; font-weight:600; margin-bottom:6px;">ที่ตั้งทรัพย์สิน (จังหวัด -> อำเภอ -> ตำบล)</label>
          <div id="address-container" class="filter-grid" style="margin-bottom: 16px; grid-template-columns: 1fr 1fr 1fr;">
            <select id="land-province" required onchange="onProvinceChange()">
              <option value="">กำลังโหลดจังหวัด...</option>
            </select>
            <select id="land-district" required disabled onchange="onDistrictChange()">
              <option value="">เลือกอำเภอ</option>
            </select>
            <select id="land-subdistrict" required disabled>
              <option value="">เลือกตำบล</option>
            </select>
          </div>

          <div class="form-group">
            <label>รายละเอียดเพิ่มเติม</label>
            <textarea id="land-desc" rows="3" required placeholder="ระบุจุดเด่น เอกสารสิทธิ์ โฉนดครุฑแดง หน้ากว้าง ฯลฯ"></textarea>
          </div>

          <div class="form-group">
            <label>เลือกรูปภาพและวิดีโอ (อัปโหลดได้หลายรายการ)</label>
            <input type="file" id="land-media" accept="image/*,video/*" multiple onchange="previewMedia(event)">
            <div class="preview-grid" id="media-preview">
              <span style="color: var(--text-muted); font-size: 0.85rem; grid-column: 1/-1; text-align: center; align-self: center;">ยังไม่ได้เลือกไฟล์</span>
            </div>
          </div>

          <div style="display: flex; gap: 10px;">
            <button type="button" class="btn btn-outline" style="flex: 1;" onclick="cancelForm()">ยกเลิก</button>
            <button type="submit" id="submit-btn" class="btn btn-primary" style="flex: 2;">เผยแพร่ประกาศ</button>
          </div>
        </form>
      </div>
    </section>
  </main>

  <div id="detail-modal" class="modal-backdrop hidden" onclick="closeModal(event)">
    <div class="modal-content" onclick="event.stopPropagation()">
      <button class="modal-close" onclick="closeModal()">&times;</button>
      <div id="modal-body"></div>
    </div>
  </div>

  <script>
    let currentMediaList = [];
    let isReadingFiles = false;
    let thaiGeoData = [];
    let isFallbackInput = false;
    const defaultImg = 'https://images.unsplash.com/photo-1500382017468-9049fed747ef?auto=format&fit=crop&w=800&q=80';

    // --- 1. โหลดฐานข้อมูล จังหวัด-อำเภอ-ตำบล (รองรับ CORS สำหรับ file:///) ---
    async function loadThailandAddress() {
      const provSelect = document.getElementById('land-province');
      const urls = [
        'https://cdn.jsdelivr.net/gh/kongvut/thai-province-data@master/api_province_with_amphure_tambon.json',
        'https://raw.githubusercontent.com/kongvut/thai-province-data/master/api_province_with_amphure_tambon.json'
      ];

      for (const url of urls) {
        try {
          const res = await fetch(url);
          if (!res.ok) continue;
          thaiGeoData = await res.json();
          thaiGeoData.sort((a, b) => a.name_th.localeCompare(b.name_th, 'th'));

          provSelect.innerHTML = '<option value="">-- เลือกจังหวัด --</option>';
          thaiGeoData.forEach(p => {
            const opt = document.createElement('option');
            opt.value = p.name_th;
            opt.textContent = p.name_th;
            provSelect.appendChild(opt);
          });
          return; // โหลดสำเร็จ ออกจากฟังก์ชันทันที
        } catch (err) {
          console.warn('ลองโหลดจากแหล่งถัดไป:', err);
        }
      }

      // กรณีไม่มีเน็ตหรือเบราว์เซอร์บล็อกการโหลดไฟล์ ให้สลับเป็นช่องพิมพ์ชื่ออัตโนมัติจะได้ไม่ค้าง
      isFallbackInput = true;
      document.getElementById('address-container').innerHTML = `
        <input type="text" id="land-province" required placeholder="พิมพ์จังหวัด">
        <input type="text" id="land-district" required placeholder="พิมพ์อำเภอ">
        <input type="text" id="land-subdistrict" required placeholder="พิมพ์ตำบล">
      `;
    }

    function onProvinceChange() {
      if (isFallbackInput) return;
      const provName = document.getElementById('land-province').value;
      const distSelect = document.getElementById('land-district');
      const subSelect = document.getElementById('land-subdistrict');

      distSelect.innerHTML = '<option value="">-- เลือกอำเภอ --</option>';
      subSelect.innerHTML = '<option value="">-- เลือกตำบล --</option>';
      subSelect.disabled = true;

      if (!provName) {
        distSelect.disabled = true;
        return;
      }

      const province = thaiGeoData.find(p => p.name_th === provName);
      if (province && province.amphure) {
        const amphures = [...province.amphure].sort((a, b) => a.name_th.localeCompare(b.name_th, 'th'));
        amphures.forEach(a => {
          const opt = document.createElement('option');
          opt.value = a.name_th;
          opt.textContent = a.name_th;
          distSelect.appendChild(opt);
        });
        distSelect.disabled = false;
      }
    }

    function onDistrictChange() {
      if (isFallbackInput) return;
      const provName = document.getElementById('land-province').value;
      const distName = document.getElementById('land-district').value;
      const subSelect = document.getElementById('land-subdistrict');

      subSelect.innerHTML = '<option value="">-- เลือกตำบล --</option>';

      if (!distName) {
        subSelect.disabled = true;
        return;
      }

      const province = thaiGeoData.find(p => p.name_th === provName);
      const amphure = province?.amphure?.find(a => a.name_th === distName);
      if (amphure && amphure.tambon) {
        const tambons = [...amphure.tambon].sort((a, b) => a.name_th.localeCompare(b.name_th, 'th'));
        tambons.forEach(t => {
          const opt = document.createElement('option');
          opt.value = t.name_th;
          opt.textContent = t.name_th;
          subSelect.appendChild(opt);
        });
        subSelect.disabled = false;
      }
    }

    // --- 2. ระบบฐานข้อมูล IndexedDB ---
    const dbName = 'LandHubDB';
    const storeName = 'lands';

    function openDB() {
      return new Promise((resolve, reject) => {
        const request = indexedDB.open(dbName, 1);
        request.onupgradeneeded = (e) => {
          const db = e.target.result;
          if (!db.objectStoreNames.contains(storeName)) {
            db.createObjectStore(storeName, { keyPath: 'id' });
          }
        };
        request.onsuccess = () => resolve(request.result);
        request.onerror = () => reject(request.error);
      });
    }

    async function getAllLandsDB() {
      const db = await openDB();
      return new Promise((resolve, reject) => {
        const tx = db.transaction(storeName, 'readonly');
        const store = tx.objectStore(storeName);
        const req = store.getAll();
        req.onsuccess = () => {
          const sorted = req.result.sort((a, b) => b.id - a.id);
          resolve(sorted);
        };
        req.onerror = () => reject(req.error);
      });
    }

    async function saveLandDB(landData) {
      const db = await openDB();
      return new Promise((resolve, reject) => {
        const tx = db.transaction(storeName, 'readwrite');
        const store = tx.objectStore(storeName);
        const req = store.put(landData);
        req.onsuccess = () => resolve();
        req.onerror = () => reject(req.error);
      });
    }

    async function migrateOldData() {
      const oldData = localStorage.getItem('land_posts');
      if (oldData) {
        try {
          const parsed = JSON.parse(oldData);
          for (const item of parsed) {
            if (!item.MediaList) {
              item.MediaList = [{ type: 'image', data: item.image || defaultImg }];
            }
            await saveLandDB(item);
          }
          localStorage.removeItem('land_posts');
        } catch (err) {
          console.error('Migration skipped:', err);
        }
      }
    }

    function checkLoginStatus() {
      const loggedInUser = localStorage.getItem('loggedInUser');
      const navGuest = document.getElementById('nav-guest');
      const navUser = document.getElementById('nav-user');
      const userGreeting = document.getElementById('user-greeting');

      if (loggedInUser) {
        navGuest.classList.add('hidden');
        navUser.classList.remove('hidden');
        userGreeting.textContent = 'สวัสดีคุณ ' + loggedInUser;
      } else {
        navGuest.classList.remove('hidden');
        navUser.classList.add('hidden');
      }
    }

    function logout() {
      localStorage.removeItem('loggedInUser');
      window.location.reload();
    }

    function showSection(sectionId) {
      document.getElementById('sec-marketplace').classList.add('hidden');
      document.getElementById('sec-post-land').classList.add('hidden');
      const target = document.getElementById('sec-' + sectionId);
      if (target) target.classList.remove('hidden');
    }

    function cancelForm() {
      document.getElementById('postLandForm').reset();
      document.getElementById('edit-id').value = '';
      if (!isFallbackInput) {
        document.getElementById('land-district').innerHTML = '<option value="">เลือกอำเภอ</option>';
        document.getElementById('land-district').disabled = true;
        document.getElementById('land-subdistrict').innerHTML = '<option value="">เลือกตำบล</option>';
        document.getElementById('land-subdistrict').disabled = true;
      }
      document.getElementById('form-action-title').textContent = 'ลงประกาศขายที่ดิน';
      document.getElementById('submit-btn').textContent = 'เผยแพร่ประกาศ';
      document.getElementById('media-preview').innerHTML = '<span style="color: var(--text-muted); font-size: 0.85rem; grid-column: 1/-1; text-align: center; align-self: center;">ยังไม่ได้เลือกไฟล์</span>';
      currentMediaList = [];
      showSection('marketplace');
    }

    async function previewMedia(event) {
      const files = Array.from(event.target.files);
      const output = document.getElementById('media-preview');
      if (files.length === 0) return;

      isReadingFiles = true;
      const submitBtn = document.getElementById('submit-btn');
      submitBtn.disabled = true;
      submitBtn.textContent = 'กำลังโหลดไฟล์...';

      output.innerHTML = '';
      currentMediaList = [];

      const readPromises = files.map(file => {
        return new Promise((resolve) => {
          const reader = new FileReader();
          const isVideo = file.type.startsWith('video');
          reader.onload = function(e) {
            resolve({
              type: isVideo ? 'video' : 'image',
              data: e.target.result
            });
          };
          reader.readAsDataURL(file);
        });
      });

      currentMediaList = await Promise.all(readPromises);

      currentMediaList.forEach(media => {
        const div = document.createElement('div');
        div.className = 'preview-item';
        if (media.type === 'video') {
          div.innerHTML = `<video src="${media.data}" muted></video>`;
        } else {
          div.innerHTML = `<img src="${media.data}">`;
        }
        output.appendChild(div);
      });

      isReadingFiles = false;
      submitBtn.disabled = false;
      submitBtn.textContent = document.getElementById('edit-id').value ? 'บันทึกการแก้ไข' : 'เผยแพร่ประกาศ';
    }

    document.getElementById('postLandForm').addEventListener('submit', async function(e) {
      e.preventDefault();
      if (isReadingFiles) {
        alert('กรุณารอให้ระบบโหลดรูปภาพหรือวิดีโอเสร็จสักครู่ครับ');
        return;
      }

      const editId = document.getElementById('edit-id').value;
      const rai = document.getElementById('land-rai').value || 0;
      const ngan = document.getElementById('land-ngan').value || 0;
      const wah = document.getElementById('land-wah').value || 0;

      const subdistrict = document.getElementById('land-subdistrict').value.trim();
      const district = document.getElementById('land-district').value.trim();
      const province = document.getElementById('land-province').value.trim();

      try {
        if (editId) {
          const allLands = await getAllLandsDB();
          const existing = allLands.find(x => x.id === Number(editId));
          if (existing) {
            existing.title = document.getElementById('land-title').value;
            existing.type = document.getElementById('land-type').value;
            existing.price = Number(document.getElementById('land-price').value);
            existing.area = `${rai} ไร่ ${ngan} งาน ${wah} ตร.ว.`;
            existing.location = `ต.${subdistrict} อ.${district} จ.${province}`;
            existing.province = province;
            existing.district = district;
            existing.subdistrict = subdistrict;
            existing.description = document.getElementById('land-desc').value;
            if (currentMediaList.length > 0) {
              existing.MediaList = currentMediaList;
            }
            await saveLandDB(existing);
            alert('แก้ไขประกาศสำเร็จแล้ว!');
          }
        } else {
          const landData = {
            id: Date.now(),
            title: document.getElementById('land-title').value,
            type: document.getElementById('land-type').value,
            price: Number(document.getElementById('land-price').value),
            area: `${rai} ไร่ ${ngan} งาน ${wah} ตร.ว.`,
            location: `ต.${subdistrict} อ.${district} จ.${province}`,
            province: province,
            district: district,
            subdistrict: subdistrict,
            description: document.getElementById('land-desc').value,
            MediaList: currentMediaList.length > 0 ? currentMediaList : [{ type: 'image', data: defaultImg }],
            seller: localStorage.getItem('loggedInUser') || 'ผู้ใช้งานทั่วไป',
            date: new Date().toLocaleDateString('th-TH')
          };
          await saveLandDB(landData);
          alert('เผยแพร่ประกาศสำเร็จแล้ว!');
        }

        cancelForm();
        await renderLands();
      } catch (err) {
        alert('เกิดข้อผิดพลาดในการบันทึก: ' + err.message);
      }
    });

    async function renderLands() {
      const listEl = document.getElementById('land-list');
      const allLands = await getAllLandsDB();
      
      const search = document.getElementById('filter-search').value.toLowerCase();
      const typeFilter = document.getElementById('filter-type').value;
      const priceFilter = document.getElementById('filter-price').value;

      const filtered = allLands.filter(item => {
        const matchSearch = item.title.toLowerCase().includes(search) || item.location.toLowerCase().includes(search);
        const matchType = !typeFilter || item.type === typeFilter;
        let matchPrice = true;
        if (priceFilter) {
          const [min, max] = priceFilter.split('-').map(Number);
          matchPrice = item.price >= min && item.price <= max;
        }
        return matchSearch && matchType && matchPrice;
      });

      if (filtered.length === 0) {
        listEl.innerHTML = '<p style="grid-column: 1/-1; text-align: center; color: var(--text-muted); padding: 40px;">ยังไม่มีประกาศขายที่ดินในระบบ</p>';
        return;
      }

      listEl.innerHTML = filtered.map(item => {
        const mediaArr = (item.MediaList && item.MediaList.length > 0) 
          ? item.MediaList 
          : [{ type: 'image', data: item.image || defaultImg }];

        const coverMedia = mediaArr[0];
        let coverHtml = '';
        if (coverMedia.type === 'video') {
          coverHtml = `<video class="card-img" src="${coverMedia.data}" muted></video>`;
        } else {
          coverHtml = `<img src="${coverMedia.data}" class="card-img" alt="${item.title}">`;
        }

        const countBadge = mediaArr.length > 1 
          ? `<span class="media-count-badge">+${mediaArr.length - 1} ไฟล์</span>` 
          : (coverMedia.type === 'video' ? `<span class="media-count-badge">🎬 วิดีโอ</span>` : '');

        return `
          <div class="card">
            <div class="card-img-wrap">
              ${coverHtml}
              <span class="badge">${item.type}</span>
              ${countBadge}
            </div>
            <div class="card-body">
              <div class="card-title">${item.title}</div>
              <div class="card-location">📍 ${item.location}</div>
              <div class="card-meta">
                <span class="card-price">฿${item.price.toLocaleString()}</span>
                <span class="card-area">${item.area}</span>
              </div>
            </div>
            <div class="card-footer">
              <span>ผู้ลงประกาศ: ${item.seller}</span>
              <div>
                <button class="btn btn-outline" style="padding: 4px 10px; font-size: 0.8rem;" onclick="openDetail(${item.id})">ดูรายละเอียด</button>
              </div>
            </div>
          </div>
        `;
      }).join('');
    }

    function resetFilters() {
      document.getElementById('filter-search').value = '';
      document.getElementById('filter-type').value = '';
      document.getElementById('filter-price').value = '';
      renderLands();
    }

    async function openDetail(id) {
      const allLands = await getAllLandsDB();
      const item = allLands.find(x => x.id === id);
      if (!item) return;

      const loggedInUser = localStorage.getItem('loggedInUser');
      const isOwner = loggedInUser && loggedInUser === item.seller;

      let editBtnHtml = '';
      if (isOwner) {
        editBtnHtml = `<button class="btn btn-primary" onclick="prepareEdit(${item.id})">แก้ไขประกาศนี้</button>`;
      } else if (!loggedInUser) {
        editBtnHtml = `<span style="color:red; font-size:0.8rem;">(ต้องเข้าสู่ระบบด้วยบัญชีผู้ลงประกาศเพื่อแก้ไข)</span>`;
      }

      const mediaArr = (item.MediaList && item.MediaList.length > 0) 
        ? item.MediaList 
        : [{ type: 'image', data: item.image || defaultImg }];

      const galleryHtml = mediaArr.map(m => {
        if (m.type === 'video') {
          return `<div class="gallery-item"><video src="${m.data}" controls style="width:100%; height:100%;"></video></div>`;
        } else {
          return `<div class="gallery-item"><img src="${m.data}" style="width:100%; height:100%; object-fit:cover;"></div>`;
        }
      }).join('');

      document.getElementById('modal-body').innerHTML = `
        <div class="media-gallery">${galleryHtml}</div>
        <span style="background:var(--primary); color:white; padding:4px 10px; border-radius:20px; font-size:0.8rem; display:inline-block; margin-top:15px;">${item.type}</span>
        <h2 style="margin:10px 0 6px;">${item.title}</h2>
        <p style="color:var(--text-muted); margin-bottom:12px;">📍 ${item.location}</p>
        <div style="display:flex; justify-content:space-between; background:#f8fafc; padding:12px; border-radius:8px; margin-bottom:16px;">
          <div><small style="color:var(--text-muted);">ราคาขาย</small><div style="font-size:1.3rem; font-weight:800; color:var(--primary);">฿${item.price.toLocaleString()}</div></div>
          <div><small style="color:var(--text-muted);">ขนาดพื้นที่</small><div style="font-size:1.1rem; font-weight:700;">${item.area}</div></div>
        </div>
        <h4 style="margin-bottom:6px;">รายละเอียด</h4>
        <p style="color:var(--text); white-space:pre-line; margin-bottom:16px;">${item.description}</p>
        <div style="display:flex; justify-content:space-between; align-items:center; border-top:1px solid var(--border); padding-top:12px;">
          <div style="font-size:0.9rem; color:var(--text-muted);">ลงประกาศโดย: <strong>${item.seller}</strong></div>
          ${editBtnHtml}
        </div>
      `;
      document.getElementById('detail-modal').classList.remove('hidden');
    }

    function closeModal() {
      document.getElementById('detail-modal').classList.add('hidden');
    }

    async function prepareEdit(id) {
      closeModal();
      const allLands = await getAllLandsDB();
      const item = allLands.find(x => x.id === id);
      if (!item) return;

      document.getElementById('edit-id').value = item.id;
      document.getElementById('land-title').value = item.title;
      document.getElementById('land-type').value = item.type;
      document.getElementById('land-price').value = item.price;
      document.getElementById('land-desc').value = item.description;

      const areaParts = item.area.match(/(\d+)\s*ไร่\s*(\d+)\s*งาน\s*(\d+)\s*ตร\.ว\./);
      if (areaParts) {
        document.getElementById('land-rai').value = areaParts[1];
        document.getElementById('land-ngan').value = areaParts[2];
        document.getElementById('land-wah').value = areaParts[3];
      }

      let prov = item.province || '';
      let dist = item.district || '';
      let sub = item.subdistrict || '';

      if (!prov) {
        const locParts = item.location.match(/ต\.(.*?)\s*อ\.(.*?)\s*จ\.(.*)/);
        if (locParts) {
          sub = locParts[1].trim();
          dist = locParts[2].trim();
          prov = locParts[3].trim();
        }
      }

      if (prov) {
        document.getElementById('land-province').value = prov;
        if (!isFallbackInput) {
          onProvinceChange();
          if (dist) {
            document.getElementById('land-district').value = dist;
            onDistrictChange();
            if (sub) {
              document.getElementById('land-subdistrict').value = sub;
            }
          }
        } else {
          document.getElementById('land-district').value = dist;
          document.getElementById('land-subdistrict').value = sub;
        }
      }

      const mediaArr = (item.MediaList && item.MediaList.length > 0) 
        ? item.MediaList 
        : [{ type: 'image', data: item.image || defaultImg }];

      currentMediaList = mediaArr;
      const previewArea = document.getElementById('media-preview');
      previewArea.innerHTML = mediaArr.map(m => {
        if (m.type === 'video') {
          return `<div class="preview-item"><video src="${m.data}" muted></video></div>`;
        } else {
          return `<div class="preview-item"><img src="${m.data}"></div>`;
        }
      }).join('');

      document.getElementById('form-action-title').textContent = 'แก้ไขประกาศที่ดิน';
      document.getElementById('submit-btn').textContent = 'บันทึกการแก้ไข';

      showSection('post-land');
    }

    window.addEventListener('DOMContentLoaded', async () => {
      checkLoginStatus();
      await loadThailandAddress();
      await migrateOldData();
      await renderLands();
    });
  </script>
</body>
