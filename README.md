# Chat API - Proyecto en Vue

**Chat API** es una aplicación de chat en tiempo real construida con Vue 3, que permite a los usuarios intercambiar mensajes de forma personalizada. Los mensajes de cada usuario se muestran con colores y alineaciones diferenciadas, proporcionando una experiencia de chat visualmente atractiva.

## Tabla de Contenidos
- [Chat API - Proyecto en Vue](#chat-api---proyecto-en-vue)
  - [Tabla de Contenidos](#tabla-de-contenidos)
  - [Características](#características)
  - [Demo](#demo)
  - [Instalación](#instalación)
  - [Uso](#uso)
  - [Componentes](#componentes)
    - [App.vue](#appvue)
      - [Props:](#props)
      - [Estilos:](#estilos)
    - [Chatbox.vue](#chatboxvue)
      - [Variables y Métodos:](#variables-y-métodos)
      - [Estilos:](#estilos-1)
  - [Personalización](#personalización)

## Características
- **Mensajes en tiempo real**: permite el envío de mensajes de texto personalizados entre dos usuarios.
- **Personalización de colores**: cada usuario puede elegir el color de fondo de su mensaje.
- **Usuarios generados aleatoriamente**: utiliza la API de [Random User](https://randomuser.me) para generar nombres y fotos de perfil para los usuarios.
- **Estilos visuales modernos**: diseño basado en sombras y transparencia para un efecto visual llamativo.

## Demo
Puedes ver una demo en vivo de la aplicación en [este enlace](https://api-chat.netlify.app/)

## Instalación

1. **Clona el repositorio**:
    ```bash
    git clone https://github.com/mr-gantiva/chat-api
    cd chat-api
    ```

2. **Instala las dependencias**:
    ```bash
    npm install
    ```

3. **Ejecuta el servidor de desarrollo**:
    ```bash
    npm run dev
    ```

4. **Accede a la aplicación**:
   Abre [http://localhost:5173](http://localhost:5173) en tu navegador.

## Uso
1. En la interfaz de usuario, verás dos paneles para los usuarios de chat, cada uno con su foto de perfil y nombre generados automáticamente.
2. Escribe un mensaje en el campo de texto del usuario y elige el color de fondo si deseas personalizarlo.
3. Haz clic en el botón "Enviar" para enviar el mensaje. Los mensajes aparecerán en el área central de chat con alineación y color específicos para cada usuario.

## Componentes

### App.vue

El componente `App.vue` maneja la visualización de mensajes en la interfaz de chat, diferenciando entre mensajes enviados por el usuario izquierdo (left) y el derecho (right).

#### Props:
- `chat`: un array de objetos que contiene los mensajes enviados, la información del usuario, y el color de fondo.

#### Estilos:
- `left__user--chat` y `right__user--chat`: aplican alineación y estilos específicos para diferenciar los mensajes según el usuario.
- `user__name`: estiliza el nombre de cada usuario.

### Chatbox.vue

El componente `Chatbox.vue` maneja la lógica de envío de mensajes y la configuración de los usuarios mediante la API `Random User`.

#### Variables y Métodos:
- **Variables**:
  - `usuarios`: almacena los datos de los usuarios generados aleatoriamente.
  - `inputText`, `inputText2`: capturan el mensaje de cada usuario.
  - `colorBox`, `colorBox2`: almacenan el color de fondo de cada usuario.
- **Métodos**:
  - `getUsuarios`: obtiene los datos de los usuarios de la API `Random User` al cargar el componente.
  - `enviarMensaje`: envía el mensaje con el texto, color y nombre del usuario activo.

#### Estilos:
- `.inputColor` y `.inputText`: estilizan los campos de entrada de color y texto.
- `.btn__enviar`: estiliza el botón de envío de mensajes con un efecto de transición.

## Personalización

- **Colores**: Los colores de los mensajes se pueden personalizar mediante el selector de color en cada panel de usuario.
- **Estilos**: Los estilos están diseñados para adaptarse a una estética moderna; puedes personalizarlos modificando las clases CSS en los componentes `App.vue` y `Chatbox.vue`.

---

¡Gracias por usar Chat API! Esperamos que encuentres esta herramienta útil para tus proyectos de comunicación en tiempo real.