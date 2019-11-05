<template>
    <div class="box">
        <p>
            <slot></slot>
        </p>
    </div>
</template>

<script>
export default {
    name: "Message",
}
</script>

<style lang="scss">
    .box{
        background: #e3e3e3;
        padding: 20px;
        border: 1px solid #ddd;
        p{
            margin: 0;
        }
    }
</style>