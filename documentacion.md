Documentación de Taller: IaaS Local con Multipass
1. Descripción del Proyecto

Este proyecto consiste en el despliegue de un sistema distribuido utilizando Infraestructura como Servicio (IaaS) de manera local. Se han configurado tres máquinas virtuales independientes para separar las capas de datos, lógica y presentación, garantizando un entorno escalable y organizado.

2. Tecnologías Utilizadas

    Multipass: Orquestación de máquinas virtuales (Ubuntu 24.04).

    PostgreSQL: Motor de base de datos relacional.

    FastAPI: Framework de alto rendimiento para la construcción de la API.

    Streamlit: Framework para la creación del dashboard interactivo.

    GitHub: Control de versiones y despliegue de código.

    Python: Lenguaje base para el backend y la visualización.

3. Arquitectura del Sistema

La comunicación se realiza a través de una red virtual interna proporcionada por Multipass:

    Capa de Datos (base1): Servidor PostgreSQL en el puerto 5432.

    Capa de Lógica (api1): API FastAPI en el puerto 8000.

    Capa de Presentación (visualizacion1): Dashboard Streamlit en el puerto 8501.

4. Evidencias de Funcionamiento de las multiples entornos virtuales

A. Base de Datos (base1)

![Evidencia de la API](./img/base.png)

B. Api (Api1)

![Evidencia de la API](./img/api.png)

C. Visualizacion (visualizacion)

![Evidencia de la API](./img/visualizacion.png)

5. Evidencias de Funcionamiento

![Evidencia de la API](./img/nav.png)


6. Archivos ejemplo para configuracion

        base.py.example
        def obtener_config_db():
            return {
                "host": "DIRECCION_IP_BASE_DATOS",
                "dbname": "NOMBRE_DB",
                "user": "USUARIO",
                "password": "PASSWORD"
            }
        config.py.example
        def obtener_url_api():
            return "http://IP_DE_TU_API:8000/empleados"

Debido a que este proyecto sigue buenas prácticas de seguridad, los archivos que contienen credenciales e IPs específicas (base.py y config.py) han sido excluidos del control de versiones mediante .gitignore.

Para replicar este proyecto, el usuario debe:

    Localizar los archivos .example en cada carpeta.

    Copiar el archivo y renombrarlo eliminando la extensión .example (ej: de base.py.example a base.py).

    Editar los valores internos con las IPs de sus propias máquinas virtuales creadas en Multipass.


7.Gestión de Archivos de Configuración

Los archivos base.py (en la API) y config.py (en la Visualización) están incluidos en el .gitignore. Esto evita que IPs locales o credenciales privadas se filtren al repositorio.

Para replicar este proyecto, siga estos pasos:

    Localice las plantillas: En las carpetas api/ y visualizacion/ encontrará archivos terminados en .example.

    Cree sus archivos locales:

        En la carpeta api/, ejecute: cp base.py.example base.py

        En la carpeta visualizacion/, ejecute: cp config.py.example config.py

    Configure sus parámetros: Abra los nuevos archivos creados y edite las direcciones IP y credenciales según la configuración de sus propias máquinas virtuales de Multipass.

8. Resumen de archivos en el Git

Para que el docente pueda replicar, tu estructura de Git debe verse así ahora:

    api/

        main.py

        base.py (Oculto por gitignore)

        base.py.example (Visible en GitHub) ✅

    visualizacion/

        app.py

        config.py (Oculto por gitignore)

        config.py.example (Visible en GitHub) ✅
