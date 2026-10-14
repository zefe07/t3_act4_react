# t3_act4_react — Mi Lista de Tareas en React

## 📌 Descripción del proyecto

Para esta actividad hice una mini aplicación de **lista de tareas** usando **React + Vite**. La idea fue poner en práctica lo que aprendí en el curso: componentes, props, estado, eventos y renderizado de listas.

La app permite:
- Escribir una nueva tarea y agregarla con un botón.
- Marcar una tarea como completada con un checkbox (se tacha el texto).
- Eliminar tareas que ya no necesito.
- Mostrar un mensaje cuando aún no hay tareas.

Separé el proyecto en varios componentes para mantener el código ordenado y entender bien cómo se pasan datos entre ellos:

## 🚀 Demo

Puedes ver el proyecto funcionando aquí:  
👉 **[https://zefe07.github.io/t3_act4_react/](https://zefe07.github.io/t3_act4_react/)**

## 🛠️ Cómo correrlo en local

```bash
git clone https://github.com/zefe07/t3_act4_react.git
cd t3_act4_react
npm install
npm run dev


📝 Cuestionario
a) ¿Qué diferencia hay entre props y state en React?
Cuando empecé a estudiar React, esta fue una de las cosas que más me costó entender, pero ya lo tengo más claro:

Las props son como los "parámetros" que un componente recibe desde afuera, normalmente desde su componente padre. Son de solo lectura, o sea, el componente que las recibe no puede cambiarlas. Sirven para pasar información (textos, números, objetos) o incluso funciones de un componente a otro.

El state, en cambio, es información que vive dentro del propio componente y que puede cambiar con el tiempo. Cuando el usuario interactúa (por ejemplo, escribe en un input o presiona un botón), el state se actualiza y React vuelve a dibujar la pantalla con los nuevos datos.

En resumen: las props vienen de afuera y no se tocan; el state es interno y cambia según lo que haga el usuario.

b) ¿Por qué es importante usar una key al renderizar una lista de elementos?
Cuando usamos .map() para mostrar una lista, React necesita una forma de identificar cada elemento por separado. Para eso sirve la key: es como un "nombre único" que le damos a cada item.

Si no ponemos key, o ponemos algo que no es único (como el índice del array), React se confunde cuando la lista cambia: por ejemplo, si borramos una tarea, puede que se tache la tarea equivocada o que el texto se mueva de lugar. Además, sin key React tiene que re-renderizar toda la lista cada vez, lo cual es menos eficiente.

En mi proyecto usé key={task.id}, donde el id lo genero con Date.now() al crear cada tarea, así cada una tiene un identificador único y React sabe exactamente qué cambiar.

c) Explica con tus propias palabras qué hace la función useState y da un ejemplo de dónde la usaste.
useState es un hook de React que me permite guardar datos que pueden cambiar dentro de un componente funcional. Me devuelve dos cosas: el valor actual y una función para actualizarlo. Cada vez que llamo a esa función con un valor nuevo, React vuelve a renderizar el componente para mostrar los cambios en pantalla.

En mi mini aplicación lo usé en dos lugares:

1) En TaskForm.jsx, para guardar lo que el usuario escribe en el input:

jsx
const [text, setText] = useState('');
Aquí text guarda el texto actual y setText lo actualiza cada vez que el usuario teclea. Cuando envío el formulario, agrego la tarea y limpio el input con setText('').

2) En App.jsx, para guardar el arreglo completo de tareas:

jsx
const [tasks, setTasks] = useState([]);
Cada vez que agrego, marco o elimino una tarea, uso setTasks para actualizar el arreglo, y React refresca automáticamente la lista en pantalla.

## 👤 Autor

**velasco martinez zeferino**  
GitHub: [@zefe07](https://github.com/zefe07)