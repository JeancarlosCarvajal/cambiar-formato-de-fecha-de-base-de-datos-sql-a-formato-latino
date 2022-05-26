# cambiar-formato-de-fecha-de-base-de-datos-sql-a-formato-latino
Cambiar el formato de fecha de Base de Datos SQL de "2022-05-05 12:30:17"  a formato latino "05 MAYO, 2022" con PHP

    // Convierte formato de Base Datos de esto "2022-05-05 12:30:17" 
    // a esto "05 MAYO, 2022"
    function fecha_latino_DB($fecha_base_dato){ 
        // Separamos la fecha de la Hora
        $fecha = explode(' ', $fecha_base_dato)[0];
        // Separamos la fecha actual en un arreglo
        $array_fecha = explode('-', $fecha);
        // Extraemnos el ano del arreglo fecha
        $ano = $array_fecha[0];
        // Etraemos el número de mes del arreglo fecha
        $numero_mes_actual = $array_fecha[1];
        // Extraemos el día del arreglo fecha
        $dia = $array_fecha[2];
        // Creamos un arreglo con los meses del ano en orden
        $array_meses = array(
            "Enero", "Feb", "Marzo", "Abril", "Mayo", "Junio", 
            "Julio", "Agosto", "Sept", "Oct", "Nov", "Dic"
        );
        // Creamos una variable para agregar el nombre del mes
        $mes_actual = "";
        // Corremos el arreglo con los meses del ano en un Foreach
        foreach ($array_meses as $numero_mes => $nombre_mes) {
            // Si $numero_mes_actual es igual al numero de mes del array
            // entonces cargamos la variable $mes_actual igual a $nombre_mes
            if(($numero_mes + 1) == $numero_mes_actual){
                $mes_actual = $nombre_mes;
            }
        }
        // Retornmos las variables concatenadas
        return (integer)$dia . ' ' . strtoupper($mes_actual) . ', ' . $ano;
    }
