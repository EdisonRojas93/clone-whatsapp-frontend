<script>
    import Avatar from "../Avatar.svelte";

    export let info = {
        name: "Amor de mis amores",
        date: "12:30 PM",
        lastMsg:
            " Lorem, ipsum dolor sit amet consectetur adipisicing elit. Quod itaque sequi ratione unde ducimus minima, mollitia doloremque culpa asperiores, saepe, sint laborum consequuntur laboriosam recusandae. Repudiandae incidunt nulla hic quidem!",
        badge: 3,
    };

    export let typing = false
</script>

<div class="chat">
    <div class="chat__avatar">
        <Avatar />
    </div>
    <div class="chat__detail flex-col">
        <div class="d-flex flex-row items-center justify-space-between">
            <span class="chat__name chat__text" title={info.name}>
                {info.name}
            </span>
            <span class="chat__date chat__text" title={info.date}>
                {info.date}
            </span>
        </div>
        <div class="d-flex flex-row items-center justify-space-between">
            {#if typing}
            <span class="chat__typing">typing...</span>
            {:else}
                 <span class="chat__text">{info.lastMsg}</span>
            {/if}
            {#if info.badge > 0}
                <span class="chat__badge">{info.badge}</span>
            {/if}
        </div>
    </div>
</div>

<style>
    .chat {
        display: flex;
        align-items: center;
        height: 70px;
        background: var(--background-white);
        justify-content: flex-start;
        padding: 8px 16px;
        width: 100%;
        border-bottom: 1px solid rgba(0, 0, 0, 0.1);
        cursor: pointer;
    }
    .chat:hover {
        background: var(--search-bar-bg);
    }
    .chat__avatar {
        width: 50px;
        height: 50px;
        flex-shrink: 0;
    }

    .chat__detail {
        display: flex;
        flex: 1;
        /* flex-shrink: 0; */
        flex-direction: column;
        margin-left: 16px;
    }

    .chat__text {
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
        max-width: 200px;
        width: 100%;
    }

    .chat__name {
        text-transform: capitalize;
        font-weight: 400;
    }

    .chat__date {
        color: var(--text-gray);
        font-size: 0.75rem;
        flex: 1;
        text-align: right;
    }

    .chat__badge{
        display: inline-block;
        width: 16px;
        height: 16px;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 50%;
        background-color: var(--whatsapp-green);
        color: var(--white);
        font-weight: 400;
        font-size: 0.8rem;
        text-align: right;
    }

    .chat__typing{
        color: var(--whatsapp-green);
    }
</style>
