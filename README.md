## Guía Esencial de Comandos Git

| Sección | Acción | Comando | Descripción |
| :--- | :--- | :--- | :--- |
| **Repositorio** | Iniciar Repositorio | `git init` | Comienza a rastrear el directorio actual. |
| **Configuración** | Config. Global (Editar) | `git config --global -e` | Abre el archivo `~/.gitconfig` en tu editor. |
| **Configuración** | Ver Credenciales | `nano ~/.git-credentials` | (Para sistemas que usan `credential.helper = store`). |
| **Alias** | Establecer Alias (ej.) | `git config --global alias.s "status --short"` | Convierte `git status --short` en `git s`. |
| **Agregar** | Agregar Archivo Específico | `git add **file**` | Agrega un archivo concreto al Staging. |
| **Agregar** | Agregar Directorio | `git add **directory**` | Agrega todos los archivos dentro del directorio. |
| **Agregar** | Agregar Todos | `git add .` | Agrega todos los archivos nuevos y modificados. |
| **Agregar** | Agregar Solo Tracked | `git add . -u` | Agrega archivos rastreados (modificados/eliminados) solamente. |
| **Agregar** | Agregar por Extensión | `git add *.* **file extension**` | Agrega archivos con una extensión específica. |
| **Commit** | Commit Estándar | `git commit -m "**message**"` | Requiere `git add` previo. |
| **Commit** | Commit Rápido (Tracked)| `git commit -am "**message**"` | Agrega automáticamente archivos *tracked* y hace commit. |
| **Commit** | Enmendar Mensaje | `git commit --amend -m "**message**"` | Corrige el mensaje del último commit. |
| **Historial** | Log Estándar | `git log` | Muestra el historial de commits. |
| **Historial** | Log con Alias | `git lg` | Muestra el log con formato gráfico y decorado (si el alias está configurado). |
| **Revertir** | Descartar Locales | `git checkout -- .` | Revierte los archivos locales a la versión del último commit. |
| **Revertir** | Revisar Hash | `git checkout **hash**` | Se mueve al código en un punto específico (detached HEAD). |
| **Reset** | Reset Soft (HEAD^) | `git reset --soft HEAD^` | Mueve HEAD al commit anterior, manteniendo cambios en Staging. |
| **Reset** | Reset Hard (Hash) | `git reset --hard **hash**` | Mueve HEAD y elimina todos los cambios posteriores a ese hash. |
| **Reflog** | Ver Registro de HEAD | `git reflog` | Muestra el historial de movimientos de HEAD para recuperación. |
| **Rename** | Renombrar/Mover | `git mv **old** **new**` | Renombra un archivo y mantiene su historial. |
| **Delete** | Eliminar | `git rm **-param** **file or directory**` | Elimina el archivo y lo prepara para el commit. |
| **Branches**| Crear Rama | `git branch **name of the branch**` | Crea una rama nueva. |
| **Branches**| Cambiar a Rama | `git checkout **name of the branch**` | Se mueve a una rama existente. |
| **Branches**| Fusionar Ramas | `git merge **name of the branch**` | Integra los cambios de una rama a la actual. |
| **Tags** | Crear Tag | `git tag -a **tag name** **hash** -m **tag message**` | Marca un commit como una versión estable (LTS). |
