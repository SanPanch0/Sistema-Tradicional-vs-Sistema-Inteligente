<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Salario - Enfoque Tradicional</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 min-h-screen flex items-center justify-center p-4">
    <div class="max-w-md w-full bg-white rounded-2xl shadow-xl overflow-hidden">
        <!-- Encabezado -->
        <div class="bg-blue-600 p-6 text-white text-center">
            <h1 class="text-2xl font-bold">Sistema Salarial Determinista</h1>
            <p class="text-blue-100 mt-1 opacity-90">Basado en Regla Fija de Negocio</p>
        </div>

        <div class="p-8">
            <!-- Descripción del Enfoque -->
            <div class="mb-6 p-4 bg-gray-50 rounded-lg border-l-4 border-blue-500">
                <p class="text-sm text-gray-600 italic">
                    "Este sistema aplica una relación lineal fija: una tarifa constante de 10 soles por cada hora trabajada."
                </p>
            </div>

            <!-- Formulario -->
            <div class="space-y-6">
                <div>
                    <label class="block text-sm font-semibold text-gray-700 mb-2">
                        Horas Trabajadas
                    </label>
                    <input 
                        type="number" 
                        id="inputHoras" 
                        value="40" 
                        placeholder="Ej: 40"
                        class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none transition-all text-lg"
                        oninput="calcularSalario()"
                    >
                </div>

                <div class="pt-4 border-t border-gray-100">
                    <div class="flex justify-between items-center mb-2">
                        <span class="text-gray-500">Tarifa por hora:</span>
                        <span class="font-medium text-gray-800">10.00 soles</span>
                    </div>
                    <div class="flex justify-between items-center bg-blue-50 p-4 rounded-xl">
                        <span class="text-blue-800 font-bold">Salario Total:</span>
                        <span id="resultadoSalario" class="text-2xl font-black text-blue-900">
                            S/ 400.00
                        </span>
                    </div>
                </div>
            </div>

            <!-- Nota Técnica -->
            <div class="mt-8 text-xs text-gray-400 text-center uppercase tracking-widest">
                Sin Aprendizaje • Comportamiento Determinista
            </div>
        </div>
    </div>

    <script>
        /**
         * Realiza el cálculo del salario basado estrictamente
         * en la fórmula lineal definida: Salario = Horas * 10
         */
        function calcularSalario() {
            const TARIFA = 10;
            const input = document.getElementById('inputHoras');
            const display = document.getElementById('resultadoSalario');
            
            let horas = parseFloat(input.value);

            // Validación de entrada para evitar valores negativos o no numéricos
            if (isNaN(horas) || horas < 0) {
                display.innerText = "S/ 0.00";
                return;
            }

            // Aplicación directa de la regla fija
            const total = horas * TARIFA;

            // Formateo del resultado a moneda local (Soles)
            display.innerText = `S/ ${total.toLocaleString('es-PE', {
                minimumFractionDigits: 2,
                maximumFractionDigits: 2
            })}`;
        }

        // Ejecución inicial al cargar la página
        window.onload = calcularSalario;
    </script>
</body>
</html>
