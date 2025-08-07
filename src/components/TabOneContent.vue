<template>
  <div class="tab-one-content">
    <div class="content-header">
      <h2>Soal dan Jawaban</h2>
      <p class="subtitle">Latihan Pemrograman</p>
    </div>

    <div class="two-column-layout">
      <!-- Kolom Kiri - Soal -->
      <div class="left-column">
        <div class="question-card">
          <div class="card-header">
            <div class="card-icon">📝</div>
            <h3>Soal Latihan</h3>
          </div>
          
          <div class="question-content">
            <div class="question-item">
              <h4>Soal 1: Transformasi Data JSON</h4>
              <p>Transformasikan data JSON berikut ke bentuk lain sesuai output:</p>
              <pre><code>[[0,2,3,4,6,8,9,11,13],
[0,3,6,8,10,11,13],
[0,2,4,6,9,10,11,13],
[0,2,3,4,6,8,10,11,13],
[0,2,3,4,6,8,9,11,13]]</code></pre>
              <p><strong>Output yang diharapkan:</strong></p>
              <pre class="expected-output"><code>- x - - - x - x - - x - x –
- x x - x x - x - x - - x –
- x - x - x - x x - - - x –
- x - - - x - x - x - - x –
- x - - - x - x - - x - x –</code></pre>
              <p>Transformasikan array angka menjadi string dengan format seperti output di atas.</p>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Kolom Kanan - Jawaban -->
      <div class="right-column">
        <div class="solution-card">
          <div class="card-header">
            <div class="card-icon">💡</div>
            <h3>Solusi</h3>
          </div>
          
          <div class="solution-actions">
            <button 
              @click="showSolution(1)" 
              :class="['solution-button', { active: activeSolution === 1 }]"
            >
              Solution 1
            </button>
            <button 
              @click="showSolution(2)" 
              :class="['solution-button', { active: activeSolution === 2 }]"
            >
              Solution 2
            </button>
          </div>
          
          <div class="solution-content">
            <!-- Solution 1 -->
            <div v-if="activeSolution === 1" class="solution-item">
              <h4>Solusi 1 Transformasi Data JSON:</h4>
              <pre><code>const input =  [
  [0,2,3,4,6,8,9,11,13],
  [0,3,6,8,10,11,13],
  [0,2,4,6,9,10,11,13],
  [0,2,3,4,6,8,10,11,13],
  [0,2,3,4,6,8,9,11,13]
]

const variable = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13];

let printout = ''
input.forEach(row => {
  const output = variable.map(v => row.includes(v) ? '-' : 'x');
  printout += output.join(' ') + '\n'
});

codeOutput.value = printout</code></pre>

              <div style="margin-top: 1rem;">
                <button @click="solutionOne" class="process-button">Process Code</button>
              </div>
              <div v-if="activeSolutionOne" class="code-output" style="margin-top: 1rem;">
                <h4>Output:</h4>
                <pre><code>{{ codeOutput }}</code></pre>
              </div>
              
              <div class="solution-explanation">
                <h5>Penjelasan Solusi:</h5>
                <p>Dari input dan output saya bisa asumsikan bahwa terdapat variable kolom dengan panjang 14 [0,1,2,3,4,5,6,7,8,9,10,11,12,13], jadi saya bisa definisi kan variableColumn = [0,1,2,3,4,5,6,7,8,9,10,11,12,13], lalu untuk mencapai output yang di harapkan, saya harus melakukan identifikasi input berdasarkan kolom yang saya definisikan dengan melakukan looping terhadap input dan variableColumn, maka saya bisa mendapatkan hasil yang di inginkan. Secara logic dari input untuk mencapai output, setiap value dari variableColumn, di check apakah row pada input mengandung value dari variableColumn jika ya maka print '-' jika tidak print 'x', logic yang sama berlaku di row selanjutnya.</p>
                <p>Algoritma ini mengubah representasi indeks numerik menjadi representasi visual dengan karakter 'x' dan '-' sesuai dengan keberadaan indeks dalam setiap array.</p>
              </div>
            </div>
            
            <!-- Solution 2 -->
            <div v-if="activeSolution === 2" class="solution-item">
              <h4>Solusi 2 Transformasi Data JSON:</h4>
              <pre><code>const input =  [
    [0,2,3,4,6,8,9,11,13],
    [0,3,6,8,10,11,13],
    [0,2,4,6,9,10,11,13],
    [0,2,3,4,6,8,10,11,13],
    [0,2,3,4,6,8,9,11,13]
  ];

  // Cari nilai max di input
  const maxVal = Math.max(...input.flat());

  // Buat variable dari 0 sampai maxVal (+1 untuk iterasi looping)
  const variable = Array.from({ length: maxVal + 1 }, (_, i) => i);

  let printout = ''
  // Loop input → map ke variable
  input.forEach(row => {
    const output = variable.map(v => row.includes(v) ? '-' : 'x');
    printout += output.join(' ') + '\n'
  });

  codeOutput.value = printout</code></pre>
              <div style="margin-top: 1rem;">
                <button @click="solutionTwo" class="process-button">Process Code</button>
              </div>
              <div v-if="activeSolutionTwo" class="code-output" style="margin-top: 1rem;">
                <h4>Output:</h4>
                <pre><code>{{ codeOutput }}</code></pre>
              </div>
              <div class="solution-explanation">
                <h5>Penjelasan Solusi:</h5>
                <p>dari soal yang saya dapatkan, saya tidak akan berasumsi apapun untuk variable, jadi hal pertama, dari input saya akan mencari dan mengambil nilai terbesar dari seluruh row lalu ditambah 1 (+1) untuk iterasi looping col.  Secara logic dari input untuk mencapai output, setiap value dari variable, di check apakah row pada input mengandung value dari variable jika ya maka print '-' jika tidak print 'x', logic yang sama berlaku di row selanjutnya.</p>
                <p>Algoritma ini mengubah representasi indeks numerik menjadi representasi visual dengan karakter 'x' dan '-' sesuai dengan keberadaan indeks dalam setiap array.</p>
              </div>
            </div>
            
            <!-- Default content when no solution is selected -->
            <div v-if="activeSolution === 0" class="no-solution">
              <p>Silakan pilih tombol Solution untuk melihat jawaban.</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// Solusi aktif yang ditampilkan (0 = tidak ada)
const activeSolution = ref(0)
const activeSolutionOne = ref(false)
const activeSolutionTwo = ref(false)
const codeOutput = ref('')

// Method untuk menampilkan solusi yang dipilih
const showSolution = (solutionNumber) => {
  if (activeSolution.value === solutionNumber) {
    // Toggle off jika diklik lagi
    activeSolution.value = 0
  } else {
    activeSolution.value = solutionNumber
  }
}

const solutionOne = () => {
  codeOutput.value = ''
  activeSolutionOne.value = true
  const input =  [
    [0,2,3,4,6,8,9,11,13],
    [0,3,6,8,10,11,13],
    [0,2,4,6,9,10,11,13],
    [0,2,3,4,6,8,10,11,13],
    [0,2,3,4,6,8,9,11,13]
  ]

  const variable = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13];

  let printout = ''
  input.forEach(row => {
    const output = variable.map(v => row.includes(v) ? '-' : 'x');
    printout += output.join(' ') + '\n'
  });

  codeOutput.value = printout
}

const solutionTwo = () => {
  codeOutput.value = ''
  activeSolutionTwo.value = true
  const input =  [
    [0,2,3,4,6,8,9,11,13],
    [0,3,6,8,10,11,13],
    [0,2,4,6,9,10,11,13],
    [0,2,3,4,6,8,10,11,13],
    [0,2,3,4,6,8,9,11,13]
  ];

  // Cari nilai max di input
  const maxVal = Math.max(...input.flat());

  // Buat variable dari 0 sampai maxVal (+1 untuk iterasi looping)
  const variable = Array.from({ length: maxVal + 1 }, (_, i) => i);

  let printout = ''
  // Loop input → map ke variable
  input.forEach(row => {
    const output = variable.map(v => row.includes(v) ? '-' : 'x');
    printout += output.join(' ') + '\n'
  });

  codeOutput.value = printout
}
</script>

<style scoped>
.tab-one-content {
  animation: fadeIn 0.5s ease-out;
  max-width: 1200px;
  margin: 0 auto;
}

.content-header {
  text-align: center;
  margin-bottom: 2rem;
}

.content-header h2 {
  font-size: 2rem;
  color: #1e293b;
  margin-bottom: 0.5rem;
}

.subtitle {
  color: #64748b;
  font-size: 1.1rem;
}

/* Layout 2 kolom */
.two-column-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
}

/* Styling untuk kolom kiri (soal) */
.left-column {
  animation: slideInLeft 0.6s ease-out;
}

.question-card {
  background: white;
  border-radius: 12px;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
  overflow: hidden;
  border: 1px solid #e2e8f0;
}

.card-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1.5rem;
  background: linear-gradient(135deg, #4f46e5 0%, #6366f1 100%);
  color: white;
}

.card-icon {
  font-size: 2rem;
}

.card-header h3 {
  font-size: 1.5rem;
  font-weight: 600;
  margin: 0;
}

.question-content {
  padding: 1.5rem;
}

.question-item {
  padding: 1.25rem;
  border-bottom: 1px solid #e2e8f0;
}

.question-item:last-child {
  border-bottom: none;
}

.question-item h4 {
  color: #1e293b;
  font-size: 1.25rem;
  margin-top: 0;
  margin-bottom: 1rem;
}

.question-item p {
  color: #475569;
  margin-bottom: 1rem;
  line-height: 1.6;
}

.question-item pre {
  background-color: #f8fafc;
  padding: 1rem;
  border-radius: 6px;
  overflow-x: auto;
  margin: 1rem 0;
  border: 1px solid #e2e8f0;
}

.question-item code {
  font-family: 'Courier New', monospace;
  color: #334155;
}

.question-resources {
  padding: 1.5rem;
  background-color: #f8fafc;
  border-top: 1px solid #e2e8f0;
}

.question-resources h4 {
  color: #1e293b;
  font-size: 1.1rem;
  margin-top: 0;
  margin-bottom: 1rem;
}

.question-resources ul {
  padding-left: 1.5rem;
  margin: 0;
}

.question-resources li {
  color: #475569;
  margin-bottom: 0.5rem;
}

/* Styling untuk kolom kanan (jawaban) */
.right-column {
  animation: slideInRight 0.6s ease-out;
}

.solution-card {
  background: white;
  border-radius: 12px;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
  overflow: hidden;
  border: 1px solid #e2e8f0;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.solution-card .card-header {
  background: linear-gradient(135deg, #0ea5e9 0%, #38bdf8 100%);
}

.solution-actions {
  display: flex;
  gap: 0.5rem;
  padding: 1rem;
  background-color: #f8fafc;
  border-bottom: 1px solid #e2e8f0;
}

.solution-button {
  padding: 0.75rem 1.25rem;
  background-color: #e2e8f0;
  color: #475569;
  border: none;
  border-radius: 6px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  flex: 1;
}

.solution-button:hover {
  background-color: #cbd5e1;
  transform: translateY(-2px);
}

.solution-button.active {
  background-color: #0ea5e9;
  color: white;
}

.process-button {
  padding: 0.75rem 1.25rem;
  background-color: #67e169;
  color: #ffffff;
  border: none;
  border-radius: 6px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  flex: 1;
}

.process-button:hover {
  background-color: #cbd5e1;
  transform: translateY(-2px);
}

.process-button.active {
  background-color: #0ea5e9;
  color: white;
}

.clear-button {
  padding: 0.75rem 1.25rem;
  background-color: #e17967;
  color: #ffffff;
  border: none;
  border-radius: 6px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  flex: 1;
}

.clear-button:hover {
  background-color: #cbd5e1;
  transform: translateY(-2px);
}

.clear-button.active {
  background-color: #0ea5e9;
  color: white;
}

.solution-content {
  padding: 1.5rem;
  flex: 1;
  overflow-y: auto;
}

.solution-item {
  animation: fadeIn 0.5s ease-out;
}

.solution-item h4 {
  color: #1e293b;
  font-size: 1.25rem;
  margin-top: 0;
  margin-bottom: 1rem;
}

.solution-item pre {
  background-color: #f8fafc;
  padding: 1rem;
  border-radius: 6px;
  overflow-x: auto;
  margin: 1rem 0;
  border: 1px solid #e2e8f0;
  font-size: 0.9rem;
  line-height: 1.5;
}

.solution-item code {
  font-family: 'Courier New', monospace;
  color: #334155;
}

.solution-explanation {
  background-color: #f0f9ff;
  padding: 1rem;
  border-radius: 6px;
  margin-top: 1.5rem;
  border-left: 4px solid #0ea5e9;
}

.solution-explanation h5 {
  color: #0e7490;
  margin-top: 0;
  margin-bottom: 0.75rem;
  font-size: 1.1rem;
}

.solution-explanation ul {
  padding-left: 1.5rem;
  margin-bottom: 1rem;
}

.solution-explanation li {
  color: #334155;
  margin-bottom: 0.5rem;
}

.solution-explanation p {
  color: #334155;
  margin: 0;
  line-height: 1.6;
}

.no-solution {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
  color: #94a3b8;
  font-style: italic;
  text-align: center;
}

/* Styling untuk output yang diharapkan */
.expected-output {
  background-color: #f1f5f9;
  border-left: 4px solid #4f46e5;
  font-family: monospace;
  font-size: 1.1rem;
  line-height: 1.5;
}

/* Animasi */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-20px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideInRight {
  from {
    opacity: 0;
    transform: translateX(20px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* Responsive */
@media (max-width: 900px) {
  .two-column-layout {
    grid-template-columns: 1fr;
  }
  
  .right-column {
    margin-top: 2rem;
  }
}
</style>
