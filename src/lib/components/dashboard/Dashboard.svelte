<script>
    import Logo from "../dashboard/img/favicon.png";
    //MODE DARK
    // @ts-ignore
    export let isDarkMode;
    // @ts-ignore
    export let handleDarkMode;
    //NavBar Oculto
    // @ts-ignore
    export let isHidden;
    // @ts-ignore
    export let handleHidden;

    isDarkMode ? 'dark' : ''

</script>

<!--HTML-->
<section class={`
    ${!isDarkMode ? '' : 'dark'} 
    ${!isHidden ? '' : 'hidden'}`
}>
    <header>
        <span class="image-container">
            <img src={Logo} alt="logo" />
        </span>

        <div class="header_text-container">
            <p>DevLessyo</p>
            <p class="low_space-text">Full Stack</p>
        </div>

        <!-- svelte-ignore a11y-no-static-element-interactions -->
        <i
            class="bx bx-chevron-right header_arrow"
            on:click={handleHidden}
            on:keypress={handleHidden}
        />
    </header>

    <nav class="menu-container">
        <div>
            <div class="search-container">
                <input type="search" placeholder="Search" />
                <i class="bx bx-search search-icon" />
            </div>
            <ul>
                <li>
                    <a href="#">
                        <i class="bx bx-home-smile" />
                        <p class="text nav-text">Dashboard</p>
                    </a>
                </li>
                <li>
                    <a href="#">
                        <i class="bx bx-bar-chart-alt-2" />
                        <p class="text nav-text">Revenue</p>
                    </a>
                </li>
                <li>
                    <a href="#">
                        <i class="bx bx-bell" />
                        <p class="text nav-text">Notifications</p>
                    </a>
                </li>
                <li>
                    <a href="#">
                        <i class="bx bx-pie-chart-alt" />
                        <p class="text nav-text">Analytics</p>
                    </a>
                </li>
                <li>
                    <a href="#">
                        <i class="bx bx-heart" />
                        <p class="text nav-text">Likes</p>
                    </a>
                </li>
                <li>
                    <a href="#">
                        <i class="bx bx-wallet" />
                        <p class="text nav-text">Wallets</p>
                    </a>
                </li>
            </ul>
        </div>
        <div>
            <li>
                <a href="#">
                    <i class="bx bx-log-out" />
                    <p
                        on:click={ () => { console.log('Log out') } }
                        on:keypress={ event => console.log(event) }
                    >
                        Logout
                    </p>
                </a>
            </li>
            <li class="theme_selector-container">
                <div class='theme_icon-container'>
                    <i class="bx bx-moon theme_icon moon" />
                    <i class="bx bx-sun theme_icon sun" />
                </div>
                <p>{ isDarkMode ? 'Dark' : 'Light' } Mode</p>
                <div class="theme_switch-container">
                    <span
                        class="theme_switch"
                        on:click={handleDarkMode}
                        on:keypress={handleDarkMode}
                    />
                </div>
            </li>
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

    p {
        font-size: 17px;
        font-weight: 500;
        white-space: nowrap;
        opacity: 1;
        font-family: var(--fonts);
    }

    i {
        display: grid;
        place-items: center;
        font-size: 20px;
        margin-right: 20px;
        margin-left: 20px;
    }

    i, p {
        color: var(--text-color);
        transition: var(--tran-02);
    }

    li {
        height: 50px;
        margin-top: 10px;
        list-style: none;
        display: flex;
        align-items: center;
    }

    a {
        height: 100%;
        width: 100%;
        display: flex;
        align-items: center;
        text-decoration: none;
        border-radius: 6px;
        transition: var(--tran-04);
    }

    a:hover {
        background-color: var(--primary-color);
    }

    a:hover p,
    a:hover i {
        color: var(--sidebar-color)
    }

    /* SIDEBAR HEADER */

    header {
        position: relative;
        display: flex;
    }

    .image-container {
        min-width: 60px;
        display: grid;
        place-items: center;
    }

    img {
        width: 40px;
        border-radius: 6px;
    }

    .header_text-container {
        display: flex;
        flex-direction: column;
    }

    .header_arrow {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        right: -45px;
        height: 25px;
        width: 25px;
        aspect-ratio: 1;
        background: var(--primary-color);
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 50%;
        color: var(--toggle-color);
        font-size: 22px;
        transition: var(--tran-04);
    }

    .header_arrow:hover {
        cursor: pointer;
        filter: brightness(1.8)
    }

    /* SIDEBAR MENU */

    .menu-container {
        height: calc(100% - 85px);
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        margin-top: 40px;
    }

    .search-container {
        position: relative;
        background-color: var(--primary-color-light);
        border-radius: 6px;
        height: 50px;
        padding: 0 20px;
    }

    /* SEARCH */

    input {
        height: 100%;
        width: 100%;
        outline: none;
        border: none;
        border-radius: 6px;
        background-color: var(--primary-color-light);
        color: var(--text-color);
        font-size: 17px;
    }

    .search-icon {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        right: -10px;
        cursor: pointer;
        padding: 10px;
        border-radius: 6px;
    }

    .search-icon:hover {
        background-color: var(--sidebar-color);
    }

    /* SIDEBAR BOTTOM OPTIONS */

    .theme_selector-container {
        position: relative;
        margin-bottom: 10px;
        border-radius: 6px;
        background-color: var(--primary-color-light);
        cursor: default;
    }

    .theme_icon-container {
        position: relative;
        width: 60px;
        height: 60px;
        display: flex;
        align-items: center;
    }

    .theme_icon {
        position: absolute;
        left: 0;
    }

    .sun {
        opacity: 0;
    }

    .theme_switch-container {
        position: absolute;
        right: 8px;
        width: 44px;
        height: 22px;
        border-radius: 25px;
        background-color: var(--toggle-color);
        margin-left: 15px;
        cursor: pointer;
    }

    .theme_switch {
        content: "";
        position: absolute;
        width: 15px;
        height: 15px;
        border-radius: 50%;
        top: 50%;
        left: 5px;
        transform: translateY(-50%);
        background-color: var(--sidebar-color);
        transition: var(--tran-03);
    }

    /* SIDEVAR CLOSED */

    section.hidden {
        width: 88px;
    }

    section.hidden p {
        opacity: 0;
    }

    section.hidden input {
        display: none;
    }
    
    section.hidden header .header_arrow {
        transform: translateY(-50%) rotate(-180deg);
    }

    /* SIDEBAR DARK MODE */

    section.dark .moon {
        opacity: 0;
    }

    section.dark .sun {
        opacity: 1;
    }

    section.dark .theme_switch {
        left: 25px;
    }
    
    section.dark a:hover p,
    section.dark a:hover i {
        color: var(--text-color)
    }

</style>
