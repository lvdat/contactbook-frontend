<template>
    <div class="page">
        <h4>Thêm mới Liên hệ</h4>
        <ContactForm
            :contact="contact"
            @submit:contact="addContact"
        />
        <p>{{ message }}</p>
    </div>
</template>
<script>
import ContactForm from '@/components/ContactForm.vue'
import ContactService from '@/services/contact.service'

export default {
    components: {
        ContactForm,
    },
    data()  {
        return {
            contact: { name: "" },
            message: "",
        }
    },
    methods: {
        async addContact(data) {
            try {
                await ContactService.create(data)
                this.message = "Đã thêm liên hệ!"
            } catch (err) {
                console.log(err)
            }
        }
    },
    created() {
        this.message = ""
    }
}
</script>