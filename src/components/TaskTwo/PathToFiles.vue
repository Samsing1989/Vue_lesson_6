<template>
    <div>
        <p>
            Задача 2. Розробити компонент (з підтримкою v-model), який дозволяє вводити шлях до файлу js (URL, що
            закінчується розширенням js). При заданні модифікатора checkPath відображати червоним фоном input, якщо шлях
            некоректний.
        </p>
    </div>
    <div class="container">
        <label class="lable">
            Веддіть шлях до файлу:

            <input type="text" class="input" v-model="getFilePath" :class="bgColor" />
        </label>
    </div>
</template>

<script>
export default {
    name: 'PathToFiles',
    data() {
        return {
            bgColor: null,
        }
    },
    props: {
        modelValue: {
            type: String,
        },
        modelModifiers: {
            default: () => ({}),
        },
    },
    computed: {
        getFilePath: {
            get() {
                return this.modelValue
            },
            set(value) {
                if (this.isValidation(value) && this.modelModifiers.checkPath) {
                    this.bgColor = 'correct'
                } else this.bgColor = 'not-correct'
                this.$emit('update:modelValue', value)
            },
        },
    },
    methods: {
        isValidation(value) {
            return /.+\.js$/.test(value)
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
    font-size: 30px;
    display: flex;
    gap: 20px;
    align-items: center;
}
.input {
    padding: 10px 20px;
    font-size: 20px;
}
.button {
    padding: 10px 20px;
    background-color: rgb(241, 197, 197);
}

.not-correct {
    background-color: red;
}
.correct {
    background-color: green;
    color: white;
}
</style>
