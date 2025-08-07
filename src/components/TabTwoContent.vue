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
              <h4>Soal 2: Transformasi Data JSON</h4>
              <p>Transformasikan data JSON berikut ke bentuk lain sesuai output:</p>
              <pre><code>[[0,1,2,3],
[0,3,1,2],
[1,2,3,4],
[2,3,1,4],
[0,2,2,3]]
              </code></pre>
              <p><strong>Output yang diharapkan:</strong></p>
              <img src="/output2.png" alt="Output visualization" />
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
          </div>
          
          <div class="solution-content">
            <!-- Solution 1 -->
            <div v-if="activeSolution === 1" class="solution-item">
              <h4>Solusi Transformasi Data JSON:</h4>
              <pre><code>const input = [
  [0, 1, 2, 3],
  [0, 3, 1, 2],
  [1, 2, 3, 4],
  [2, 3, 1, 4],
  [0, 2, 2, 3],
];

let printout = ''
input.forEach((row, i) => {
  row.forEach((value, j) => {
    if (i > 0 && value === input[i - 1][j]) {
      row[j] = '+';
    }
    if (j > 0 && value === row[j - 1]) {
      row[j] = '-';
    }
  });
  printout += row.join(' | ') + '\n'
});
dataMatrix.value = printout

Solusi ini saya berikan untuk print console,
untuk print table bapak, ibu bisa langsung check code yang saya buat
pada component TabTwoContent.vue bagian script

Catatan:
- untuk tanda + pada cell berarti merge dengan row sebelumnya
- untuk tanda - pada cell berarti merge dengan col sebelumnya</code></pre>

              <div style="margin-top: 1rem;">
                <button @click="solutionOne" class="process-button">Process Code</button>
              </div>
              <div v-if="activeSolutionOne" class="code-output" style="margin-top: 1rem;">
                <h4>Output:</h4>
                <pre><code>{{ dataMatrix }}</code></pre>
                <div v-html="codeOutput"></div>
              </div>
              <div class="solution-explanation">
                <h5>Penjelasan Solusi:</h5>
                <p>Dari soal yang saya dapatkan, saya melakukan Analisa bahwa cell yang berdekatan dan nilainya sama akan di merge, baik row maupun cell, jadi saya bisa melakukan iterasi dari input yang ada untuk indentifikasi col dan row apakah terdapat nilai yang sama untuk cel atau row sebelumnya. jika sama maka merge. dari yang sudah saya kerjakan masih terdapat beberapa kekurangan, yang belum bisa saya pecahkan. yang merge lebih dari 2 cell belum bisa saya pecahkan. lalu jika ada merge cell di row dan col koordinat yang sama, saya masih belum bisa memecahkan.</p>
                <p>Algoritma ini mengubah representasi indeks numerik merge cell dengan keberadaan indeks dalam setiap array.</p>
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

const input = [
  [0, 1, 2, 3],
  [0, 0, 1, 2],
  [1, 2, 3, 4],
  [2, 3, 1, 4],
  [0, 2, 2, 3],
];

// Buat tabel HTML dengan merging
function generateMergedTable(matrix) {
  const rows = matrix.length;
  const cols = Math.max(...matrix.map(r => r.length));
  const mergeInfo = Array.from({ length: rows }, () =>
    Array.from({ length: cols }, () => ({ rowspan: 1, colspan: 1, skip: false }))
  );

  // Phase 1: Handle special characters first (+ and -)
  input.forEach((row, i) => {
    row.forEach((value, j) => {
      if (i > 0 && value === input[i - 1][j]) {
        if (i > 0 && !mergeInfo[i-1][j].skip) {
          mergeInfo[i-1][j].rowspan += 1;
          mergeInfo[i][j].skip = true;
        }
      }

      if (j > 0 && value === row[j - 1]) {
        if (j > 0 && !mergeInfo[i][j-1].skip) {
          mergeInfo[i][j-1].colspan += 1;
          mergeInfo[i][j].skip = true;
        }
      }
    });
  });

  // Generate HTML table
  let html = `<div style="overflow-x: auto; margin: 20px;">
  <table border="1" cellpadding="8" style="border-collapse: collapse; min-width: 800px; width: 100%; margin: 0 auto;">\n`;
  matrix.forEach((row, r) => {
    html += '  <tr>\n';
    row.forEach((cell, c) => {
      if (mergeInfo[r][c].skip) return;
      const { rowspan, colspan } = mergeInfo[r][c];
      html += `    <td${rowspan > 1 ? ` rowspan="${rowspan}"` : ''}${
        colspan > 1 ? ` colspan="${colspan}"` : ''
      } style="text-align:center; min-width: 100px; padding: 15px; font-size: 16px; white-space: nowrap;">${cell ?? ''}</td>\n`;
    });
    html += '  </tr>\n';
  });
  html += '</table>\n</div>';
  return html;
}

const dataMatrix = ref('')
const solutionOne = async () => {
  activeSolutionOne.value = true
  codeOutput.value = await generateMergedTable(input)
  let printout = ''
  input.forEach((row, i) => {
    row.forEach((value, j) => {
      if (i > 0 && (value === input[i - 1][j] || value == '+' || value == '-')) {
        row[j] = '+';
      }
      if (j > 0 && (value === row[j - 1] || value == '+' || value == '-')) {
        row[j] = '-';
      }
    });
    printout += row.join(' | ') + '\n'
  });
  dataMatrix.value = printout
};

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

.output-image {
  margin-top: 1.5rem;
  margin-bottom: 1.5rem;
  padding: 1rem;
  background-color: #f8fafc;
  border-radius: 8px;
  border: 1px solid #e2e8f0;
}

.output-image h5 {
  color: #1e293b;
  margin-top: 0;
  margin-bottom: 1rem;
  font-size: 1rem;
}

.output-visualization {
  max-width: 100%;
  border: 1px solid #e2e8f0;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
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
