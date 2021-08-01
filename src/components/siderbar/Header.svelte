<script>
    import Avatar from "../Avatar.svelte";
    import ButtonIcon from "../ButtonIcon.svelte";
    import userProfile from "../../assets/user-profile.jpeg";
    import { mdiMessageBulleted, mdiDotsVertical } from "@mdi/js";

    const handler = () => {
        console.log('funciona perro')
    }
</script>

<section class="header">
    <div class="header__avatar">
        <Avatar src={userProfile} />
    </div>
    <div class="header__actions">
        <ButtonIcon on:click={handler} src={mdiMessageBulleted} />
        <ButtonIcon icon={mdiMessageBulleted} />
        <ButtonIcon icon={mdiDotsVertical} />
    </div>
</section>

<style>
    .header {
        background: var(--sidebar-header);
        height: 60px;
        padding: 8px 16px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .header__avatar {
        width: 50px;
        height: 50px;
    }

    .header__actions {
        display: flex;
        flex: 1;
        max-width: 50%;
        justify-content: space-between;
    }

</style>
