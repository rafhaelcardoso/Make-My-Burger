<template>
    <div id="main-banner">
        <h1>Make your Burger</h1>
    </div>
</template>

<script>
export default {
    name: "Banner"
}
</script>

<style scoped>
    #main-banner {
        background-image: url('/public/img/imghead.jpg');
        background-size: cover;
        background-position: 0 -400px;
        height: 300px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        width: 100%;
        margin-bottom: 50px;
    }

    #main-banner h1 {
        color: #fff;
        text-align: center;
        font-size: 60px;
        padding: 20px 40px;
        text-shadow: 0px 0px 20px rgba(0, 0, 0, 0.25);
    }

    #main-banner h1:hover {
        text-shadow: 0px 0px 20px rgba(255, 255, 255, 0.35);
        transition: 1s;
    }

    @media (max-width: 1061px) {
  #main-banner {
    background-position: right bottom;
  }
  }
</style>