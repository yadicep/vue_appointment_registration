<script>
    export default {
    props: {
            title: {
                type: String,
                required: true, 
            },
            bgClass: {
                type: String,
                default: '', 
            },
        },
    };
</script>

<template>
    <div :class="`py-5 ${bgClass} text-danger`"> 
        <h5>{{ title }}</h5>
        <slot></slot>
    </div>
</template>