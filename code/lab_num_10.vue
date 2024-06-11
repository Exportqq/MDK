<template>
    <div>
      <select v-model="selectedGroup">
        <option v-for="group in groups" :value="group">{{ group }}</option>
      </select>
      <button @click="filterStudents">Показать студентов с задолженностями</button>
      <ul>
        <li v-for="student in filteredStudents" :key="student.id">
          {{ student.name }} - Группа: {{ student.group }} - Оценки: {{ student.grades }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        students: [
          { id: 1, name: 'Иван', group: 217, grades: [3, 4, 2] },
          { id: 2, name: 'Мария', group: 218, grades: [4, 5, 3] },
          { id: 3, name: 'Миша', group: 219, grades: [4, 5, 3] },
          { id: 4, name: 'Егор', group: 217, grades: [4, 2, 3] },
          { id: 5, name: 'Саня', group: 218, grades: [4, 4, 3] },
          { id: 6, name: 'Алексей', group: 219, grades: [3, 3, 4] },
          { id: 7, name: 'Ольга', group: 217, grades: [5, 4, 4] },
          { id: 8, name: 'Павел', group: 218, grades: [4, 3, 5] },
          { id: 9, name: 'Елена', group: 219, grades: [4, 5, 5] },
          { id: 10, name: 'Андрей', group: 218, grades: [3, 2, 4] },
          { id: 11, name: 'Наталья', group: 218, grades: [5, 4, 3] },
          { id: 12, name: 'Дмитрий', group: 219, grades: [4, 3, 4] },
          { id: 13, name: 'Анна', group: 217, grades: [5, 5, 4] }, 
          { id: 14, name: 'Кирилл', group: 218, grades: [3, 4, 5] },
          { id: 15, name: 'Татьяна', group: 219, grades: [4, 4, 3] },
          { id: 16, name: 'Ирина', group: 218, grades: [3, 3, 3] },
          { id: 17, name: 'Артем', group: 218, grades: [4, 5, 4] },
          { id: 18, name: 'Екатерина', group: 219, grades: [5, 2, 4] },
          { id: 19, name: 'Владимир', group: 219, grades: [4, 3, 5] },
          { id: 20, name: 'Светлана', group: 218, grades: [3, 4, 3] }
        ],
        groups: [217, 218, 219], 
        selectedGroup: 217,
      };
    },
    computed: {
      filteredStudents() {
        return this.students.filter(student => {
          return student.group === this.selectedGroup && student.grades.some(grade => grade < 3);
        });
      },
    },
    methods: {
      filterStudents() {
        // сюда кароче планировалась фильтрацию студентов, типо по алфавиту и тд, но я понял что голодный и ушел....
      },
    },
  };
  </script>
  