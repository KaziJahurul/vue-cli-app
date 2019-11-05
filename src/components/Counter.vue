<template>
    <div class="counter">
        The Count is: {{ count }}
        <p>
            <button @click="count += 1">Count increamemnt</button>
        </p>
    </div>
</template>

<script>
export default {
    name: 'counter',
    data() {
        return {
            count: 0,
        }
    }
}
</script>

<style lang="scss">
    
</style>