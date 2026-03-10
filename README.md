## Análisis de Violaciones SOLID

| Principio | Método/Sección afectada | Descripción de la violación | 
| ----- | ----- | ----- | 
| **SRP** | `calculateTotal` + `applyDiscount` + `saveOrder` + `sendEmail` + `printReport` | La clase asume 5 responsabilidades completamente distintas: lógica de negocio , reglas de descuento, persistencia de datos, notificación externa y formato de presentación. Esto viola el Principio de Responsabilidad Única, ya que la clase tiene múltiples razones para cambiar. | 
| **OCP** | `applyDiscount` (if/else sobre customerType) | El uso de condicionales estrictos (`if/else`) para el tipo de cliente viola el Principio de Abierto/Cerrado. Si el negocio decide agregar un nuevo tipo de cliente (ej. "PLATINUM"), es obligatorio modificar el código fuente de esta clase, en lugar de extender el comportamiento mediante nuevas clases abstractas o interfaces. | 
| **DIP** | Toda la clase (dependencias internas sin abstracciones) | La clase depende de detalles de implementación concretos (como instanciar `new ArrayList<>()` y usar `System.out.println` directamente para bases de datos y "emails"). Viola el Principio de Inversión de Dependencias porque un módulo de alto nivel que es el procesamiento de órdenes está fuertemente acoplado a módulos de bajo nivel, en lugar de depender de abstracciones inyectadas. |
