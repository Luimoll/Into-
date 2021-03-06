---
title: Configurar la visibilidad de un repositorio
intro: Puedes elegir quién puede ver tu repositorio.
redirect_from:
  - /articles/making-a-private-repository-public/
  - /articles/making-a-public-repository-private/
  - /articles/converting-a-public-repo-to-a-private-repo/
  - /articles/setting-repository-visibility
  - /github/administering-a-repository/setting-repository-visibility
  - /github/administering-a-repository/managing-repository-settings/setting-repository-visibility
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
topics:
  - Repositories
shortTitle: Visibilidad del repositorio
---

## Acerca de los cambios a la visibilidad de un repositorio

Los propietarios de las organizaciones pueden restringir la capacidad de cambiar la visibilidad de un repositorio únicamente para otros propietarios de organizaciones. Para obtener más información, consulta la sección "[Restringir los cambios a la visibilidad del repositorio en tu organización](/organizations/managing-organization-settings/restricting-repository-visibility-changes-in-your-organization)".

Te recomendamos revisar las siguientes consideraciones antes de que cambies la visibilidad de un repositorio.

{% ifversion ghes or ghae %}

{% warning %}

**Advertencia:** Los cambios en la visbilidad de un repositorio grande o en una red de repositorio podrían afectar a la integridad de los datos. Los cambios en la visibilidad también pueden tener efectos accidentales en las bifurcaciones. {% data variables.product.company_short %} recomienda lo siguiente antes de que cambies la visibilidad de una red de un repositorio.

- Espera a un periodo de actividad reducida en {% data variables.product.product_location %}.

- Contacta a tu {% ifversion ghes %}administrador de sitio{% elsif ghae %}propietario de empresa{% endif %} antes de proceder. Tu {% ifversion ghes %}administrador de sitio{% elsif ghae %}propietario de empresa{% endif %} puede contactar al {% data variables.contact.contact_ent_support %} para obtener más instrucciones.

{% endwarning %}

{% endif %}

### Convertir un repositorio en privado
{% ifversion fpt or ghes %}
* {% data variables.product.product_name %} separará las bifurcaciones públicas del repositorio público y las pondrá en una red nueva. Las bifurcaciones públicas no se hacen privadas.{% endif %}
* Si cambias la visibilidad de un repositorio de interna a privada, {% data variables.product.prodname_dotcom %} eliminará las bifurcaciones que pertenezcan a cualquiera de los usuarios sin acceso al repositorio que recientemente se hizo privado. {% ifversion fpt or ghes %}La visibilidad de cualquier bifurcación también cambiará a privada.{% elsif ghae %}Si el repositorio interno tiene cualquier bifurcación, la visibilidad de éstas ya será privada.{% endif %} Para obtener más información, consulta la sección "[¿Qué pasa con las bifurcaciones cuando un repositorio se borra o cambia su visibilidad?](/articles/what-happens-to-forks-when-a-repository-is-deleted-or-changes-visibility)"{% ifversion fpt %}
* Si utilizas {% data variables.product.prodname_free_user %} para cuentas de usuario o de organización, algunas características no estarán disponibles en el repositorio después de que cambies la visibilidad a privada. {% data reusables.gated-features.more-info %}{% endif %}
* Cualquier sitio de {% data variables.product.prodname_pages %} publicado se dejará de publicar automáticamente.{% ifversion fpt %} Si agregaste un dominio personalizado al sitio de {% data variables.product.prodname_pages %}, deberás eliminar o actualizar tus registros de DNS antes de que hagas al repositorio privado para evitar el riesgo de que alguien más tome el dominio. Para obtener más información, consulta la sección "[Administrar un dominio personalizado para tu sitio de {% data variables.product.prodname_pages %}](/articles/managing-a-custom-domain-for-your-github-pages-site)".{% endif %}{% ifversion fpt %}
* {% data variables.product.prodname_dotcom %} ya no incluirá el repositorio en el {% data variables.product.prodname_archive %}. Para obtener más información, consulta la sección "[Acerca de archivar el contenido y los datos en {% data variables.product.prodname_dotcom %}](/github/creating-cloning-and-archiving-repositories/about-archiving-content-and-data-on-github#about-the-github-archive-program)".{% endif %}{% ifversion fpt %}
* Las características de la {% data variables.product.prodname_GH_advanced_security %}, tales como el {% data variables.product.prodname_code_scanning %}, dejarán de funcionar a menos de que el repositorio pertenezca a una organización que sea parte de una empresa con una licencia para {% data variables.product.prodname_advanced_security %} y suficientes plazas disponibles. {% data reusables.advanced-security.more-info-ghas %}{% endif %}{% ifversion ghes %}
* El acceso anónimo de Git ya no está disponible. Para obtener más información, consulta la sección "[Habilitar el acceso de lectura anónima en Git para un repositorio](/enterprise/{{ currentVersion }}/user/articles/enabling-anonymous-git-read-access-for-a-repository)".{% endif %}

{% ifversion fpt or ghae or ghes %}

### Convertir un repositorio en interno

{% note %}

**Nota:** {% data reusables.gated-features.internal-repos %}

{% endnote %}

* Cualquier bifurcación del repositorio se mantendrá en la red del mismo y {% data variables.product.product_name %} mantendrá la relación entre el repositorio raíz y la bifurcación. Para obtener más información, consulta la sección "[¿Qué le sucede a las bifurcaciones cuando se elimina un repositorio o cuando cambia la visibilidad?](/articles/what-happens-to-forks-when-a-repository-is-deleted-or-changes-visibility)"

{% endif %}

{% ifversion fpt or ghes %}

### Convertir un repositorio en público

* {% data variables.product.product_name %} se deslindará de las bifurcaciones privadas y lasconvertirá en repositorios privados independientes. Para obtener más información, consulta la sección "[¿Qué sucede con las bifurcaciones cuando se borra un repositorio o cuando cambia su visibilidad?](/articles/what-happens-to-forks-when-a-repository-is-deleted-or-changes-visibility#changing-a-private-repository-to-a-public-repository)"{% ifversion fpt %}
* Si vas a convertir tu repositorio privado en uno público como parte de un movimiento hacia la creación de un proyecto de código abierto, consulta las [Guías de Código Abierto](http://opensource.guide) para encontrar tips ylineamientos útiles. También puedes tomar un curso gratuito sobre cómo administrar un proyecto de código abierto con [{% data variables.product.prodname_learning %}]({% data variables.product.prodname_learning_link %}). Una vez que tu repositorio es público, también puedes ver el perfil de la comunidad de tu repositorio para ver si tu proyecto cumple con las mejoras prácticas para los colaboradores de apoyo. Para obtener más información, consulta "[Ver el perfil de tu comunidad](/articles/viewing-your-community-profile)"
* El repositorio obtendrá acceso automático a las características de la {% data variables.product.prodname_GH_advanced_security %}.

Para obtener más información sobre cómo mejorar la seguridad del repositorio, consulta la sección "[Asegurar tu repositorio](/code-security/getting-started/securing-your-repository)".{% endif %}

{% endif %}

## Cambiar la visibilidad de un repositorio

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-settings %}
3. Debajo de "Zona de Peligro", a la derecha de "Cambiar la visibilidad del repositorio", da clic en **Cambiar la visibilidad**. ![Botón de cambiar la visibilidad](/assets/images/help/repository/repo-change-vis.png)
4. Selecciona una visibilidad.
{% ifversion fpt %}
   ![Diálogo de opciones para la visbilidad del repositorio](/assets/images/help/repository/repo-change-select.png){% else %}
![Dialog of options for repository visibility](/assets/images/enterprise/repos/repo-change-select.png){% endif %}
5. Para verificar que estás cambiando la visibilidad del repositorio correcto, teclea el nombre del repositorio para el cual quieres cambiar la visibilidad.
6. Da clic en **Entiendo, cambiar la visibilidad del repositorio**.
{% ifversion fpt %}
   ![Botón de confirmar cambio para la visibilidad de un repositorio](/assets/images/help/repository/repo-change-confirm.png){% else %}
![Confirm change of repository visibility button](/assets/images/enterprise/repos/repo-change-confirm.png){% endif %}


## Leer más
- "[About repositories](/repositories/creating-and-managing-repositories/about-repositories#about-repository-visibility)"
