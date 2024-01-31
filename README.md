# REPASO DEL MÓDULO 3 | COHORTE FT46b 📆

```
 _____         _                  _                ___                
|  ___|       (_)                | |              / _ \              
| |__   _ __   _  ___   ___    __| |  ___  ___   / /_\ \ _ __   _ __  
|  __| | '_ \ | |/ __| / _ \  / _` | / _ \/ __|  |  _  || '_ \ | '_ \
| |___ | |_) || |\__ \| (_) || (_| ||  __/\__ \  | | | || |_) || |_) |
\____/ | .__/ |_||___/ \___/  \__,_| \___||___/  \_| |_/| .__/ | .__/
       | |                                              | |    | |    
       |_|                                              |_|    |_|     
```

La siguiente es sólo una guía, tienen libertad de modificar lo que quieran.
La idea es practicar y llegar con todo al CheckPoint !!!
Con mucho 💛 para la Cohorte FT46b

Ariel Romero...

---

## Objetivos

- Desarrollar el servidor de una App que permita administrar episodios.
- Repasar los temas vistos durante el módulo 3.
- Utilizar modularización y buenas prácticas.

## Estructura del proyecto

Se entrega un boilerplate con la siguiente estructura:

```
/ m3-repaso-ft46b
    / src
        / controllers
        / routes
        / utils
          app.js
      index.js
```

## 1. Instalar las dependencias necesarias y crear script

- express
- nodemon
- morgan (opcional)

```bash
npm install express morgan
npm install --save-dev nodemon
```

- Crear el script en el package.json para poder levantar servidor con nodemon

```json
"scripts": {
    "start": "nodemon ./index.js"
```

## 2. Levantar servidor

- Modifica los archivos necesarios para levantar el servidor.
- Crea un servidor modularizado.
    - El archivo "index.js" sólo icluirá el ".listen"

## 3. Creando las rutas principales

- Modularizar cada ruta principal en un archivo distinto.
- Utilizaremos las siguientes rutas principales.
    - localhost:3001/user
    - localhost:3001/episode

## 4. Configurando Middlewares

- Configura los Middlewares necesarios.
- No olvides utilizar `app.use(express.json())`
- También puedes incluir la configuración de CORS

```js
app.use((req, res, next) => {
  res.header("Access-Control-Allow-Origin", "*");
  res.header("Access-Control-Allow-Credentials", "true");
  res.header(
    "Access-Control-Allow-Headers",
    "Origin, X-Requested-With, Content-Type, Accept"
  );
  res.header("Access-Control-Allow-Methods", "GET, POST, OPTIONS, PUT, DELETE");
  next();
});
```

## 5. Estructura de allEpisodes

- Crearemos y exportaremos dentro de la carpeta "utils" el archivo "allEpisodes.js", y dentro de este archivo la variable "allEpisodes" (no olvides exportarla...).
    - Será un array, donde almacenaremos todos los "episodios".
      - Nuestros episodios tendrán la siguiente estructura:

```js
allEpisodes = [
  {
    id: 2,
    name: "Lawnmower Dog",
    air_date: "December 9, 2013",
    episode: "S01E02",
    completed: false || true,
  },
];
```

- Tomaremos desde la Rick&Morty API los datos de cada episodio
  - https://rickandmortyapi.com/api/episode/2

## 6. CRUD de episodes

- Create: Crear
- Read: Leer
- Update: Actualizar
- Delete: Borrar

### POST /episode/:id

- Tomaremos la propiedad "name", "air_date" y "episode" de la Rick&Morty API.
  - Instalamos "axios" para poder hacer peticiones a la API:

```bash
npm install axios
```

- Recibe por params el id del episodio que deseamos agregar.
- Realiza la petición "axios" a la siguiente url:
  - `https://rickandmortyapi.com/api/episode/${id}`
- Crea un nuevo "episode" con las propiedades:
  - id: toma el valor desde lo recibido por la API
  - name: toma el valor desde lo recibido por la API
  - episode: toma el valor desde lo recibido por la API
  - completed: que se inicializa en false (indica si el usuario completó el episodio)
- Agrega el episodio creado al array de "episodes".
- Devuelve el array de "episodes".
- Si el episodio no existe, devuelve un mensaje indicativo.

### GET /episode?id

- Recibe el id del episode por query.
- Si recibe id por query devuelve el episodio correspondiente.
  - Si el id no corresponde a un episodio devuelve un mensaje indicativo.
- Si no recibe el id por query devuelve todos los episodios.

### PUT /episode/:id

- Recibe por params el id del episodio.
- Recibe por body nuevos datos del episode: name, airdate, episode y completed.
  - Puede recibir uno, dos, tres o los cuatro valores para modificar: Se deberán modificar los valores recibidos.
  - Si no recibe ningún valor devuelve un mensaje indicativo.
- Si encuentra un episodio con el id indicado realiza las modificaciones.
- Si no encuentra un episodio con el id indicado, devuelve un mensaje indicativo.

### DELETE /episode/:id

- Recibe por params el email del episode.
- Borra el "episode" si es que la encuentra y devuelve todos los episodios.
- Si no encuentra episode que borrar envía mensaje indicativo.

---

## Sobre la configuración de GIT

- Podemos revisar nuestras credenciales ingresando por consola:

```bash
git config --list
```

- Configurando nuestras credenciales:
    - Por ejemplo:
      - Si nuestro usuario es CohorteFT46b
      - Y nuestro email es: ejemplo@gmail.com

```bash
git config --global user.name "CohorteFT46b"
git config --global user.email ejemplo@gmail.com
```

- Y para subir nuestros cambios a GitHub:

```bash
git add .
git commit -m "aquí nuestro comentario"
git push
```

⚠️ NO OLVIDAR CHEQUEAR QUE LOS CAMBIOS SE REFLEJEN EN EL REPO DE GITHUB ⚠️

---

# ÉXITOS 👍
