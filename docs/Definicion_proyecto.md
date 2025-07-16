# Comando del Hogar

## Objetivo

Desarrollar un un sistema de contabilidad personal
para el hogar que simplifica el registro de transacciones y proporcione una visión clara
de la situacion financiera familiar

## Alcance

Permitir el registro de gastos, ingresos y transferencias simples
a través de un bot de Telegram, almacenar los registros en una base de datos PostgreSQL en la nube.
Tambien se podrá consultar vencimiento de deudas/servicios y  
usando el principio de partida doble, y mostrará un Estado de Resultados y un Balance de Situacion patrimonial básicos
en un Dashboard de Streamlit

## Requerimientos funcionales


### Macro-Requerimientos 1: Gestión de Entidades Fundamentales (Core Entities)
- **RF 1.1:** El sistema debe permitir la creacion, lectura, actualización y borrado de usuarios.
- **RF1.2:** El sistema debe permitir la gestión de un plan de cuentas de usuarios.
- **RF 1.3:** El sistema debe permitir la gestión de métodos de pago asociados a un usuario.
- **RF 1.4** El sistema debe permitir la gestión de proveedores de servicios.

### Macro-Requerimientos 2: Motor Contable y Registro de Transacciones
- **RF 2.1** Por cada operación financiera, el sistema debe generar al menos dos asientos en un Libro Diario 
- **RF-2.2:** El sistema debe permitir a un usuario autorizado registrar un Gasto Simple (débito a una cuenta de gasto, crédito a una cuenta de activo/pasivo) a través del bot.
- **RF-2.3:** El sistema debe permitir a un usuario autorizado registrar un Ingreso Simple (débito a una cuenta de activo, crédito a una cuenta de ingreso) a través del bot.
- **RF-2.4:** El sistema debe permitir a un usuario autorizado registrar una Transferencia entre Cuentas Propias (débito a una cuenta de activo, crédito a otra cuenta de activo).

### Macro-Requerimiento 3: Gestión de Facturas y Servicios
- **RF-3.1:** El sistema debe permitir el registro de una Factura de Servicio con su proveedor, monto y fecha de vencimiento, asignándole un estado inicial de "pendiente".
- **RF-3.2** El sistema debe ser capaz de procesar una imagen de una factura (OCR) para extraer automáticamente los datos del proveedor, monto y vencimiento.
- **RF-3.3:** El sistema debe permitir "pagar" una factura pendiente, lo cual debe generar la transacción contable correspondiente y actualizar el estado de la factura a "pagada".
- **RF-3.4:** El sistema debe enviar una notificación automática (ej. por Telegram) al usuario X días antes del vencimiento de una factura pendiente.

### Macro-Requerimiento 4: Macro-Requerimiento 4: Reporting y Visualización de Datos
- **RF-04.1:** El dashboard debe mostrar un Estado de Resultados para un período de tiempo seleccionable (ej. mes actual), detallando el total de Ingresos, el total de Gastos y el Resultado Neto.
- **RF-04.2:** El dashboard debe mostrar un Balance de Situación Patrimonial a una fecha determinada, mostrando los saldos de las cuentas de Activo, Pasivo y Patrimonio Neto.
- **RF-04.3:** El dashboard debe permitir visualizar el saldo actual de cada Método de Pago (cuentas bancarias, billeteras, etc.).
- **RF-04.4:** El dashboard debe presentar un gráfico de breakdown de gastos por categoría para un período de tiempo seleccionable.

### Macro-Requerimientos 5: Funcionalidades Avanzadas de Planificacion
- **RF-05.1:** El sistema debe permitir a un usuario crear un Presupuesto Mensual, asignando montos límite a diferentes categorías de gasto.
- **RF-05.2:** El dashboard debe mostrar el progreso del presupuesto en tiempo real, comparando el gasto real con el monto asignado para cada categoría.
- **RF-05.3:** El sistema debe permitir la configuración de Transacciones Recurrentes (ej. sueldo, alquiler, suscripciones) para que se generen automáticamente en la fecha correspondiente.
- **RF-05.4:** El sistema debe proveer una proyección de flujo de caja para los próximos 30 días, basada en el saldo actual, las transacciones recurrentes y un promedio de gastos variables históricos.

### Macro-Requerimiento 6: Analítica Avanzada y Machine Learning
- **RF-6.1** (ML - Clasificación de Transacciones): El sistema debe incluir un modelo de Machine Learning que sugiera automáticamente la categoría de un gasto basado en su descripción textual.
- **RF-6.2** (ML - Detección de Anomalías): El sistema debe implementar un modelo que alerte al usuario sobre transacciones anómalas o sospechosas.
- **RF-6.3** (ML - Forecasting de Gastos): El sistema debe ser capaz de proyectar el gasto total para el resto del mes en una categoría específica, basado en el gasto actual y los patrones históricos.

## Requerimientos no funcionales

### Usabilidad
- **RNF-U1**: Los usuarios deben poder crear una estructura tabular básica en menos de 5 minutos de entrenamiento
- **RNF-U2**: El sistema debe proporcionar mensajes de error claros y descriptivos para operaciones inválidas

### Portabilidad
- **RNF-P1**: El sistema debe ser compatible con Java 8 o versiones superiores
- **RNF-P2**: El sistema debe funcionar en Windows y Linux

### Seguriidad
- **RNF-S1**: Las operaciones de copia profunda deben garantizar independencia total de memoria
- **RNF-S2**: El sistema debe manejar archivos CSV malformados sin terminar abruptamente

### Mantenibilidad
- **RNF-M1**: Las operaciones de filtrado deben ser extensibles para nuevos operadores de comparación

### Performance
- **RNF-PE1**: La importación de archivos CSV debe procesar al menos 1,000 filas por segundo

### Funcionalidad
- **RNF-F1**: El sistema debe incluir mecanismos de medición de tiempo de ejecución a la hora de leer archivos externos

### Dependencia

---

## 👥 Autor

- **Agustin Rebechi** - [AgustinRebechi](https://github.com/AgustinRebechi) 