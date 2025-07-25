<template>
  <div class="student-list-view">
    <h1>Student List</h1>
    <div v-if="loading" class="loading">Loading students...</div>
    <div v-else-if="error" class="error">{{ error }}</div>
    <div v-else class="students-container">
      <StudentCard 
        v-for="student in students" 
        :key="student.id" 
        :student="student" 
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import StudentCard from '@/components/StudentCard.vue'
import StudentService from '@/views/services/StudentService'
import type { Student } from '@/type'

const students = ref<Student[]>([])
const loading = ref(false)
const error = ref('')

onMounted(() => {
  loading.value = true
  StudentService.getStudents()
    .then((response) => {
      students.value = response
      loading.value = false
    })
    .catch((err) => {
      console.error('There was an error!', err)
      error.value = 'Failed to load students'
      loading.value = false
    })
})
</script>

<style scoped>
.student-list-view {
  padding: 20px;
  max-width: 1200px;
  margin: 0 auto;
}

.student-list-view h1 {
  text-align: center;
  color: #333;
  margin-bottom: 20px;
}

.loading, .error {
  text-align: center;
  padding: 20px;
  font-size: 18px;
}

.error {
  color: #e74c3c;
}

.students-container {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

@media (min-width: 768px) {
  .students-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
    gap: 20px;
  }
}
</style>