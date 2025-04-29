# Creado por: Joel Antonio Jaquez López - 23369

# Introducción a React con CDN

Este ejercicio tiene como objetivo familiarizarse con el uso de React y ReactDOM mediante CDNs, crear componentes funcionales en React y trabajar con el manejo de estados usando `useState`. Además, se aplica el concepto de pasar datos entre componentes hijos y padres mediante `props`.

## Objetivos del Ejercicio
1. **Cargar React y ReactDOM mediante CDN**: Aprender a integrar React y ReactDOM sin necesidad de herramientas de construcción (como Webpack).
2. **Crear componentes funcionales simples**: Familiarizarse con la creación y renderización de componentes en React.
3. **Uso de JSX**: Trabajar con JSX en un entorno donde Babel se encarga de la transpilación.
4. **Manejo de estado con `useState`**: Usar `useState` para manejar estados locales dentro de los componentes.
5. **Interacción entre componentes**: Pasar datos de un componente hijo a un componente padre mediante `props`.
6. **Renderizar listas dinámicas**: Mostrar listas de comentarios que se actualizan dinámicamente.

## Estructura del Proyecto

Este proyecto consta de un solo archivo `index.html`, donde se encuentran los siguientes elementos:

1. **CDNs de React y Babel**: 
   - React (versión 18)
   - ReactDOM (versión 18)
   - Babel standalone para procesar JSX sin necesidad de herramientas externas

2. **Componente Greeting**: 
   - Un componente básico que muestra un saludo "¡Hola, bienvenido a React!".

3. **Componente CommentForm**:
   - Permite al usuario agregar un comentario.
   - Usa un campo de entrada (`input`) y un botón para enviar el comentario.

4. **Componente App**:
   - Administra el estado de los comentarios usando `useState`.
   - Renderiza la lista de comentarios y actualiza la vista cada vez que se agrega uno nuevo.

## Instrucciones

1. **React y ReactDOM**: Los CDNs de React y ReactDOM se incluyen en el `<head>` del documento HTML.
2. **Div con id="root"**: Este `div` es donde se montará la aplicación React.
3. **Componente Greeting**: Se crea un componente `Greeting` que renderiza un mensaje de bienvenida.
4. **Componente CommentForm**: Permite al usuario enviar comentarios que son pasados al componente padre `App` mediante props.
5. **Renderización de la lista de comentarios**: Cada vez que un nuevo comentario es agregado, la lista de comentarios se actualiza y se renderiza automáticamente.

## Uso

Para ver el proyecto en acción:

1. **Descargar o clonar este repositorio**.
2. **Abrir el archivo `index.html` en tu navegador**.
3. **Escribir un comentario** en el campo de texto y hacer clic en "Agregar tarea" para ver cómo la lista de comentarios se actualiza automáticamente.
4. **Puedes acceder al siguiente enlace del servidor de la clase http://awita.site/usuarios/jaq23369/Intro_React/ para probar el ejercicio**.

## Requisitos

- No se necesita configuración adicional ni herramientas de construcción.
- Este proyecto solo usa las siguientes bibliotecas desde CDN:
  - React: `https://unpkg.com/react@18/umd/react.development.js`
  - ReactDOM: `https://unpkg.com/react-dom@18/umd/react-dom.development.js`
  - Babel: `https://unpkg.com/@babel/standalone/babel.min.js`

## Limitaciones

- El proyecto está estructurado de manera que no se utilizan archivos `.js` externos. Todo el código debe estar contenido dentro del archivo `index.html`.
- No se usan librerías adicionales ni gestores de paquetes como npm o yarn.
- El código solo depende de las bibliotecas mencionadas y está diseñado para ejecutarse en un entorno donde Babel se encarga de la transpilación de JSX en el navegador.

## Ejemplo de Código

Aquí hay un extracto del código del archivo `index.html` que contiene los componentes y la estructura básica de la aplicación:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Intro a React con CDN</title>

    <!-- React -->
    <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>

    <!-- ReactDOM -->
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>

    <!-- Babel para procesar JSX -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
</head>
<body>
    <div id="root"></div>

    <script type="text/babel">
        function CommentForm({onAddTask}) {
            const [inputValue, setInputValue] = React.useState('');

            const handleSubmit = (e) => {
                e.preventDefault();
                if (inputValue.trim() !== '') {
                    onAddTask(inputValue);
                    setInputValue('');
                }
            };

            return (
                <form onSubmit={handleSubmit}>
                    <input
                        type="text"
                        placeholder="Escribe una tarea..."
                        value={inputValue}
                        onChange={(e) => setInputValue(e.target.value)}
                    />
                    <button type="submit">Agregar tarea</button>
                </form>
            );
        }

        function App(){
            const [tasks, setTasks] = React.useState([]);

            const addTask = (newTask) => {
                setTasks([...tasks, newTask]);
            };

            return (
                <div>
                    <h1>¡Hola, bienvenido a React con CDN!</h1>
                    <h2>Mi To Do List</h2>
                    <CommentForm onAddTask={addTask} />
                    <ul>
                        {tasks.map((task, index) => (
                            <li key={index}>{task}</li>
                        ))}
                    </ul>
                </div>
            );
        }

        const root = ReactDOM.createRoot(document.getElementById('root'));
        root.render(<App />);
    </script>
</body>
</html>```



