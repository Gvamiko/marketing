<template>
    <div>
        <navbar/>
        <div class="container row_position">
            <form action="#" class=" form_bg">
                <div class="row">
                    <div class="col-md-8 text_email1">
                        <label class="form-label" for="exhibition">გამოფენის დასახელება</label>
                        <input type="text" class="form-control input_form"  id="exhibition">
                        <label for="disabledTextInput" class="form-label mt-3 qui">გთხოვთ აკრიფოთ გასაგზავნი ტექსტი</label>
                        <QuillEditor theme="snow" class="input_form qui_h"/>
                        <input type="submit" class=" btn btn-success w-100  mt-3"  value="გაგზავნა">
                    </div>
                    <div class="col-md-4">
                        <div id="emailApp" class="">
                            <!-- Form for adding emails -->
                            <form @submit.prevent="addEmail">
                                <label class="form-label" for="emailInput">შეიყვანეთ ელ. ფოსტა</label>
                                <div class="input-group mb-3">
                                    <input type="email" class="form-control input_form_add" v-model="newEmail" required aria-label="Recipient's username" aria-describedby="button-addon2">
                                    <button type="submit" class="btn btn-secondary ">

                                    <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor"    class="bi bi-person-plus" viewBox="0 0 16 16">
                                        <path d="M6 8a3 3 0 1 0 0-6 3 3 0 0 0 0 6m2-3a2 2 0 1 1-4 0 2 2 0 0 1 4 0m4 8c0 1-1 1-1 1H1s-1 0-1-1 1-4 6-4 6 3 6 4m-1-.004c-.001-.246-.154-.986-.832-1.664C9.516 10.68 8.289 10 6 10s-3.516.68-4.168 1.332c-.678.678-.83 1.418-.832 1.664z"/>
                                        <path fill-rule="evenodd" d="M13.5 5a.5.5 0 0 1 .5.5V7h1.5a.5.5 0 0 1 0 1H14v1.5a.5.5 0 0 1-1 0V8h-1.5a.5.5 0 0 1 0-1H13V5.5a.5.5 0 0 1 .5-.5"/>
                                    </svg>
                                </button>
                                </div>
                            </form>
                            <!-- List to display added emails -->
                            <ol class="mt-4 ">
                                <li v-for="(email, index) in emails" :key="index">
                                    {{ email }}
                                    <button class="btn  btn_delete" @click="deleteEmail(index)">
                                        <svg xmlns="http://www.w3.org/2000/svg" width="25" height="25" fill="currentColor" class="bi bi-x delete_icon" viewBox="0 0 16 16">
                                        <path d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708"/>
                                        </svg>
                                    </button>
                                </li>
                            </ol>
                        </div>
                    </div>
                </div>
            </form>          
        </div>
    </div>
</template>

<script>
    import navbar from '../../components/navbar.vue'
    import { QuillEditor } from '@vueup/vue-quill'
    export default {

        
    data() {
    return {
        selected: '0',
        selected1: '0',
        newEmail: '',
        emails: []
    }
   },
    components: {
        navbar,
        QuillEditor,
    },
    mounted(){
        
    },
    methods: {
        addEmail() {
            if (this.newEmail) {
                this.emails.push(this.newEmail);
                this.newEmail = ''; // Clear input field after adding
            }
        },
        deleteEmail(index) {
            this.emails.splice(index, 1); // Remove email at the given index
        }
    }
   }

</script>

<style scoped>
.text_email1 {
    height: 250px !important;
}
.btn_delete {
    border: none !important;
    background-color: none !important;
}
.delete_icon {
    width: 30px !important;
    height: 30px !important;
}
</style>
