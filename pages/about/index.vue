<template>
    <div>
        <h1 class="text-center mt-5">About DadJokes</h1>
        <hr>
        <p>Here we want to share some dad's jokes with you guys</p>
    </div>
</template>

<script>
export default {
    head() {
        return {
            title: 'About The App',
            meta: [
                {
                    hid:'description',
                    name:'description',
                    content:'Best place for corny dad jokes',
                }
            ]
        }
    }
}
</script>