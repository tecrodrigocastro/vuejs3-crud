<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
    <div class="card">
        <div class="card-header">
            <h4>
                Students
                <RouterLink to="/student/create" class="btn btn-primary float-end"> Add Student</RouterLink>
            </h4>
        </div>
        <div class="card-body">
            <table class="table table-bordered">
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
                <tbody>
                    <tr></tr>
                </tbody>
            </table>
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
        getStudents(){
            axios.get('https://650496acc8869921ae2539d1.mockapi.io/api/students').then(res => {
                console.log(res)
            });
        }
    }
}
</script>
