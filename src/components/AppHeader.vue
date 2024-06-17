<template lang="">
   <header>
    <h1>The anime Quote</h1>
   </header>
</template>
<script>
export default {
    name: 'AppHeader'
}
</script>
<style lang="scss" scoped>
    header{
        padding :24px 32px;
        display: flex;
        justify-content: center;

        h1{
            font-size: 32px;
            color: var(--dark);
            font-weight: 700;
            text-transform: uppercase;
            padding-bottom: 8px;
            border-bottom: 5px solid #000;
        }
    }
</style>