# Niby Discord Bot - El único e inigualable.

> **Este repositorio es privado por ahora. Si llega a 100 estrellas, haré público el código completo. 2 años de desarrollo, aquí, para todos.**

<div align="center">
 <a href="https://discord.gg/MBPsvcphGf" target="_blank"><img src="https://img.shields.io/maintenance/yes/2023?style=for-the-badge&label=MANTENIDO" /></a>
 <a href="https://discord.gg/MBPsvcphGf" target="_blank"><img src="https://img.shields.io/discord/879397504075063297?color=blue&label=soporte&style=for-the-badge&logoColor=white" /></a>
 <a href="https://www.postgresql.org" target="_blank"><img src="https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white"/></a>
 <a href="https://www.nodejs.org" target="_blank"><img src="https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white"/></a>
</div>

# Handler Híbrido, Shardeado, Clusterizado y con Caché! | V14

El mejor handler **de la historia** de Discord.js en Español (y 17 idiomas más...)

> 👤 *Creado por **`dewstouh`***

> <img src="https://cdn.discordapp.com/icons/879397504075063297/a_36490f721aa5fd41f84422ba9942a855.png" width="20" style="border-radius: 50%;"></img> [El Mundo de Niby](https://discord.com/invite/MBPsvcphGf)

# 📋 Tabla de Contenidos

- [Handler Híbrido, Shardeado, Clusterizado y con Caché! | V14](#handler-híbrido-shardeado-clusterizado-y-con-caché--v14)
- [📋 Tabla de Contenidos](#-tabla-de-contenidos)
  - [✍ Configuración](#-configuración)
    - [☑️ Requisitos](#️-requisitos)
    - [📋 Instalación](#-instalación)
    - [⚙️ Configuración](#️-configuración)
    - [🔨 Creación de Comandos (HÍBRIDOS)](#-creación-de-comandos-híbridos)
      - [💬 Comandos de Prefijo](#-comandos-de-prefijo)
    - [🔲 Creación de Menús Contextuales](#-creación-de-menús-contextuales)
      - [👤 Menú Contextual de Usuario](#-menú-contextual-de-usuario)
      - [💬 Menú Contextual de Mensaje](#-menú-contextual-de-mensaje)
    - [🔲 Creación de Botones](#-creación-de-botones)
    - [🔲 Creación de Menús](#-creación-de-menús)
    - [🔲 Creación de Modales](#-creación-de-modales)
      - [🔼 Pasando Datos en los CustomIDs](#-pasando-datos-en-los-customids)
        - [Handler de Botón `ticket-create`](#handler-de-botón-ticket-create)
  - [💪 Características de Handler](#-características-de-handler)
  - [👌 Contenido de Handler](#-contenido-de-handler)
  - [💛 Contribuciones](#-contribuciones)
  - [🔰 Soporte](#-soporte)

## ✍ Configuración

### ☑️ Requisitos

-  Crear un bot en el [Portal de Developers de Discord](https://discord.com/developers/applications) y activarle los intentos de: Contenido de Mensaje **(obligatorio)**, Miembros de Servidores y Presencia **(opcionales)**.
-  Tener [NodeJS](https://nodejs.org) instalado en el equipo.
   ⚠️ Se recomienda instalar la versión LTS `18.x.x` para evitar posibles errores. ⚠️
-  Un [cluster de MongoDB](https://www.mongodb.com/es/cloud/atlas/) para conectar la base de datos.
-  Un [servidor de Redis](https://redis.io/) para la caché de la base de datos y caché general del bot.
-  Un [servidor de Lavalink (4.0.0 Mínimo)](https://github.com/lavalink-devs/Lavalink/releases/) para la reproducción de música
-  Java 11 para el Servidor de Lavalink
   -  [Java 20 para Linux x86 64 bits](https://www.azul.com/core-post-download/?endpoint=zulu&uuid=552f1968-bc8e-428b-ab56-9a90d70873d0).
   -  [Java 17 para Linux AMPERE](https://www.azul.com/core-post-download/?endpoint=zulu&uuid=c25072ad-8241-4c2f-88fc-2ae732a571a7).
   -  [Java 20 para Windows 64 bits](https://www.azul.com/core-post-download/?endpoint=zulu&uuid=b4690837-fde2-43a4-b471-14ce36b4e01c).
   -  [Java 17 para Windows 32 bits](https://www.azul.com/core-post-download/?endpoint=zulu&uuid=2a37094d-da2b-4970-86d0-a28bae65caef).
   -  [MacOS 64 bits](https://www.azul.com/core-post-download/?endpoint=zulu&uuid=3aabd267-a304-4fc9-b814-1d9f8ab280c8).
   -  MacOS 32 bits: No disponible.
-  El [Gestor de Procesos PM2](https://www.npmjs.com/package/pm2) _(recomendado para el hosteo 24/7 con auto reinicios)_ `npm i pm2 -g && pm2 startup`
-  Es recomendable hostearlo en un VPS o una Raspberry PI para dejar tu bot 24/7 encendido.

### 📋 Instalación

1. Clonado de repositorio
```bash
git clone https://github.com/El-Mundo-de-Niby/handler-v14
```

2. Instalación de módulos
```bash
npm install
```

### ⚙️ Configuración

Encontrarás un archivo llamado `example.env`, renómbralo a `.env` e introduce los datos que se solicitan para el funcionamiento del bot.

_⚠️ Nunca compartas el contenido de tu `.env` con nadie_

```
# BOT -- ESSENTIALS
BOT_TOKEN = "OBTEN TU TOKEN EN https://discord.dev" #contraseña de acceso al bot | https://discord.com/developers/applications
DATABASE_URL = "mongodb+srv://<nombre>:<contraseña>@cluster0.lrfcz.mongodb.net/nombreDB" #url de acceso al cluster de mongodb | https://www.mongodb.com/cloud/atlas/
LANGUAGE = "SpanishES"

# BOT -- SHARDING & CLUSTERING

TOTAL_SHARDS = 0 #shards
SHARDS_PER_CLUSTER = 0 #shards por cada cluster
SHARDING_MODE="process"


# DB -- CACHING
CACHE_DB = "true"
REDIS_URL = "127.0.0.1:6379"

# BOT -- DEFAULT DATA

PREFIX = "," #prefijo de comandos
STATUS = "discord.gg/niby" #texto de estado del bot
STATUS_TYPE = "Watching" #Playing, Streaming, Listening, Competing | https://discord-api-types.dev/api/discord-api-types-v10/enum/ActivityType
COLOR = "#FFFFFF" #color de embeds por defecto
COOLDOWN_COLOR = "#ff9d00" #color de embeds por defecto
ERROR_COLOR = "#FF0000"
OWNER_IDS = "La id de los owners separada por espacios" #owners del bot que podrán ejecutar los comandos de dueño
DISCORD = "https://discord.gg/MBPsvcphGf"

VERSION = "1.0.0"

# DASHBOARD -- CONFIG

DASHBOARD = "true"
WEB_DOMAIN = "localhost"
PORT = 3000
```

> También se incluye un fichero llamado `.env.test`, este sirve para iniciar el bot con una configuración exclusiva para __testeos__ o __desarrollo__ y no afectar a la configuracion principal.

Cuando tengas el bot configurado y con sus módulos instalados, puedes encenderlo usando `npm run start` o si lo quieres encender en modo desarrollo puedes usar `npm run dev`.

### 🔨 Creación de Comandos (HÍBRIDOS)

#### 💬 Comandos de Prefijo

En el contenido de `/src/comandos`, podrás encontrar las categorías de los comandos, para crear una categoría, es tan sencillo como crear una carpeta dentro de esta ruta, por ejemplo:

-  `/src/comandos/Prueba`

Para crear comandos dentro de esta categoría, tendrás que crear un archivo con el nombre del comando con formato `.js`, por ejemplo:

-  `/src/comandos/Prueba/ping.js`

Después, tendrás que crear la estructura (objeto) del comando con la siguiente plantilla:

```js
export default {
   PERMISSIONS: ['Administrator', 'KickMembers', 'BanMembers'], //permisos que necesitará el usuario para ejecutar el comando
   BOT_PERMISSIONS: ['Administrator', 'KickMembers', 'BanMembers'], //permisos que necesitará el bot para ejecutar el comando
   ALIASES: ['alias1', 'alias2', 'alias3'], // Nombres adiciionales para llamar al comando.
   OWNER: true, // Solo los dueños del bot podrán ejecutar el comando
   GUILD_ONLY: true, //Solo se puede ejecutar en un servidor
   NSFW: true, // Solo se puede si el canal tiene NSFW activado
   PREMIUM: true, // Solo se puede ejecutar si el usuario es premium
   LEVEL: 0, // Nivel mínimo para ejecutar el comando
   execute(client, message, args, prefix, guildData, userData) {
      //ejecución del comando
      return message.reply(`\`${client.ws.ping}ms\``);
   },
} as Command;
```

⌚ No es necesario especificar el nombre del comando. El nombre del comando será igual al nombre del archivo.

Para ejecutar el comando que hayamos creado, es tan sencillo como ejecutar en nuestro bot `<Prefijo>ping`

_⚠️ Si creas dos comandos con el mismo nombre, el bot solo ejecutará uno de ellos. ⚠️_
> No obstante, se puede ejecutar cada comando con `<prefijo><categoria> <nombre>` o `<prefijo><categoria><subcategoria> <nombre>`, de esta manera, si se podrán ejecutar comandos con el mismo nombre.

### 🔲 Creación de Menús Contextuales

Un menú contextual es aquel menú que aparece cuando haces clic derecho sobre un Usuario o un Mensaje, para crear un menú contextual personalizado para uno de ellos es tan sencillo como:

#### 👤 Menú Contextual de Usuario

Para crear un menú contextual de usuario debemos de crear el fichero con el nombre del menú dentro de la carpeta `./src/components/contextmenus/User`, una plantilla de ejemplo puede ser:

```js
export default {
   PERMISSIONS: ['Administrator'],
   BOT_PERMISSIONS: ['Administrator'],
   // ...propiedades de un comando normal (cooldown, nsfw, premium, guildOnly, etc)
   async execute(client, interaction, guildData, userData) {
      const { username } = interaction.targetUser;
      console.log(username);
   },
} as Component;
```

#### 💬 Menú Contextual de Mensaje

Para crear un menú contextual de mensaje debemos de crear el fichero con el nombre del menú dentro de la carpeta `./src/components/contextmenus/Message`, una plantilla de ejemplo puede ser:

```js
export default {
   PERMISSIONS: ['Administrator'],
   BOT_PERMISSIONS: ['Administrator'],
      // ...propiedades de un comando normal (cooldown, nsfw, premium, guildOnly, etc)
   async execute(client, interaction, guildData, userData) {
      await interaction.reply({
         content: 'Hi!',
      });
   },
};
```

### 🔲 Creación de Botones

Para crear un botón se puede hacer de la siguiente manera:

`./src/components/buttons/Ticket/create.js` - para botones con customId: `ticket-create`

o:

`./src/components/buttons/ticket-create.js`

```js
export default {
       // ...propiedades de un comando normal (cooldown, nsfw, premium, guildOnly, etc)
   async execute(client, interaction, args, guildData, userData) {
      await interaction.reply({
         content: `Creando tu ticket... porfavor espera...`,
         ephemeral: true,
      });
      //resto de codigo...
   },
} as Component;
```

### 🔲 Creación de Menús

Para crear un menú se puede hacer de la siguiente manera:

`./src/components/menus/Role/add.js` - para botones con customId: `role-add`

o:

`./src/components/Role/role-add.js`

```js
export default {
       // ...propiedades de un comando normal (cooldown, nsfw, premium, guildOnly, etc)
   async execute(client, interaction, args, guildData, userData) {
      let role = interaction.values[0]; //Primera selección
      await interaction.member.roles.add(role);
      await interaction.reply({
         content: `Rol <@&${role}> añadido!`,
         ephemeral: true,
      });
   },
} as Component;
```

### 🔲 Creación de Modales

Para crear un botón se puede hacer de la siguiente manera:

`./src/components/modals/User/report.js` - para modales con customId: `user-report-{idUsuario}`

o:

`./src/components/modals/user-report.js`

```js
export default {
       // ...propiedades de un comando normal (cooldown, nsfw, premium, guildOnly, etc)
   async execute(client, interaction, args, guildData, userData) {
      let userIdToReport = args[0]; //Obtenemos el dato pasado por el customId
      await interaction.reply({
         content: `El usuario <@${userIdToReport}> ha sido reportado!`,
         ephemeral: true,
      });
   },
} as Component;
```

#### 🔼 Pasando Datos en los CustomIDs

Para pasar variables en el customId como por ejemplo `ticket-create-{idUsuario}` y facilitar el acceso a los datos, se puede hacer creando los customIds de los handlers de interacciones añadiendo `{dato}` en estos como en el siguiente ejemplo:

```js
let userId = interaction.user.id;

new ButtonBuilder().setLabel('Crear Ticket').setCustomId(`ticket-create-{${userId}}`).setStyle('Secondaty');
```

Es importante tener en cuenta que el dato se deberá de pasar entre llaves: `{dato}`, si no, el bot no lo detectará como dato y no lo pasará en la variable `args`

El handler de la interacción tendrá la variable `args`, que devolverá un array de los datos especificados en el customId:

##### Handler de Botón `ticket-create`

Supongamos que tenemos nuestro handler del crear tickets dentro de `./src/components/buttons/Ticket/create`

```js
export default {
       // ...propiedades de un comando normal (cooldown, nsfw, premium, guildOnly, etc)
   async execute(client, interaction, args, guildData, userData) {
      let userIdWhoClicked = args[0];

      console.log(userIdWhoClicked); // 282942681980862474

      console.log(args); // ["282942681980862474"]
   },
} as Component;
```

En la variable `args` encontraremos el array de datos pasados en el customId, al que podemos acceder fácilmente usando `args`, `args.join()` o `args[NºIndice]`

_Cada propiedad disponible en los comandos como PERMISSIONS, BOT_PERMISSIONS, COOLDOWN, GUILD_ONLY... también se puede añadir en los handler de interacciones (Botones, Menús, Menús Contextuales y Modales)_

## 💪 Características de Handler

-  ✅ En TYPESCRIPT! Con TIPADOS!
-  ✅ Código SEGURO.
-  ✅ Base de Datos MongoDB
-  ✅ Caché de Base de Datos con Redis
-  ✅ Caché General de Bot con Redis
-  ✅ Shardeado y Clusterizado
-  ✅ Dashboard
-  ✅ Handler para Dashboard
-  ✅ Altamente escalable
-  ✅ Organizado, fácil de entender.
-  ✅ Logs personalizados.
-  ✅ Logs de errores en archivos (`./logs/{fecha}.log`).
-  ✅ Logs de errores en Discord (Webhook).
-  ✅ Comandos de Prefijo.
-  ✅ Comandos de Slash.
-  ✅ Handler de Botones.
-  ✅ Handler de Menús.
-  ✅ Handler de Menús Contextuales.
-  ✅ Handler de Modales.
-  ✅ Handlers Configurados Semi-Automaticamente.
-  ✅ Comandos e Interacciones con Sistema Cooldown.
-  ✅ Comandos e Interacciones con Sistema de Permisos.
-  ✅ Sistema premium.
-  ✅ Recarga el bot sin tener que reiniciar, evitando spams a la API de Discord.
-  ✅ Sistema Multilenguaje Semi-Automático.
-  ✅ Funciones de Javascript personalizadas (Array.random, Number.random, String.isValidUrl()... etc).
-  ✅ Preparado para soportar +50k servidores.


## 👌 Contenido de Handler
- 👑 Comandos de Dueño
- ⚙️ Ajustes `(Bot | Sistemas | Servidor | Comandos)`
- 🔰 Información `(Bot | Usuario | Servidor)`
- 🎶 Sistema de Música
- 🪙 Sistema de Economía
- 👀 Filtros `(Audio | Ecualización | Velocidad | Tono)`
- 🔞 Comandos NSFW `(Anime | Real | Otros)`
- 🌍 [Sitio web](http://localhost://3002)

## 💛 Contribuciones

Gracias por usar este código! Si quieres apoyarnos puedes hacerlo realizando una [donación a través de PayPal](https://paypal.me/mfdewstouh).

Todas las donaciones serán utilizadas para mejorar el servicio, los bots, la calidad de los videos y su contenido. ¡Gracias!

## 🔰 Soporte

Si necesitas ayuda, puedes acudir a nuestro <img src="https://cdn.discordapp.com/icons/879397504075063297/a_36490f721aa5fd41f84422ba9942a855.png" width="16" style="border-radius: 50%;"></img> [Servidor de Soporte](https://discord.gg/MBPsvcphGf) y podrás encontrar canales de ayuda en la sección de `🖥️ Programación`.

**_Testeado y funcionando correctamente en la versión NodeJS `18.17.0` y npm `9.0.0`_**
