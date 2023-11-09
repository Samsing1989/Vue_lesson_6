<template>
    <div>
        <p>
            Задача 1. Розробити компонент для введення віку користувача (з підтримкою v-model). При заданні модифікатора
            check не допускати введення некоректного віку (вік не може бути більшим за 150). При заданні модифікатора
            setColor задавати фон (вік менше 10 – зелений, від 10 до 21 – жовтий, інакше – оранжевий).
        </p>
    </div>
    <div class="container">
        <label class="lable">
            Введіть вік користувача:
            <input type="number" v-model="getUserAge" class="imput" :class="colorAge" />
        </label>
    </div>
</template>

<script>
export default {
    name: 'UserAge',
    data() {
        return {
            colorAge: null,
        }
    },
    props: {
        modelValue: {
            type: Number,
        },
        modelModifiers: {
            default: () => ({}),
        },
    },

    computed: {
        getUserAge: {
            get() {
                return this.modelValue
            },
            set(value) {
                if (this.modelModifiers.check) {
                    if (value >= 150) value = ''
                }
                if (this.modelModifiers.setColor) {
                    this.colorAge = this.colorValue(value)
                }
                this.$emit('update:modelValue', value)
            },
        },
    },
    methods: {
        colorValue(value) {
            if (value < 10) return 'younger'
            else if (value <= 21) return 'average'
            else return 'others'
        },
    },
}
</script>

<style lang="css" scoped>
.container {
    display: flex;
    align-items: center;
    justify-content: center;
}
.lable {
    font-size: 30px;
}
.imput {
    padding: 10px;
    font-size: 20px;
}
.younger {
    background-color: green;
}
.average {
    background-color: yellow;
}
.others {
    background-color: orange;
}
</style>
