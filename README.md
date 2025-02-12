# Actividad-evaluable-diagramas-de-casos-de-uso

## Trabajo a realizar:

- Crea el diagrama de uso haciendo uso de platuml, representado los actores y casos de uso que identifiques en los requisitos.
- Describe, haciendo uso de la plantilla, al menos el caso de uso "Sacar dinero", con las interacciones que tiene entre el actor y el caso de uso.
- Responde a las siguiente pregunta:¿Para qué me sirve tener/realizar un diagrama de casos de uso modelando el sistema que se representa? ¿Qué aporta?


## Diagrama de uso con platumlm
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

![](https://cdn-0.plantuml.com/plantuml/dpng/VP11IyD048Nl-oiUlRVWLKgfr4l1auhtOJCj8vjPcDaKGVplXcmDMTIU4jvyxy6tUozaPUXJe5YouP24jJ384UjlC8w5z9mO1tfdovy1mE0SoHchDqhIaJc35PpWueLxMe4Sbtfh-AEUZPqCdIXRdZYfMGk-6gcVs5YZrBcoJ1hscOjOksarQh27YtZ62wKkuwW-d2HEYbD1Sv4ne2XP_sWzII-5yIXaadyLxi9N2E7wObYlTxFxCgkURTXQBI-pGlZfOREPXt6FxLOqfg7ZtIuqApUuw-OD8YozC6ArKZ7-AAoTZrXZ_p-s7xz3dxu1)


### Caso de Uso: Sacar dinero
#### Flujo:
1. El cliente hace la peticion de validarse.
2. El sistema valida la identidad del cliente.
3. El cliente selecciona "Retirar dinero".
4. El sistema solicita la cantidad de dinero a retirar.
5. El cliente introduce la cantidad a retirar.
6. El sistema verifica si el saldo es suficiente.
7. El sistema tambien verifica si se a excedido el limite diario.
8. Si es suficiente y no se a excedido el limite, el sistema emite el dinero y actualiza el saldo.
9. El sistema informa al cliente sobre la transacción y permite la retirada.

#### Flujos Alternativos:
- **Saldo Insuficiente**: Si el saldo es insuficiente, el sistema muestra un mensaje y no se realiza la transacción.
- **Límite Diario Excedido**: Si se supera el límite, el sistema muestra un mensaje de "Límite diario alcanzado".

### ¿Para qué sirve un diagrama de casos de uso?

Un diagrama de casos de uso sirve para facilitar la visualización de cómo los usuarios interactúan con el sistema, ayudando a los desarrolladores a comprender mejor el flujo del sistema. Es una buena base clara para desarrollar y documentar las funcionalidades del sistema, a la vez que permite identificar los requisitos que debe cumplir en diferentes situaciones. También ayuda a detectar posibles fallos o escenarios no cubiertos en el flujo de trabajo y sirve como referencia para realizar pruebas funcionales del sistema.
