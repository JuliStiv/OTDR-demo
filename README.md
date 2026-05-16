# OTDR-demo

Repositorio de pruebas para el desarrollo del proyecto de Reflectómetro Óptico en el Dominio del Tiempo (OTDR). Este espacio está destinado a la centralización de código para el ESP32, simulaciones, esquemáticos en KiCad y documentación.

## 1. Estructura del Repositorio

Para mantener el orden y evitar conflictos con los archivos de diseño, el repositorio se organiza bajo la siguiente estructura de directorios:

* **docs/**: Contiene la documentación técnica del proyecto, notas de diseño, especificaciones del sistema y el marco teórico necesario para el desarrollo.
* **pcb/**: Dedicado exclusivamente a los archivos de diseño electrónico. Dentro de esta carpeta, el subdirectorio `OTDR_test/` almacena los esquemáticos y placas de prueba preliminares desarrollados en KiCad.
* **README.md**: Archivo principal de presentación e instrucciones básicas de operación para el equipo.

## 2. Flujo de Trabajo con Git

Con el fin de garantizar la integridad del diseño de la PCB y del firmware, todos los integrantes del equipo deben adoptar de forma estricta el siguiente flujo de trabajo basado en ramas:

1. **Sincronizar la rama principal:** Antes de iniciar cualquier modificación local, en la rama principal, descarga los cambios más recientes del servidor remoto para evitar desajustes:
   ```bash
   git checkout main
   git pull origin main

2. **Crear una rama de trabajo independiente:** No realizar modificaciones de manera directa sobre la rama `main`. Habilitá siempre una rama específica que describa brevemente la tarea a resolver (por ejemplo, el desarrollo de un bloque del circuito o una función del firmware):
  ```bash
  git checkout -b rama-mi-tarea
  ```

3. **Registrar y confirmar modificaciones:** Una vez concluidos los cambios dentro de los directorios asignados, añade los archivos al área de preparación y consolida un commit local acompañado de un mensaje claro, conciso y descriptivo:
  ```bash
  git add .
  git commit -m "Añadir circuito de sensado preliminar en KiCad"
  ```

4. **Subir la rama:** Envía tus modificaciones locales a la plataforma para que queden disponibles en la nube:
  ```bash
  git push origin rama-mi-tarea
  ```

5. **Aperturea de pull request:** En la interfaz web del repositorio en GitHub y genera un Pull Request. Ningún cambio se incorporará de forma directa a la rama principal sin contar con la revisión previa y la aprobación de los demás miembros del equipo.

# Conflictos con KiCad
Debido a que las modificaciones sobre archivos de diseño electrónico de texto estructurado (`*.kicad_sch` y `*.kicad_pcb`) generan conflictos de fusión (merge conflicts) que resultan extremadamente difíciles de solucionar manualmente y que pueden corromper las placas, se establecen las siguientes reglas:

| Regla de Control | Descripción Técnica Operativa |
| :--- | :--- |
| **Edición Exclusiva** | Prohibido modificar el mismo archivo de KiCad de forma simultánea por dos integrantes. Coordinar la asignación de bloques del circuito antes de iniciar la edición. |
| **Aislamiento de Respaldos** | Los archivos temporales de bloqueo (`*.lck`) y las copias de seguridad (`*-bak`) autogeneradas por KiCad deben ser excluidas mediante el archivo de configuración `.gitignore`|
