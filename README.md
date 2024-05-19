
<html lang="es">
<head>
    <title>Ordenación por Burbuja</title>
</head>
<body>
    <h1>Ordenación por Burbuja en JavaScript</h1>
    <p>Array original de cartas de corazones: <span id="original"></span></p>
    <p>Array ordenado de cartas de corazones: <span id="ordenado"></span></p>
    <script>
        // Función de ordenación por burbuja
        function bubbleSort(arr) {
            let n = arr.length;
            for (let i = 0; i < n - 1; i++) {
                for (let j = 0; j < n - i - 1; j++) {
                    if (arr[j] > arr[j + 1]) {
                        // Intercambiar elementos
                        let temp = arr[j];
                        arr[j] = arr[j + 1];
                        arr[j + 1] = temp;
                    }
                }
            }
            return arr;
        }

        // Array de ejemplo de cartas de corazones (1=As, 11=Jota, 12=Reina, 13=Rey)
        let cartasCorazones = [1, 13, 12, 11, 2, 7, 5, 3, 9, 10, 8, 6, 4];

        // Mostrar el array original de cartas en el documento HTML
        document.getElementById("original").textContent = cartasCorazones.join(", ");

        // Ordenar el array de cartas usando el método de la burbuja
        let cartasOrdenadas = bubbleSort(cartasCorazones);

        // Mostrar el array de cartas ordenado en el documento HTML
        document.getElementById("ordenado").textContent = cartasOrdenadas.join(", ");
    </script>
</body>
</html>
