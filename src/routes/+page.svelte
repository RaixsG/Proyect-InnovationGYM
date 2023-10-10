<script>
    import Dashboard from "../lib/components/dashboard/Dashboard.svelte";
    import { theme } from "../store/store.js";

    //DISGUISE NavBar
    let isHidden = false;

    const handleHidden = () => {
        isHidden = isHidden ? false : true;
    }

</script>

<div class:dark={$theme === 'Dark'}>
    <header>
        <Dashboard
            isHidden={ isHidden }
            handleHidden={ handleHidden }
        />
    </header>
</div>

<style>
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