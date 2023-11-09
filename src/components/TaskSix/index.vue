<template>
    <card-number
        v-model:cardModelValue="card"
        v-model:experyModelValue="expery"
        v-model:secureModelValue="secure"
        @keydown="onKeyDown"
    />
</template>

<script>
import CardNumber from '@/components/TaskSix/CardNumber.vue'
export default {
    components: {
        CardNumber,
    },
    name: 'TaskSix',
    data() {
        return {
            card: null,
            expery: null,
            secure: null,
        }
    },
    methods: {
        onKeyDown(event) {
            const key = event.key
            const isDigit = key >= '0' && key <= '9'
            const isBackspace = key === 'Backspace'
            if (!isDigit && !isBackspace) event.preventDefault()
        },
    },
}
</script>

<style lang="scss" scoped></style>
