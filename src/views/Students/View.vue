<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
    <div class="container">
        <div class="card">
            <div class="card-header">
                <h4>
                    Students
                    <RouterLink to="/student/create" class="btn btn-primary float-end"> Add Student</RouterLink>
                </h4>
            </div>
            <div class="card-body table-responsive-md">
                <table class="table table-bordered ">
                    <thead>
                        <tr>
                            <th>Id</th>
                            <th>Name</th>
                            <th>Course</th>
                            <th>Email</th>
                            <th>Phone</th>
                            <th>Created At</th>
                            <th>Action</th>
                        </tr>
                    </thead>
                    <tbody v-if="this.students.length > 0">
                        <tr v-for="(student, index) in this.students" :key="index">
                            <td>{{ student.id }}</td>
                            <td>{{ student.name }}</td>
                            <td>{{ student.course }}</td>
                            <td>{{ student.email }}</td>
                            <td>{{ student.phone }}</td>
                            <td>{{ student.createdAt }}</td>
                            <td>
                                <button href="#" class="btn btn-danger" type="button"> Delete</button>
                                <RouterLink to="/" class="btn btn-info"> Edit</RouterLink>
                            </td>
                        </tr>
                    </tbody>
                    <tbody v-else>
                        <tr>
                            <td colspan="7"> No data found</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: 'students',
    data() {
        return {
            students: [],
        }
    },
    mounted() {
        this.getStudents();
    },
    methods: {
        getStudents() {
            axios.get('https://650496acc8869921ae2539d1.mockapi.io/api/students').then(res => {
                this.students = res.data
                console.log(this.students)
            });
        }
    }
}
</script>
