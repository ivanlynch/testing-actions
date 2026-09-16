# GitHub verified commit lab

Este repositorio reproduce el comportamiento de una rama que exige commits con firma verificada.

## Escenario

- Rama protegida: `signed-commit-lab`.
- Archivo modificado por las pruebas: `lab/counter.txt`.
- Workflow: **Verified commit lab**.

El workflow ofrece dos métodos:

1. `unsigned-local-git`: crea un commit local con `git commit` y confirma que GitHub rechaza el push por falta de firma verificada.
2. `github-signed-graphql`: usa la mutación GraphQL `createCommitOnBranch`, confirma que GitHub acepta el commit y verifica mediante la API que quedó marcado como `Verified`.

Cada ejecución escribe un valor único en `lab/counter.txt`. El método sin firma no debe modificar la rama remota; el método GraphQL sí debe hacerlo.
