<script lang="ts">
    import { createEventDispatcher } from 'svelte'
    export let innerHtml: string
    export let toPage: number
    export let activePage: number

    const dispatch = createEventDispatcher()
    const handlePageClick = (page: number) => dispatch('pageChange', page)
</script>

<li class={`navLink primary ${activePage === toPage ? 'active' : ''}`} on:click|preventDefault={() => handlePageClick(toPage)}>
    {innerHtml}
</li>

<style>
    .navLink {
        margin: 0;
        padding: 0 0.5em;
        border-bottom: 1px solid transparent;
        background-color: var(--bg);
        font-size: 1.2rem;
        cursor: pointer;
        transition: all 0.3s ease-in;
    }
    .navLink:after {
        content: '*';
        color: var(--bodyFont);
        opacity: 0;
        transition: all 0.3s ease-in;
    }
    .navLink:hover {
        color: var(--bodyFont);
        border-bottom: 1px solid var(--primary);
    }
    .navLink:hover::after {
        opacity: 1;
    }
    .navLink.active {
        border-bottom: 1px solid var(--secondary);
        background-color: var(--offBg);
    }
    .navLink.active::after {
        opacity: 1;
    }
</style>
