<template>
    <div>
        <b-navbar type="light" variant="light">
            <!-- container -->
            <div class="container">
                <b-navbar-brand href="#">
                    Dad Jokes
                </b-navbar-brand>

                <b-navbar-nav class="direction">
                    <b-nav-item href="/" class="ml-5">Home</b-nav-item>
                    <b-nav-item href="/about" class="ml-5">About</b-nav-item>
                    <b-nav-item href="/jokes" class="ml-5">Jokes</b-nav-item>
                </b-navbar-nav>
            </div>
        </b-navbar>
    </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.direction {
    direction: rtl;
}
</style>