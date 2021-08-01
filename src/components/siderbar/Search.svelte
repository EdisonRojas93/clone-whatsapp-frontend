<script>
    import ButtonIcon from "../../components/ButtonIcon.svelte";
    import { mdiMagnify, mdiArrowLeft } from "@mdi/js";

    let seachText = "";
    let placeholder = "";

    let isSearch = false;
    let searchTextRef;

    $: seachText = isSearch ? seachText : "";
    $: if (isSearch) {
        searchTextRef.focus();
        placeholder = "";   
    } else {
        placeholder = "Search or start new chat";
    }
</script>

<section class="search">
    <div class="search__input">
        <ButtonIcon
            icon={isSearch ? mdiArrowLeft : mdiMagnify}
            on:click={() => {
                isSearch = !isSearch;
            }}
        />
        <input
            bind:this={searchTextRef}
            class="search__input--text"
            type="text"
            bind:value={seachText}
            {placeholder}
            on:focus={() => {
                isSearch = true;
            }}
        />
    </div>
</section>

<style>
    .search {
        background: var(--search-bar-bg);
        height: 50px;
        padding: 8px 16px;
        display: flex;
    }

    .search__input {
        background: var(--background-white);
        width: 100%;
        border-radius: 25px;
        display: flex;
        align-items: center;
        padding: 8px;
    }

    .search__input--text {
        border: none;
        width: 100%;
        padding: 0 8px;
        line-height: 24px;
        margin-left: 32px;
        font-size: 1rem;
    }

    .search__input--text:focus {
        border: none;
        outline: none;
    }
</style>
