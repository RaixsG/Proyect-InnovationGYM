<script>
    // IMPORTS
    import Header from "./elements/Header.svelte";
    import { Search, ListSections, Logout, Mode } from "./elements/menu/index";

    //MODE DARK
    // @ts-ignore
    /**
     * @type {any}
     */
    export let isDarkMode;
    // @ts-ignore
    /**
     * @type {any}
     */
     export let handleDarkMode;
    //NavBar Oculto
    // @ts-ignore
    /**
     * @type {any}
     */
    export let isHidden;
    // @ts-ignore
    /**
     * @type {any}
     */
    export let handleHidden;

    isDarkMode ? "dark" : "";
</script>

<!--HTML-->
<section
    class={`
        ${!isDarkMode ? "" : "dark"} 
        ${!isHidden ? "" : "hidden"}
    `}
>
    <Header {handleHidden} />

    <nav class="menu-container">
        <div>
            <Search />
            <ListSections />
        </div>
        <div>
            <Logout />
            <Mode
                handleDarkMode = { handleDarkMode }
                isDarkMode = { isDarkMode }
            />
        </div>
    </nav>
</section>

<style>
    /* SIDEBAR GENERAL */
    section {
        height: 100vh;
        position: fixed;
        top: 0;
        left: 0;
        height: 100%;
        width: 250px;
        padding: 10px 14px;
        background: var(--sidebar-color);
        transition: var(--tran-05);
    }

    /* SIDEBAR MENU */
    .menu-container {
        height: calc(100% - 85px);
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        margin-top: 40px;
    }
    
    /* SIDEVAR CLOSED */
    section.hidden {
        width: 88px;
    }
</style>
