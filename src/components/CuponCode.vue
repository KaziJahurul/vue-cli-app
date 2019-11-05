<template>
    <div class="cupon_code">
        <!-- <input type="text" v-model="cupon"> -->
        <!-- <input type="text" :value="coupon" @input="coupon = $event.target.value"> -->
        <input type="text" :value="coupon" @input="coupon = $event.target.value">
    </div>
</template>

<script>
export default {
    name: 'coupon',
    data() {
        return {
             coupon: 'FREEBEE',
        };
    },
}
</script>