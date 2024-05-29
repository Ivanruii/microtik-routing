---
title: "Enrutamiento entre routers Microtik "
description: "Trabajo de subida de nota módulo MSI"
pubDate: "Jul 08 2022"
heroImage: "/blog-routing-1.png"
---

#### Trabajo de subida de nota módulo MSI - Iván Ruiz Zorrilla

### Estructura de red a realizar:

![](/post-routing/Screenshot_1.png)

### Esquema con direcciones IP e interfaces para la posterior realización de la estructura:

![](/blog-routing-1.png)

### Notas:

- Crear direccionamientos para cada interfaz.

- Usando eth15 como interfaz para las redes LAN.

- Creación de rutas estáticas desde R1 hacia R3.

- R2 es el que conoce las rutas de ambos lados y redirige las peticiones de R1 hacia R3 y viceversa.

### Creando direcciones y rutas en R1 (6A:8B:26:DC:91:4D)

#### Address List:

Creadas las direcciones de las interfaces de R1 y RAL 1

![](/post-routing/Screenshot_2.png)

#### Route List:

Se crean las rutas para poder acceder a R2 y R3 y para poder acceder a la RAL 1 desde otra red.
Tal y como lo he organizado la RAL 1 está en la interfaz ether15.

![](/post-routing/Screenshot_3.png)

### Creando direcciones y rutas en R2 (A6:88:F8:DF:AC:20)

#### Address List:

Creando las direcciones IP para la interfaz que conecta con la RAL 2, R1 y R3.

![](/post-routing/Screenshot_4.png)

#### Route List:

Creadas las rutas para poder conectar R1 con R3. R2 es el router más importante y el que hace que las conexiones de una punta a otra funcionen, También hay que poner las rutas de RAL 1, RAL 2 y RAL 3.

Las rutas de RAL 1 y RAL 3 crean poniendo de gateway la correspondiente interfaz visible más cercana a R2 y después crear las rutas desde el siguiente router que redireccione a esta red.

Ejemplo: Para acceder a RAL 3 desde R2 hay que poner como gateway 10.12.12.2/30 que es la interfaz de R3.

![](/post-routing/Screenshot_5.png)

### Creando direcciones y rutas en R3 (FA:E2:0A:C6:56:87)

#### Address List:

Creadas las direcciones de las interfaces de R3 y RAL 3

#### Route List:

Se crean las rutas para poder acceder a R1 y R2 y para poder acceder a la RAL 3 desde otra red.

Tal y como lo he organizado la RAL 3 está en la interfaz ether15.

![](/post-routing/Screenshot_6.png)

### Comprobaciones:

#### R1 - 6A:8B:26:DC:91:4D

##### R1 --> R2

![](/post-routing/Screenshot_7.png)

##### R1 --> R3

![](/post-routing/Screenshot_8.png)

##### R1 --> RAL 1

![](/post-routing/Screenshot_9.png)

##### R1 --> RAL 2

![](/post-routing/Screenshot_10.png)

##### R1 --> RAL 3

![](/post-routing/Screenshot_11.png)

#### R2 - A6:88:F8:DF:AC:20

##### R2 --> R1

![](/post-routing/Screenshot_12.png)

##### R2 --> R3

![](/post-routing/Screenshot_13.png)

##### R2 --> RAL 1

![](/post-routing/Screenshot_14.png)

##### R2 --> RAL 2

![](/post-routing/Screenshot_15.png)

##### R2 --> RAL 3

![](/post-routing/Screenshot_16.png)

#### R3 - FA:E2:0A:C6:56:87

##### R3 --> R1

![](/post-routing/Screenshot_17.png)

##### R3 --> R2

![](/post-routing/Screenshot_18.png)

##### R3 --> RAL 1

![](/post-routing/Screenshot_19.png)

##### R3 --> RAL 2

![](/post-routing/Screenshot_20.png)

##### R3 --> RAL 3

![](/post-routing/Screenshot_21.png)
