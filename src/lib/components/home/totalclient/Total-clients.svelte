<script>
    import Tabla from "$lib/components/global/Tabla.svelte";
    import BarGraphics from "$lib/components/global/Bar-graphics.svelte";

    let headers = ['N° Cliente', 'Nombre', 'Estado', 'Fecha de registro'];
    let data = [
        {'N° Cliente': 1, Nombre: 'Prueba 1', Estado: 'Activo', 'Fecha de registro': '01/01/2021'},
        {'N° Cliente': 2, Nombre: 'Prueba 2', Estado: 'Activo', 'Fecha de registro': '01/01/2021'},
        {'N° Cliente': 3, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/01/2021'},
    ]


</script>

<section class="total">
    <h2>Clientes en el Ultimo Mes</h2>
    <Tabla { headers } { data } />
    <h2>Clientes por Mes</h2>
    <BarGraphics />
</section>