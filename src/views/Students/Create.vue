<template>
    <div class="container mt-5">
        <div class="card">
            <div class="card-header">
                <h4>Add Students</h4>
            </div>
            <div class="card-body">
                <div class="mb-3">
                    <label for="">Name</label>
                    <input type="text" v-model="model.student.name" class="form-control">
                </div>
                <div class="mb-3">
                    <label for="">Course</label>
                    <input type="text" v-model="model.student.course" class="form-control">
                </div>
                <div class="mb-3">
                    <label for="">Email</label>
                    <input type="text" v-model="model.student.email" class="form-control">
                </div>
                <div class="mb-3">
                    <label for="">Phone</label>
                    <input type="text" v-model="model.student.phone" class="form-control">
                </div>
                <div class="mb-3">
                    <button type="button" @click="saveStudent" class="btn btn-success"> Add </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: "studentCreate",
    data() {
        return {
            model: {
                student: {
                    name: 'adryanne',
                    course: 'eng ',
                    email: 'teste2test@gmail.com',
                    phone: '387826643',
                }
            }
        }
    },
    mounted() {
        this.saveStudent();
    },
    methods: {
        saveStudent() {
            axios.post('https://650496acc8869921ae2539d1.mockapi.io/api/students', this.model.student).then(res => {
                console.log(res);
                alert(res.data.message);

                this.model.student = {
                    name: '',
                    course: '',
                    email: '',
                    phone: '',
                }
            }).catch(function (error) {
                if (error.response) {
                    console.error(error.response.data);
                    console.error(error.response.status);
                    console.error(error.response.headers);
                } else if (error.request) {
                    console.error(error.request);
                } else {
                    console.error('Error', error.message);
                }
            })
        }
    }
}
</script>