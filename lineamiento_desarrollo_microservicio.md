# 📌 **Índice - Lineamientos de Desarrollo de Microservicios**

## 1⃣ Introducción  
- **1.1** Propósito de este documento  
- **1.2** Alcance y objetivos  
- **1.3** Normas generales de nomenclatura y estilo  

## 2⃣ Principios de Desarrollo  
- **2.1** Aplicación de la Arquitectura Hexagonal (Ports & Adapters)  
- **2.2** Uso de Domain-Driven Design (DDD) en el modelado de negocio  
- **2.3** Implementación de Event-Driven Architecture (EDA) con Kafka  
- **2.4** Desacoplamiento y modularidad en microservicios  
- **2.5** Gobernanza y aprobación de implementaciones  

## 3⃣ Organización de los Microservicios  
- **3.1** Tipos de microservicios y sus responsabilidades  
  - **3.1.1** Microservicios Core (CRUD y eventos)  
  - **3.1.2** Microservicios de Orquestación  
  - **3.1.3** Microservicios de Integración (APIs externas)  
  - **3.1.4** Microservicios de Soporte (autenticación, logs, correos)  
- **3.2** Comunicación entre microservicios (Eventos vs. APIs REST)  
- **3.3** Versionado y ciclo de vida de los microservicios  

## 4⃣ Nomenclatura y Convenciones de Código  
- **4.1** Estándares de nomenclatura para microservicios  
- **4.2** Convenciones en nombres de clases, métodos y variables  
- **4.3** Estándares de nombres en endpoints y rutas API  
- **4.4** Convenciones para nombres de eventos en Kafka  
- **4.5** Nomenclatura de DTOs y contratos de servicio  

## 5⃣ Tipos de Respuestas y Manejo de Errores  
- **5.1** Formato estándar de respuestas  
- **5.2** Codificación de errores y mensajes  
- **5.3** Tipos de errores y estructura de respuesta  
  - **5.3.1** Errores de validación (`400 BAD REQUEST`)  
  - **5.3.2** Errores de autenticación (`401 UNAUTHORIZED`)  
  - **5.3.3** Errores de autorización (`403 FORBIDDEN`)  
  - **5.3.4** Recurso no encontrado (`404 NOT FOUND`)  
  - **5.3.5** Errores del servidor (`500 INTERNAL SERVER ERROR`)  
- **5.4** Implementación de middleware global para manejo de errores  
- **5.5** Registro de errores en logs y monitoreo  
- **5.6** Envío Asíncrono de Logs de Auditoría  

## 6⃣ Contratos de Servicios y API Design  
- **6.1** Definición de contratos antes de la implementación  
- **6.2** Uso obligatorio de Swagger/OpenAPI para documentar servicios  
- **6.3** Proceso de aprobación del contrato antes del desarrollo  
- **6.4** Contratos de servicios por tipo de microservicio  
  - **6.4.1** Contrato para Microservicios Core  
  - **6.4.2** Contrato para Microservicios de Orquestación  
  - **6.4.3** Contrato para Microservicios de Integración  
  - **6.4.4** Contrato para Microservicios de Soporte  
- **6.5** Exposición de la documentación mediante una URL pública  
  - **6.5.1** Cada servicio debe exponer su contrato en `/api-docs` con Swagger  
  - **6.5.2** La URL debe ser accesible dentro del ecosistema de microservicios  
  - **6.5.3** Todos los contratos deben versionarse y mantenerse actualizados  
- **6.6** Estandarización de endpoints y rutas  
- **6.7** Políticas de autenticación y autorización en APIs  

## 7⃣ Desarrollo y Estructura de Código  
- **7.1** Estructura de carpetas y organización del código  
- **7.2** Separación de capas dentro del microservicio  
- **7.3** Uso de DTOs y validaciones con Class Validator  
- **7.4** Implementación de pruebas unitarias y de integración  
- **7.5** Seguridad en la manipulación de datos  

## 8⃣ Seguridad y Gobernanza de Microservicios  
- **8.1** Políticas de autenticación y autorización (OAuth2, JWT)  
- **8.2** Seguridad en la comunicación entre microservicios  
- **8.3** Uso de API Gateway para control de acceso  
- **8.4** Implementación de CORS y Rate Limiting  
- **8.5** Encriptación de datos sensibles  
- **8.6** Restricción de Mensajes de Error Expuestos  

## 9⃣ Estrategias de Observabilidad y Monitoreo  
- **9.1** Logging estructurado y centralizado  
- **9.2** Implementación de métricas con Prometheus y Grafana  
- **9.3** Uso de tracing distribuido con Jaeger  
- **9.4** Alertas y monitoreo en tiempo real (incluye auditoría de errores críticos con Kafka)  

## 🔠 Despliegue y CI/CD  
- **10.1** Contenerización con Docker  
- **10.2** Orquestación con Kubernetes  
- **10.3** Pipelines de CI/CD con validaciones automáticas  
- **10.4** Estrategias de rollback y actualización  

## 1️⃣1️ Gobernanza por IA en Microservicios  
- **11.1** Validación automática de contratos y código antes de implementación  
- **11.2** Análisis de patrones y detección de anomalías  
- **11.3** Sugerencias de optimización y refactorización  
- **11.4** Registro de cambios estructurales y mejoras  
- **11.5** Envío Asíncrono de Logs y Auditoría  

---

### 📌 **Actualización Clave:**  
👉 **Cada microservicio debe exponer su contrato de API y documentación en una URL accesible (`/api-docs`).**  
👉 **Se debe solicitar aprobación del contrato antes de la implementación.**  
👉 **Cada contrato debe versionarse para evitar rupturas en integraciones.**  


---

# 💼 **1️⃣ Introducción**

## 🔹 **1.1 Propósito de este documento**
Este documento establece los lineamientos para el desarrollo de microservicios dentro de la arquitectura definida, garantizando estandarización, calidad, seguridad y gobernanza en el ecosistema de servicios.  
Los microservicios deben cumplir con los principios de **Arquitectura Hexagonal (Ports & Adapters), Domain-Driven Design (DDD) y Event-Driven Architecture (EDA)**, asegurando modularidad, escalabilidad y bajo acoplamiento.  

Este documento servirá como referencia para la **Inteligencia Artificial (IA)** encargada de gobernar la arquitectura, asegurando que cada implementación sea validada antes de su desarrollo.
Toda documentación y creacion de todo tipo de objetos se realizara bajo el idioma español
---

## 🔹 **1.2 Alcance y Objetivos**
👉 Definir **estándares** y **mejores prácticas** para el desarrollo de microservicios.  
👉 Establecer **políticas de validación y aprobación** antes de la implementación.  
👉 Garantizar la **seguridad, modularidad y escalabilidad** de los servicios.  
👉 Estandarizar el **formato de contratos y documentación** de cada servicio.  
👉 Implementar una **gobernanza centralizada** mediante IA para validar la arquitectura.  

🔍 **Alcance:**  
✔ Aplica a **todos los microservicios** dentro del ecosistema.  
✔ Define las **reglas para contratos de API, manejo de errores y documentación**.  
✔ Especifica los **lineamientos de despliegue y monitoreo**.  

---

## 🔹 **1.3 Normas Generales de Nomenclatura y Estilo**

📚 **Nombres de Microservicios:**  
- Deben seguir el formato `ms_<nombre_del_servicio>`, por ejemplo: `ms_pedidos`, `ms_autenticacion`.  
- Los servicios deben ser **claros, descriptivos y alineados con el dominio de negocio**.  

📚 **Estructura de Endpoints:**  
- Los endpoints deben seguir el estándar RESTful con rutas en **kebab-case**.  
- Ejemplo:  
  ```plaintext
  GET /api/v1/pedidos/{pedido_id}
  POST /api/v1/pedidos
  PUT /api/v1/pedidos/{pedido_id}
  DELETE /api/v1/pedidos/{pedido_id}
  ```

📚 **Nombres de Variables y Métodos:**  
- Se debe utilizar **camelCase** para variables y métodos en TypeScript.  
- Se debe utilizar **PascalCase** para nombres de clases y controladores.  

📚 **Nombres de Eventos Kafka:**  
- Los eventos deben nombrarse en **kebab-case**.  
- Ejemplo: `pedido-creado`, `usuario-registrado`, `factura-generada`.  

📚 **Documentación y Contratos:**  
🔹 **Cada microservicio debe exponer su contrato de API en `/api-docs` utilizando Swagger**.  
🔹 **Todos los contratos deben pasar por una aprobación antes de su implementación**.  
🔹 **Cada versión de API debe documentarse para evitar rupturas en integraciones**.  

📚 **Gobernanza por IA:**  
🚀 **La IA debe validar que cada implementación cumpla con estos lineamientos antes del desarrollo**.  

---
## 2️⃣ **Principios de Desarrollo**

### 🔹 **2.1 Aplicación de la Arquitectura Hexagonal (Ports & Adapters)**
La arquitectura hexagonal permite desarrollar microservicios altamente desacoplados y modulares. Se basa en la separación entre la lógica de negocio y sus interfaces externas, garantizando la flexibilidad y la independencia tecnológica.

📌 **Principios clave:**
- La lógica de negocio se encapsula dentro de los **casos de uso** y **entidades de dominio**.
- Las interacciones con bases de datos, APIs externas y sistemas de mensajería se manejan a través de **adaptadores**.
- Se utilizan **puertos (interfaces)** para definir los puntos de entrada y salida del microservicio.
- Facilita la prueba de unidades sin depender de la infraestructura externa.

✅ **Beneficios:**
✔ Separación de responsabilidades y mayor mantenibilidad.
✔ Flexibilidad para cambiar tecnologías sin afectar la lógica central.
✔ Código más modular y reutilizable.

---

### 🔹 **2.2 Uso de Domain-Driven Design (DDD) en el modelado de negocio**
Domain-Driven Design (DDD) permite diseñar microservicios basados en modelos de negocio sólidos, alineados con la realidad operativa de la empresa.

📌 **Principios clave:**
- **Entidades**: Representan objetos con identidad única dentro del dominio.
- **Value Objects**: Representan datos inmutables sin identidad propia.
- **Aggregates**: Definen límites en la manipulación de entidades relacionadas.
- **Repositorios**: Controlan la persistencia y recuperación de objetos de dominio.
- **Servicios de dominio**: Contienen lógica que no pertenece a una entidad específica.
- **Eventos de dominio**: Permiten la comunicación entre servicios sin acoplamiento directo.

✅ **Beneficios:**
✔ Código alineado con el negocio, facilitando su comprensión.
✔ Modelo flexible y fácilmente extensible.
✔ Reducción de dependencias entre módulos.

---

### 🔹 **2.3 Implementación de Event-Driven Architecture (EDA) con Kafka**
La arquitectura basada en eventos permite la comunicación asíncrona entre microservicios, asegurando la escalabilidad y resiliencia del sistema.

📌 **Principios clave:**
- Los microservicios se comunican mediante **eventos en Kafka** en lugar de llamadas directas.
- Cada evento tiene un esquema definido para garantizar la compatibilidad.
- Se implementa **event sourcing** cuando se requiere trazabilidad completa de cambios.
- Se utilizan **topics** organizados por dominio para segmentar eventos.

✅ **Beneficios:**
✔ Desacoplamiento total entre microservicios.
✔ Mayor capacidad de escalabilidad horizontal.
✔ Mejor tolerancia a fallos en la comunicación.
✔ Facilita la auditoría y el monitoreo del sistema.

---

### 🔹 **2.4 Desacoplamiento y Modularidad en Microservicios**
El sistema debe garantizar que cada microservicio sea independiente, modular y fácilmente reemplazable.

📌 **Principios clave:**
- Los microservicios deben **tener una única responsabilidad** (Single Responsibility Principle - SRP).
- La comunicación entre servicios debe ser asíncrona mediante eventos siempre que sea posible.
- La lógica de negocio no debe depender de detalles de implementación específicos.
- Cada microservicio debe contar con **su propio almacenamiento de datos**, evitando dependencias directas entre bases de datos.
- Se deben implementar **interfaces bien definidas** para la interacción con otros sistemas.

✅ **Beneficios:**
✔ Facilita el mantenimiento y la evolución del sistema.
✔ Reducción del impacto de cambios en otros servicios.
✔ Mejora el rendimiento mediante el escalado independiente.

---

### 🔹 **2.5 Gobernanza y Aprobación de Implementaciones**
Para garantizar la calidad del sistema, toda nueva implementación debe seguir un proceso de validación y aprobación.

📌 **Principios clave:**
- **Antes de desarrollar un microservicio, se debe definir y aprobar su contrato de API en Swagger/OpenAPI.**
- **Cada nuevo servicio o modificación estructural debe ser aprobado por el Comité de Arquitectura.**
- **Toda nueva funcionalidad debe cumplir con los lineamientos establecidos en esta documentación.**
- **La IA validará automáticamente si la implementación sigue las reglas antes de su despliegue.**
- **Cualquier cambio fuera del estándar deberá ser documentado y aprobado antes de su implementación.**

✅ **Beneficios:**
✔ Garantiza que las implementaciones sigan la arquitectura definida.
✔ Evita discrepancias en el diseño y desarrollo de servicios.
✔ Reduce errores y problemas de integración.
✔ Mantiene la documentación actualizada y alineada con el sistema.

📌 **Importante:**
🔹 **Los desarrolladores no pueden proceder con una implementación sin la aprobación previa del contrato del servicio.**
🔹 **Cada cambio en la arquitectura debe ser registrado y reflejado en la documentación oficial.**

## 3️⃣ Organización de los Microservicios

### 3.1 Tipos de microservicios y sus responsabilidades
Los microservicios en la arquitectura se clasifican en diferentes tipos según su función y su relación con el ecosistema.

#### 3.1.1 Microservicios Core (CRUD y eventos)
Estos microservicios representan las entidades fundamentales del sistema y se encargan de:
- Gestionar las operaciones **CRUD** sobre las entidades de negocio.
- Emitir eventos a otros microservicios cuando ocurren cambios relevantes en su dominio.
- Exponer API REST con endpoints bien definidos y documentados en Swagger.
- Mantener la integridad de los datos a través de validaciones y reglas de negocio.
- Implementar repositorios con **TypeORM** para interactuar con **PostgreSQL**.

#### 3.1.2 Microservicios de Orquestación
Estos microservicios se encargan de coordinar el flujo de trabajo entre múltiples microservicios. Sus principales responsabilidades incluyen:
- Orquestar procesos que involucran varias entidades de negocio.
- Implementar patrones como **Saga** para garantizar la consistencia en transacciones distribuidas.
- Controlar el flujo de eventos y las dependencias entre servicios.
- Garantizar que los eventos sean procesados de manera idempotente para evitar inconsistencias.

#### 3.1.3 Microservicios de Integración (APIs externas)
Estos microservicios gestionan la interacción con sistemas externos, asegurando que los datos sean transformados y adaptados correctamente. Sus principales funciones incluyen:
- Consumir APIs de terceros mediante clientes HTTP seguros.
- Implementar caché para evitar consultas innecesarias a servicios externos.
- Manejar autenticación y autorización con OAuth2, API Keys o JWT.
- Adaptar los datos de entrada y salida para mantener coherencia con el sistema interno.

#### 3.1.4 Microservicios de Soporte (autenticación, logs, correos)
Estos servicios proporcionan funcionalidades auxiliares y no representan entidades de negocio. Entre sus principales responsabilidades están:
- Servicio de **autenticación y autorización** con gestión de usuarios y roles.
- Servicio de **logging centralizado**, recolectando logs estructurados para monitoreo y auditoría.
- Servicio de **notificaciones**, permitiendo el envío de correos, SMS o notificaciones push.
- Servicio de **configuración centralizada**, gestionando variables y configuraciones para los demás microservicios.

### 3.2 Comunicación entre microservicios (Eventos vs. APIs REST)
La comunicación entre microservicios puede realizarse de dos formas principales:

- **APIs REST:** Se utiliza para operaciones sincrónicas, en las que un microservicio necesita obtener datos o realizar acciones inmediatas sobre otro microservicio.
  - Ejemplo: Consultar información de un usuario a través de un endpoint.

- **Eventos con Kafka:** Se usa para interacciones asincrónicas, donde un microservicio emite un evento sin necesidad de esperar una respuesta inmediata.
  - Ejemplo: Cuando se crea una orden, se emite un evento que otros microservicios pueden procesar sin afectar el tiempo de respuesta.

Reglas para la comunicación:
- Siempre que sea posible, se deben **priorizar eventos** en lugar de llamadas directas a APIs REST.
- Los eventos deben estar bien definidos y documentados en **contratos** dentro del repositorio.
- La estructura del payload de los eventos debe mantenerse estable y versionarse si es necesario.
- Los microservicios deben manejar correctamente la **reintentos y fallos en la comunicación** para garantizar confiabilidad.

### 3.3 Versionado y ciclo de vida de los microservicios
El versionado de microservicios es crucial para evitar rupturas en el ecosistema. Se aplican las siguientes reglas:

- Se sigue el esquema **SemVer (Semantic Versioning)** para versionar APIs:
  - **v1.0.0**: Primera versión estable.
  - **v1.1.0**: Nueva funcionalidad sin cambios disruptivos.
  - **v2.0.0**: Cambio mayor que rompe compatibilidad con versiones anteriores.
- Cada API debe exponer su versión en la ruta (`/api/v1/resource`).
- Los cambios en el esquema de eventos también deben versionarse y documentarse en Swagger/OpenAPI.
- Todo cambio en la estructura de la API debe ser aprobado antes de su implementación.
- Se recomienda tener pruebas de regresión antes de actualizar una versión de microservicio en producción.

# ✨ **4️⃣ Nomenclatura y Convenciones de Código**

La nomenclatura de los microservicios y sus componentes debe seguir un estándar claro y coherente para garantizar la mantenibilidad, escalabilidad y entendimiento del sistema.

---

## ✨ **4.1 Estándares de Nomenclatura para Microservicios**

Cada microservicio debe seguir la siguiente convención de nombres según su tipo y aplicación:

### 🔹 **Formato General:**
`<tipo_servicio>-<nombre_negocio>-<nombre_aplicacion>`

### 🔹 **Ejemplo de Aplicaciones:**
- `sigeszeus`: Aplicación principal de gestión
- `zeuscommerce`: Aplicación de comercio electrónico
- `zeusauth`: Servicio de autenticación centralizado

### 🔹 **Ejemplos de Nomenclatura Aplicada:**
- **Microservicios Core:**
  - `core-pedidos-sigeszeus`
  - `core-clientes-zeuscommerce`
- **Microservicios de Orquestación:**
  - `orq-facturacion-sigeszeus`
  - `orq-pagos-zeuscommerce`
- **Microservicios de Integración:**
  - `int-reniec-sigeszeus`
  - `int-pasarela-zeuscommerce`
- **Microservicios de Soporte:**
  - `sup-logs-zeusauth`
  - `sup-notificaciones-sigeszeus`

---

## ✨ **4.2 Convenciones en Nombres de Clases, Métodos y Variables**

### **4.2.1 Clases y Archivos**
- **Clases:** `PascalCase`
  - Ejemplo: `PedidoService.ts`, `UsuarioController.ts`
- **Interfaces:** Prefijo con `I` y en `PascalCase`.
  - Ejemplo: `IPedidoRepository.ts`
- **Archivos de configuración:** `kebab-case`.
  - Ejemplo: `database-config.ts`, `auth-middleware.ts`

### **4.2.2 Métodos y Variables**
- **Métodos:** `camelCase`, con verbos que indiquen la acción.
  - Ejemplo: `obtenerPedidos()`, `crearUsuario()`
- **Variables:** `camelCase` para variables locales y `SCREAMING_SNAKE_CASE` para constantes.
  - Ejemplo:
    ```typescript
    const MAX_RETRIES = 3;
    let totalPedidos = 10;
    ```

---

## ✨ **4.3 Estándares de Nombres en Endpoints y Rutas API**

Los endpoints deben seguir la estructura REST y usar nombres en **plural**.

- **Recursos principales:** `/api/<nombre_recurso>`
  - Ejemplo: `/api/pedidos`, `/api/usuarios`
- **Acciones específicas:** `/api/<nombre_recurso>/<accion>`
  - Ejemplo: `/api/pedidos/generar-factura`
- **Uso de versionado:** Prefijo con `v` y número.
  - Ejemplo: `/api/v1/pedidos`
- **Ejemplo de endpoints bien estructurados:**
  - `GET /api/v1/usuarios`
  - `POST /api/v1/usuarios`
  - `PUT /api/v1/usuarios/{id}`
  - `DELETE /api/v1/usuarios/{id}` (eliminación lógica)

---

## ✨ **4.4 Convenciones para Nombres de Eventos en Kafka**

Los eventos de Kafka deben seguir la estructura **`<sujeto>.<accion>`** y estar en `kebab-case`.

- **Formato general:** `<origen>.<accion>`
- **Ejemplos:**
  - `pedido.creado`
  - `usuario.autenticado`
  - `pago.procesado`

Los nombres de los **topics de Kafka** deben incluir el contexto del dominio:
- `core.pedidos.creado`
- `orq.facturacion.completada`
- `int.sunat.factura-enviada`

---

## ✨ **4.5 Nomenclatura de DTOs y Contratos de Servicio**

Los DTOs deben seguir un esquema de nombres claro para diferenciar peticiones y respuestas.

- **Formato:** `<NombreAccion><TipoObjeto>Dto`
- **Ejemplos:**
  - `CrearPedidoDto`
  - `ActualizarUsuarioDto`
  - `RespuestaPagoDto`

Cada contrato de servicio debe documentarse en Swagger y exponerse en `/api-docs` dentro del microservicio.

---

### 📌 **Resumen de Buenas Prácticas:**
✅ Los nombres de microservicios deben reflejar su rol (`core`, `orq`, `int`, `sup`).
✅ Las clases deben nombrarse en `PascalCase`.
✅ Los métodos y variables deben seguir `camelCase`.
✅ Las rutas API deben ser en plural y versionadas.
✅ Los eventos Kafka deben ser en `kebab-case` y reflejar su acción.
✅ Los DTOs deben tener nombres descriptivos según la acción.

---
# ➜ **5 Tipos de Respuestas y Manejo de Errores**

## ⭐ **5.1 Formato Estándar de Respuestas**

Todas las respuestas de los microservicios deben seguir una estructura estandarizada con los siguientes elementos:

```json
{
  "estado": {
    "exito": true,
    "codigoHttp": 200,
    "mensaje": "Exito",
    "idTransaction": 12322321321784821
  },
  "dato": {
    "resultado": {
      "id": 123,
      "nombre": "Juan Pérez",
      "edad": 30
    }
  },
  "error": []
}
```

### **Estructura de la Respuesta:**
- **estado:** Contiene la información sobre el resultado de la operación.
- **dato:** Contiene el objeto resultado cuando la operación es exitosa.
- **error:** Lista de errores cuando la operación falla.

---

## ⭐ **5.2 Codificación de Errores y Mensajes**

Cada error debe incluir un **código estandarizado** y un mensaje descriptivo. Ejemplo:

```json
"error": [
  {
    "codigo": "campoRequerido",
    "mensaje": "El campo 'correoElectronico' es obligatorio."
  }
]
```

Los **códigos de error** deben seguir el formato `camelCase` y describir la causa del error de manera clara.

---

## ⭐ **5.3 Tipos de Errores y Estructura de Respuesta**

### **5.3.1 Errores de Validación (`400 BAD REQUEST`)**
```json
{
  "status": {
    "exito": false,
    "codigoHttp": 400,
    "mensaje": "Error en validaciones",
    "idTransaction": 12322321321784821
  },
  "dato": {
    "resultado": null
  },
  "error": [
    {
      "codigo": "campoRequerido",
      "mensaje": "El campo 'email' es obligatorio."
    }
  ]
}
```

### **5.3.2 Errores de Autenticación (`401 UNAUTHORIZED`)**
```json
{
  "status": {
    "exito": false,
    "codigoHttp": 401,
    "mensaje": "Error de autenticación",
    "idTransaction": 12322321321784821
  },
  "dato": {
    "resultado": null
  },
  "error": [
    {
      "codigo": "credencialesInvalidas",
      "mensaje": "El usuario o contraseña son incorrectos."
    }
  ]
}
```

### **5.3.3 Errores de Autorización (`403 FORBIDDEN`)**
```json
{
  "status": {
    "exito": false,
    "codigoHttp": 403,
    "mensaje": "Error de autorización",
    "idTransaction": 12322321321784821
  },
  "dato": {
    "resultado": null
  },
  "error": [
    {
      "codigo": "accesoDenegado",
      "mensaje": "No tienes permisos para acceder a este recurso."
    }
  ]
}
```

### **5.3.4 Recurso No Encontrado (`404 NOT FOUND`)**
```json
{
  "status": {
    "exito": false,
    "codigoHttp": 404,
    "mensaje": "Recurso no encontrado",
    "idTransaction": 12322321321784821
  },
  "dato": {
    "resultado": null
  },
  "error": [
    {
      "codigo": "recursoNoEncontrado",
      "mensaje": "El recurso solicitado no existe."
    }
  ]
}
```

### **5.3.5 Errores del Servidor (`500 INTERNAL SERVER ERROR`)**
```json
{
  "status": {
    "codigoHttp": 500,
    "mensaje": "Ocurrió un error inesperado. Por favor, inténtalo de nuevo más tarde.",
    "idTransaction": 12322321321784821
  },
  "dato": {
    "resultado": null
  },
  "error": [
    {
      "codigo": "errorTecnico",
      "mensaje": "Por favor, contacta con el soporte e indica el ID de la transacción."
    }
  ]
}
```

---

## ⭐ **5.4 Implementación de Middleware Global para Manejo de Errores**
Todos los microservicios deben contar con un middleware que capture y maneje los errores de manera uniforme.

```typescript
import { ExceptionFilter, Catch, ArgumentsHost, HttpException, Logger } from '@nestjs/common';
import { Response } from 'express';

@Catch(HttpException)
export class FiltroErroresGlobal implements ExceptionFilter {
  private readonly logger = new Logger(FiltroErroresGlobal.name);

  catch(exception: HttpException, host: ArgumentsHost) {
    const ctx = host.switchToHttp();
    const response = ctx.getResponse<Response>();
    const status = exception.getStatus();
    const exceptionResponse: any = exception.getResponse();

    const respuesta = {
      status: {
        exito: false,
        codigoHttp: status,
        mensaje: exceptionResponse?.message || 'Error inesperado',
        idTransaction: Math.floor(Math.random() * 1000000000).toString()
      },
      dato: { resultado: null },
      error: exceptionResponse?.details || []
    };

    this.logger.error(`Error ${status}: ${JSON.stringify(respuesta)}`);
    response.status(status).json(respuesta);
  }
}
```

---

## ⭐ **5.5 Registro de Errores en Logs y Monitoreo**
- Todos los errores deben ser registrados en un sistema de logs centralizado como **Elastic Stack, Grafana Loki o Datadog**.
- Se recomienda incluir trazabilidad de `idTransaction` para seguimiento de errores en producción.

---

## ⭐ **5.6 Envío Asíncrono de Logs de Auditoría**
Los errores críticos deben enviarse a **Kafka** para su monitoreo en tiempo real.

```json
{
  "evento": "errorDetectado",
  "origen": "coreAutenticacionSigesZeus",
  "detalle": {
    "codigo": "autenticacionFallida",
    "mensaje": "Token JWT inválido"
  },
  "fecha": "2025-01-28T14:50:00Z"
}
```

---

📌 **Este es el formato estandarizado para respuestas y manejo de errores en todos los microservicios.** 🚀


# ➜ **6 Contratos de Servicios y API Design**

## ⭐ **6.1 Definición de Contratos Antes de la Implementación**

Antes de desarrollar cualquier microservicio, es obligatorio definir un **contrato de servicio** que especifique los siguientes aspectos:
- Endpoints y rutas.
- Tipos de peticiones (GET, POST, PUT, DELETE).
- Cuerpo de las solicitudes y respuestas.
- Códigos de estado HTTP esperados.
- Errores posibles y estructura de respuestas de error.
- Dependencias con otros servicios.

Esto permite garantizar la interoperabilidad entre los diferentes microservicios y facilita la documentación previa a la implementación.

---

## ⭐ **6.2 Uso Obligatorio de Swagger/OpenAPI para Documentar Servicios**

Cada microservicio debe exponer su documentación mediante **Swagger (OpenAPI 3.0)**. Esto permite:
- Generar documentación automatizada y siempre actualizada.
- Facilitar la integración con otros equipos y sistemas.
- Probar los endpoints desde una interfaz web.

Ejemplo de configuración en **NestJS**:

```typescript
import { DocumentBuilder, SwaggerModule } from '@nestjs/swagger';

const config = new DocumentBuilder()
  .setTitle('Usuarios API')
  .setDescription('API para la gestión de usuarios')
  .setVersion('1.0')
  .addBearerAuth()
  .build();

const document = SwaggerModule.createDocument(app, config);
SwaggerModule.setup('api-docs', app, document);
```

---

## ⭐ **6.3 Proceso de Aprobación del Contrato Antes del Desarrollo**

Para garantizar calidad y alineación con la arquitectura establecida, el contrato de cada microservicio debe pasar por un proceso de aprobación antes de su desarrollo. Este proceso consta de las siguientes etapas:

1. **Definición del Contrato:**
   - El desarrollador o equipo encargado redacta el contrato de servicio basado en las necesidades del negocio.
   - Se deben incluir endpoints, tipos de datos, validaciones y estructura de respuestas.

2. **Revisión Técnica:**
   - El equipo de arquitectura revisa el contrato para garantizar que cumple con los estándares establecidos en este documento.
   - Se verifican aspectos como seguridad, consistencia con otras APIs y cumplimiento de nomenclatura.

3. **Pruebas de Compatibilidad:**
   - Se valida la interoperabilidad con otros microservicios.
   - Se realizan pruebas con herramientas como Postman o Mock Servers.

4. **Aprobación Formal:**
   - Una vez revisado y validado, el contrato debe ser aprobado formalmente por el equipo de arquitectura.
   - Se registra la versión inicial del contrato en el repositorio correspondiente.

5. **Publicación del Contrato:**
   - El contrato aprobado se publica en la documentación del microservicio (Swagger, OpenAPI o repositorio de documentación).
   - Se notifica a los equipos interesados sobre su disponibilidad y uso.

📌 **Este proceso asegura que todos los contratos sean diseñados de manera consistente, segura y compatible con la arquitectura del sistema.** 🚀

---

## ⭐ **6.4 Contratos de Servicios por Tipo de Microservicio**

Los contratos de servicios deben definirse según el tipo de microservicio, estableciendo reglas específicas para cada categoría.

### **6.4.1 Contrato para Microservicios Core**

Los microservicios core se encargan de la gestión de entidades principales dentro del sistema. Su contrato debe definir:
- **CRUD** de entidades principales.
- **Eventos de dominio** emitidos por el microservicio.
- **Reglas de validación estrictas**.

Ejemplo de contrato de servicio para un microservicio de gestión de usuarios:

```yaml
openapi: 3.0.0
info:
  title: API de Usuarios
  description: Microservicio para la gestión de usuarios.
  version: 1.0.0
paths:
  /usuarios:
    get:
      summary: Obtener la lista de usuarios
      responses:
        '200':
          description: Lista de usuarios obtenida exitosamente
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Usuario'
    post:
      summary: Crear un nuevo usuario
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Usuario'
      responses:
        '201':
          description: Usuario creado exitosamente
        '400':
          description: Error de validación en los datos ingresados
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '409':
          description: El usuario ya existe
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
components:
  schemas:
    Usuario:
      type: object
      required:
        - nombre
        - email
        - edad
      properties:
        id:
          type: integer
          example: 123
        nombre:
          type: string
          minLength: 3
          maxLength: 50
          example: "Juan Pérez"
        email:
          type: string
          format: email
          example: "juan.perez@example.com"
        edad:
          type: integer
          minimum: 18
          maximum: 99
          example: 30
    Error:
      type: object
      properties:
        codigo:
          type: string
          example: "campoRequerido"
        mensaje:
          type: string
          example: "El campo 'email' es obligatorio."
```
 
### **6.4.2 Contrato para Microservicios de Orquestación**

Los microservicios de orquestación son responsables de coordinar el flujo de trabajo entre varios microservicios. Se encargan de manejar transacciones distribuidas y procesos complejos que requieren la interacción de múltiples servicios.

Ejemplo de contrato para un microservicio de orquestación de pedidos:

```yaml
openapi: 3.0.0
info:
  title: API de Orquestación de Pedidos
  description: Microservicio que coordina la creación y procesamiento de pedidos.
  version: 1.0.0
paths:
  /procesar-pedido:
    post:
      summary: Orquestar el procesamiento de un pedido
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Pedido'
      responses:
        '202':
          description: Pedido en proceso
        '422':
          description: Error de negocio
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
components:
  schemas:
    Pedido:
      type: object
      required:
        - idPedido
        - clienteId
      properties:
        idPedido:
          type: string
          format: ulid
          example: "01AN4Z07BY79KA1307SR9X4MV3"
        clienteId:
          type: integer
          example: 101
        estado:
          type: string
          enum: ["pendiente", "procesado", "enviado"]
          example: "pendiente"
    Error:
      type: object
      properties:
        codigo:
          type: string
          example: "pedidoInvalido"
        mensaje:
          type: string
          example: "El pedido no puede procesarse debido a datos incorrectos."
```

---

### **6.4.3 Contrato para Microservicios de Integración**

Los microservicios de integración permiten la comunicación con sistemas externos, adaptando datos y manejando autenticación con terceros.

Ejemplo de contrato para la integración con una pasarela de pagos:

```yaml
openapi: 3.0.0
info:
  title: API de Integración con Pasarela de Pagos
  description: Microservicio que se conecta con una pasarela de pagos externa.
  version: 1.0.0
paths:
  /realizar-pago:
    post:
      summary: Realizar un pago a través de la pasarela
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Pago'
      responses:
        '200':
          description: Pago realizado exitosamente
        '400':
          description: Error en la validación del pago
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '503':
          description: Servicio externo no disponible
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
components:
  schemas:
    Pago:
      type: object
      required:
        - monto
        - moneda
        - metodoPago
      properties:
        monto:
          type: number
          minimum: 1.0
          example: 100.50
        moneda:
          type: string
          example: "USD"
        metodoPago:
          type: string
          enum: ["tarjeta", "transferencia", "paypal"]
          example: "tarjeta"
    Error:
      type: object
      properties:
        codigo:
          type: string
          example: "pagoFallido"
        mensaje:
          type: string
          example: "El pago no pudo ser procesado. Intente nuevamente."
```

---

### **6.4.4 Contrato para Microservicios de Soporte**

Los microservicios de soporte brindan funcionalidades auxiliares como autenticación, envío de notificaciones y monitoreo del sistema.

Ejemplo de contrato para un servicio de notificaciones:

```yaml
openapi: 3.0.0
info:
  title: API de Notificaciones
  description: Microservicio encargado de enviar notificaciones a los usuarios.
  version: 1.0.0
paths:
  /enviar-correo:
    post:
      summary: Enviar un correo electrónico
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Correo'
      responses:
        '200':
          description: Correo enviado exitosamente
        '400':
          description: Error en la validación del correo
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
components:
  schemas:
    Correo:
      type: object
      required:
        - destinatario
        - asunto
        - mensaje
      properties:
        destinatario:
          type: string
          format: email
          example: "usuario@example.com"
        asunto:
          type: string
          maxLength: 100
          example: "Bienvenido a nuestra plataforma"
        mensaje:
          type: string
          maxLength: 500
          example: "Gracias por registrarte en nuestro servicio."
    Error:
      type: object
      properties:
        codigo:
          type: string
          example: "errorEnvio"
        mensaje:
          type: string
          example: "No se pudo enviar el correo. Verifique los datos ingresados."
```

## ⭐ **6.5 Exposición de la Documentación Mediante una URL Pública**

### **6.5.1 Cada Servicio Debe Exponer su Contrato en `/api-docs` con Swagger**
Cada microservicio debe proveer su documentación accesible en la ruta `/api-docs`.
Ejemplo:
```
https://mi-microservicio.dominio.com/api-docs
```

- La documentación debe generarse automáticamente con **Swagger/OpenAPI** y reflejar la versión actual del servicio.
- Se recomienda proteger el acceso con autenticación cuando sea necesario.

### **6.5.2 La URL Debe Ser Accesible Dentro del Ecosistema de Microservicios**

- Los contratos de servicio deben ser accesibles para todos los equipos de desarrollo y consumo dentro de la infraestructura de microservicios.
- Se puede exponer la documentación a nivel interno a través de una **API Gateway** o una plataforma de descubrimiento de servicios.
- Si el servicio es público, la documentación debe estar accesible sin autenticación, con una política clara de consumo.

### **6.5.3 Todos los Contratos Deben Versionarse y Mantenerse Actualizados**

- Las versiones de las APIs deben seguir **SemVer (Semantic Versioning)**.
- Se recomienda mantener **al menos 2 versiones activas** antes de descontinuar una API.
- Cualquier cambio en la API debe reflejarse en la documentación antes de la implementación.

---

## ⭐ **6.6 Estandarización de Endpoints y Rutas**

Para garantizar consistencia, los endpoints deben cumplir con las siguientes reglas:

- **Uso de nombres en plural** para representar colecciones.
  - ✅ `/usuarios`, `/pedidos`
  - ❌ `/usuario`, `/pedido`
- **Uso de verbos HTTP adecuados:**
  - `GET /usuarios` → Obtener lista de usuarios.
  - `POST /usuarios` → Crear un nuevo usuario.
  - `PUT /usuarios/{id}` → Actualizar un usuario existente.
  - `DELETE /usuarios/{id}` → Eliminación lógica de un usuario.
- **Incluir versión en la ruta** (`/api/v1/recurso`).
- **Evitar incluir verbos en la URL:**
  - ✅ `/usuarios`
  - ❌ `/obtenerUsuarios`
- **Utilizar `camelCase` en los parámetros de la URL:**
  - ✅ `/usuarios/{usuarioId}`
  - ❌ `/usuarios/{usuario_id}`

📌 **Estas reglas garantizan que los endpoints sean predecibles y fáciles de consumir.**

---

## ⭐ **6.7 Políticas de Autenticación y Autorización en APIs**

### **6.7.1 Autenticación**
- **Uso obligatorio de JWT (JSON Web Tokens)** para autenticar solicitudes.
- Todas las APIs privadas deben requerir un token válido en el encabezado `Authorization`.
- Implementación de autenticación con **OAuth 2.0** si se necesita interoperabilidad con terceros.

Ejemplo de autenticación en Swagger:
```yaml
components:
  securitySchemes:
    BearerAuth:
      type: http
      scheme: bearer
      bearerFormat: JWT
security:
  - BearerAuth: []
```

### **6.7.2 Autorización**
- **Control de acceso basado en roles (RBAC)** para definir permisos en cada endpoint.
- **Reglas de autorización** aplicadas en los controladores de cada servicio.

Ejemplo de validación de permisos en **NestJS**:
```typescript
import { CanActivate, ExecutionContext, Injectable } from '@nestjs/common';

@Injectable()
export class RolGuard implements CanActivate {
  canActivate(context: ExecutionContext): boolean {
    const request = context.switchToHttp().getRequest();
    return request.user?.rol === 'admin';
  }
}
```

📌 **Estas políticas aseguran que el acceso a las APIs esté correctamente controlado y protegido.** 🚀

