<template>
    <div class="container mt-5 mb-5">
        <RouterLink to="/student/create" class="btn btn-success">add student</RouterLink>
        <div class="card">
            <h3 class="text-center p-4 bg-primary">All Students CURD Operation </h3>
            <table class="table table-striped">
                <thead class="table-dark">
                    <tr>
                        <th scope="col">#ID</th>
                        <th scope="col">Name</th>
                        <th scope="col">Email</th>
                        <th scope="col">Usertype</th>
                        <th scope="col">Action</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(studentRecord, index) in students" :key="index">
                        <th>{{ studentRecord.id }}</th>
                        <td>{{studentRecord.name}}</td>
                        <td>{{studentRecord.email}}</td>

                        <td v-if="studentRecord.usertype == 0 ">
                            <span class="badge text-bg-info">Users</span>
                        </td>
                        <td v-else>
                            <span class="badge text-bg-success">Admin</span>
                        </td>
                        <td>
                            <button class="btn btn-primary">Edit</button>
                            <button @click="DeleteUser(studentRecord.id)" class="btn btn-danger m-2"> Delete</button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: "student",
    data() {
        return {
            students: [], // Corrected the property name to match the one used in getStudent method
        };
    },
    mounted() {
        this.getStudent();
        // console.log('sajid askajskad');
    },
    methods: {
        getStudent() {
            axios.get('http://localhost:8000/api/userApi').then(res => {
                this.students = res.data.users; // Corrected the property name
                console.log(this.students);
            });
        },
        DeleteUser(id){
            axios.delete(`http://localhost:8000/api/userApi/${id}/delete`).then(res => {
                alert(res.data.message)
            });
        }
    },
};
</script>
