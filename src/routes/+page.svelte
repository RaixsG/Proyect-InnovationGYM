<script>
    import Dashboard from "../lib/components/dashboard/Dashboard.svelte";
    import { theme } from "../store/theme.js";

    //DISGUISE NavBar
    let isHidden = false;

    const handleHidden = () => {
        isHidden = isHidden ? false : true;
    }

</script>

<div >
    <header>
        <Dashboard
            isHidden={ isHidden }
            handleHidden={ handleHidden }
        />
    </header>
</div>

<style>
    
</style>