<template>
    <email-address v-model.domen.ckack="addressEmail" />
    <div class="body">{{ addressEmail }}</div>
</template>

<script>
import EmailAddress from '@/components/TaskThree/EmailAddress.vue'
export default {
    name: 'TaskThree',
    components: { EmailAddress },
    data() {
        return {
            addressEmail: null,
        }
    },
}
</script>

<style>
.body {
    font-size: 20px;
}
</style>
