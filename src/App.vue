<script setup>
import { ref } from 'vue'
const menu = ref(false)
const nav = [['projects','ผลงาน'],['skills','ทักษะ'],['experience','ประสบการณ์'],['education','การศึกษา'],['activities','กิจกรรม'],['contact','ติดต่อ']]
const skills = [
 ['Programming','SQL · PHP · C · C++ · C# · JavaScript · Python · Java · HTML · CSS · Dart'],
 ['Design & multimedia','Photoshop · Illustrator · Canva · Premiere Pro · After Effects · CapCut'],
 ['Network & IoT','ติดตั้งและตั้งค่า LAN/WLAN, Router, Switch และ Access Point ทดลองใช้ ESP32 เซนเซอร์ และ Servo Motor ในระบบให้อาหารสัตว์อัจฉริยะ'],
 ['Application development','พัฒนาเว็บแอป ไฮบริดแอป และเนทีฟแอป ออกแบบฐานข้อมูล SQL และ NoSQL รวมถึงพัฒนาและทดสอบ API']
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
    <section id="skills" class="group-section"><small>ทักษะ</small><h2>ความสามารถหลัก</h2><div class="grid2"><article v-for="[name,detail] in skills" :key="name" class="tile"><h3>{{name}}</h3><p>{{detail}}</p></article></div></section>
    <section id="projects" class="group-section"><small>ผลงาน</small><h2>ผลงานที่ภาคภูมิใจ</h2><article class="tile"><small>เว็บแอปพลิเคชัน</small><h3>ระบบจัดตารางเรียนอัตโนมัติด้วย CP-SAT</h3><p>ใช้ CP-SAT Solver จัดคาบเรียนภายใต้เงื่อนไขที่ซับซ้อน ช่วยลดคาบเรียนซ้ำซ้อน และลดเวลาในการจัดตารางสอน</p></article></section>
    <section id="education" class="group-section"><small>การศึกษา</small><h2>ประวัติการศึกษา</h2><div class="grid2"><article v-for="[level,school,field,gpa] in education" :key="level" class="tile"><h3>{{level}}</h3><p>{{school}} · {{field}}</p><em>GPA {{gpa}}</em></article></div></section>
    <section id="activities" class="group-section"><small>กิจกรรม</small><h2>กิจกรรมและเกียรติบัตร</h2><div class="grid2"><figure class="photo"><img src="/showcase.jpg" loading="lazy" alt="บูธจัดแสดงผลงาน"><figcaption>ผลงานเว็บไซต์และโครงการด้าน IT</figcaption></figure><figure class="photo"><img src="/award.jpg" loading="lazy" alt="ภาพกิจกรรมรับเกียรติบัตร"><figcaption>ภาพกิจกรรมรับเกียรติบัตร</figcaption></figure>
        <a v-for="cert in certificates" :key="cert.file" class="photo certificate" :href="'./certificates/' + cert.file">
          <img :src="'./certificates/' + (cert.preview || cert.file)" loading="lazy" alt="">
          <div class="caption"><strong>{{ cert.title }}</strong><p>{{ cert.detail }}</p><span>{{ cert.preview ? 'เปิด PDF' : 'ดูภาพเต็ม' }}</span></div>
        </a>
      </div>
    </section>
    <section id="contact" class="group-section"><small>ติดต่อ</small><h2>ช่องทางติดต่อ</h2><div class="grid2"><a class="tile" href="mailto:pserith009@gmail.com"><small>อีเมล</small><h3>pserith009@gmail.com</h3></a><a class="tile" href="tel:+66979681021"><small>โทรศัพท์</small><h3>097-968-1021</h3></a></div></section>
  </main>
  <footer>© อชิรวิชญ์ พวงพิลา</footer>
</template>

