<template>
    <div class="container">
        <div class="row">
            <div class="col-md-8">
                <h1 class="text-center bg-primary p-3">add student</h1>
                <div class="card">
                    <form class="row g-3 m-4 needs-validation"   novalidate>
                        <div class="col-md-12">
                            <label for="validationCustom01" class="form-label">Name</label>
                            <input type="text" class="form-control" v-model="model.student.name" required>
                            <div class="invalid-feedback">
                                Name fields in required
                            </div>
                        </div>
                        <div class="col-md-12">
                            <label for="validationCustom01" class="form-label">Eamil</label>
                            <input type="email" class="form-control" v-model="model.student.email" required>
                            <div class="invalid-feedback">
                                Email fields in required
                            </div>
                        </div>
                        <div class="col-md-12">
                            <label for="validationCustom01" class="form-label">UserType</label>
                            <select class="form-select" aria-label="Default select example"
                                v-model="model.student.usertype">
                               
                                <option value="1" selected>admin</option>
                                <option value="2">user</option>
                                <option value="3">employee</option>
                            </select>
                            <div class="valid-feedback">
                                selected fields in required
                            </div>
                        </div>

                        <div class="col-12">
                            <button class="btn btn-primary" @click="saveStudent" type="button">Save Changes</button>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>

</template>
<script>
import axios from 'axios';

export default {
    name: 'studentCreate',
    data() {
        return {
            model: {
                student: {
                    name: '',
                    email: '',
                    usertype: '',
                }
            }
        }
    },
    methods: {
        saveStudent() {
            axios.post('http://localhost:8000/api/userApi', this.model.student)
                .then(res => {
                    alert(res.data.message)
                })
                
        }
    },
    mounted() {
        (() => {
            'use strict';

            // Fetch all the forms we want to apply custom Bootstrap validation styles to
            const forms = document.querySelectorAll('.needs-validation');

            // Loop over them and prevent submission
            Array.from(forms).forEach(form => {
                form.addEventListener('submit', event => {
                    if (!form.checkValidity()) {
                        event.preventDefault();
                        event.stopPropagation();
                    }

                    form.classList.add('was-validated');
                }, false);
            });
        })();
    }
}
</script>