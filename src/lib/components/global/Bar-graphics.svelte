<script>
    import { onMount } from "svelte";
    import * as d3 from "d3";

    let data = [
        {'N° Cliente': 1, Nombre: 'Prueba 1', Estado: 'Activo', 'Fecha de registro': '01/01/2021'},
        {'N° Cliente': 2, Nombre: 'Prueba 2', Estado: 'Activo', 'Fecha de registro': '01/01/2021'},
        {'N° Cliente': 3, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/01/2021'},
        {'N° Cliente': 4, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/01/2021'},
        {'N° Cliente': 5, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/02/2021'},
        {'N° Cliente': 6, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/02/2021'},
        {'N° Cliente': 7, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/02/2021'},
        {'N° Cliente': 8, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/02/2021'},
        {'N° Cliente': 9, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/03/2021'},
        {'N° Cliente': 10, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/03/2021'},
        {'N° Cliente': 11, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/03/2021'},
        {'N° Cliente': 12, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/03/2021'},
        {'N° Cliente': 13, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/03/2021'},
        {'N° Cliente': 14, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/04/2021'},
        {'N° Cliente': 15, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/04/2021'},
        {'N° Cliente': 16, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/04/2021'},
        {'N° Cliente': 17, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/05/2021'},
        {'N° Cliente': 18, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/05/2021'},
        {'N° Cliente': 19, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/05/2021'},
        {'N° Cliente': 20, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/06/2021'},
        {'N° Cliente': 21, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/06/2021'},
        {'N° Cliente': 22, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/06/2021'},
        {'N° Cliente': 23, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/07/2021'},
        {'N° Cliente': 24, Nombre: 'Prueba 3', Estado: 'Activo', 'Fecha de registro': '01/07/2021'},
    ];

    let meses = [
        "Enero",
        "Febrero",
        "Marzo",
        "Abril",
        "Mayo",
        "Junio",
        "Julio",
        "Agosto",
        "Septiempre",
        "Octubre",
        "Noviembre",
        "Diciembre"
    ];

    let conteoMeses = Array(12).fill(0); //
    // console.log(conteoMeses);
    data.forEach((item) => {
        let partesFecha = item['Fecha de registro'].split("/"); // Separar la fecha de registro en partes
        // console.log(partesFecha)
        let fechaRegistro = new Date(partesFecha[2], partesFecha[1] - 1, partesFecha[0]); // Crear un objeto Date a partir de la fecha de registro
        // console.log(fechaRegistro);
        let mes = fechaRegistro.getMonth(); // Obtener el mes (0-11) de la fecha de registro
        // console.log(mes);
        conteoMeses[mes]++; // Incrementar el conteo de clientes en el mes correspondiente
        // console.log(conteoMeses)
    });

    let data_length = meses.map((mes, i) => ({mes, count: conteoMeses[i]})); // Crear el array data_length a partir de los conteos de meses

    let colors = d3.scaleOrdinal(d3.schemeCategory10);
    onMount(() => {
        let width = 500;
        let height = 250;
        let barWidth = width / data_length.length;
        console.log(barWidth)

        let svg = d3
            .select("#bar-graphics")
            .append("svg")
            .attr("width", width)
            .attr("height", height);

        svg.selectAll("rect")
            .data(data_length) // Asignamos los datos a las barras
            .enter()
            .append("rect")
            .attr("x", (d, i) => i * barWidth)
            .attr("y", (d) => height - d.count * 35) // Multiplicamos por 35 para tener barras de tamaño decente
            .attr("width", barWidth - 1) // Restamos 1 para tener un poco de espacio entre las barras
            .attr("height", (d) => d.count * 35)
            .attr("fill", (d, i) => colors(i));

        svg.selectAll("text")
            .data(data_length)
            .enter() 
            .append("text")
            .text((d) => d.mes) // Asignamos el texto a cada barra
            .attr("x", (d, i) => i * barWidth) // Posicionamos el texto en el centro de cada barra
            .attr("y", (d) => height - d.count * 1) // Multiplicamos por 1 para tener el texto justo encima de las barras
            .attr('transform', (d, i) => `rotate(90, ${i * barWidth}, ${height})`) // Rotamos el texto 90 grados
            .attr("dy", "-0.3em") // Desplaza el texto un poco hacia arriba para que no se superponga con las barras
            .attr("text-anchor", "middle") // Centra el texto horizontalmente
            .attr("font-size", "15px");
    });
</script>

<div id="bar-graphics" />
