---
tags: [Getting Started, Payments, Request Methods, SEPA Transactions]
---

# Métodos de Pago

Para crear un pago de cliente mediante una Transacción primaria, debe incluir el objeto PaymentMethod en la llamada JSON. Según el tipo de solicitud, realizará algunos cambios en el objeto paymentMethod para reflejar diferentes instrumentos de pago y tipos de transacciones.

Para realizar un pago con tarjeta, utilice el PaymentCardPaymentMethod:

```json
{
  "paymentCard": {
    "number": "5424180279791732",
    "expiryDate": {
      "month": "03",
      "year": "21"
    },
    "securityCode": "977"
  }
}
```

Para aceptar un pago con token, use el PaymentTokenPaymentMethod:

```json
{
  "paymentToken": {
    "value": "1235325235236",
    "function": "DEBIT",
    "securityCode": "977"
  }
}
```

Dentro del objeto PaymentMethod, proporcionará diferentes valores según el tipo de método de pago que se utilice para el pago. Esto define el instrumento de pago que el cliente está utilizando para realizar la transacción. Las opciones disponibles se definen a continuación. Estos se actualizarán periódicamente a medida que haya más métodos de pago disponibles.

Se accede a más información sobre los cambios de carga asociados con cada uno de estos métodos haciendo clic en paymentMethodType.

| paymentMethodType | Descripción                                                                                                                                                                                                          |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| PAYMENT_CARD      | El método de pago Tarjeta de pago cubre todos los tipos y redes de tarjetas de crédito y débito. Su contrato de adquisición comercial le indicará para cuál de las redes de pago puede aceptar pagos.                |
| PAYMENT_TOKEN     | El método de pago del token de pago le permite utilizar un token creado por nosotros, en lugar de los detalles del método de pago real. Se proporciona más información sobre el uso de tokens aquí.                  |
| SEPA A SEPA       | Es la transacción que permite al cliente pagarle a través de una solicitud de banco a banco a través de la red europea SEPA.                                                                                         |
| WALLET            | Habilita el pago a través de una transacción de Wallet. Las transacciones de billetera requieren un objeto PaymentMethod específico. Se proporciona más información sobre este objeto en la sección Pagos de Wallet. |

## Transacciones SEPA

Para usar el tipo de solicitud ```SepaSaleTransaction```, el objeto paymentMethod se reemplaza por el objeto SEPA. El objeto sepa incluye todos los puntos de datos necesarios para ejecutar una transacción SEPA. SEPA significa "Área Única Europea de Pagos" y permite que los pagos se ejecuten inmediatamente entre cuentas bancarias a bajo costo. Actualmente, esta capacidad solo está habilitada para pagos nacionales en Alemania. Se añadirán países adicionales en un futuro próximo.

Debe estar registrado para pagos SEPA y tener un ID de referencia de mandato para proporcionar y completar el objeto de mandato.

El objeto PaymentMethod de SEPA se muestra a continuación:

```json
{
  "sepa": {
    "iban": "DE34500100600032121604",
    "name": "Alan Turner",
    "country": "DEU",
    "email": "AlanTurner@Bonn.com",
    "mandate": {
      "reference": "3JLCSTIG",
      "url": "https://www.fiserv.com",
      "signatureDate": "2020-10-15",
      "type": "SINGLE"
    }
  }
}
```

---

## Ver más

- [Tipos de Solicitud](?path=docs/español/pagos/3-1-tipos-solicitudes.md)
- [Formas de Pagos](?path=docs/español/pagos/3-3-formas-pagos.md)
- [Pos-autorización & Devoluciones](?path=docs/español/pagos/3-4-post-aut.md)
- [3-D Secure](?path=docs/español/pagos/3-5-3d-secure.md)
- [Verificación de Tarjeta](?path=docs/español/pagos/3-6-verificacion-tarjeta.md)
- [Conversion de Moneda](?path=docs/español/pagos/3-7-conversion-moneda.md)
- [Redirección Administrada](?path=docs/español/pagos/3-8-redireccion-administrada.md)
- [Pedidos](?path=docs/español/pagos/3-9-pedidos.md)
- [URL Pago](?path=docs/español/pagos/3-10-pago-url.md)
- [Pagos Recurrentes](?path=docs/español/pagos/3-11-pagos-recurrentes.md)
- [Tokenización](?path=docs/español/pagos/3-12-tokenizacion.md)
- [Códigos de Error](?path=docs/español/pagos/3-13-codigos-error.md)

---
