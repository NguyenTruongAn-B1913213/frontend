<template>
    <div v-if="contact" class="page">
        <h4>Thêm Tên Liên hệ</h4>
        <ContactForm
            :contact="contact"
            @submit:contact="createContact"
        />
        <p>{{ message }}</p>
    </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue"
import ContactService from "@/services/contact.service";
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
        async createContact(data) {
            try {
                await ContactService.create(data);
                this.message = "Thêm Tên Liên Hệ thành công.";
                console.log(data);
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