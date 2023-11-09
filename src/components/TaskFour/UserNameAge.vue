<template>
    <div>
        <ul>
            Задача 4. Розробити компонент для вводу віку користувача та імені. Робити форматування при заданні
            відповідних модифікаторів відповідних полів input:
            <li>ім’я користувача - у випадку порожнього поля (червони фон)</li>
            <li>вік (вік менший за 18 – колір фону червоний, інакше – зелений).</li>
        </ul>
    </div>
    <div class="container">
        <label class="lable">
            Ім'я користувача
            <input type="text" v-model="userName" :class="colorUser" class="input" />
        </label>
        <label class="lable">
            вік користувача
            <input type="number" v-model="userAge" :class="colorAge" class="input" />
        </label>
    </div>
</template>

<script>
export default {
    name: 'UserNameAge',
    data() {
        return {
            colorUser: 'bg-red',
            colorAge: null,
        }
    },
    props: {
        nameModelValue: {
            type: String,
        },
        nameModelModifiers: {
            default: () => ({}),
        },
        ageModelValue: {
            type: Number,
        },
        ageModelModifiers: {
            default: () => ({}),
        },
    },
    computed: {
        userName: {
            get() {
                return this.nameModelValue
            },
            set(value) {
                if (value.length > 0 && this.nameModelModifiers) {
                    this.colorUser = 'bg-transparent'
                }
                this.$emit('update: nameModelValue', value)
            },
        },
        userAge: {
            get() {
                return this.ageModelValue
            },
            set(value) {
                this.AgeChech(value)
                this.$emit('update:ageModelValue', value)
            },
        },
    },
    methods: {
        AgeChech(value) {
            if (value < 18) this.colorAge = 'bg-red'
            else this.colorAge = 'bg-green'
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
}
.input {
    padding: 10px;
}
.bg-red {
    background-color: red;
}
.bg-green {
    background-color: green;
}
.bg-transparent {
    background-color: transparent;
}
</style>
