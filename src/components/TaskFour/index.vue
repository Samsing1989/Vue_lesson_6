<template>
    <user-name-age v-model:nameModelValue="getUser" v-model:ageModelValue.color="getAge" />
</template>

<script>
import UserNameAge from '@/components/TaskFour/UserNameAge.vue'
export default {
    name: 'TaskFour',

    components: {
        UserNameAge,
    },
    data() {
        return {
            getUser: null,
            getAge: null,
        }
    },
}
</script>

<style></style>
