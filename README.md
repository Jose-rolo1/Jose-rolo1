<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Herramientas de IA</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background-color: #000; /* Fondo negro */
            color: #fff; /* Texto blanco */
        }
        h1 {
            text-align: center;
            color: #fff; /* Título en blanco */
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 8px;
            text-align: left;
            color: #fff; /* Texto en la tabla en blanco */
        }
        th {
            background-color: #4CAF50;
            color: white; /* Encabezados en blanco */
        }
        tr:nth-child(even) {
            background-color: #222; /* Fila par en gris oscuro */
        }
        tr:hover {
            background-color: #444; /* Color al pasar el ratón por las filas */
        }
        #admin-section {
            display: none;
            margin-top: 20px;
        }
        input {
            margin: 5px 0;
            padding: 10px;
            width: calc(100% - 22px); /* Ajusta el ancho para dejar espacio para el padding */
            border: none;
            border-radius: 5px;
            box-sizing: border-box; /* Asegura que el padding no afecte el tamaño total */
        }
        /* Ajustes específicos para campos de usuario y contraseña */
        #username, #password {
            width: calc(50% - 12px); /* Ajuste de ancho para ser más pequeños */
        }
        button {
            padding: 10px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 10px; /* Espacio superior para los botones */
        }
        button:hover {
            background-color: #45a049; /* Color de botón al pasar el ratón */
        }
        #login-message {
            color: red;
        }
    </style>
</head>
<body>

    <h1>Herramientas Gratuitas de IA para Generar Imágenes</h1>

    <div id="login-section">
        <h2>Iniciar Sesión como Administrador</h2>
        <input type="text" id="username" placeholder="Usuario" />
        <input type="password" id="password" placeholder="Contraseña" />
        <button onclick="login()">Iniciar Sesión</button>
        <p id="login-message"></p>
    </div>

    <div id="admin-section">
        <h2>Agregar Herramientas</h2>
        <input type="text" id="tool-name" placeholder="Nombre" />
        <input type="text" id="tool-url" placeholder="URL" />
        <input type="text" id="tool-description" placeholder="Descripción" />
        <button onclick="addTool()">Agregar Herramienta</button>
        <button onclick="logout()">Cerrar Sesión</button> <!-- Botón de Cerrar Sesión -->
    </div>

    <table id="tool-table">
        <tr>
            <th>Nombre</th>
            <th>URL</th>
            <th>Descripción</th>
            <th>Acciones</th> <!-- Nueva columna para acciones -->
        </tr>
        <tr>
            <td>AI Painter (BoredHumans)</td>
            <td><a href="https://boredhumans.com/ai_painter.php" target="_blank">boredhumans.com</a></td>
            <td>Herramienta gratuita para pintar personajes con IA.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
        <tr>
            <td>Artbreeder</td>
            <td><a href="https://www.artbreeder.com/" target="_blank">artbreeder.com</a></td>
            <td>Combina imágenes y crea personajes o paisajes. Tiene una versión gratuita.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
        <tr>
            <td>Artflow.ai</td>
            <td><a href="https://artflow.ai/" target="_blank">artflow.ai</a></td>
            <td>Genera personajes y escenas a partir de texto. Tiene una versión gratuita limitada.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
        <tr>
            <td>Avatarify</td>
            <td><a href="https://avatarify.ai/" target="_blank">avatarify.ai</a></td>
            <td>Crea avatares animados a partir de fotos. Versión gratuita disponible.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
        <tr>
            <td>Craiyon (DALL-E mini)</td>
            <td><a href="https://www.craiyon.com/" target="_blank">craiyon.com</a></td>
            <td>Generador de imágenes basado en descripciones textuales, completamente gratuito.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
        <tr>
            <td>Deep Dream Generator</td>
            <td><a href="https://deepdreamgenerator.com/" target="_blank">deepdreamgenerator.com</a></td>
            <td>Genera imágenes surrealistas a partir de IA. Versión gratuita disponible.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
        <tr>
            <td>DeepAI Image Generator</td>
            <td><a href="https://deepai.org/machine-learning-model/text2img" target="_blank">deepai.org</a></td>
            <td>Genera imágenes a partir de texto con IA. Versión gratuita disponible.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
        <tr>
            <td>DeepArt.io</td>
            <td><a href="https://deepart.io/" target="_blank">deepart.io</a></td>
            <td>Transforma imágenes en arte con IA. Tiene una versión gratuita con limitaciones.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
        <tr>
            <td>Dream by WOMBO</td>
            <td><a href="https://www.wombo.art/" target="_blank">dream.ai</a></td>
            <td>Genera arte a partir de descripciones de texto. Gratis, con resultados rápidos.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
        <tr>
            <td>Dreamlike.art</td>
            <td><a href="https://dreamlike.art/" target="_blank">dreamlike.art</a></td>
            <td>Generador gratuito basado en Stable Diffusion para crear arte digital desde texto.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
        <tr>
            <td>Fotor</td>
            <td><a href="https://www.fotor.com/" target="_blank">fotor.com</a></td>
            <td>Herramienta de edición de fotos y generación de arte. Tiene funciones gratuitas.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
        <tr>
            <td>NightCafe Studio</td>
            <td><a href="https://nightcafe.studio/" target="_blank">nightcafe.studio</a></td>
            <td>Generador de arte por IA que permite crear obras a partir de descripciones.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
        <tr>
            <td>Runway ML</td>
            <td><a href="https://runwayml.com/" target="_blank">runwayml.com</a></td>
            <td>Plataforma creativa para generar y editar imágenes con IA. Tiene funciones gratuitas.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
        <tr>
            <td>StarryAI</td>
            <td><a href="https://starryai.com/" target="_blank">starryai.com</a></td>
            <td>Generador de arte basado en IA con opciones gratuitas.</td>
            <td><span class="admin-action" style="display: none;"><button onclick="deleteTool(this)">Eliminar</button></span></td> <!-- Botón de eliminar oculto por defecto -->
        </tr>
    </table>

    <script>
        let loggedIn = false; // Estado de inicio de sesión

        function login() {
            const username = document.getElementById('username').value; // Captura el usuario
            const password = document.getElementById('password').value; // Captura la contraseña

            // Verifica las credenciales
            if ((username === 'Jose' && password === '2343@') || (username === 'Javier' && password === '2343@')) {
                loggedIn = true; // Cambia el estado de inicio de sesión
                document.getElementById('admin-section').style.display = 'block'; // Muestra la sección de administración
                document.getElementById('login-section').style.display = 'none'; // Oculta la sección de inicio de sesión

                // Mostrar botones de eliminar solo para administradores
                document.querySelectorAll('.admin-action').forEach(action => {
                    action.style.display = 'inline'; // Muestra los botones de eliminar
                });
            } else {
                document.getElementById('login-message').innerText = 'Usuario o contraseña incorrectos.'; // Mensaje de error
            }
        }

        function logout() {
            loggedIn = false; // Cambia el estado de inicio de sesión
            document.getElementById('admin-section').style.display = 'none'; // Oculta la sección de administración
            document.getElementById('login-section').style.display = 'block'; // Muestra la sección de inicio de sesión
            document.getElementById('username').value = ''; // Limpia el campo de usuario
            document.getElementById('password').value = ''; // Limpia el campo de contraseña
            document.getElementById('login-message').innerText = ''; // Limpia el mensaje de error

            // Ocultar botones de eliminar cuando se cierra sesión
            document.querySelectorAll('.admin-action').forEach(action => {
                action.style.display = 'none'; // Oculta los botones de eliminar
            });
        }

        function addTool() {
            if (!loggedIn) {
                alert('Debes estar logueado como administrador para agregar herramientas.'); // Mensaje de advertencia
                return;
            }

            const name = document.getElementById('tool-name').value; // Captura el nombre de la herramienta
            const url = document.getElementById('tool-url').value; // Captura la URL de la herramienta
            const description = document.getElementById('tool-description').value; // Captura la descripción de la herramienta

            if (name && url && description) {
                const table = document.getElementById('tool-table'); // Obtiene la tabla
                const rows = Array.from(table.rows).slice(1); // Obtiene las filas de la tabla, excluyendo el encabezado

                // Verificar si la URL ya existe
                const urlExists = rows.some(row => row.cells[1].innerText === url); // Comprueba si la URL ya está en la tabla
                if (urlExists) {
                    alert('Esta URL ya está registrada.'); // Mensaje si la URL ya existe
                    return;
                }

                // Crear nueva fila
                const newRow = table.insertRow(-1); // Inserta una nueva fila al final de la tabla
                const cell1 = newRow.insertCell(0); // Crea una nueva celda para el nombre
                const cell2 = newRow.insertCell(1); // Crea una nueva celda para la URL
                const cell3 = newRow.insertCell(2); // Crea una nueva celda para la descripción
                const cell4 = newRow.insertCell(3); // Crea una nueva celda para las acciones

                cell1.innerHTML = name; // Asigna el nombre a la celda
                cell2.innerHTML = `<a href="${url}" target="_blank">${url}</a>`; // Asigna la URL a la celda
                cell3.innerHTML = description; // Asigna la descripción a la celda
                cell4.innerHTML = `<span class="admin-action"><button onclick="deleteTool(this)">Eliminar</button></span>`; // Asigna el botón de eliminar

                // Limpiar los campos de entrada
                document.getElementById('tool-name').value = ''; // Limpia el campo del nombre
                document.getElementById('tool-url').value = ''; // Limpia el campo de la URL
                document.getElementById('tool-description').value = ''; // Limpia el campo de la descripción

                // Ordenar la tabla después de agregar la nueva herramienta
                sortTable(); // Llama a la función para ordenar la tabla
            } else {
                alert('Por favor, completa todos los campos.'); // Mensaje si faltan campos
            }
        }

        function deleteTool(button) {
            const row = button.parentElement.parentElement.parentElement; // Obtiene la fila que contiene el botón
            row.parentElement.removeChild(row); // Elimina la fila de la tabla
        }

        function sortTable() {
            const table = document.getElementById('tool-table'); // Obtiene la tabla
            const rows = Array.from(table.rows).slice(1); // Obtiene las filas de la tabla

            // Ordenar filas por nombre
            rows.sort((a, b) => {
                const nameA = a.cells[0].innerText.toLowerCase(); // Obtiene el nombre de la herramienta
                const nameB = b.cells[0].innerText.toLowerCase(); // Obtiene el nombre de la herramienta
                return nameA.localeCompare(nameB); // Compara los nombres
            });

            rows.forEach(row => table.appendChild(row)); // Vuelve a añadir las filas ordenadas a la tabla
        }
    </script>

</body>
</html>
