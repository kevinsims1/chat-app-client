<template>
    <Layout>
        <div> 
            <h1>Welcome Back, Lets Chat Around!</h1>
        </div>
    </Layout>
</template>

<script>
    import Layout from './layout';

    export default {
        components: {
            Layout
        }
    }
</script>

<style scoped>
    

    div{
        height: 100vh;
        width: 100%;
        background: red;
        display: flex;
        flex-direction: column;
        justify-content: center;
        text-align: center;
    }

    
</style>
<style>
    body{
        height: 100%;
        width: 100%;
        padding: 0;
        margin: 0
    }
    
    html{
        height: 100%;
        width: 100%
    }
</style>