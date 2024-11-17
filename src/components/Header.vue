<script>
    export default {
    props: {
            title: {
                type: String,
                required: true, 
            },
            bgClass: {
                type: String,
                default: 'bg-dark bg-gradient', 
            },
        },
    };
</script>

<template>
    <header :class="`py-2 ${bgClass} text-white text-center shadow`">
        <h3>{{ title }}</h3>
        <slot></slot>
    </header>
</template>