<template>
    <section id="contact" class="mt-32">
        <SectionHeader title="Contact Me" />
        <div class="py-8 lg:py-16 px-4 mx-auto max-w-screen-md">
            <form class="space-y-8" @submit.prevent="sendEmail">
                <div v-for="(item, index) in inputs" :key="index">
                    <Input :id="item.id" :label="item.label" :type="item.type" :placeholder="item.placeholder"
                        :rows="item.rows" v-model="form[item.id]" />

                </div>
                <div class="flex justify-between">
                    <Button label="Send" type="submit" />

                    <div class="mt-2 flex justify-center space-x-2 md:space-x-7 mr-4">
                        <a href="https://www.linkedin.com/in/bahij-darwisy-farras-6324451a2?"
                            class="text-gray-600 hover:text-blue-700">
                            <Icon icon="fa-brands:linkedin" style="font-size: 1.8rem;" />
                        </a>
                        <a href="https://github.com/darwisyf"
                            class="text-gray-600 hover:text-gray-800 dark:hover:text-gray-400">
                            <Icon icon="fa-brands:github" style="font-size: 1.8rem;" />
                        </a>
                        <a href="https://instagram.com/darwisyy.f" class="text-gray-600 hover:text-pink-500">
                            <Icon icon="fa-brands:instagram" style="font-size: 1.8rem;" />
                        </a>
                    </div>
                </div>
            </form>
        </div>
    </section>
</template>
<script setup>
import SectionHeader from '@/components/UI/SectionHeader.vue';
import Input from '@/components/UI/Input.vue';
import Button from '@/components/UI/Button.vue';
import { ref, reactive } from 'vue';
import { Icon } from '@iconify/vue';
import emailjs from '@emailjs/browser';

const form = reactive({
    email: '',
    subject: '',
    message: ''
})

const inputs = ref([
    {
        id: 'email',
        label: 'Your Email',
        type: 'email',
        placeholder: 'email@example.com',
        rows: undefined
    },
    {
        id: 'subject',
        label: 'Subject',
        type: 'text',
        placeholder: 'Let me know how can i help you',
        rows: undefined
    },
    {
        id: 'message',
        label: 'Message',
        type: 'textarea',
        placeholder: 'Leave a message!',
        rows: 6
    },
])

const sendEmail = () => {
    emailjs.send(
        'service_3cq7dcj',
        'template_yn9xzzk',
        {
            form_email: form.email,
            subject: form.subject,
            message: form.message
        },
        'oTZWR3WU7FPx5LNb8'
    )
        .then(() => {
            alert('Message sent successfully')
            form.email = ''
            form.subject = ''
            form.message = ''
        })
        .catch(() => {
            alert('Failed to send message')
        })
}
</script>
