<template>
    <div>
        <p>
            Задача 5. Спробуйте відтворити фрагмент. Компонент ProductsFilters через v-model повертає 2 значення
            фільтра: продавець, бренд. При заданні модифікатора “check” відображати секцію зеленою рамкою, якщо фільтр з
            відповідної секції (продавець чи бренд) не обрано.
        </p>
    </div>
    <div class="container">
        <filter-card class="filter" :notebooks-data="notebooksList" @clickShop="selectShop" @clickBrand="selectBrand" />
        <card-list class="card" :product-data="filterProduct()" />
    </div>
</template>

<script>
import FilterCard from '@/components/TaskFive/FilterCard.vue'
import CardList from '@/components/TaskFive/CardList.vue'
import { notebooksList } from '@/constants/3_data_notebooks'

export default {
    name: 'TaskFive',
    components: {
        FilterCard,
        CardList,
    },

    data() {
        return {
            notebooksList,
            selectShops: [],
            selectBrands: [],
        }
    },

    methods: {
        selectShop(arr) {
            this.selectShops = [...arr]
        },
        selectBrand(arr) {
            this.selectBrands = [...arr]
        },
        cartFilter(arrFilter, toFilter, category) {
            return arrFilter.filter((card) => {
                for (const el of toFilter) {
                    if (el === card[category]) return card
                }
            })
        },
        productFilterData() {
            let res = this.cartFilter(this.notebooksList, this.selectShops, 'shop')
            return this.cartFilter(res, this.selectBrands, 'brand')
        },
        filterProduct() {
            if (this.selectShops.length === 0 && this.selectBrands.length === 0) return this.notebooksList
            else if (this.selectShops.length !== 0 && this.selectBrands.length === 0)
                return this.cartFilter(this.notebooksList, this.selectShops, 'shop')
            else if (this.selectShops.length === 0 && this.selectBrands.length !== 0)
                return this.cartFilter(this.notebooksList, this.selectBrands, 'brand')
            else return this.productFilterData()
        },
    },
}
</script>

<style>
.container {
    display: flex;
    gap: 30px;
}

.filter {
    border: 2px solid #000;
    width: 300px;
}
.card {
    border: 2px solid #000;
}
</style>
