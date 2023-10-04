<script>
    import Dashboard from "../lib/components/dashboard/Dashboard.svelte";
    //DARKMODE
    let isDarkMode = true;

    const handleDarkMode = () => {
        isDarkMode = isDarkMode ? false : true;
    };
    //DISGUISE NavBar
    let isHidden = false;

    const handleHidden = () => {
        isHidden = isHidden ? false : true;
    }

</script>

<div class={ isDarkMode ? 'dark' : '' }>
    <header>
        <Dashboard
            isDarkMode={ isDarkMode }
            handleDarkMode={ handleDarkMode }

            isHidden={ isHidden }
            handleHidden={ handleHidden }
        />
    </header>
</div>

<style>
    :global(body) {
        background-color: var(--black);
    }

    .dark {
        /* ====Colors==== */
        --body-color: #18191a;
        --sidebar-color: #242526;
        --primary-color: #3a3b3c;
        --primary-color-light: #3a3b3c;
        --toggle-color: #fff;
        --text-color: #ccc;
    }
</style>