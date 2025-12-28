---
theme: seriph
background: /bg.jpg
class: 'text-center'
highlighter: shiki
lineNumbers: false
info: |
  ## Web-based Smart Mfg Review
  Academic English Presentation
drawings:
  presenterOnly: true
transition: slide-left
---

<h1 v-motion :initial="{ opacity: 0, y: -50 }" :enter="{ opacity: 1, y: 0, transition: { duration: 800 } }">
  A Review of Web-Based Technologies
</h1>
<h2 v-motion :initial="{ opacity: 0, y: -30 }" :enter="{ opacity: 1, y: 0, transition: { duration: 800, delay: 200 } }">
  for Remote Monitoring in Smart Manufacturing
</h2>

<div class="pt-12" v-motion :initial="{ opacity: 0 }" :enter="{ opacity: 1, transition: { duration: 600, delay: 400 } }">
  <span class="text-2xl text-gray-500">Industry 4.0 & IIoT Context</span>
</div>

<div class="abs-br m-6 flex gap-2" v-motion :initial="{ opacity: 0, x: 50 }" :enter="{ opacity: 1, x: 0, transition: { duration: 600, delay: 600 } }">
  <span class="text-sm text-gray-400">Zeliang Hu / Tongji University</span>
</div>

---
layout: two-cols
transition: slide-up
---

<h1 v-motion :initial="{ opacity: 0, x: -50 }" :enter="{ opacity: 1, x: 0, transition: { duration: 600 } }">
  Introduction: <br>
  The Motivation
</h1>

<v-clicks>

<div v-motion :initial="{ opacity: 0, y: 20 }" :enter="{ opacity: 1, y: 0, transition: { duration: 500 } }">
<h3>🏭 Physical Constraints</h3>
<p>Monitoring is driven by <strong>hazardous environments</strong>, remote locations (offshore/mining), and adverse weather.</p>
</div>

<div v-motion :initial="{ opacity: 0, y: 20 }" :enter="{ opacity: 1, y: 0, transition: { duration: 500 } }">
<h3>🚫 Legacy SCADA Limitations</h3>
<ul>
<li><strong>Platform Dependent:</strong> Locked to Windows.</li>
<li><strong>High Cost:</strong> Prohibitive maintenance & travel.</li>
<li><strong>Rigid:</strong> Complex local installation.</li>
</ul>
</div>

<div v-motion :initial="{ opacity: 0, y: 20 }" :enter="{ opacity: 1, y: 0, transition: { duration: 500 } }">
<h3>✅ B/S Architecture Solution</h3>
<ul>
<li><strong>Ubiquity:</strong> Accessible via Smartphones/Tablets.</li>
<li><strong>Zero-Install:</strong> Browser-based monitoring.</li>
</ul>
</div>

</v-clicks>

::right::

<div class="ml-4 mt-16 text-center" v-motion :initial="{ opacity: 0, scale: 0.8, x: 50 }" :enter="{ opacity: 1, scale: 1, x: 0, transition: { duration: 700, delay: 300 } }">
  <img src="https://images.unsplash.com/photo-1581091226825-a6a2a5aee158?auto=format&fit=crop&w=600&q=80" class="rounded-xl shadow-lg" />
  <div class="text-sm text-gray-400 mt-2">Remote Access to Heavy Machinery</div>
</div>

---
transition: view-transition
---

<h1 v-motion :initial="{ opacity: 0, y: -30 }" :enter="{ opacity: 1, y: 0, transition: { duration: 600 } }">
  1. Data Acquisition Protocols
</h1>

<p v-motion :initial="{ opacity: 0 }" :enter="{ opacity: 1, transition: { duration: 500, delay: 200 } }">
  Paradigm Shift: From HTTP to Light-weight Standards
</p>

<div class="grid grid-cols-2 gap-10 mt-10 relative">

<div v-motion :initial="{ opacity: 0, x: -50 }" :enter="{ opacity: 1, x: 0, transition: { duration: 600, delay: 400 } }">

<h3>🐢 HTTP (Legacy)</h3>
<ul>
<li><strong>Request-Response</strong> Model.</li>
<li>Heavy Headers & TCP Handshakes.</li>
<li>Inefficient for high-frequency sensor streams.</li>
</ul>

<div class="mt-4 flex justify-center" v-motion :initial="{ opacity: 0, scale: 0.9, y: 30 }" :enter="{ opacity: 1, scale: 1, y: 0, transition: { duration: 700, delay: 800 } }">
  <img src="https://plus.unsplash.com/premium_photo-1683758342945-e0e47a14a66d?q=80&w=1740&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" class="h-40 w-auto object-contain" />
</div>

</div>

<div v-motion :initial="{ opacity: 0, x: 50 }" :enter="{ opacity: 1, x: 0, transition: { duration: 600, delay: 600 } }">

<h3>🚀 MQTT & WebSocket (IIoT)</h3>
<ul>
<li><strong>Publish-Subscribe</strong> Model (Decoupled).</li>
<li><strong>WebSocket:</strong> Full-duplex "Server Push" for alerts.</li>
<li>Reduces bandwidth & battery usage.</li>
</ul>

<div class="mt-4 flex justify-center" v-motion :initial="{ opacity: 0, scale: 0.9, y: 30 }" :enter="{ opacity: 1, scale: 1, y: 0, transition: { duration: 700, delay: 800 } }">
  <img src="/R.jpg" class="h-40 w-auto object-contain" />
</div>

</div>

</div>


---
layout: two-cols
transition: slide-up
---

<h1>
  2. Backend Architecture
</h1>

<p>
  Handling Heterogeneous Data Streams
</p>

<v-clicks>

<div v-once v-motion :initial="{ opacity: 0, x: -30 }" :enter="{ opacity: 1, x: 0, transition: { duration: 500 } }">
<h3>⚡ Node.js (Event-Driven)</h3>
<ul>
<li><strong>Non-blocking I/O:</strong> Solves "C10k problem".</li>
<li>Ingests diverse sources (LoRaWAN, API, CSV).</li>
<li>Proven in agricultural DSS.</li>
</ul>
</div>

<div v-once v-motion :initial="{ opacity: 0, x: -30 }" :enter="{ opacity: 1, x: 0, transition: { duration: 500 } }">
<h3>💾 TSDB (Data Management)</h3>
<ul>
<li><strong>Time-Series Databases (e.g., InfluxDB)</strong>.</li>
<li>Essential for timestamped vibration/temp logs.</li>
<li>Superior write speeds over MySQL.</li>
</ul>
</div>

</v-clicks>

::right::

<div class="ml-4 mt-10 p-4 bg-gray-900 rounded-lg text-xs font-mono text-green-400">

```javascript
// Node.js Event Loop for IoT Ingestion
const mqtt = require('mqtt')
// Handling LoRaWAN & CSV streams asynchronously
client.on('message', (topic, payload) => {
  // Non-blocking write to InfluxDB
  influx.writePoints([{
    measurement: 'vibration_log',
    fields: { value: parseFloat(payload) }
  }])
})
```

</div>

---
transition: fade
---
<h1 v-motion :initial="{ opacity: 0, y: -30 }" :enter="{ opacity: 1, y: 0, transition: { duration: 600 } }"> 3. Visualization & Digital Twins </h1>

<p v-motion :initial="{ opacity: 0 }" :enter="{ opacity: 1, transition: { duration: 500, delay: 200 } }"> Bridging Physical Machinery and Digital Representations </p>

<div class="flex justify-center items-center h-80 gap-4">

<div class="w-1/3 bg-gray-100 p-4 rounded text-center opacity-50" v-motion :initial="{ opacity: 0, x: -100, scale: 0.8 }" :enter="{ opacity: 0.5, x: 0, scale: 1, transition: { duration: 600, delay: 400 } }"> <h3>Legacy 2D</h3> <div class="text-6xl">📉</div> <p>Numerical Dashboards</p> <p class="text-xs">Lacks spatial context & leads to ambiguity.</p> </div>

<div class="text-4xl" v-motion :initial="{ opacity: 0, scale: 0 }" :enter="{ opacity: 1, scale: 1, transition: { duration: 500, delay: 700, type: 'spring' } }">➡️</div>

<div class="w-1/2 bg-blue-100 p-4 rounded text-center border-2 border-blue-500" v-motion :initial="{ opacity: 0, x: 100, scale: 0.8, rotate: -10 }" :enter="{ opacity: 1, x: 0, scale: 1, rotate: 0, transition: { duration: 700, delay: 800, type: 'spring', stiffness: 100 } }"> <h3>3D Digital Twins</h3> <div class="text-6xl">🏗️</div> <p><strong>Three.js / Model Viewer / Unity</strong></p> <ul class="text-left text-sm mt-2"> <li><strong>Google Model Viewer:</strong> Lightweight components.</li> <li><strong>Dynamic Adaptation:</strong> Vue.js + Unity WebGL.</li> <li><strong>Result:</strong> Reduced ambiguity in spare parts ID.</li> </ul> </div>

</div>

---
transition: slide-down
class: bg-black text-white
---
<h1 v-motion :initial="{ opacity: 0, y: -30 }" :enter="{ opacity: 1, y: 0, transition: { duration: 600 } }"> 4. Security Challenges 🛡️ </h1>

<p v-motion :initial="{ opacity: 0 }" :enter="{ opacity: 1, transition: { duration: 500, delay: 200 } }"> Connecting ICS to Open Web Expands Attack Surface </p>

<div class="grid grid-cols-2 gap-12 mt-16">

<div v-click class="border-l-4 border-red-500 pl-4" v-motion :initial="{ opacity: 0, x: -50, rotate: -5 }" :enter="{ opacity: 1, x: 0, rotate: 0, transition: { duration: 600 } }">

<h3>🚨 Combined Attack Vector</h3>

<p><strong>MitM + XSS </strong></p>

<ul> <li>Attacker intercepts unencrypted MQTT.</li> <li>Injects malicious JS into sensor payload.</li> <li><strong>Impact:</strong> Dashboard executes script, stealing session cookies to control machinery.</li> </ul>

</div>

<div v-click class="border-l-4 border-yellow-500 pl-4" v-motion :initial="{ opacity: 0, x: 50, rotate: 5 }" :enter="{ opacity: 1, x: 0, rotate: 0, transition: { duration: 600 } }">

<h3>🛡️ Defense Mechanisms</h3>

<p><strong>ML-based Intrusion Detection</strong></p>

<ul> <li><strong>Problem:</strong> 99.7% of brokers are unencrypted.</li> <li><strong>Solution:</strong> Use ML (e.g., J48, k-NN) at the Edge to detect XSS/SQL anomalies.</li> </ul>

</div>

</div>

---
transition: slide-left
---
<h1 v-motion :initial="{ opacity: 0, y: -30 }" :enter="{ opacity: 1, y: 0, transition: { duration: 600 } }"> Conclusion </h1>

<p v-motion :initial="{ opacity: 0 }" :enter="{ opacity: 1, transition: { duration: 500, delay: 200 } }"> Synthesizing the Technical Layers </p>

<div class="mt-8">

<ol> <li v-motion :initial="{ opacity: 0, x: -30 }" :enter="{ opacity: 1, x: 0, transition: { duration: 500, delay: 400 } }"> <strong>Protocols:</strong> Lightweight <strong>MQTT</strong> reduces bandwidth/battery. </li>

<li v-motion :initial="{ opacity: 0, x: -30 }" :enter="{ opacity: 1, x: 0, transition: { duration: 500, delay: 600 } }"> <strong>Backend:</strong> <strong>Node.js</strong> efficiently handles concurrent heterogeneous I/O. </li>

<li v-motion :initial="{ opacity: 0, x: -30 }" :enter="{ opacity: 1, x: 0, transition: { duration: 500, delay: 800 } }"> <strong>Visualization:</strong> <strong>Web Components</strong> & <strong>Unity</strong> enable immersive Digital Twins. </li>

<li v-motion :initial="{ opacity: 0, x: -30 }" :enter="{ opacity: 1, x: 0, transition: { duration: 500, delay: 1000 } }"> <strong>Security:</strong> Must mitigate <strong>Cross-Protocol Injection</strong> via ML-IDS. </li> </ol>

</div>

<div class="mt-12 p-4 bg-blue-50 border-l-4 border-blue-500" v-motion :initial="{ opacity: 0, y: 30, scale: 0.95 }" :enter="{ opacity: 1, y: 0, scale: 1, transition: { duration: 600, delay: 1200, type: 'spring' } }"> <p class="font-bold">Future Direction:</p> Integrating robust <strong>Cybersecurity measures</strong> and <strong>Edge Computing</strong> for resilient manufacturing. </div>

---
layout: center
class: text-center
transition: fade
---

<div class="text-[100px]" style="color: var(--slidev-theme-primary)" v-motion :initial="{ opacity: 0, scale: 0.5 }" :enter="{ opacity: 1, scale: 1, transition: { duration: 1500, type: 'spring', stiffness: 20 } }"> Thank You </div> 


<div class="mt-10 text-sm text-gray-400" v-motion :initial="{ opacity: 0 }" :enter="{ opacity: 1, transition: { duration: 500, delay: 600 } }"> Hu Zeliang / Dept. of Mechanical Engineering </div>