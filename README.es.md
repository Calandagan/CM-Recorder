# CM Recorder · Mihono Studios

**Herramienta gratuita desarrollada por [Mihono Studios](https://mihonostudios.com) para la comunidad de Umamusume.**

Graba y consulta carreras de **Steam Global**: Room Match, grupos/finales de
Champions Meeting y Practice. El código fuente se mantiene privado.

## Descargar y empezar

**Versión 0.3.0 preliminar para Windows x64.** [Descargar ZIP completo](https://github.com/Calandagan/CM-Recorder/releases/download/v0.3.0-beta.1/CMRecorder-0.3.0-Global-Test-20261107-173013-092.zip).

1. Extrae toda la carpeta fuera del directorio del juego. No necesitas herramientas de desarrollo ni otra aplicación de captura.
2. Cierra otras aplicaciones de grabación de carreras que puedan ocupar la conexión de captura.
3. Abre **Start CM Recorder.cmd** o **CMRecorder.exe**.
4. Revisa **Capture settings → Global capture setup**. Si reconoce una captura
   compatible y verificada, la reutiliza sin modificarla. Si falta, cierra Global y usa **Install capture**.
5. Activa **Record races**, abre Global desde Steam y espera **Global capture connected**.
6. Después de la carrera, usa **Inspect** o **Export recordings → Download ZIP**.

La WebUI está en **http://127.0.0.1:8078/**. Conserva la carpeta portable completa.
**Open Offline.cmd** permite consultar lo grabado sin conectarse al juego.

La compilación pasó las pruebas automatizadas y comprobaciones offline del
ejecutable. No consta todavía la aceptación de este paquete concreto en un PC
limpio ni una prueba completa de captura en el juego. Se publica como pre-release.

## Funciones

- Resultados y detalles de corredoras, retratos e iconos disponibles.
- Filtros de habilidades de aceleración, velocidad, pasivas verdes, recuperación, debuff y otras.
- Activaciones registradas, datos de replay disponibles y estadísticas por circuito.
- **Skill activation consistency**: menor frecuencia observada primero, mínimo de
  participaciones, propias/todas e inclusión opcional de pasivas verdes.
- Explicaciones conservadoras: incompatibilidad con requisitos del catálogo actual
  cuando hay evidencia suficiente; motivo no confirmado en los demás casos.
- Exportación de datos para análisis y reproductores independientes.

Una ausencia registrada no demuestra un fallo de probabilidad. Las muestras pequeñas
se señalan y las observaciones desconocidas se excluyen del porcentaje.

## Datos, licencia y ayuda

Un componente de captura se carga dentro del juego y entrega los datos de carrera
a un grabador local. El navegador muestra esos datos desde tu propio PC: no es una
cuenta web ni una grabación de pantalla. Las grabaciones se guardan en tu PC,
sin subida automática. Conservar nombres rivales
es opcional; revisa cualquier export antes de compartirlo. JP y DMM no están soportados.
Los archivos locales y ZIP exportados no están cifrados por la aplicación. El
ejecutable actual no tiene firma digital. Los controles del panel local ayudan
frente a peticiones de otras páginas, pero no protegen de malware que ya tenga
acceso a tu cuenta de Windows. No hace falta abrir puertos del router ni desactivar
el antivirus. Comprueba la descarga y revisa cualquier alerta antes de ejecutarla.

La instalación nueva añade componentes propios de captura con el juego cerrado;
no sustituye el ejecutable original. El programa no envía inputs ni acelera el juego.

Descarga y uso gratuitos bajo [LICENSE.txt](LICENSE.txt), de carácter propietario.
Los componentes de terceros conservan sus licencias. El programa no se apropia de
tus grabaciones ni prohíbe herramientas independientes por leer su formato.
Proyecto no oficial y sin afiliación ni respaldo de Cygames.

Documentación técnica y guías en inglés:

- [Instalación, actualización y desinstalación](docs/GETTING_STARTED.md)
- [Solución de problemas](docs/TROUBLESHOOTING.md)
- [Cómo funciona la herramienta](docs/HOW_IT_WORKS.md)
- [Privacidad y datos locales](docs/PRIVACY.md)
- [Ciberseguridad, permisos y límites](docs/SECURITY.md)
- [Consistencia de habilidades](docs/SKILL_CONSISTENCY.md)
- [Formato de exportaciones](docs/RECORDING_FORMAT.md)
- [Novedades](CHANGELOG.md)

[Reportar un problema](https://github.com/Calandagan/CM-Recorder/issues/new/choose) · [Web oficial](https://mihonostudios.com)
