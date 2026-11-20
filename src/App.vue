<script setup>
import { ref } from 'vue'
const menu = ref(false)
const viewer = ref(null)
const selected = ref(null)

function openViewer(src, title, pdf = false) {
  selected.value = { src, title, pdf }
  viewer.value.showModal()
}

const photos = [
  { src: './showcase.jpg', title: 'ผลงานเว็บไซต์และโครงการด้าน IT' },
  { src: './award.jpg', title: 'ภาพกิจกรรมรับเกียรติบัตร' }
]
const nav = [['projects','ผลงาน'],['skills','ทักษะ'],['experience','ประสบการณ์'],['education','การศึกษา'],['activities','กิจกรรม'],['contact','ติดต่อ']]
const skills = [
  {
    name: 'การเขียนโปรแกรม', category: 'code', icon: 'M8 7l-5 5 5 5m8-10 5 5-5 5m-3-14-2 18',
    tools: ['SQL','PHP','C','C++','C#','JavaScript','Python','Java','HTML','CSS','Dart']
  },
  {
    name: 'ออกแบบและมัลติมีเดีย', category: 'design', icon: 'M4 20l4-1 12-12-3-3L5 16l-1 4zm10-13 3 3',
    tools: ['Photoshop','Illustrator','Canva','Premiere Pro','After Effects','CapCut']
  },
  {
    name: 'เครือข่ายและ IoT', category: 'network', icon: 'M9 3h6v5H9zM2 16h7v5H2zm13 0h7v5h-7zm-3-8v4m-7 4v-4h14v4',
    tasks: ['ติดตั้งและตั้งค่าเครือข่าย LAN/WLAN รวมถึง Router, Switch และ Access Point','ทดลองใช้ ESP32 เซนเซอร์ และ Servo Motor ในระบบให้อาหารสัตว์อัจฉริยะ']
  },
  {
    name: 'การพัฒนาแอปพลิเคชัน', category: 'apps', icon: 'M2 4h15v12H2zM4 20h9m3-11h6v12h-6z',
    tasks: ['พัฒนาเว็บแอป ไฮบริดแอป และเนทีฟแอป','ออกแบบและจัดการฐานข้อมูล SQL และ NoSQL','พัฒนาและทดสอบ API']
  }
]
const education=[['ปวส.','วิทยาลัยเทคนิคเลย','เทคโนโลยีสารสนเทศ','3.92'],['ปวช.','วิทยาลัยเทคนิคเลย','เทคโนโลยีสารสนเทศ','3.95'],['มัธยมศึกษาตอนต้น','โรงเรียนบ้านปากปวน','ม.1 – 3','3.45'],['ประถมศึกษา','โรงเรียนบ้านปากปวน','ป.1 – 6','2.99']]

const stats = [
  ['experience', '7 เดือน', 'ระยะเวลาฝึกงานรวม', '◷'],
  ['education', '3.92', 'เกรดเฉลี่ยสะสม ปวส.', '☆'],
  ['skills', '4 ด้าน', 'ทักษะและความสามารถ', '⌘'],
  ['projects', 'CP-SAT', 'โครงการที่ภาคภูมิใจ', '▦']
]
const certificates = [
  { file: 'ai-award.jpg', title: 'ทักษะเทคโนโลยีปัญญาประดิษฐ์ ระดับ ปวส.', detail: 'รองชนะเลิศอันดับ 3 · มาตรฐานระดับเหรียญเงิน' },
  { file: 'nt-internship.jpg', title: 'ฝึกประสบการณ์วิชาชีพกับ NT', detail: 'ส่วนขายและบริการลูกค้าเลย · พ.ศ. 2567' },
  { file: 'cyber-cadet.jpg', title: 'ปฏิบัติหน้าที่ รด.ไซเบอร์', detail: 'มณฑลทหารบกที่ 28 · พ.ศ. 2566' },
  { file: 'achirawit.pdf', preview: 'pdf-preview.jpg', title: 'Cabling Contest Training #13', detail: 'เกียรติบัตรเข้าร่วมการอบรม' }
]
</script>
<template>
  <header class="flex items-center justify-between">
    <a class="brand flex items-center gap-2" href="#top" @click="menu=false"><img src="/dan.jpg" alt="">อชิรวิชญ์ พวงพิลา</a>
    <button class="toggle" :aria-expanded="menu" aria-controls="mainnav" aria-label="เมนูนำทาง" @click="menu=!menu">☰</button>
    <nav id="mainnav" :class="{ open:menu }" aria-label="เมนูหลัก"><a v-for="[id,label] in nav" :key="id" :href="'#'+id" @click="menu=false">{{label}}</a></nav>
  </header>
  <main id="top">
    <section class="profile">
      <div class="cover"><img src="/showcase.jpg" alt=""></div>
      <img class="avatar" src="/dan.jpg" alt="อชิรวิชญ์ พวงพิลา">
      <div class="profile-body">
        <h1>อชิรวิชญ์ พวงพิลา</h1><p class="alias">แดน · Dan</p>
        <p class="muted">ฝึกงาน 2 แผนก · ทักษะ 4 ด้าน</p>
        <p class="role">นักศึกษาเทคโนโลยีสารสนเทศ</p>
        <p>วิทยาลัยเทคนิคเลย · สนใจการพัฒนาเว็บแอปพลิเคชัน ระบบเครือข่าย และ IoT</p>
        <ul class="facts"><li><span aria-hidden="true">⌖</span> จังหวัดเลย ประเทศไทย</li><li><span aria-hidden="true">▤</span> ปวส. เทคโนโลยีสารสนเทศ · GPA 3.92</li></ul>
        <div class="actions"><a href="#contact">ติดต่อแดน</a><a href="#projects">ชมผลงาน</a></div>
        <nav class="tabs" aria-label="ส่วนต่าง ๆ ของแฟ้มสะสมผลงาน"><a v-for="[id,label] in nav" :key="id" :href="'#'+id">{{label}}</a></nav>
      </div>
    </section>
    <section class="group-section"><div class="summary-heading"><span class="symbol" aria-hidden="true">◴</span><div><h2>ภาพรวม</h2><small>แฟ้มสะสมผลงาน · อชิรวิชญ์ พวงพิลา</small></div></div>
      <div class="grid2"><a v-for="[id,value,label,icon] in stats" :key="id" class="tile stat" :href="'#'+id"><span class="symbol" aria-hidden="true">{{icon}}</span><div><strong>{{value}}</strong><p>{{label}}</p></div></a></div>
    </section>
    <section id="experience" class="group-section"><small>ฝึกงาน</small><h2>ประสบการณ์ฝึกงาน</h2>
      <article class="tile"><small>บริษัท โทรคมนาคมแห่งชาติ จำกัด (มหาชน)</small><h3>วิศวกรรมบริการ <em>5 เดือน</em></h3><p>ตรวจสอบคุณภาพสัญญาณอินเทอร์เน็ต เดินสายและติดตั้งอุปกรณ์กระจายสัญญาณ ณ สถานที่ของลูกค้า พร้อมลงพื้นที่ตรวจเช็กและซ่อมบำรุงโครงข่าย</p></article>
      <article class="tile"><small>บริษัท โทรคมนาคมแห่งชาติ จำกัด (มหาชน)</small><h3>สื่อสารข้อมูล <em>2 เดือน</em></h3><p>ติดตามสถานะวงจรสื่อสาร ตั้งค่าอุปกรณ์เครือข่าย ทดสอบความเร็วและเสถียรภาพก่อนส่งมอบ จัดทำผังเครือข่ายและบันทึกผลการแก้ไขปัญหา</p></article>
    </section>
    <section id="skills" class="group-section">
      <small>ทักษะ</small><h2>ความสามารถหลัก</h2>
      <div class="grid2">
        <article v-for="skill in skills" :key="skill.category" class="skill-card" :class="skill.category">
          <div class="skill-heading">
            <span class="skill-icon" aria-hidden="true"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round"><path :d="skill.icon"/></svg></span>
            <h3>{{ skill.name }}</h3>
          </div>
          <ul v-if="skill.tools" class="skill-tools"><li v-for="tool in skill.tools" :key="tool">{{ tool }}</li></ul>
          <ul v-else class="skill-tasks"><li v-for="task in skill.tasks" :key="task">{{ task }}</li></ul>
        </article>
      </div>
    </section>
    <section id="projects" class="group-section"><small>ผลงาน</small><h2>ผลงานที่ภาคภูมิใจ</h2><article class="tile"><small>เว็บแอปพลิเคชัน</small><h3>ระบบจัดตารางเรียนอัตโนมัติด้วย CP-SAT</h3><p>ใช้ CP-SAT Solver จัดคาบเรียนภายใต้เงื่อนไขที่ซับซ้อน ช่วยลดคาบเรียนซ้ำซ้อน และลดเวลาในการจัดตารางสอน</p></article></section>
    <section id="education" class="group-section"><small>การศึกษา</small><h2>ประวัติการศึกษา</h2><div class="grid2"><article v-for="[level,school,field,gpa] in education" :key="level" class="tile"><h3>{{level}}</h3><p>{{school}} · {{field}}</p><em>GPA {{gpa}}</em></article></div></section>
    <section id="activities" class="group-section"><small>กิจกรรม</small><h2>กิจกรรมและเกียรติบัตร</h2><div class="grid2"><button v-for="photo in photos" :key="photo.src" class="photo gallery-trigger" type="button" aria-haspopup="dialog" @click="openViewer(photo.src, photo.title)">
          <img :src="photo.src" loading="lazy" alt=""><strong class="photo-title">{{ photo.title }}</strong>
        </button>
        <button v-for="cert in certificates" :key="cert.file" type="button" aria-haspopup="dialog" class="photo certificate gallery-trigger" @click="openViewer('./certificates/' + cert.file, cert.title, cert.file.endsWith('.pdf'))">
          <img :src="'./certificates/' + (cert.preview || cert.file)" loading="lazy" alt="">
          <span class="caption"><strong>{{ cert.title }}</strong><span class="detail">{{ cert.detail }}</span><span class="view-label">{{ cert.preview ? 'เปิด PDF' : 'ดูภาพเต็ม' }}</span></span>
        </button>
      </div>
    </section>
    <section id="contact" class="group-section"><small>ติดต่อ</small><h2>ช่องทางติดต่อ</h2><div class="grid2"><a class="tile" href="mailto:pserith009@gmail.com"><small>อีเมล</small><h3>pserith009@gmail.com</h3></a><a class="tile" href="tel:+66979681021"><small>โทรศัพท์</small><h3>097-968-1021</h3></a></div></section>
  </main>
  <footer>© อชิรวิชญ์ พวงพิลา</footer>
  <dialog ref="viewer" class="viewer" aria-labelledby="viewer-title" @close="selected = null" @click="($event.target === viewer) && viewer.close()">
    <div v-if="selected" class="viewer-panel">
      <div class="viewer-head"><h2 id="viewer-title">{{ selected.title }}</h2><button type="button" autofocus @click="viewer.close()">ปิด ×</button></div>
      <template v-if="selected.pdf">
        <iframe :src="selected.src" :title="selected.title"></iframe>
        <a :href="selected.src" download>ดาวน์โหลด PDF</a>
      </template>
      <img v-else :src="selected.src" :alt="selected.title">
    </div>
  </dialog>
</template>



