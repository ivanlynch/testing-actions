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

## Resultado comprobado

- [Ruleset activo](https://github.com/ivanlynch/testing-actions/rules/23556770): exige firmas verificadas en `signed-commit-lab`.
- [Control negativo](https://github.com/ivanlynch/testing-actions/actions/runs/35130378784): GitHub rechazó el commit local sin firma con `GH013`.
- [Prueba positiva](https://github.com/ivanlynch/testing-actions/actions/runs/35130434481): `createCommitOnBranch` actualizó correctamente la rama protegida.
- [Commit resultante](https://github.com/ivanlynch/testing-actions/commit/7c173a1494edb82e1ca218d53daa508752c37a05): la API de GitHub reporta `verified: true` y `reason: valid`.
