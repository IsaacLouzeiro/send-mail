<template>
    <div class="w-100 h-100 d-flex flex-column align-items-center justify-content-around">
        <div class="text-center">
            <h2 class="text-success">Send Mail Template</h2>
            <p class="text-secondary">Send mail from a Landing Page With VueJs and EmailJS</p>
        </div>
        <form @submit.prevent="sendMail($event)" class="row container">
            <div class="col-sm-6 py-2">
                <label class="form-label">Name</label>
                <input 
                    class="form-control"
                    type="text" 
                    v-model="name"
                    name="name"
                    placeholder="Your Name"
                >
            </div>
            
            <div class="col-sm-6 py-2">
                <label class="form-label">Email</label>
                <input 
                    class="form-control"
                    type="text" 
                    v-model="email"
                    name="email"
                    placeholder="Your Email"
                >
            </div>

            <div class=" py-2">
                <label class="form-label">Message</label>
                <textarea 
                    class="form-control"
                    name="message" 
                    v-model="message"
                    cols="30" rows="5"
                    placeholder="Message">
                </textarea>
            </div>

            <input type="submit" value="Send" class="btn btn-success col-3 mx-auto mt-4">
        </form>

        <div>
            Created With ❤ by <a href="https://isaaclouzeiro.dev.br" target="_blank" class="link-item">Isaac Louzeiro</a>
        </div>
    </div>
</template>

<script>
import emailjs from 'emailjs-com';

export default {
    name: 'ContactForm',
    data() {
        return {
            name: '',
            email: '',
            message: ''
        }
    },
    methods: {
        sendMail(e) {
            try {
                emailjs.sendForm('YOUR_SERVICE_ID', 'YOUR_SERVICE_ID', e.target, 'YOUR_SERVICE_ID', {
                    name: this.name,
                    email: this.email,
                    message: this.message
                })
            } catch(error) {
                console.log({error})
            }

            // reset
            this.name = ''
            this.email = ''
            this.message = ''
        }
    }
}
</script>