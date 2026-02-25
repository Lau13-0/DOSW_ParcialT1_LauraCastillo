# DOSW_ParcialT1_LauraCastillo
###  Diagrama de contexto

![Diagrama de Contexto](DOSW-ParcialT1\docs\images/Diagrama%20de%20Contexto.png)

Figura: Diagrama de contexto del sistema (archivo: `docs/image/Diagrama de Contexto.png`)

### Patrones de diseño en el caso de estudio

- **Nombre del patrón:** Template Method

- **Tipo de patrón:** Comportamiento

**Justificación:** 
En el sistema SILABINFO, el proceso de reserva sigue una estructura general común para todos los tipos de recursos:

- Validar el tipo de usuario.
- Validar el tiempo máximo permitido.
- Validar disponibilidad.
- Validar condiciones específicas del recurso (capacidad, proyector, materia, etc.).
- Confirmar o rechazar la reserva.

El patrón Template Method permite definir en una clase abstracta el algoritmo general de validación de reserva y delegar ciertos pasos específicos a las subclases correspondientes (Salón, Oficina, Sala de Estudio, Equipo).

Asi se mantiene una estructura común para el proceso de reserva,se evita duplicación de código, se garantiza que todas las reservas sigan el mismo flujo lógico.

Se cumple el principio Open/Closed, permitiendo extender nuevos tipos de recursos sin modificar el algoritmo base.

Este patrón se aplicaría en el requerimiento funcional relacionado con la validación y confirmación de reservas según las reglas de cada recurso.

- **Nombre del patrón:** Factory Method

- **Tipo de patrón:** Patrón Creacional

**Justificación:** 
El sistema SILABINFO gestiona distintos tipos de recursos: salones, oficinas, salas de estudio y equipos. Aunque todos son recursos, cada uno tiene características y reglas propias.

Para evitar la creación directa de objetos mediante múltiples estructuras condicionales, se puede aplicar el patrón Factory Method, el cual delega la responsabilidad de creación de objetos a subclases especializadas.

Con este patron podemos:
- Reducir el acoplamiento entre el código cliente y las clases concretas.
- Facilitar la escalabilidad del sistema en caso de agregar nuevos tipos de recursos.
- Aplicar el principio Single Responsibility, separando la lógica de creación de la lógica de negocio.

El Factory Method se relaciona directamente con el requerimiento funcional que indica permitir la creación de reservas considerando las reglas específicas de cada tipo de recurso.

### Requerimientos del Sistema
A continuación, se presentan cinco requerimientos del sistema SILABINFO, clasificados en funcionales y no funcionales.

**Requerimientos Funcionales**
**RF1 – Crear reserva de recurso académico**

El sistema debe permitir a los usuarios (profesores, monitores y estudiantes) crear una reserva de un recurso académico (salón, oficina, sala de estudio o equipo), ingresando la información requerida según el tipo de recurso.

**Patrón asociado:** Factory Method
Este requerimiento utiliza el patrón Factory Method para crear dinámicamente el tipo de recurso correspondiente sin acoplar el código a clases concretas.

**RF2 – Validar reglas específicas según el tipo de recurso**

El sistema debe validar automáticamente las reglas de negocio asociadas al tipo de recurso antes de confirmar la reserva, tales como:

- Tiempo máximo permitido.
- Tipo de usuario autorizado.
- Capacidad del recurso.
- Existencia de la materia.
- Disponibilidad en la fecha y hora solicitada.

**Patrón asociado:** Template Method
Este requerimiento utiliza el patrón Template Method, ya que el proceso general de validación sigue una estructura común, pero cada tipo de recurso implementa reglas específicas dentro del algoritmo.

**RF3 – Confirmar o denegar la reserva**

El sistema debe notificar al usuario si la reserva fue confirmada o rechazada, indicando el motivo en caso de denegación (por ejemplo: tiempo excedido, recurso no disponible o usuario no autorizado).

**Requerimientos No Funcionales**
**RNF1 – Diseño responsive**

El sistema debe ser responsive, permitiendo su correcta visualización y funcionamiento en diferentes dispositivos (computadores, tablets y dispositivos móviles).

**RNF2 – Consistencia visual institucional**

El sistema debe mantener los colores institucionales del programa de Ingeniería de Sistemas y utilizar una tipografía legible para garantizar una experiencia de usuario adecuada.

### Diagrama de casos de uso y historias de usuario

RF1 – Crear reserva de recurso académico (Factory Method)

RF2 – Validar reglas específicas según el tipo de recurso (Template Method)

Ambos son el núcleo del sistema, porque sin creación y validación no existe el proceso de reserva.

**Diagrama de Casos de Uso:**

![Diagrama de Contexto](DOSW-ParcialT1\docs\images/Diagrama%20de%20casos%20de&Contexto.png)

**Historias de Usuario**
**Historia de Usuario 1 – Crear reserva de recurso**

**ID:** HU1
**Nombre:** Crear reserva de recurso académico

Como usuario del sistema (profesor, monitor o estudiante)
Quiero registrar una reserva de un recurso académico ingresando la información requerida
Para asegurar el uso del recurso en una fecha y hora específica.

**Criterios de aceptación:**

- El sistema debe permitir seleccionar el tipo de recurso.
- El sistema debe solicitar los datos requeridos según el tipo.
- El sistema debe crear el recurso correspondiente utilizando el patrón Factory Method.
- El sistema debe enviar la solicitud al proceso de validación.

**Historia de Usuario 2 – Validar reglas de reserva**

**ID:** HU2
**Nombre:** Validar reglas de negocio de la reserva

Como sistema SILABINFO
Quiero validar las reglas específicas según el tipo de recurso
Para confirmar o rechazar la reserva correctamente.

**Criterios de aceptación:**

- El sistema debe validar el tipo de usuario.
- Debe validar el tiempo máximo permitido.
- Debe validar capacidad del recurso.
- Debe validar disponibilidad.
- Debe validar existencia de materia cuando aplique.
- El proceso debe implementarse usando el patrón Template Method, manteniendo un flujo común de validación.

### Requerimientos del sistema
**1. Lista general de requerimientos**

El sistema SILABINFO tiene los siguientes requerimientos:

**1.1 Requerimientos funcionales**

El sistema de SILABINFO debe tener la capacidad de:

1. Permitir a profesores, monitores y estudiantes crear reservas de recursos académicos.

2. Validar automáticamente las reglas de negocio según el tipo de recurso.

3. Confirmar o denegar la reserva según el resultado de las validaciones.

**1.2 Requerimientos no funcionales**

1. El sistema de SILABINFO debe tener:

2. Diseño responsive adaptable a diferentes dispositivos.

3. Uso de colores institucionales y tipografía legible acorde al programa de Ingeniería de Sistemas.

**2. Diagramas de caso de uso**
**2.1 Requerimiento Funcional 1**
|Campo |Descripción|
|--------:|-------------|
|ID	|RF-01|
|Nombre del requerimiento	|Crear reserva de recurso académico|
|Descripción	|El sistema debe permitir a los usuarios (profesores, monitores y estudiantes) crear una reserva de un recurso académico ingresando la información requerida según el tipo de recurso.|
|Precondiciones	|Para que el sistema cumpla con este requerimiento, SILABINFO debe tener previamente registrados los recursos (salones, oficinas, salas de estudio y equipos). Además, debe estar disponible la integración con Enlace.|
|Actor	|Profesor, Monitor, Estudiante|
|Flujo principal	| 1. El actor selecciona el tipo de recurso que desea reservar.
2. El sistema solicita los datos requeridos según el tipo de recurso.
3. El actor ingresa la información solicitada.
4. El sistema crea la instancia del recurso utilizando el patrón Factory Method.
5. El sistema envía la solicitud al proceso de validación.|
|Diagrama de caso de uso|![Diagrama de Contexto](DOSW-ParcialT1\docs\images/caso1.png)|
|Poscondiciones|	Se espera como resultado que la solicitud de reserva quede registrada y enviada al proceso de validación.|

**2.2 Requerimiento Funcional 2**
|Campo |	Descripción|
|--------:|-------------|
|ID	 |RF-02 
|Nombre del requerimiento	|Validar reglas de negocio de la reserva
Descripción	El sistema debe validar automáticamente las reglas específicas del tipo de recurso antes de confirmar o rechazar la reserva.|
|Precondiciones|	Para que el sistema cumpla con este requerimiento, debe existir una solicitud de reserva creada (RF-01) y los datos del usuario deben poder validarse contra Enlace.|
|Actor	|Sistema SILABINFO (interactuando con Enlace)|
|Flujo principal|	1. El sistema recibe la solicitud de reserva.
2. El sistema valida el tipo de usuario (profesor, monitor o estudiante).
3. El sistema valida el tiempo máximo permitido.
4. El sistema valida capacidad y disponibilidad del recurso.
5. El sistema valida existencia de materia cuando aplique.
6. El sistema confirma o rechaza la reserva según el resultado de las validaciones, siguiendo la estructura del patrón Template Method.|
|Diagrama de contexto|![Diagrama de Contexto](DOSW-ParcialT1\docs\images/caso2.png)|
|Poscondiciones	|Se espera como resultado que la reserva quede confirmada o rechazada con su respectiva notificación al usuario.|

### Epica - Historia de usuario - Tareas

**Requerimiento seleccionado**
RF-02 – Validar reglas de negocio de la reserva

**Patrón aplicado:** Template Method

**Épica**

**Nombre:** Permitir que un estudiante pueda reservar un salón de clase

**Descripción:**
Como parte de la mejora del sistema SILABINFO, se requiere habilitar el proceso para que un estudiante pueda solicitar la reserva de un salón de clase, garantizando que el sistema valide automáticamente todas las reglas de negocio antes de confirmar o rechazar la solicitud.

**Historia de Usuario**

**ID:** HU-01
**Nombre:** Solicitud de reserva de salón por estudiante

Como estudiante
Quiero solicitar la reserva de un salón de clase
Para utilizarlo en una fecha y hora determinada.

**Criterios de aceptación:**

**El estudiante debe ingresar:**

- Nombre del salón.
- Fecha y hora inicial.
- Tiempo de la reserva.
- Número de puestos requeridos.
- Si requiere proyector o computadores.
- El sistema debe validar:
- Si el estudiante está autorizado para reservar ese recurso.
- Si el tiempo solicitado no supera el máximo permitido.
- Si el salón tiene la capacidad suficiente.
- Si el salón está disponible.
- El sistema debe confirmar o rechazar la reserva.

**Tareas Técnicas**
**Tarea 1:** 
- Ajustar reglas de autorización
- Implementar validación del tipo de usuario.
- Verificar si el estudiante tiene permisos para reservar salones.
- Conectar con Enlace para validar información del estudiante.

**Tarea 2:**
- Implementar validación usando Template Method
- Crear clase abstracta ValidadorReserva.
- Definir el método plantilla validarReserva().
- Implementar clase concreta ValidadorSalon.
- Programar validaciones específicas:
- Capacidad.
- Tiempo máximo.
- Disponibilidad.
- Requerimientos de proyector o computadores.

**Tarea 3:** 
- Integrar validación con el flujo de reserva
- Conectar la solicitud del estudiante con el validador.
- Si alguna validación falla, generar mensaje de rechazo.
- Si todas las validaciones pasan, confirmar la reserva.

**Tarea 4:** 
- Pruebas del flujo completo
- Probar caso exitoso.
- Probar caso donde el salón esté ocupado.
- Probar caso donde el tiempo exceda el máximo permitido.
- Probar caso donde el estudiante no esté autorizado.
- Relación con el patrón Template Method

Se aplica el patrón Template Method porque:

- Existe un flujo general para validar reservas.
- Las reglas específicas del salón se implementan en una subclase.
- Se garantiza consistencia en el proceso.
- Se evita duplicación de código.

**Nota importante:** Esta claro en el enunciado que los salones solo pueden ser reservados por profesores o monitores, pero esta sera una opcion en donde se busque optimizar los salones que no son usados por profesores y monitores, ya que muchos estudiantes se sienten mejor estudiando ellos o su grupo en un salon. 
