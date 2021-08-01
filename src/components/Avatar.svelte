<script>
    import user from "../assets/user.svg";
    export let src = user;

</script>

<div class="avatar">
    <img {src} alt="avatar" />
</div>

<style>
    .avatar{
        border-radius: 50%;
        width: 100%;
        height: 100%;
        overflow: hidden;
    }
    img {
        width: 100%;
        height: 100%;  
    }
</style>
