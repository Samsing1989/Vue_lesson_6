<template>
    <div class="container">
        <label class="lable">
            CARD NUMBER
            <input type="text" maxlength="19" class="input" v-model="numberCard" />
        </label>
        <div class="body">
            <label class="lable">
                EXPIRY DATE
                <input type="text" maxlength="5" class="input" v-model="experyDate" />
            </label>
            <label class="lable">
                SECURE CODE
                <input type="text" maxlength="3" class="input" v-model="secureCode" />
            </label>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardNumber',
    props: {
        cardModelValue: {
            type: String,
        },

        experyModelValue: {
            type: String,
        },

        secureModelValue: {
            type: String,
        },
    },
    computed: {
        numberCard: {
            get() {
                return (this.cardModelValue ?? '').toString().replace(/(\d{4}(?=\S+))/g, '$1 ')
            },
            set(value) {
                value = value.replace(/\D/g, '')
                this.$emit('update:cardModelValue', value)
            },
        },
        experyDate: {
            get() {
                return (this.experyModelValue ?? '').replace(/(\d{2})(\d{2})/, '$1/$2')
            },
            set(value) {
                this.$emit('update:experyModelValue', value)
            },
        },
        secureCode: {
            get() {
                return this.secureModelValue
            },
            set(value) {
                this.$emit('update:secureModelValue', value)
            },
        },
    },
}
</script>

<style lang="css" scoped>
.container {
    padding: 50px;
    max-width: 600px;
}
.lable {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-bottom: 20px;
}
.input {
    padding: 10px;
    font-size: 20px;
}

.body {
    display: flex;
    gap: 10px;
    justify-content: space-between;
}
</style>
