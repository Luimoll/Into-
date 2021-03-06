---
title: Mover un archivo a una nueva ubicación
intro: 'You can move a file to a different directory on {% data variables.product.product_name %} or by using the command line.'
redirect_from:
  - /articles/moving-a-file-to-a-new-location
  - /github/managing-files-in-a-repository/moving-a-file-to-a-new-location
  - /articles/moving-a-file-to-a-new-location-using-the-command-line
  - /github/managing-files-in-a-repository/moving-a-file-to-a-new-location-using-the-command-line
  - /github/managing-files-in-a-repository/managing-files-on-github/moving-a-file-to-a-new-location
  - /github/managing-files-in-a-repository/managing-files-using-the-command-line/moving-a-file-to-a-new-location-using-the-command-line
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
topics:
  - Repositories
shortTitle: Mover un archivo
---

Además de cambiar la ubicación del archivo, también puedes [actualizar los contenidos de tu archivo](/articles/editing-files-in-your-repository), o [darle un nuevo nombre](/articles/renaming-a-file) en la misma confirmación.

## Moving a file to a new location on {% data variables.product.product_name %}

{% tip %}

**Tips**:

- Si tratas de mover un archivo en un repositorio al cual no tienes acceso, bifurcaremos el proyecto a tu cuenta de usuario y te ayudaremos a enviar [una solicitud de extracción](/articles/about-pull-requests) al repositorio original después de confirmar tu cambio.
- Algunos archivos, como imágenes, necesitan que los muevas desde la línea de comando. Para obtener más información, consulta "[Mover un archivo a una nueva ubicación utilizando la línea de comando](/articles/moving-a-file-to-a-new-location-using-the-command-line)".
- {% data reusables.repositories.protected-branches-block-web-edits-uploads %}

{% endtip %}

1. En tu repositorio, navega hasta el archivo que deseas mover.
2. En la esquina superior derecha de la vista del archivo, haz clic en {% octicon "pencil" aria-label="The edit icon" %} para abrir el editor de archivos. ![Icono Edit file (Editar archivo)](/assets/images/help/repository/move-file-edit-file-icon.png)
3. En el campo de nombre de archivo, cambia el nombre del archivo utilizando estos lineamientos: ![Editar el nombre del archivo](/assets/images/help/repository/moving_files.gif)
    - Para mover el archivo **dentro de una subcarpeta**, escribe el nombre de la carpeta que deseas, seguido de `/`. El nombre de tu nueva carpeta se convierte en el nuevo elemento en la ruta de navegación.
    - Para mover el archivo dentro de un directorio **encima de la ubicación actual del archivo**, coloca tu cursor al comienzo del campo de nombre de archivo, después escribe `../` para subir un nivel completo de directorio, o presiona la tecla de `retroceso` para editar el nombre de la carpeta padre.
{% data reusables.files.write_commit_message %}
{% data reusables.files.choose_commit_branch %}
{% data reusables.files.propose_file_change %}

## Mover un archivo a una nueva ubicación utilizando la línea de comando

Puedes utilizar la línea de comando para mover archivos dentro de un repositorio al eliminar el archivo de la ubicación anterior y después agregarlo en la nueva ubicación.

Muchos archivos pueden [moverse directamente en {% data variables.product.product_name %}](/articles/moving-a-file-to-a-new-location), pero algunos archivos, como imágenes, necesitan que los muevas desde la línea de comando.

{% data reusables.command_line.manipulating_file_prereqs %}

1. En la computadora, mueve el archivo a una nueva ubicación dentro del directorio que fue creado localmente en tu computadora cuando clonaste el repositorio.
{% data reusables.command_line.open_the_multi_os_terminal %}
3. Utiliza `git status` para verificar la nueva ubicación y la ubicación anterior del archivo.
  ```shell
  $ git status
  > # On branch <em>your-branch</em>
  > # Changes not staged for commit:
  > #   (use "git add/rm <file>..." to update what will be committed)
  > #   (use "git checkout -- <file>..." to discard changes in working directory)
  > #
  > #     deleted:    /<em>old-folder</em>/<em>image.png</em>
  > #
  > # Untracked files:
  > #   (use "git add <file>..." to include in what will be committed)
  > #
  > #     /<em>new-folder</em>/<em>image.png</em>
  > #
  > # no changes added to commit (use "git add" and/or "git commit -a")
  ```
{% data reusables.git.stage_for_commit %} Esto eliminará, o `git rm`, el archivo de la ubicación antigua y agregará, o `git add`, el archivo en la nueva ubicación.
  ```shell
  $ git add .
  # Agrega el archivo a tu repositorio local y lo presenta para la confirmación.
  # {% data reusables.git.unstage-codeblock %}
  ```
5. Utiliza `git status` para verificar los cambios preparados para confirmar.
  ```shell
  $ git status
  > # On branch <em>your-branch</em>
  > # Changes to be committed:
  > #   (use "git reset HEAD <file>..." to unstage)
  > #
  > #    renamed:    /old-folder/image.png -> /new-folder/image.png
  # Displays the changes staged for commit
  ```
{% data reusables.git.commit-file %}
  ```shell
  $ git commit -m "Move file to new directory"
  # Commits the tracked changes and prepares them to be pushed to a remote repository.
  # {% data reusables.git.reset-head-to-previous-commit-codeblock %}
  ```
{% data reusables.git.git-push %}
