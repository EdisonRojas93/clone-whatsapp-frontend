<script>
    import { mdiHome } from "@mdi/js";
    export let icon = mdiHome;
</script>

<button class="btn-icon" on:click>
    <svg style="width:24px;height:24px" viewbox="0 0 24 24">
        <path fill="currentColor" d={icon} />
        <!-- account -->
    </svg>
</button>

<style>
    .btn-icon {
        border: 0;
        padding: 2px;
        height: 24px;
        width: 24px;
        background: transparent;
        cursor: pointer;
    }
</style>
