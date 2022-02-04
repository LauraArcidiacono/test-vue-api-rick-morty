# test-vue-api-rick-morty

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your unit tests
```
npm run test:unit
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

# Prueba

La prueba consiste en realizar un listado de personajes de rick and morty.

## Parte easy

### Requisitos

* Los datos se sacarán directamente de la [API de Rick and Morty](https://rickandmortyapi.com/documentation/#get-all-characters).
* El listado debe tener una paginador infinito, es decir según se haga scroll se deben seguir mostrando personajes.
* Los usuarios tienes 3 estados y se desea mostra de un color en función del estado:
  * alive: verde
  * dead: rojo
  * unknown: gris

## Parte media

### Requisitos

Se desea añadir un buscador inteligente

* Se deben poder filtrar por name y status.
* Se desea que el usuario pueda introducir "name:valor" para buscar por nombre.
* Se desea que el usuario pueda introducir "status:valor" para buscar por estado.

Nota: se valora que se tenga en cuenta que en un futuro sea sencillo, 
añadir nuevos filtros.

## Parte hardcore

Se desea guardar las veces que pasa el ratón por encima de un personaje.

### Requisitos

 * Se guardará cuantas veces se ha pasado el ratón por encima de la card de un personaje.
 * Cada 10 segundos se mostrará por consola en formato json (e.g. [{"name": "Rick Sanchez", "times": 3}])

Nota: en esta fase se valorará el rendimiento de la app tanto en el renderizado como en el consumo de memoria.

## Diseño

[Diseño](https://www.figma.com/file/zBijv6sU9rJNDlP9vNw30w/Untitled?node-id=0%3A1)
