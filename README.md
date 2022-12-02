# API RestFull desarrollada en Deno

## Requisitos
- __Deno__ 
``` 
VERSIÓN ACTUAL
PS C:\Users\zeus> deno --version
deno 1.26.2 (release, x86_64-pc-windows-msvc)
v8 10.7.193.16
typescript 4.8.3
PS C:\Users\zeus>
```

- __Deno plugin en VS Studio Code__
```
Deno
v3.14.0
denoland 299,011
A language server client for Deno.
```

- __MongDB & MariaDB__
- Alguna herramienta para probar APIS como:
     - __RapidAPI__ Puedes instalar la extension en Visual Studio Code.
	 - __[PostMan](https://www.postman.com/)__
	 - __U otra__

---
## Instalacion del servidor
Puedes clonar en una carpeta en especifico utilizando PowerShell o Git.
```
mkdir NOMBRE_DIRECTORIO 
git clone https://github.com/asyncr/deno_api NOMBRE_DIRECTORIO 
```
O directamente.
```
git clone https://github.com/asyncr/deno_api
```
---
## Configuración del servidor
Revisa que los datos del archivo __connectors.ts__ correspondan a tus bases de datos.
~~~
/config/connectors.ts
~~~
---
## Ejecucion del servidor
Es necesario recompilar todos los modulos para que se descarguen nuevamente.
```
deno cache --reload .\dependences.ts
```
Es posible que marque error debido a que __denodb__ incorpora en sus modulos  la librería __std__
la cuál esta deprecada a partir de la version __0.161.0__

Por lo que se debe forzar a instalarse.
```
deno install --allow-write -f --allow-read --unstable --allow-net .\dependences.ts
```
Y por ultimo correr el servidor.
```
deno run --allow-net --allow-write --allow-read --allow-env .\server.ts
```
---
Result
```
PS C:\Users\zeus\Desktop\denoland> ls
    Directorio: C:\Users\zeus\Desktop\denoland
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----    17/11/2022  12:24 p. m.                  .vscode
d-----    17/11/2022  12:24 p. m.                  config
d-----    17/11/2022  12:24 p. m.                  controllers
d-----    17/11/2022  12:24 p. m.                  interfaces
d-----    17/11/2022  12:24 p. m.                  middleware
d-----    17/11/2022  12:24 p. m.                  repositories
d-----    17/11/2022  12:24 p. m.                  routes
d-----    17/11/2022  12:24 p. m.                  services
-a----    10/11/2022  10:45 p. m.           1062   dependences.ts
-a----    10/11/2022  10:45 p. m.           1598   README.md
-a----    10/11/2022  10:45 p. m.            764   server.ts
PS C:\Users\zeus\Desktop\denoland> deno cache --reload .\dependences.ts
Download ⠼ https://deno.land/std@0.161.0/crypto/util.ts                                                                                             Warning Implicitly using latest version (v3.2.0) for https://deno.land/x/dotenv/mod.ts
Download ⠼ https://deno.land/x/dotenv@v3.2.0/mod.ts                                                                                                 Warning Implicitly using latest version (v11.1.0) for https://deno.land/x/oak/mod.ts
Download ⠼ https://deno.land/x/oak@v11.1.0/mod.ts                                                                                                   Warning Implicitly using latest version (v1.1.0) for https://deno.land/x/denodb/mod.ts
Download ⠼ https://deno.land/x/denodb@v1.1.0/mod.ts                                                                                                 Warning Implicitly using latest version (v2.7) for https://deno.land/x/djwt/mod.ts
Download ⠼ https://deno.land/std@0.161.0/crypto/_wasm_crypto/lib/deno_std_wasm_crypto.generated.mjs                                                 Warning Implicitly using latest version (v0.2.10) for https://deno.land/x/expect/mod.ts
Download ⠼ https://deno.land/x/expect@v0.2.10/mod.ts                                                                                                Warning Implicitly using latest version (0.162.0) for https://deno.land/std/http/http_status.ts
Download ⠦ https://deno.land/x/postgres@v0.14.2/connection/message.ts                                                                               Warning Implicitly using latest version (0.162.0) for https://deno.land/std/fmt/colors.ts
Download ⠧ https://deno.land/std@0.162.0/fmt/colors.ts                                                                                              Warning Implicitly using latest version (0.162.0) for https://deno.land/std/node/assert.ts
Warning Implicitly using latest version (0.162.0) for https://deno.land/std/node/events.ts
Warning Implicitly using latest version (0.162.0) for https://deno.land/std/node/stream.ts
Warning Implicitly using latest version (0.162.0) for https://deno.land/std/node/url.ts
Download ⠧ https://deno.land/std@0.162.0/node/url.ts                                                                                                Warning Implicitly using latest version (0.162.0) for https://deno.land/std/node/util.ts
Warning Implicitly using latest version (0.162.0) for https://deno.land/std/path/mod.ts
Warning Implicitly using latest version (0.162.0) for https://deno.land/std/uuid/mod.ts
PS C:\Users\zeus\Desktop\denoland> deno install --allow-write -f --allow-read --unstable --allow-net .\dependences.ts
✅ Successfully installed dependences
C:\Users\zeus\.deno\bin\dependences.cmd
C:\Users\zeus\.deno\bin\dependences (shell)
PS C:\Users\zeus\Desktop\denoland> deno run --allow-net --allow-write --allow-read --allow-env .\server.ts
Server running on port 8080
```