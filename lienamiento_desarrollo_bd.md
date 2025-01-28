# 📌 Índice de Lineamientos para el Desarrollo de Componentes de Base de Datos

## 1️⃣ Introducción
- **1.1** Propósito de este documento  
- **1.2** Alcance y objetivos  

## 2️⃣ Principios Generales
- **2.1** Estandarización  
- **2.2** Desempeño y escalabilidad  
- **2.3** Modularidad  
- **2.4** Seguridad  
- **2.5** Documentación y versionamiento  

## 3️⃣ **Organización de la Base de Datos**  
- **3.1** Esquemas y Segmentación de Datos  
- **3.2** Uso de PostgreSQL como Motor de Base de Datos  
- **3.3** Políticas de Almacenamiento y Estructuración  
  - **3.3.1** Uso de ULID para Identificadores Primarios  
  - **3.3.2** Estándar de Campos Base y Auditoría  
  - **3.3.3** Reglas para Eliminación de Registros (Solo Eliminación Lógica)   

## 4️⃣ Nomenclatura y Estilo
- **4.1** Convenciones de nombres  
  - **4.1.1** Bases de datos y esquemas  
  - **4.1.2** Tablas y columnas  
  - **4.1.3** Índices y llaves foráneas  
  - **4.1.4** Vistas y procedimientos almacenados  
  - **4.1.5** Eventos y triggers  
- **4.2** Formato y estilo de código SQL  
- **4.3** Estándares de nomenclatura en consultas y scripts  

## 5️⃣ Desarrollo de Scripts
- **5.1** Scripts de creación  
- **5.2** Scripts de mantenimiento  
- **5.3** Scripts de carga de datos  
- **5.4** Estrategias de versionado  
- **5.5** Estandarización de nombres en scripts  

## 6️⃣ Seguridad y Gobernanza de Datos
- **6.1** Políticas de acceso y permisos  
- **6.2** Encriptación y protección de datos sensibles  
- **6.3** Auditoría y logging de transacciones  
- **6.4** Control de concurrencia y transacciones seguras  
- **6.5** Eliminación lógica en lugar de eliminación física  

## 7️⃣ Identificadores Únicos y Campos Base
- **7.1** Implementación de ULID como identificador estándar  
- **7.2** Campos base obligatorios en todas las tablas  
- **7.3** Campos de auditoría obligatorios  
- **7.4** Normas de estructuración de claves primarias y foráneas  

## 8️⃣ Gobernanza por IA en la Base de Datos
- **8.1** Validación automática de estructuras de datos  
- **8.2** Revisión de esquemas y scripts antes de la ejecución  
- **8.3** Propuesta de nombres de objetos en la BD para aprobación previa  
- **8.4** Registro y auditoría de cambios estructurales  
- **8.5** Aprobación del Comité de Arquitectura para modificaciones fuera del estándar  

## 9️⃣ Cumplimiento y Validación
- **9.1** Revisión obligatoria antes del despliegue  
- **9.2** Pruebas de rendimiento e integridad antes de pasar a producción  
- **9.3** Registro de cambios en documentación oficial  
- **9.4** Plan de rollback en caso de fallos en la BD  

---

# 🏗️ **1. Introducción**

## 📌 **1.1 Propósito de este documento**
Este documento define los **lineamientos para el desarrollo de componentes de Base de Datos (BD)** en el sistema.  
Su propósito es establecer estándares claros que garanticen:  

✅ **Consistencia** en la estructura y organización de los datos.  
✅ **Seguridad** mediante políticas de acceso y protección de la información.  
✅ **Eficiencia y desempeño** en consultas y almacenamiento.  
✅ **Mantenibilidad** para facilitar la evolución del sistema sin comprometer su estabilidad.  

Toda implementación de BD debe seguir la **arquitectura establecida** en la documentación de arquitectura, y cualquier modificación fuera del estándar **requerirá la aprobación del Comité de Arquitectura antes de su desarrollo**.  

---

## 📌 **1.2 Alcance y objetivos**
Los lineamientos descritos en este documento aplican a **todas las bases de datos** del sistema, independientemente del módulo o servicio en el que se utilicen.  
Se enfocan en los siguientes aspectos clave:  

🔹 **Estructura y organización de la base de datos**  
- Definir el uso de **esquemas y segmentación de datos**.  
- Establecer **nombres estandarizados para bases de datos, tablas y columnas**.  
- Regular **eliminaciones lógicas en lugar de eliminaciones físicas**.  

🔹 **Reglas de nomenclatura y estilo de código SQL**  
- Definir convenciones de nombres para **índices, llaves foráneas, funciones y procedimientos almacenados**.  
- Establecer **prácticas recomendadas para la escritura de consultas SQL**.  

🔹 **Seguridad y gobernanza de datos**  
- Aplicar **roles y permisos** para restringir accesos.  
- Implementar **cifrado y auditoría de datos sensibles**.  

🔹 **Uso de identificadores y auditoría**  
- Definir el **uso obligatorio de ULID** como identificador único en todas las tablas.  
- Establecer **campos base y campos de auditoría obligatorios** en cada tabla.  

🔹 **Gobernanza por IA en la base de datos**  
- La IA **validará automáticamente** que las estructuras de datos cumplan con los estándares definidos.  
- **Antes de crear objetos en la BD, la IA deberá solicitar una aprobación previa** para la nomenclatura de estos objetos.  
- **No se ejecutarán cambios en la BD si no están alineados con este documento**.  

---

✅ **Regla Clave:**  
🚀 **La IA no podrá realizar ninguna modificación en la base de datos si no está alineada con este documento.**  
Si se requiere un cambio fuera del estándar, este deberá ser **aprobado por el Comité de Arquitectura** y documentado antes de su implementación.

# 🏗️ **2. Principios Generales**

## 📌 **2.1 Estandarización**
La estandarización es clave para garantizar la **consistencia y mantenibilidad** de la base de datos.  
Todos los objetos deben seguir las convenciones establecidas en este documento.  

✅ Uso de **nombres uniformes** para bases de datos, tablas, columnas, índices y funciones.  
✅ Definición de **convenciones de nomenclatura** claras y predecibles.  
✅ Aplicación de **reglas de estilo SQL** para garantizar código limpio y entendible.  

---

## 📌 **2.2 Desempeño y Escalabilidad**
El diseño de la base de datos debe priorizar el **rendimiento y la capacidad de crecimiento del sistema**.  

🔹 **Optimización de consultas** mediante índices y estrategias adecuadas.  
🔹 **Uso eficiente de PostgreSQL**, aprovechando características como **particionamiento y caché**.  
🔹 **Evitar consultas costosas** y mejorar tiempos de respuesta en operaciones críticas.  
🔹 **Reducción de redundancia**, aplicando principios de **normalización** en el modelado de datos.  

---

## 📌 **2.3 Modularidad**
Para evitar bases de datos monolíticas y difíciles de escalar, los datos deben organizarse de manera modular.  

✅ Cada módulo o funcionalidad debe **tener su propio esquema** dentro de la base de datos.  
✅ **No mezclar tablas de diferentes procesos de negocio** en un mismo esquema.  
✅ **Los objetos de base de datos deben ser reutilizables** y evitar duplicidad de lógica.  

---

## 📌 **2.4 Seguridad**
La seguridad es un principio fundamental en el manejo de la base de datos.  

🔹 **Gestión de accesos y permisos** con `GRANT` y `REVOKE`.  
🔹 **Cifrado de datos sensibles**, tanto en tránsito como en reposo.  
🔹 **Uso de roles de usuario específicos** en lugar de accesos directos a las tablas.  
🔹 **Evitar almacenamiento de contraseñas en texto plano**, aplicando hashing con `bcrypt` o `Argon2`.  

---

## 📌 **2.5 Documentación y Versionamiento**
Todos los cambios en la base de datos deben estar **documentados y versionados correctamente**.  

✅ Cada cambio debe registrarse en **scripts de migración versionados** (`001_init.sql`, `002_data.sql`).  
✅ Se debe mantener un **historial de cambios** para garantizar trazabilidad.  
✅ La IA validará automáticamente los cambios y **evitará modificaciones sin documentación previa**.  

 # 🏗️ **3. Organización de la Base de Datos**

## 📌 **3.1 Esquemas y Segmentación de Datos**
La estructura de la base de datos debe reflejar la separación de módulos y funcionalidades para mantener la escalabilidad y la organización.

✅ Cada **proyecto** tendrá una o varias **bases de datos**, dependiendo de su tamaño y complejidad.  
✅ Para proyectos pequeños, se utilizará **una única BD dividida en esquemas**.  
✅ Cada BD debe contener al menos **un esquema dedicado a una funcionalidad específica**.  
✅ **No se deben mezclar tablas de distintos procesos de negocio** en un mismo esquema.  
✅ El **motor de base de datos estándar será PostgreSQL**.  

Ejemplo de segmentación por esquemas:  

| **Esquema** | **Funcionalidad** |
|-------------|------------------|
| `zeus_idp`  | Gestión de identidad y autenticación |
| `zeus_pedidos`  | Gestión de pedidos y transacciones |
| `zeus_facturacion` | Procesos de facturación y pagos |
| `zeus_usuarios` | Administración de usuarios y permisos |

---

## 📌 **3.2 Convención de Esquemas y Tablas**
Para mantener una estructura uniforme y facilitar la administración, se establecen las siguientes reglas de nomenclatura:

🔹 **Esquemas**: `snake_case`, basado en la funcionalidad (Ejemplo: `zeus_idp`).  
🔹 **Tablas**: `snake_case`, prefijo con el esquema o módulo (Ejemplo: `facturacion_cliente`).  
🔹 **Columnas**: `snake_case`, con nombres descriptivos (Ejemplo: `fecha_creacion`).  
🔹 **Identificadores (ID)**: El **PK de cada tabla debe llamarse `<nombre_tabla>_id`**, donde `<nombre_tabla>` es el nombre real de la tabla.  
  - Ejemplo para la tabla `cliente`: `cliente_id VARCHAR(26) PRIMARY KEY DEFAULT generate_ulid()`.  
  - Ejemplo para la tabla `pedido`: `pedido_id VARCHAR(26) PRIMARY KEY DEFAULT generate_ulid()`.  
🔹 **Índices**: `idx_<tabla>_<columna>` (Ejemplo: `idx_cliente_dni`).  
🔹 **Llaves Foráneas**: `fk_<tabla_origen>_<tabla_destino>` (Ejemplo: `fk_pedido_cliente`).  
🔹 **Vistas**: `vw_<nombre_descriptivo>` (Ejemplo: `vw_ventas_diarias`).  
🔹 **Funciones**: `fn_<nombre_descriptivo>` (Ejemplo: `fn_calcular_descuento`).  
🔹 **Procedimientos Almacenados**: `sp_<nombre_descriptivo>` (Ejemplo: `sp_generar_factura`).  

🚀 **📌 Regla Clave:**  
📌 **Antes de crear cualquier objeto en la BD, la IA deberá solicitar una aprobación previa para su propuesta de nombres y validar que cumplan con los estándares definidos en este documento.**  

---

## 📌 **3.3 Campos Base y Auditoría**
Todas las tablas de la base de datos deben incluir un conjunto de **campos estándar** para trazabilidad y auditoría.

✅ **Campos Base** (Obligatorios en todas las tablas):
```sql
<nombre_tabla>_id VARCHAR(26) PRIMARY KEY DEFAULT generate_ulid(), -- Identificador único basado en ULID
estado_registro VARCHAR(3) DEFAULT 'ACT' NOT NULL, -- Estado del registro (ACT: Activo, ELI: Eliminado)
fecha_registro TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
usuario_registro VARCHAR(255) NOT NULL
```
✅ **Campos de Auditoría** (Opcionales para trazabilidad avanzada):
```sql
fecha_modificacion TIMESTAMP,
usuario_modificacion VARCHAR(255),
fecha_eliminacion TIMESTAMP,
usuario_eliminacion VARCHAR(255),
transaccion_id VARCHAR(255)
```
✅ **Uso de ULID en los identificadores primarios para garantizar unicidad y mejor rendimiento en PostgreSQL.
```sql
CREATE TABLE zeus_idp.aplicacion (
    aplicacion_id VARCHAR(26) PRIMARY KEY DEFAULT zeus_idp.generate_ulid(),
    estado_registro VARCHAR(3) DEFAULT 'ACT' NOT NULL,
    fecha_registro TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
    usuario_registro VARCHAR(255) NOT NULL,
    fecha_modificacion TIMESTAMP,
    usuario_modificacion VARCHAR(255),
    fecha_eliminacion TIMESTAMP,
    usuario_eliminacion VARCHAR(255),
    transaccion_id VARCHAR(255),
    client_id VARCHAR(32) UNIQUE NOT NULL,
    client_secret TEXT NOT NULL,
    nombre VARCHAR(255) NOT NULL,
    redirect_uri TEXT NOT NULL,
    estado VARCHAR(3) DEFAULT 'ACT' NOT NULL
);
```
### 📌 **Importante**
✅ **El identificador primario (PK) de cada tabla debe llamarse** `<nombre_tabla>_id` **y utilizar ULID como valor por defecto.**  

✅ **No se permite la eliminación física de registros** en la base de datos, solo **eliminación lógica** (`estado_registro = 'ELI'`).  

✅ **Las transacciones deben registrar siempre el usuario y la fecha de modificación.**  

# 4️⃣ **Nomenclatura y Estilo**

## 📌 **4.1 Reglas de Nomenclatura**  

Para garantizar **consistencia, claridad y mantenibilidad**, se establecen las siguientes reglas para la nomenclatura de los objetos en la base de datos:

### 🔹 **Bases de Datos y Esquemas**
- Se utilizará el formato `snake_case`.
- **Ejemplo:**  
  ```sql
  zeus_bd_finanzas  -- Base de datos
  zeus_idp          -- Esquema
  ```

### 🔹 **Tablas**
- Formato: `snake_case` con prefijo que identifique la funcionalidad.
- **Ejemplo:**
  ```sql
  facturacion_cliente
  pedido_detalle
  ```

### 🔹 **Columnas**
- Formato: `snake_case` con nombre descriptivo.
- **Regla Clave:**  
  - El **identificador primario (PK)** de cada tabla **debe llamarse `<nombre_tabla>_id`**.
  - Se usará **ULID** como valor por defecto.  
- **Ejemplo:**
  ```sql
  cliente_id
  pedido_id
  factura_id
  fecha_creacion
  monto_total
  ```

### 🔹 **Índices**
- Formato: `idx_<tabla>_<columna>`.
- **Ejemplo:**
  ```sql
  idx_cliente_dni
  idx_pedido_fecha
  ```

### 🔹 **Llaves Foráneas**
- Formato: `fk_<tabla_origen>_<tabla_destino>`.
- **Ejemplo:**
  ```sql
  fk_pedido_cliente
  fk_factura_pedido
  ```

### 🔹 **Vistas**
- Formato: `vw_<nombre_descriptivo>`.
- **Ejemplo:**
  ```sql
  vw_ventas_diarias
  vw_pedidos_pendientes
  ```

### 🔹 **Funciones y Procedimientos Almacenados**
- **Funciones:** `fn_<nombre_descriptivo>`.  
  - **Ejemplo:**
    ```sql
    fn_calcular_descuento
    ```
- **Procedimientos Almacenados:** `sp_<nombre_descriptivo>`.  
  - **Ejemplo:**
    ```sql
    sp_generar_factura
    ```

---

## 📌 **4.2 Estilo y Formato de Código**  

Para mantener un código **limpio, legible y estandarizado**, se deben seguir las siguientes reglas:  

✅ **Uso de mayúsculas** para palabras clave SQL.  
```sql
SELECT * FROM cliente WHERE estado = 'ACT';
```  
✅ **Uso de minúsculas** para nombres de **tablas, columnas, vistas, índices y funciones**.  
✅ **Indentación adecuada** en estructuras SQL complejas.  
✅ **Uso de comentarios** en funciones, procedimientos y scripts críticos.  
✅ **Antes de crear cualquier objeto en la BD, la IA deberá solicitar una aprobación previa** para su propuesta de nombres y validar que estos cumplan con los estándares definidos en este documento.  
✅ **Todo script debe estar bien documentado incluso los nombres de los campos tiene que estar brevemente su descripción para su mejor entendimiento
---

## 📌 **4.3 Ejemplo de Creación de Tabla con Nomenclatura y Estilo Correcto**  

```sql
CREATE SCHEMA IF NOT EXISTS zeus_idp;

-- Crear extensiones necesarias
CREATE EXTENSION IF NOT EXISTS pgcrypto;
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

-- Crear función para generar un ULID en PostgreSQL
CREATE OR REPLACE FUNCTION zeus_idp.generate_ulid()
RETURNS VARCHAR(26) AS $$
DECLARE
    ulid VARCHAR(26);
BEGIN
    SELECT encode(uuid_send(uuid_generate_v4()), 'base32') INTO ulid;
    RETURN ulid;
END;
$$ LANGUAGE plpgsql;

-- Crear la tabla de aplicaciones registradas (clientes)
CREATE TABLE zeus_idp.aplicacion (
    aplicacion_id VARCHAR(26) PRIMARY KEY DEFAULT zeus_idp.generate_ulid(),
    estado_registro VARCHAR(3) DEFAULT 'ACT' NOT NULL, -- ACT: Activo, ELI: Eliminado
    fecha_registro TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
    usuario_registro VARCHAR(255) NOT NULL,
    fecha_modificacion TIMESTAMP,
    usuario_modificacion VARCHAR(255),
    fecha_eliminacion TIMESTAMP,
    usuario_eliminacion VARCHAR(255),
    transaccion_id VARCHAR(255),
    client_id VARCHAR(32) UNIQUE NOT NULL,
    client_secret TEXT NOT NULL,
    nombre VARCHAR(255) NOT NULL,
    redirect_uri TEXT NOT NULL,
    estado VARCHAR(3) DEFAULT 'ACT' NOT NULL
);
```

---

## 📌 **4.4 Campos Base y Auditoría**  

### 🔹 **Campos Base (Obligatorios en todas las tablas)**
| Nombre del Campo     | Tipo de Dato    | Descripción |
|----------------------|----------------|-------------|
| `<nombre_tabla>_id` | `VARCHAR(26)`   | Identificador único (ULID) |
| `estado_registro`   | `VARCHAR(3)`    | Estado del registro (`ACT`, `ELI`) |
| `fecha_registro`    | `TIMESTAMP`     | Fecha de creación |
| `usuario_registro`  | `VARCHAR(255)`  | Usuario que creó el registro |

### 🔹 **Campos de Auditoría (Opcionales para trazabilidad avanzada)**
| Nombre del Campo        | Tipo de Dato    | Descripción |
|-------------------------|----------------|-------------|
| `fecha_modificacion`    | `TIMESTAMP`     | Fecha de la última modificación |
| `usuario_modificacion`  | `VARCHAR(255)`  | Usuario que modificó el registro |
| `fecha_eliminacion`     | `TIMESTAMP`     | Fecha en que se eliminó el registro |
| `usuario_eliminacion`   | `VARCHAR(255)`  | Usuario que eliminó el registro |
| `transaccion_id`        | `VARCHAR(255)`  | ID de la transacción asociada |

---

## 📌 **4.5 Reglas Claves e Importantes**  

✅ **El identificador primario (PK) de cada tabla debe llamarse `<nombre_tabla>_id` y utilizar ULID como valor por defecto.**  
✅ **No se permite la eliminación física de registros en la base de datos, solo eliminación lógica (`estado_registro = 'ELI'`).**  
✅ **Las transacciones deben registrar siempre el usuario y la fecha de modificación.**  

---

# 📌 **5. Desarrollo de Scripts**

## 📌 **5.1 Scripts de Creación**
👉 Todos los scripts de creación deben iniciar con la validación de existencia del objeto (`IF NOT EXISTS`).  
👉 Uso de `CASCADE` en eliminaciones solo cuando sea estrictamente necesario.  
👉 Definir **llaves primarias (PRIMARY KEY)** en todas las tablas.  
👉 Aplicar **restricciones de integridad referencial** (`FOREIGN KEY`, `CHECK`, `UNIQUE`).  
👉 Agregar índices en columnas utilizadas en consultas frecuentes.  
👉 **Todo script debe estar bien documentado para su mejor entendimiento, indicando propósito, contexto y dependencias.**  

```sql
-- Ejemplo de creación de tabla con validación previa
CREATE TABLE IF NOT EXISTS ventas (
    venta_id VARCHAR(26) PRIMARY KEY DEFAULT generate_ulid(),
    cliente_id VARCHAR(26) NOT NULL,
    monto DECIMAL(10,2) NOT NULL,
    fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
    estado_registro VARCHAR(3) DEFAULT 'ACT' NOT NULL,
    FOREIGN KEY (cliente_id) REFERENCES clientes(cliente_id),
    INDEX idx_ventas_cliente (cliente_id)
);
```

---

## 📌 **5.2 Scripts de Mantenimiento**
👉 Mantener una estructura de **versionado incremental** en los scripts (`001_init.sql`, `002_data.sql`).  
👉 Incluir un script de **rollback** para revertir cambios en caso de error.  
👉 Todos los scripts deben ser **probados en entornos de desarrollo antes de pasar a producción**.  
👉 **Cada cambio en la estructura de la base de datos debe incluir una descripción detallada de su propósito y su impacto en el sistema.**  

```sql
-- Ejemplo de script de mantenimiento con rollback
ALTER TABLE ventas ADD COLUMN descuento DECIMAL(5,2) DEFAULT 0;

-- Rollback del cambio
ALTER TABLE ventas DROP COLUMN descuento;
```

---

## 📌 **5.3 Scripts de Carga de Datos**
👉 Se deben insertar datos iniciales **usando COPY en lugar de INSERT masivos**, cuando sea posible.  
👉 Utilizar `UPSERT (INSERT ... ON CONFLICT UPDATE)` para evitar duplicados.  
👉 Evitar el uso de valores `NULL` en columnas no nulas.  
👉 Mantener registros de auditoría para cambios críticos.  
👉 **Incluir comentarios explicativos en los scripts para facilitar la comprensión y futura modificación.**  

```sql
-- Ejemplo de carga de datos con UPSERT
INSERT INTO clientes (cliente_id, nombre, email)
VALUES ('01GZ8WYZC0N2M5', 'Juan Pérez', 'juan@example.com')
ON CONFLICT (cliente_id)
DO UPDATE SET email = EXCLUDED.email;
```

---

## 📌 **5.4 Estrategias de Versionado**
👉 Todos los cambios en la base de datos deben seguir un **esquema de versionado** estructurado.  
👉 Se deben numerar los scripts en orden secuencial (`001_init.sql`, `002_data.sql`, etc.).  
👉 **Cada script debe tener un encabezado con fecha, autor y descripción del cambio.**  
👉 Se debe mantener un registro de versiones en la base de datos (`schema_version`).  

```sql
-- Ejemplo de control de versión
CREATE TABLE IF NOT EXISTS schema_version (
    version_id SERIAL PRIMARY KEY,
    nombre_script VARCHAR(255) NOT NULL,
    fecha_aplicacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## 📌 **5.5 Estandarización de Nombres en Scripts**
👉 Los nombres de scripts deben ser **claros y descriptivos**, siguiendo el formato:
- `NNN_nombre_descriptivo.sql` (Ejemplo: `003_agregar_campo_estado.sql`).  
👉 Todos los objetos en la base de datos deben seguir las convenciones establecidas en la arquitectura:
- Tablas: **snake_case** (`ventas_clientes`).  
- Columnas: **snake_case** (`monto_total`).  
- Índices: `idx_<tabla>_<columna>` (`idx_ventas_cliente`).  
👉 Los nombres de los **procedimientos almacenados y funciones** deben ser descriptivos y en **infinitivo** (`calcular_descuento`).  

---

## 📌 **Regla Clave**
🚀 **📌 Todo script debe estar bien documentado con comentarios explicativos sobre su propósito, contexto y dependencias.**  

```sql
-- Este script inicializa la tabla de clientes y carga datos de prueba.
-- Es necesario ejecutarlo antes de otros scripts relacionados con ventas.
```
# 📌 **6. Seguridad y Gobernanza de Datos**

## 📌 **6.1 Políticas de Acceso y Permisos**
👉 Se deben definir roles y permisos en PostgreSQL bajo el **principio de mínimos privilegios**.  
👉 Uso de **roles personalizados** para agrupar permisos de lectura, escritura y administración.  
👉 **Todos los accesos a la base de datos deben registrarse** en logs de auditoría.  
👉 Se restringirá el acceso directo a tablas, usando **vistas y procedimientos almacenados** cuando sea necesario.  

```sql
-- Creación de un rol de solo lectura para reportes
CREATE ROLE reportes READ ONLY;
GRANT SELECT ON ALL TABLES IN SCHEMA zeus_idp TO reportes;
```

---

## 📌 **6.2 Encriptación y Protección de Datos Sensibles**
👉 Implementar **cifrado en reposo y en tránsito** utilizando **TLS 1.2+**.  
👉 Uso de **column-level encryption** para información sensible como contraseñas o datos personales.  
👉 Aplicación de **hashing seguro** (`bcrypt`, `Argon2`) para almacenamiento de credenciales.  
👉 Los identificadores sensibles deben ser **anonimizados** en logs y reportes públicos.  

```sql
-- Ejemplo de cifrado de una columna en PostgreSQL
CREATE EXTENSION IF NOT EXISTS pgcrypto;

ALTER TABLE zeus_idp.usuarios ADD COLUMN password_hash TEXT;

UPDATE zeus_idp.usuarios
SET password_hash = crypt('password123', gen_salt('bf'))
WHERE usuario_id = '01GZ8WYZC0N2M5';
```

---

## 📌 **6.3 Auditoría y Logging de Transacciones**
👉 Todas las modificaciones en **tablas sensibles** deben registrarse en una **tabla de auditoría**.  
👉 Implementación de **triggers** para registrar cambios en registros críticos.  
👉 Uso de **UUID o ULID** para rastrear transacciones en logs.  

```sql
-- Creación de una tabla de auditoría
CREATE TABLE zeus_idp.auditoria (
    auditoria_id VARCHAR(26) PRIMARY KEY DEFAULT zeus_idp.generate_ulid(),
    tabla_afectada VARCHAR(255) NOT NULL,
    operacion VARCHAR(10) NOT NULL,
    usuario VARCHAR(255) NOT NULL,
    fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
    transaccion_id VARCHAR(255) NOT NULL
);
```

---

## 📌 **6.4 Control de Concurrencia y Transacciones Seguras**
👉 Se deben utilizar **bloqueos optimistas** (`SELECT FOR UPDATE`) en transacciones críticas.  
👉 Implementación de **mecanismos de rollback** para asegurar la consistencia de datos.  
👉 Uso de **savepoints** en transacciones largas para mejorar la recuperación ante fallos.  
👉 **Todas las transacciones deben registrar el usuario y la fecha de modificación**.  

```sql
-- Uso de SELECT FOR UPDATE para evitar problemas de concurrencia
BEGIN;
SELECT saldo INTO saldo_actual FROM zeus_idp.cuentas WHERE cuenta_id = '01GZ8WYZC0N2M5' FOR UPDATE;

IF saldo_actual >= 100 THEN
    UPDATE zeus_idp.cuentas SET saldo = saldo - 100 WHERE cuenta_id = '01GZ8WYZC0N2M5';
END IF;

COMMIT;
```

---

## 📌 **6.5 Eliminación Lógica en Lugar de Eliminación Física**
👉 **No se permite la eliminación física de registros**. En su lugar, se debe marcar el estado como `ELI` (eliminado).  
👉 **Los siguientes campos base deben estar presentes en todas las tablas**:  
   - `estado_registro`: Controla el estado (`ACT`, `INA`, `ELI`).  
   - `fecha_registro`: Registra la fecha de creación.  
   - `usuario_registro`: Usuario que creó el registro.  
   - `fecha_modificacion`: Última fecha de modificación.  
   - `usuario_modificacion`: Último usuario que modificó el registro.  
   - `fecha_eliminacion`: Fecha en la que se eliminó el registro.  
   - `usuario_eliminacion`: Usuario que eliminó el registro.  
   - `transaccion_id`: Identificador único de la transacción.  

```sql
-- Ejemplo de eliminación lógica
UPDATE zeus_idp.usuarios
SET estado_registro = 'ELI',
    fecha_eliminacion = CURRENT_TIMESTAMP,
    usuario_eliminacion = 'admin',
    transaccion_id = 'TX12345'
WHERE usuario_id = '01GZ8WYZC0N2M5';
```
# ⭐️ **7. Identificadores Únicos y Campos Base**

## ⭐️ **7.1 Implementación de ULID como Identificador Estándar**

✅ Todos los identificadores primarios (PK) de las tablas deben utilizar **ULID** en lugar de UUID para mejorar la indexación y ordenación de registros.
✅ Se debe utilizar la función **generate_ulid()** en PostgreSQL para generar identificadores de manera automática.

```sql
-- Crear extensión necesaria para ULID
CREATE EXTENSION IF NOT EXISTS pgcrypto;
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

-- Crear esquema si no existe
CREATE SCHEMA IF NOT EXISTS zeus_idp;

-- Crear función para generar ULID
CREATE OR REPLACE FUNCTION zeus_idp.generate_ulid()
RETURNS VARCHAR(26) AS $$
DECLARE
    ulid VARCHAR(26);
BEGIN
    SELECT encode(uuid_send(uuid_generate_v4()), 'base32') INTO ulid;
    RETURN ulid;
END;
$$ LANGUAGE plpgsql;
```

## ⭐️ **7.2 Campos Base Obligatorios en Todas las Tablas**

✅ Todas las tablas deben contener los siguientes campos base:

```sql
estado_registro VARCHAR(3) DEFAULT 'ACT' NOT NULL,  -- ACT: Activo, INA: Inactivo, ELI: Eliminado
fecha_registro TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
usuario_registro VARCHAR(255) NOT NULL
```

## ⭐️ **7.3 Campos de Auditoría Obligatorios**

✅ Todas las tablas deben incluir los siguientes campos de auditoría para trazabilidad de cambios:

```sql
fecha_modificacion TIMESTAMP,
usuario_modificacion VARCHAR(255),
fecha_eliminacion TIMESTAMP,
usuario_eliminacion VARCHAR(255),
transaccion_id VARCHAR(255)
```

## ⭐️ **7.4 Normas de Estructuración de Claves Primarias y Foráneas**

✅ El identificador primario (PK) debe seguir el formato `<nombre_tabla>_id`.
✅ Todas las claves primarias deben ser de tipo **VARCHAR(26)** y generadas con `generate_ulid()`.
✅ Las claves foráneas deben mantener una relación con las claves primarias usando `ON DELETE SET NULL` o `ON DELETE CASCADE` según el caso.

```sql
CREATE TABLE zeus_idp.aplicacion (
    aplicacion_id VARCHAR(26) PRIMARY KEY DEFAULT zeus_idp.generate_ulid(),
    estado_registro VARCHAR(3) DEFAULT 'ACT' NOT NULL,
    fecha_registro TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
    usuario_registro VARCHAR(255) NOT NULL,
    fecha_modificacion TIMESTAMP,
    usuario_modificacion VARCHAR(255),
    fecha_eliminacion TIMESTAMP,
    usuario_eliminacion VARCHAR(255),
    transaccion_id VARCHAR(255),
    client_id VARCHAR(32) UNIQUE NOT NULL,
    client_secret TEXT NOT NULL,
    nombre VARCHAR(255) NOT NULL,
    redirect_uri TEXT NOT NULL,
    estado VARCHAR(3) DEFAULT 'ACT' NOT NULL
);
```
 # 📈 **8. Gobernanza por IA en la Base de Datos**

## 📈 **8.1 Validación Automática de Estructuras de Datos**
✅ La IA validará automáticamente que todas las estructuras de la base de datos cumplan con los lineamientos establecidos en este documento.  
✅ Se verificará que las tablas, claves primarias, claves foráneas e índices sigan el esquema de nomenclatura definido.  
✅ Las restricciones de integridad, triggers y auditoría serán revisadas para asegurar su correcto funcionamiento.  
✅ La IA generará reportes automáticos con advertencias y recomendaciones sobre posibles mejoras en la estructura de la base de datos.  

---

## 📈 **8.2 Revisión de Esquemas y Scripts Antes de la Ejecución**
✅ Todos los scripts de creación, modificación o eliminación de estructuras serán analizados por la IA antes de su ejecución.  
✅ Se verificará que los cambios propuestos no generen conflictos de integridad ni afecten la interoperabilidad de la base de datos.  
✅ La IA sugerirá correcciones automáticas si detecta estructuras que no cumplen con los estándares.  
✅ Solo los scripts aprobados podrán ejecutarse en entornos de desarrollo, pruebas y producción.  

---

## 📈 **8.3 Propuesta de Nombres de Objetos en la BD para Aprobación Previa**
✅ Antes de crear nuevas tablas, columnas, índices o cualquier otro objeto en la base de datos, la IA generará una propuesta de nombres basada en los estándares definidos.  
✅ El equipo de arquitectura revisará y aprobará los nombres propuestos antes de proceder con su implementación.  
✅ Se asegurará que los nombres sean claros, representativos del dominio y alineados con las convenciones establecidas.  

---

## 📈 **8.4 Registro y Auditoría de Cambios Estructurales**
✅ Todos los cambios realizados en la base de datos serán registrados en una tabla de auditoría.  
✅ Se guardará la información de qué cambio fue realizado, quién lo ejecutó, cuándo y con qué justificación.  
✅ La IA generará reportes periódicos con un historial de modificaciones y recomendaciones para futuras optimizaciones.  
✅ Se implementará un control de versiones de la estructura de la base de datos para facilitar la trazabilidad.  

```sql
-- Tabla de auditoría de cambios estructurales
CREATE TABLE IF NOT EXISTS auditoria_bd (
    auditoria_id VARCHAR(26) PRIMARY KEY DEFAULT generate_ulid(),
    nombre_objeto VARCHAR(255) NOT NULL,
    tipo_cambio VARCHAR(50) NOT NULL, -- CREACION, MODIFICACION, ELIMINACION
    fecha_cambio TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
    usuario VARCHAR(255) NOT NULL,
    descripcion TEXT
);
```

---

## 📈 **8.5 Aprobación del Comité de Arquitectura para Modificaciones Fuera del Estándar**
✅ Cualquier cambio en la estructura de la base de datos que no esté contemplado en los lineamientos establecidos requerirá aprobación del Comité de Arquitectura.  
✅ En caso de que un cambio sea aprobado, se actualizará este documento para reflejar la nueva norma y garantizar que futuras implementaciones lo tomen en cuenta.  
✅ La IA no procederá con ninguna modificación fuera del estándar sin la debida aprobación y actualización de la documentación.  

## 9️⃣ Cumplimiento y Validación

### 📌 **9.1 Revisión Obligatoria Antes del Despliegue**
👉 Antes de desplegar cualquier cambio en la base de datos, se debe realizar una revisión exhaustiva del script y estructura.

👉 Todos los scripts deben ser validados por el equipo de arquitectura y aprobados según los lineamientos establecidos.

👉 Se deben realizar pruebas en un entorno de staging antes de aplicar los cambios en producción.

---

### 📌 **9.2 Pruebas de Rendimiento e Integridad Antes de Pasar a Producción**
👉 Se deben ejecutar pruebas de rendimiento sobre las consultas y estructuras de datos para evitar degradaciones.

👉 Se utilizará **EXPLAIN ANALYZE** para analizar tiempos de respuesta de las consultas críticas.

👉 Las nuevas estructuras de datos deben someterse a pruebas de carga para garantizar escalabilidad.

👉 Se debe validar la consistencia de los datos antes y después de cualquier migración.

---

### 📌 **9.3 Registro de Cambios en Documentación Oficial**
👉 Todo cambio estructural debe ser registrado en la documentación oficial.

👉 Los scripts de modificaciones deben incluir comentarios explicativos sobre su propósito y efectos.

👉 Se debe actualizar el historial de cambios en el repositorio de documentación.

---

### 📌 **9.4 Plan de Rollback en Caso de Fallos en la BD**
👉 Todo despliegue debe contar con un **plan de rollback** en caso de errores en producción.

👉 Se deben generar **backups previos** antes de realizar cualquier modificación.

👉 Se deben definir estrategias para revertir cambios estructurales sin afectar la integridad de los datos.

🚀 **📌 Cumplir con estas normas garantiza estabilidad, seguridad y consistencia en la base de datos del sistema.**





