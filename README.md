
<html lang="es">
<head>
    <title>Ordenación por Burbuja</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .array {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>Ordenación por Burbuja en JavaScript</h1>
    <p>Inserte sus propios valores de cartas y haga clic en "Insertar" para guardar los datos. Luego haga clic en "Ordenar" para ver el proceso de ordenación por burbuja.</p>

    <div>
        <label for="cartasInput">Cartas (separadas por comas):</label>
        <input type="text" id="cartasInput" placeholder="Ejemplo: 1, 13, 12, 11, 2, 7">
        <button onclick="insertarCartas()">Insertar</button>
        <button onclick="ordenarCartas()">Ordenar</button>
    </div>

    <div class="array">
        <h2>Cartas de corazones original:</h2>
        <p id="originalArray"></p>
    </div>
    <div class="array">
        <h2>Proceso de ordenación:</h2>
        <pre id="sortingProcess"></pre>
    </div>
    <div class="array">
        <h2>Cartas de corazones ordenadas:</h2>
        <p id="sortedArray"></p>
    </div>

    <script>
        // Función de ordenación por burbuja
        function bubbleSort(arr) {
            let n = arr.length;
            let process = '';
            for (let i = 0; i < n - 1; i++) {
                for (let j = 0; j < n - i - 1; j++) {
                    if (arr[j] > arr[j + 1]) {
                        // Intercambiar elementos
                        let temp = arr[j];
                        arr[j] = arr[j + 1];
                        arr[j + 1] = temp;
                    }
                    process += `Paso ${i * (n - 1) + j + 1}: ${arr.join(", ")}\n`;
                }
            }
            return { sortedArray: arr, process: process };
        }

        // Función para insertar cartas en localStorage
        function insertarCartas() {
            let input = document.getElementById("cartasInput").value;
            let cartasCorazones = input.split(',').map(Number);

            // Insertar en localStorage
            localStorage.setItem('cartasCorazones', JSON.stringify(cartasCorazones));

            // Mostrar mensaje de éxito
            alert('Cartas insertadas exitosamente.');
        }

        // Función para ordenar las cartas ingresadas por el usuario
        function ordenarCartas() {
            // Seleccionar desde localStorage
            let cartasCorazones = JSON.parse(localStorage.getItem('cartasCorazones'));

            if (!cartasCorazones) {
                alert('No hay cartas guardadas. Por favor, inserte algunas cartas primero.');
                return;
            }

            // Mostrar el array original de cartas en la página
            document.getElementById("originalArray").innerText = cartasCorazones.join(", ");

            // Ordenar el array de cartas usando el método de la burbuja
            let result = bubbleSort(cartasCorazones);

            // Mostrar el proceso de ordenación
            document.getElementById("sortingProcess").innerText = result.process;

            // Mostrar el array de cartas ordenado en la página
            document.getElementById("sortedArray").innerText = result.sortedArray.join(", ");
        }
    </script>
</body>
</html>
