# Actividad-evaluable-diagramas-de-casos-de-uso

## Trabajo a realizar:

- Crea el diagrama de uso haciendo uso de platuml, representado los actores y casos de uso que identifiques en los requisitos.
- Describe, haciendo uso de la plantilla, al menos el caso de uso "Sacar dinero", con las interacciones que tiene entre el actor y el caso de uso.
- Responde a las siguiente pregunta:¿Para qué me sirve tener/realizar un diagrama de casos de uso modelando el sistema que se representa? ¿Qué aporta?

```uml
@startuml
actor Cliente as cliente
rectangle Cajero{
   usecase "Validarse en el sistema" as validar
   usecase "Ingresar dinero" as ingresar
   usecase "Transferencia" as transferencia
   usecase "Retirar dinero" as retirar
   usecase "Aviso Saldo Insuficiente" as notificacion
   usecase "Aviso Limite Diario" as notificacion1
}


cliente --> validar
cliente --> ingresar
cliente --> transferencia
cliente --> retirar

ingresar ..> validar : <<include>>
transferencia ..> validar : <<include>>
retirar ..> validar : <<include>>

notificacion .> retirar : <<extends>>
notificacion1 .> retirar : <<extends>>

@enduml
```
