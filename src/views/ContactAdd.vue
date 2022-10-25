<template>
    <div class="page">
        <h4>Tạo liên hệ</h4>
        <ContactForm :contact="contact" @submit:contact="uploadContact" />
        <p>{{ message }}</p>
    </div>
</template>
<script>
import ContactForm from '../components/ContactForm.vue';
import ContactService from '../services/contact.service';

export default {
    components: {
        ContactForm
    },
    data() {
        return {
            contact: {},
            message: ""
        }
    },
    methods: {
        async uploadContact(data) {
            try {
                
                // console.log(data.file);
                await ContactService.create(data)
                this.message = "Liên hệ được tạo thành công."
            }
            catch (error) {
                console.log(error)
            }
        }
    },


}
</script>
<style>

</style>