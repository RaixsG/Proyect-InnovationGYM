<script>
    export let headers = [];
    export let data = [];

</script>

<table>
    <thead>
        <tr>
            {#each headers as header}
                <th>{header}</th>
            {/each}
        </tr>
    </thead>
    <tbody>
        {#each data as row}
            <tr>
                {#each Object.values(row) as cell}
                    <td>{cell}</td>
                {/each}
            </tr>
        {/each}
    </tbody>
    <tfoot>
        <tr>
            {#each headers as header}
                <th>{header}</th>
            {/each}
        </tr>
    </tfoot>
</table>

<style>
    table {
        width: 100%;
        border-collapse: collapse;
    }

    tfoot {
        filter: opacity(0.5);
    }

    th, td {
        border: 1px solid var(--text-color);
        padding: 8px;
    }

    th {
        background-color: var(--primary-color);
        color: white;
    }

    tr:nth-child(even) {
        background-color: var(--sidebar-color);
    }

</style>