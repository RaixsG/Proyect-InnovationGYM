<script>
    import { theme } from '../store/theme';
    import '../styles.css';
</script>

<div class:dark={$theme === 'Dark'}>
    <slot  />
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