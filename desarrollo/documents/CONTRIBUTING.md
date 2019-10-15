# Guia para contribuir

La forma de contribuir a cualquier proyecto de Auronix es mediante [Pull Requests](https://help.github.com/en/articles/about-pull-requests)

En este documento se definen las convenciones que seguimos en el flujo de trabajo y ofrecemos ligas a guias para hacer mas facil el que aceptemos tus contribuciones.

Para contribuir se asume que estas familiarizado con git y github. Puedes aprender [aqui](https://guides.github.com/introduction/git-handbook/)

## Cómo contribuir

Tu PR debe ser un branch que este actualizado con la ultima versión estable. Utilizamos las metodología de [git-flow](https://nvie.com/posts/a-successful-git-branching-model/)

Los Pull Requests (PRs) son la única manera en que puedes contruibuir a algun proeycto.
Para que tu PR sea aceptado debe seguir una lista de requerimientos:

- La contribucion debe estar claramente explicada con lenguaje simple y debes adjuntar un ejemplo minimo que reproduce la funcionalidad.
- Todo el código debe cumplir con las guias de estilo dependiendo del lenguaje:
    - Para php: seguimos el estandard de [PSR](https://www.php-fig.org/psr/), y al correr [php-fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer) no debe arrojar ninguna advertencia.
    - Para javascript: Seguimos las recomendaciones de la [guia de Airbnb](https://github.com/airbnb/javascript)
    - Para C#: seguimos las [C# coding conventions](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
    - Para otros lenguajes, se requieren guias de estilo similares.
- Debe (por lo general) incluir pruebas, y todos deben pasar.
    - Si el PR es un bug fix, debe incluir pruebas unitarias que reproduzcan el error a corregir.    
    - Si el PR es un nuevo feature, debe incluir una serie de pruebas que cubran la nueva funcionalidad.
    - Todos los PRs deben pasar un code review de almenos uno de los líderes o mantenedores del proyecto.   

### Formato de los mensajes del commit

Todo commit debe tener una descripcion que exlpiqué lo que cambio, en qupe contexto y el issue en github con el que se relaciona:

```
Yggdrasyl: foundation, Adds Cache driver for Redis. Fixes #623
```

El formato se puede describir formalmente como:

```
<paquete>: <subpaquete>, <Descripción>. [Fixes #<issue-number>]
```

tip: para la descripciónes útil pensar completar la siguiente frase: "cuando aprueben este commit ______". ([mas info](https://chris.beams.io/posts/git-commit/))

pro-tip: si durante el desarrollo hiciste muchos commits puedes condensarlo en uno solo con `git rebase -i HEAD~[N]` ([mas info](https://www.internalpointers.com/post/squash-commits-into-one-git))

