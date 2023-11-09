<template>
    <path-to-files v-model.checkPath="filesPath" />
</template>

<script>
import PathToFiles from '@/components/TaskTwo/PathToFiles.vue'
export default {
    name: 'TaskTwo',
    components: { PathToFiles },
    data() {
        return {
            filesPath: null,
        }
    },
}
</script>

<style></style>
