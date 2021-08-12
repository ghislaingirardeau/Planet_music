<template>
    <button class="btn-primary">
        {{item}}
    </button>
</template>

<script>
export default {
    props: {
        item: String
    },
}
</script>