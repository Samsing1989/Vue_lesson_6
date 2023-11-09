<template>
    <user-age v-model.check.setColor="age" />
    <!-- <div>user age -- {{ age }}</div> -->
</template>

<script>
import UserAge from '@/components/TaskOne/UserAge.vue'
export default {
    name: 'TaskOne',
    components: {
        UserAge,
    },
    data() {
        return {
            age: null,
        }
    },
}
</script>

<style lang="scss" scoped></style>
