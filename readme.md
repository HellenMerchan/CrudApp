<h1 align="center">CRUD App</h1>

<p align="center">Una aplicación web sencilla para crear, leer, actualizar y eliminar datos, diseñada con un enfoque moderno y fácil de usar.</p>

<p align="center">
  <img src="https://img.shields.io/badge/licencia-MAC-green" alt="Licencia MIT">
  <img src="https://img.shields.io/badge/versi%C3%B3n-1.1-blue" alt="Versión">
  <img src="https://img.shields.io/badge/contribuidores-5-brightgreen" alt="Contribuidores">
</p>

# Índice

1. [Introducción](#introducción)
2. [Estructura de la CRUD](#estructura-de-la-crud)
3. [Visualización](#visualización)
4. [Tecnologías](#tecnologías)
5. [Codificación](#codificación)
6. [Despliegue](#despliegue)

## Introducción

Esta aplicación de registro se generó con el proposito de almacenar y editar la base de datos de un centro medico, con el fin de llevar el control de lugar fecha y hora en la que los pacientes y/o el personal ingresan a las instalaciones.

Las aplicaciones CRUD (Create, Read, Update, Delete) han cobrado una relevancia significativa en el desarrollo de software moderno, especialmente en la gestión de datos y usuarios. Una CRUD APP para el registro de usuarios es esencial en múltiples contextos, desde plataformas de comercio electrónico hasta sistemas internos de empresas. Este tipo de aplicación permite a las organizaciones llevar un control detallado de sus usuarios, mejorando la eficiencia en la gestión de la información y proporcionando una base sólida para el análisis y la toma de decisiones. Con las mejoras introducidas en la versión actual, como la captura automática de fecha, hora y ubicación de los usuarios, se incrementa aún más la utilidad de la aplicación, brindando un contexto más completo sobre los registros. Además, una CRUD APP facilita la administración de permisos y roles, asegurando que solo el personal autorizado tenga acceso a información sensible. En resumen, la implementación de una CRUD APP para el registro de usuarios no solo optimiza los procesos operativos, sino que también contribuye a la seguridad, precisión y contextualización de los datos en una organización.

## Estructura de la CRUD

**Header**:Donde aparece el logo y la descripción en título de Registro de Usuarios.
**Logo**: Logo alusivo a la compañia usuaria de la CRUD APP.
**Formulario de registro de Datos**:Tiene dos campos Nombre completo y email.
**Tabla de Registros**: Aparece el resgito de los datos, incluyendo fecha/hora, ubicación junto a la acción para editar el registro (Unicamente se puede modificar el Nombre y/o el correo electronico).

## Visualización

Se detallan las consideraciones de diseño y usabilidad de la landing page, incluyendo aspectos como:

-   **Diseño Responsivo**: La CRUD APP se adaptada a diferentes dispositivos móviles facilitando su visualización.
-   **Paleta de Colores**: Se utilizaron conceptos de psicología del color y diseño gráfico para internet, a fin de generar una experiencia de usuario inigualable.
-   **Tipografía**: Se incorporaron estilos vanguardista de diseño editorial para generar una mejor experiencia del lectura a los visitantes. Se usa la tipografia Carving Soft.

A continuación se presenta en imágen la representación de la CRUD APP:

![](preview.png)

## Tecnologías

Lista de las tecnologías y herramientas utilizadas para el desarrollo de la landing page, tales como:

-   **HTML5**: Estructuración del contenido buscando el estándar que incorpora las últimas tendencias de maquetación.
-   **CSS3**: Estilos y diseño visual aconmpañados de técnicas como flat design y UX/UI
-   **JavaScript**: Interactividad y funcionalidades dinámicas que facilitan la interacción del ususario.
-   **Herramientas de Desarrollo**: Visual Studio Code y Git.
-   **PhotoShop**: Edición de logo.

## Codificación

### HTML

```html
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Control de Acceso</title>
        <link rel="stylesheet" href="styles.css" />
        <link rel="icon" href="LogoRecosad.png" type="image/x-icon" />
    </head>

    <body>
        <header class="header">
            <img src="LogoRecosad.png" alt="Logo" class="logo" />
        </header>
        <main class="container">
            <h2 class="crud_title">Registro de Usuarios</h2>
            <section class="crud">
                <!-- Creamos un formulario para ingresar datos. Etiquetas con id para modificar en Js y Class en CSS -->
                <form id="formRegister" class="crud_form">
                    <input
                        type="text"
                        placeholder="Nombre Completo"
                        id="nameinput"
                        class="form_input"
                    />
                    <input
                        type="email"
                        placeholder="Email"
                        id="emailinput"
                        class="form_input"
                    />
                    <input type="hidden" id="fechaHora" name="fechaHora" />
                    <input type="hidden" id="ubicacion" name="ubicacion" />

                    <!-- Este botón tiene una clase general "button" y agregamos modificadores como button--primary -->
                    <button
                        type="submit"
                        id="submitbutton"
                        class="button button--primary"
                    >
                        Agregar
                    </button>
                </form>

                <!-- Creamos una tabla para que se visualicen los datos -->
                <table class="crudtable">
                    <thead>
                        <tr>
                            <th class="table_header">Nombre Completo</th>
                            <th class="table_header">E-mail</th>
                            <th class="table_header">Fecha /Hora</th>
                            <th class="table_header">Ubicación</th>
                            <th class="table_header">Acción</th>
                        </tr>
                    </thead>

                    <!-- Creamos el cuerpo de la tabla que se agrega o elimina automaticamente -->
                    <tbody id="tablebody" class="table_body"></tbody>
                </table>
            </section>
        </main>
        <script src="app.js"></script>
    </body>
</html>
```

### CSS

```CSS
/* fuente importada de Google Fonts */
@font-face {
    font-family: carving;
    src: url(MADECarvingSoftPERSONALUSE-Regular.otf);
}
/* Se reinician los espacios que se agregan por defecto, quedan en 0 */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* todo texto tendrá la fuente Montserrat, botones, entradas de texto, body, etc. */
body,
button,
input {
    font-family: "carving", sans-serif;
}

body {
    max-width: 100dvw;
    display: grid;
    grid-template-rows: auto 1fr auto;
    min-height: 100dvh;
}

main {
    max-width: 100%;
    display: grid;
    place-content: center;
}

/* Estilo para el contenedor del header */
.header {
    padding: 1px; /* Espaciado alrededor del logo */
    background-color: #2c332c;
    width: 100%; /* Fondo blanco para el área del logo (opcional) */
    z-index: 1000; /* Para asegurarte de que el logo esté sobre otros elementos */
    display: flex;
    justify-content: center;
}

/* Estilo para el logo */
.logo {
    width: 250px; /* Ajusta el tamaño del logo según sea necesario */
    height: auto; /* Mantiene la relación de aspecto */
    /* margin-top: 0px;
    margin-left: -100px; */
}

/* La clase container estará centrada, que es el contenedor "padre" de todo el formulario */
.container {
    max-width: 800px;
    /* margin-left: auto;
    margin-right: auto; */
    margin: auto;
    border-radius: 8px;
    padding: 20px;
    box-shadow: 0 0 10px 0 black;
}

.crud_title {
    text-align: center;
    color: rgb(100, 100, 114);
    margin: 3rem;
}

.crud_form {
    display: flex;
    margin: 10px 0;
}

/* Tamaño de fuente de las entradas a 1rem unidad relativa, equivale al tamaño por defecto del navegador, 2rem = 18px * 2  */
.form_input {
    flex: 1;
    padding: 5px;
    margin-right: 10px;
    font-size: 1rem;
}

/* Estilos al botón "padre" o en general  */
.button {
    padding: 5px 10px;
    border: none;
    border-radius: 5px;
    font-weight: 700;
}

/* efecto al pasar el mouse sobre el botón, crece 1.2  */
.button:hover {
    transform: scale(1.2);
}

/* Estilos especificos a "botón "primary" pero conserva propiedades del botón general "padre" */
.button--primary {
    background-color: #7fef91;
}

/* Estilos especificos a "botón "secundary" que se crean automaticamente en la celda "acciones"*/
.button--secundary {
    background-color: #7fef91;
}

/* Estilos especificos a "botón "terciary" que se crean automaticamente en la celda "acciones"*/
/* .button--terciary {
    background-color: #dc3545;
    color: #f0f0f0;
} */

/* Estilos a la tabla del Crud */
.crudtable {
    width: 100%;
    border-collapse: collapse;
}

.table_header,
.table_body td {
    border: 1px solid #cccccc;
    padding: 5px;
}

.table_header {
    background-color: #2c332c;
    color: white;
}

/* Estilos para el tercer elemento de la tablebody lo que serán los botones de la celda "acciones" */
.table_body td:nth-child(3) {
    display: flex;
    justify-content: space-around;
}

```

### JAVASCRIPT

```JS
//adquirimos los elementos del DOM donde vamos a ingresar los datos de usuario:
//declaramos constantes que son variables que no cambian en el tiempo//
const form = document.getElementById("formRegister");
const nameinput = document.getElementById("nameinput");
const emailinput = document.getElementById("emailinput");

//donde vamos a pintar los datos de Usuario//
const tablebody = document.getElementById("tablebody");

// **Nuevos elementos Hellen para fecha, hora y ubicación**
const fechaHoraInput = document.getElementById("fechaHora"); // Campo oculto en HTML
const ubicacionInput = document.getElementById("ubicacion"); // Campo oculto en HTML

// Para almacenar estos datos en el localStore, al actualizar, no se borre la info:
// Se crea una variable "let" que es dinamica, con el nombre "data" porque será nuesta base de datos
// Json.parse porque esos datos los adquirimos y convertimos en objetos almacenables como los arrays
// Guardamos en localStore en el navegador bajo la función formData() que son los datos de nuestro formulario:

let data = JSON.parse(localStorage.getItem("formData")) || [];

// Creamos funcion para que al evento "submit" click al boton (agregar), almacene la información en memoria

// **Capturar fecha y hora automáticamente**
const fechaHoraActual = new Date().toLocaleString();
fechaHoraInput.value = fechaHoraActual; // Asignamos la fecha y hora al campo oculto

form.addEventListener("submit", function (event) {
    //elimina comportamientos por defecto del formulario
    event.preventDefault();

    const name = nameinput.value;
    const email = emailinput.value;

    // **Capturar ubicación automáticamente**
    navigator.geolocation.getCurrentPosition(function (position) {
        const ubicacion =
            "Latitud: " +
            position.coords.latitude +
            ", Longitud: " +
            position.coords.longitude;
        ubicacionInput.value = ubicacion; // Asignamos la ubicación al campo oculto

        // Continuar el registro si name y email están presentes
        if (name && email) {
            const newData = {
                name,
                email,
                fechaHora: fechaHoraActual, // **Agregar la fecha y hora a la data**
                ubicacion: ubicacionInput.value, // **Agregar la ubicación a la data**
            };
            data.push(newData);
            saveDataToLocalStorage();
            renderTable();
            form.reset(); // Limpia el formulario
        } else {
            alert("Favor llenar todos los campos");
        }
    });
});

//Función para guardar los datos del formulario:
function saveDataToLocalStorage() {
    localStorage.setItem("formData", JSON.stringify(data));
}

//Función para renderizar o actualizar el formulario, limpia el contenido de la tabla para nuevo registro:
function renderTable() {
    tablebody.innerHTML = "";

    //Para generar todos los registros del formulario en una tabla necesitamos iterar el "data" (toda la información) y crear la tabla
    // compuesta de un item e index, cada elemento tendrá su puesto en la tabla.
    data.forEach(function (item, index) {
        const row = document.createElement("tr");
        const nameCell = document.createElement("td");
        const emailCell = document.createElement("td");
        const fechaHoraCell = document.createElement("td"); // **Nueva celda Hellen para fecha y hora**
        const ubicacionCell = document.createElement("td"); // **Nueva celda Hellen para ubicación**
        const actionCell = document.createElement("td");

        // Dentro de la celda "action" o acciones creamos dos botones un editar y otro eliminar.
        const editButton = document.createElement("button");
        /* const deleteButton = document.createElement('button') */

        // Agregamos el contenido de la celda, texto para name y email.
        nameCell.textContent = item.name;
        emailCell.textContent = item.email;
        fechaHoraCell.textContent = item.fechaHora; // **Mostrar la fecha y hora**
        ubicacionCell.textContent = item.ubicacion; // **Mostrar la ubicación**

        // Agregamos el texto en los botones.
        editButton.textContent = "Editar";
        // deleteButton.textContent = 'Eliminar';

        // asignamos las clases a los botones que aparecen en la celda "acciones".
        editButton.classList.add("button", "button--secundary");
        /* deleteButton.classList.add('button', 'button--terciary'); */

        // Eventos de escucha con funciones para los botones de la celda "acciones" editar y eliminar.
        editButton.addEventListener("click", function () {
            editData(index);
        });

        /* deleteButton.addEventListener('click', function () {
            deleteData(index);
        }) */

        // Agregamos los botones a la celda de acciones.
        actionCell.appendChild(editButton);
        /* actionCell.appendChild(deleteButton); */

        // Creamos las filas o celdas para los textos que capture en la data:
        row.appendChild(nameCell);
        row.appendChild(emailCell);
        row.appendChild(fechaHoraCell); // **Agregado por Hellen celda de fecha y hora a la fila**
        row.appendChild(ubicacionCell); // **Agregado por Hellen celda de ubicación a la fila**
        row.appendChild(actionCell);

        // Creamos las filas para nuestro tablebody "la que aparece con la data":
        tablebody.appendChild(row);
    });
}

// Confección de las funciones de editar y eliminar
function editData(index) {
    const item = data[index];
    nameinput.value = item.name;
    emailinput.value = item.email;

    // Añade los campos ocultos al editar (Hellen)
    document.getElementById("fechaHora").value = item.fechaHora;
    document.getElementById("ubicacion").value = item.ubicacion;

    data.splice(index, 1);
    saveDataToLocalStorage();
    renderTable();
}

/* function deleteData(index) {
    data.splice(index, 1);
    saveDataToLocalStorage();
    renderTable();
} */

renderTable();

```

## Despliegue

### Para el despliegue de la página se uso GitHub Pages:

**Pasos para Desplegar el Proyecto en GitHub Pages**:

1. Asegúrate de que todos los cambios están confirmados (committed) y empujados (pushed) al repositorio principal en GitHub.
2. En el repositorio de GitHub, ve a la sección de "Settings" (Configuración).
3. Desplázate hasta la sección "GitHub Pages".
4. En "Source" (Fuente), selecciona la rama que contiene tu archivo `index.html` (generalmente `main` o `master`).
5. Haz clic en "Save" (Guardar).
6. GitHub generará un enlace donde tu sitio estará disponible.

**Configuración del Entorno de Producción**:

-   Verifica que todos los enlaces y recursos externos estén accesibles en la URL proporcionada por GitHub Pages.

---

**En este link se en cuenta la [CRUD APP](https://atreyus-dev.github.io/CRUD-app/)**
