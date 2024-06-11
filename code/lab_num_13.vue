<template>
    <div>
      <div>
        <h3>Сгенерированная последовательность:</h3>
        <p>{{ sequence }}</p>
      </div>
      <div>
        <h3>Среднее значение: {{ mean }}</h3>
        <h3>Дисперсия: {{ variance }}</h3>
      </div>
      <div>
        <h3>Гистограмма:</h3>
        <div v-for="(count, index) in histogram" :key="index">
          Интервал {{ index }}: {{ '*'.repeat(count) }}
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        sequence: [],
        mean: 0,
        variance: 0,
        histogram: Array(10).fill(0)
      };
    },
    created() {
      const seq1 = Array.from({length: 40}, () => Math.random() * 4 + 1);
      const seq2 = Array.from({length: 40}, () => Math.random() * 4 + 1);
  
      const combinedSeq = seq1.concat(seq2).sort((a, b) => a - b);
  
      this.sequence = combinedSeq;
  
      this.mean = combinedSeq.reduce((acc, val) => acc + val, 0) / combinedSeq.length;
  
      const squaredDifferences = combinedSeq.map(val => (val - this.mean) ** 2);
      this.variance = squaredDifferences.reduce((acc, val) => acc + val, 0) / combinedSeq.length;
  
      for (let i = 0; i < combinedSeq.length; i++) {
        const interval = Math.floor(combinedSeq[i]) - 1;
        this.histogram[interval]++;
      }
    }
  };
  </script>
  