<template>
    <div>
        <p>
            Задача 3. Розробити компонент (з підтримкою v-model), який дозволяє вводити e-mail з домену “edu” (приклад:
            ivan-hopko@inv.mn.edu). Частинка «@inv.mn.edu» додається автоматично (користувач не вводить її). При заданні
            модифікатора check відображати червоним фоном input, якщо некоректний.
        </p>
    </div>
    <div class="container">
        <label class="lable">
            Введіть Email
            <input class="input" type="email" v-model.lazy="isEmailAddress" :class="!isEmailCorrect" />
        </label>
    </div>
</template>

<script>
export default {
    name: 'EmailAddress',
    data() {
        return {}
    },
    props: {
        modelValue: {
            type: String,
            default: '',
        },
        modelModifiers: {
            default: () => ({}),
        },
    },
    computed: {
        isEmailAddress: {
            get() {
                return this.modelValue
            },
            set(value) {
                if (value && this.modelModifiers.domen) {
                    if (this.isEmailDomen(value)) {
                        return value
                    } else value += '@inv.mn.edu'
                }
                this.$emit('update:modelValue', value)
            },
        },
        isEmailCorrect() {
            return this.modelModifiers.check && /[^@]*@inv\.mn\.edu$/.test(this.isEmailAddress)
        },
    },
    methods: {
        isEmailDomen(val) {
            let register = /.*@inv\.nm\.edu/
            return register.test(val)
        },
    },
}
</script>

<style lang="css" scoped>
.container {
    display: flex;
    justify-content: center;
}
.lable {
    font-size: 24px;
}
.input {
    padding: 10px;
    font-size: 20px;
}
</style>
