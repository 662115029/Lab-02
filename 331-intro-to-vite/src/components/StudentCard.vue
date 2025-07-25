<template>
  <div class="student-card">
    <div class="student-image">
      <img :src="student.image" :alt="student.name" />
    </div>
    <div class="student-info">
      <h3>{{ student.name }} {{ student.surname }}</h3>
      <p><strong>Student ID:</strong> {{ student.studentId }}</p>
      <p><strong>GPA:</strong> {{ student.gpa.toFixed(2) }}</p>
      <p><strong>Pen Amount:</strong> {{ student.penAmount }}</p>
      <p><strong>Description:</strong> {{ student.description }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { Student } from '@/type'

defineProps<{
  student: Student
}>()
</script>

<style scoped>
.student-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 16px;
  margin: 8px;
  display: flex;
  gap: 16px;
  background: white;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.student-image img {
  width: 100px;
  height: 100px;
  object-fit: cover;
  border-radius: 50%;
}

.student-info {
  flex: 1;
}

.student-info h3 {
  margin: 0 0 8px 0;
  color: #333;
}

.student-info p {
  margin: 4px 0;
  color: #666;
}
</style>