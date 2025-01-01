<template>
    <div>
        <input type="text" placeholder="Enter your name">
    </div>
    <button>Submit</button>
</template>
<script lang="ts">
export default {
    name: 'MyForm',
    props: {
        msg: {
            type: String,
            required: true
        }
    }
};
</script>

<style>
button {
    margin: 10px;
}
</style>
