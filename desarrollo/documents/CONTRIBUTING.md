# Guía para contribuir

La forma de contribuir a cualquier proyecto de Auronix es mediante [Pull Requests](https://help.github.com/en/articles/about-pull-requests)

En este documento se definen las convenciones que seguimos en el flujo de trabajo y ofrecemos ligas a guías para hacer mas fácil que aceptemos tus contribuciones.

Para contribuir se asume que estas familiarizado con Git y Github. Puedes aprender [en la guía de Github](https://guides.github.com/introduction/git-handbook/)

## Cómo contribuir

Tu PR debe ser una rama que esté actualizada con la última versión estable. Utilizamos la metodología de [git-flow](https://nvie.com/posts/a-successful-git-branching-model/)

Los Pull Requests (PRs) son la única manera en que puedes contribuir a algún proyecto.

Para que tu PR sea aceptado debe cumplir los siguientes requerimientos:

- Tu cambio debe estar claramente explicado con lenguaje simple y debes adjuntar un ejemplo mínimo que reproduce la funcionalidad.
- Todo el código debe cumplir con las guías de estilo dependiendo del lenguaje:
    - Para php: seguimos el estándar de [PSR 1y 12](https://www.php-fig.org/psr/), y al correr [php-fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer) no debe arrojar ninguna advertencia.
    - Para javascript: Seguimos las recomendaciones de la [guía de Airbnb](https://github.com/airbnb/javascript)
    - Para C#: seguimos las [Convenciones de código de C#](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
    - Para otros lenguajes, se requieren guías de estilo similares.
- Debe (por lo general) incluir pruebas, y todas deben pasar.
    - Si el PR es un bug fix, debe incluir pruebas unitarias que reproduzcan el error a corregir.    
    - Si el PR es un nuevo feature, debe incluir una serie de pruebas que cubran la nueva funcionalidad.
    - Todos los PRs deben pasar un code review de al menos uno de los líderes o líderes del proyecto.   

### Formato de los mensajes del commit

Todo commit debe tener una descripción que explique lo que cambió, en qué contexto y el issue en Github con el que se relaciona. ejemplo:

```
Yggdrasyl: foundation, Adds Cache driver for Redis. Fixes #623
```

El formato se puede describir formalmente como:

```
<paquete>: <subpaquete>, <Descripción>. [Fixes #<issue-number>]
```

Debes asegurarte de que la descripción sea clara y concisa, por regla general debe poder contestar la pregunta ¿Qué va a pasar cuando este commit se acepte?

```
Ejemplo de descripción mala:

Se agrega if

Ejemplo de descripción buena:

Se valida que el usuario exista antes de obtener mensajes.
```

Puedes aprender más de cómo escribir mensajes claros [aquí](https://chris.beams.io/posts/git-commit/).

pro-tip: si durante el desarrollo hiciste muchos commits puedes condensarlo en uno solo con `git rebase -i HEAD~[N]` ([más info](https://www.internalpointers.com/post/squash-commits-into-one-git))

