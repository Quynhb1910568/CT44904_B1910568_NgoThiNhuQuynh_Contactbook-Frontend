<template>
    <div class="page">
        <h4>Thêm liên hệ</h4>
        <ContactForm :contact="contact" @submit:contact="postContact" />
        <p>{{ message }}</p>
    </div>
</template>
<script>
import ContactForm from "../components/ContactForm.vue";
import ContactService from "../services/contact.service";
export default {
    components: {
        ContactForm,
    },
    data() {
        return {
            contact: {},
            message: "",
        };
    },
    methods: {
        async postContact(data) {
            try {
                await ContactService.create(data);
                this.message = "Thông tin được thêm thành công.";
            } catch (error) {
                console.log(error);
            }
        },
    },
    created() {
        this.message = "";
    },
};
</script>