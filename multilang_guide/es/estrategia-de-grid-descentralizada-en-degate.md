---
description: Estrategia de Grid Descentralizada en DEX
---

# Estrategia de Grid Descentralizada en DeGate

### ¿Qué es la Estrategia de Grid?

\
La Estrategia de Grid o trading de Grid es un mecanismo de trading que automatiza la compra y venta dentro de un rango definido. Permite colocar una serie de órdenes de compra y venta dentro de un rango de precios designado; cuando se ejecuta una orden de compra, automáticamente se coloca otra orden de venta en un nivel de Grid superior, y viceversa. La estrategia de Grid funciona mejor en mercados laterales cuando los precios fluctúan regularmente dentro de un rango definido, permitiéndote obtener ganancias con pequeños cambios de precio.

En [DeGate](https://app.degate.com/?utm_source=dcaguidebook), puedes realizar una estrategia de [Grid ](https://app.degate.com/en/grid/USDC/ETH/?utm_source=gridguidebook)descentralizada sin comisiones y de manera auto-custodiada.

{% embed url="https://www.youtube.com/watch?v=uvkBgcWa6zc&t=6s" %}



### Estrategia de Grid en acción: comprando bajo y vendiendo alto Beneficios de la Estrategia de Grid

\
La Estrategia de Grid es popular entre los traders que no tienen el lujo de tiempo o energía para estar observando el mercado constantemente. Algunas de las ventajas notables de la Estrategia de Grid incluyen:

* **Automatización**: Los límites de precio superior e inferior se definen primero, después de lo cual se colocan y ejecutan automáticamente las órdenes de compra/venta de la Grid según el movimiento del precio del activo subyacente. La estrategia de Grid funciona 24/7 (esencialmente comprando bajo y vendiendo alto), generando ganancias pasivas para los traders.
* **Adaptabilidad**: La densidad de la Grid puede optimizarse para diversas circunstancias. A corto plazo, se pueden configurar cientos de Grids para capturar micro ganancias de los cambios de precio del día; a largo plazo, seleccionar un rango mayor puede permitir al trader obtener ganancias del movimiento lateral general.
* **Rentabilidad**: El trading de Grid funciona mejor en mercados laterales cuando el mercado no muestra una tendencia clara. Un trader no necesita necesariamente predecir si el precio del activo en cuestión va a subir o bajar, y no se requiere ninguna intervención una vez que se ha iniciado una estrategia de Grid, salvo para monitorear los resultados.

### Desafíos del Diseño de la Estrategia de Grid (Descentralizada) 

La función de Estrategia de Grid se encuentra comúnmente en los intercambios centralizados (CEX). La ejecución de operaciones es más sencilla en los CEX, ya que los usuarios no tienen la custodia de sus fondos. En el mercado actual, no existen protocolos de trading de Grid descentralizados debido a un par de desafíos:

* Firma de Cartera: Una configuración típica de trading de Grid puede consistir en 2 a 200 niveles de Grid, dependiendo de la entrada del usuario. Cada nivel de Grid representa una orden límite de compra o venta que requiere la firma de la cartera del usuario. Además, la autorización de la firma generalmente toma algunos segundos, lo que puede afectar la ejecución de la orden de Grid donde los mercados se mueven en microsegundos.
* Firma en Vivo Bajo Demanda: En un escenario de mercado en vivo, los precios pueden subir o bajar dentro de un corto período de tiempo. Esto afectará las órdenes de Grid que pueden cambiar de una orden de compra a una de venta, o viceversa. Estas órdenes inversas requerirían la autorización en vivo de la firma del usuario, lo que puede ser difícil de obtener si el usuario está lejos de su computadora.

### Introducción a la Estrategia de Grid Descentralizada 

Para lograr el objetivo de construir una función de estrategia de Grid descentralizada, primero identificamos y definimos las constantes en una configuración estándar de estrategia de Grid.

**Constantes**

* Cantidad por Nivel: Activos asignados para cada nivel de Grid, según lo determinado por la entrada del usuario.
* Desplazamiento de la Grid: Diferencia entre cada nivel de Grid, determinada por el rango de precios y el número de niveles de Grid.
* Desplazamiento de la Orden: Diferencia entre cada orden, creada para el cálculo de órdenes inversas. Equivalente al desplazamiento de la Grid.

**Grids de Compra/Venta**\
Básicamente, la configuración estándar de la estrategia de Grid es un bot de trading bidireccional. Para simplificar las complicaciones con respecto a la firma del usuario, la configuración de la estrategia de Grid se divide en 2 categorías de Grid:

* Grid de Compra: configuración de órdenes de Grid de compra.
* Grid de Venta: configuración de órdenes de Grid de venta.

**Firmas de la Grid**\
El siguiente paso es configurar las firmas de transacción para cada Grid de compra/venta. Las constantes previamente definidas se agrupan en cada firma de transacción de Grid. Críticamente, la firma de la transacción estará vinculada a la primera orden de Grid, que se define como la Grid más cercana al precio de mercado actual, y las órdenes de Grid subsiguientes se configurarán en consecuencia con la autorización de firma de la primera orden de Grid.

Por ejemplo, el precio de mercado actual de ETH es de $2000,

* Para la Grid de Compra: la primera orden de Grid ("Compra 1") se define en el nivel de Grid más cercano a <$2000.
* Para la Grid de Venta: la primera orden de Grid ("Venta 1") se define en el nivel de Grid más cercano a >$2000.

Básicamente, esto resuelve la necesidad de que el usuario firme múltiples transacciones mientras la estrategia de Grid está activa.



{% hint style="info" %}
Ejemplo: ETH/USDC\
El Usuario A configura una estrategia de Grid manual para ETH/USDC en el rango de $1800 - $2300, mientras que el precio actual de ETH es de $2050. Se añaden 10 líneas de Grid con activos asignados de 0.5 ETH y 950 USDC.
{% endhint %}



Como resultado, se configuran 5 Grids de venta y 5 Grids de compra según los parámetros de entrada.

Para la Grid de Venta, el usuario deberá aprobar y firmar la "Firma de Transacción de la Grid de Venta" en el primer nivel de Grid de venta (también conocido como "Venta 1"), lo que permitirá que el mecanismo de la estrategia de Grid configure las órdenes de Grid de venta subsiguientes.

Para la Grid de Compra, el usuario deberá aprobar y firmar la "Firma de Transacción de la Grid de Compra" en el primer nivel de Grid de compra (también conocido como "Compra 1"), lo que permitirá que el mecanismo de la estrategia de Grid configure las órdenes de Grid de compra subsiguientes.

¡El usuario simplemente se relaja y observa cómo la estrategia de Grid ejecuta las diversas órdenes de Grid (esencialmente comprando bajo y vendiendo alto), generando ganancias pasivas para el usuario!

Gracias a este diseño técnico innovador, los usuarios ahora pueden disfrutar de los beneficios del trading de Grid y al mismo tiempo tener la custodia total de sus propios activos.

<figure><img src="../.gitbook/assets/grid gif1 (1).gif" alt=""><figcaption><p>Diseño técnico innovador de la Estrategia de Grid Descentralizada</p></figcaption></figure>

### &#x20;Estrategias para el Trading de Grid

\
Existen 3 estrategias comunes utilizadas en el Trading de Grid que dependen en gran medida de las tendencias del mercado y el rendimiento del activo relacionado.

#### Estrategia de Grid Normal

Esta es mejor desplegada en un mercado fluctuante en el que el activo subyacente se está consolidando o moviéndose en rango. A través de una Estrategia de Grid Normal, el trader puede configurar tanto órdenes de compra como de venta dentro del rango de precios predefinido, obteniendo efectivamente ganancias pasivas de la acción del precio del activo.

<figure><img src="../.gitbook/assets/Normal-Grid-EN-v2m (1) (1).gif" alt=""><figcaption></figcaption></figure>

#### Estrategia de Grid de Compra

Esta estrategia es mejor desplegada en un mercado bajista en el que el precio del token subyacente podría caer más. A través de una Estrategia de Grid de Compra, el trader puede establecer una serie de órdenes de compra por debajo del precio de mercado, permitiéndole comprar el activo a un precio bajo. Además, las órdenes de Grid se convertirán en órdenes de venta si el precio rebota, beneficiando al trader dentro del rango de la Grid.

<figure><img src="../.gitbook/assets/Buy-Grid-v20m (1).gif" alt=""><figcaption></figcaption></figure>



#### Estrategia de Grid de Venta

Esta es similar a la Estrategia de Grid de Compra, pero en una dirección diferente. La Estrategia de Grid de Venta es mejor desplegada en un mercado alcista en el que el token subyacente apreciará más. A través de una Estrategia de Grid de Venta, el trader puede establecer una serie de órdenes de venta por encima del precio de mercado, permitiéndole vender el activo a un precio alto. Además, las órdenes de Grid se convertirán en órdenes de compra si el precio cae, beneficiando al trader dentro del rango de la Grid.

<figure><img src="../.gitbook/assets/Sell-Grid-v3m (1).gif" alt=""><figcaption></figcaption></figure>

### Conclusión

El trading de Grid es una estrategia de trading automatizada que no se ve afectada por emociones y está completamente determinada por el código. Esta estrategia se ejecuta mejor en un mercado lateral, generando ingresos pasivos para los usuarios sin tener que observar constantemente el mercado.

Además, aprovechando el diseño descentralizado de DeGate en su función de estrategia de Grid, los usuarios ahora tendrán la custodia total de sus fondos mientras.



### Guía de Estrategia de Grid

\
La Estrategia de Grid o grid trading es una poderosa herramienta de trading que automatiza la compra y venta dentro de un rango definido. Una estrategia de grid coloca automáticamente órdenes de compra cuando los precios bajan y órdenes de venta cuando suben, permitiéndote capitalizar las fluctuaciones del mercado y generar ganancias.

¿Cómo configurar la Estrategia de Grid en DeGate?

Veamos un ejemplo guiado utilizando el par ETH/USDC.

<figure><img src="../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

### Seleccionar modo de Estrategia de Grid

Hay 2 modos de Estrategia de Grid para elegir:

* Auto: Configura la Estrategia de Grid utilizando parámetros generados automáticamente y recomendados por el sistema.
* Manual: Personaliza los parámetros de la Estrategia de Grid según tus preferencias.

{% hint style="info" %}
Para los nuevos usuarios en la Estrategia de Grid, se recomienda comenzar con el modo \[Auto].
{% endhint %}

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

#### Configurar la Estrategia de Grid \[AUTO]

1 . Haz clic en la pestaña \[Auto].

2 . Ingresa la cantidad a asignar para la Estrategia de Grid \[ETH/USDC]. Ingresa la cantidad en ETH o USDC, y el sistema calculará la cantidad correspondiente para la Estrategia de Grid.

{% hint style="info" %}
Asegúrate de tener suficiente ETH y USDC en tu balance de DeGate.
{% endhint %}

<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

3. Se mostrarán los parámetros recomendados.
4. Haz clic en "Crear Estrategia de Grid" para completar la configuración y comenzar a ganar.

<figure><img src="../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

#### Configurar la Estrategia de Grid \[MANUAL] 

Haz clic en la pestaña \[Manual]. Puedes modificar los parámetros para tu Estrategia de Grid personalizada.

Rango de Precios: Los precios límite superior e inferior definen el rango de precios en el que funcionará la Estrategia de Grid.

Asignación Inicial: La cantidad de fondos para asignar a la Estrategia de Grid. Ingresa la cantidad en ETH o USDC, y el sistema calculará la cantidad correspondiente.

Número de Grids: La cantidad de órdenes de compra y venta que la Estrategia de Grid colocará dentro del rango de precios.

Cantidad por Grid (≥$50): La cantidad de ETH asignada a cada orden de grid.

Haz clic en "Crear Estrategia de Grid" para completar la configuración y comenzar a ganar.

{% hint style="info" %}
Existe un requisito de tamaño mínimo de orden de $50 para cada orden de grid.
{% endhint %}

<figure><img src="../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

Para una rentabilidad óptima, se recomienda configurar la Estrategia de Grid de manera que el precio de mercado actual caiga dentro del rango de precios.

\
