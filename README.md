## Análisis de Violaciones SOLID

| Principio | Método/Sección afectada | Descripción de la violación | 
| ----- | ----- | ----- | 
| **SRP** | `calculateTotal` + `applyDiscount` + `saveOrder` + `sendEmail` + `printReport` | La clase asume 5 responsabilidades completamente distintas: lógica de negocio , reglas de descuento, persistencia de datos, notificación externa y formato de presentación. Esto viola el Principio de Responsabilidad Única, ya que la clase tiene múltiples razones para cambiar. | 
| **OCP** | `applyDiscount` (if/else sobre customerType) | El uso de condicionales estrictos (`if/else`) para el tipo de cliente viola el Principio de Abierto/Cerrado. Si el negocio decide agregar un nuevo tipo de cliente (ej. "PLATINUM"), es obligatorio modificar el código fuente de esta clase, en lugar de extender el comportamiento mediante nuevas clases abstractas o interfaces. | 
| **DIP** | Toda la clase (dependencias internas sin abstracciones) | La clase depende de detalles de implementación concretos (como instanciar `new ArrayList<>()` y usar `System.out.println` directamente para bases de datos y "emails"). Viola el Principio de Inversión de Dependencias porque un módulo de alto nivel que es el procesamiento de órdenes está fuertemente acoplado a módulos de bajo nivel, en lugar de depender de abstracciones inyectadas. |

## Maven corriendo
<img width="1029" height="420" alt="image" src="https://github.com/user-attachments/assets/bbae5aa9-81c2-4771-980e-ed2f4d737f73" />

## Funcionando 
<img width="1019" height="362" alt="image" src="https://github.com/user-attachments/assets/03887482-4d8a-4def-b2ed-5ca867935c05" />
