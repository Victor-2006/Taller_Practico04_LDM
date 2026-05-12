# Victor Sánchez, Guillermo Sánchez, Diego González

# Taller_Practico04_LDM

# Propuesta tecnica

# Bloque A: Análisis de Mercado y Selección

## 1. Justifica la elección basándote en el perfil de la empresa (25 empleados, presupuesto ajustado, necesidad de personalización en el etiquetado).

 Elegimos Odoo ya que tiene un precio bastante asequible para una empresa de pocos empleados que en este caso es de 25, permite comenzar con modulos basicos y luego se pueden ir ampliando funcionalidades.

Odoo permite personalizar etiquetas que en este caso serian facturas, recibos...

A diferencia de otras aplicaciones no requiere suscripciones caras, no necesita una infraestructura avanzada y puede desplegarse en servidores cloud

A parte tiene una arquitectura de OpenSource

## 2. Cálculo de TCO: Realiza una estimación a 3 años. No olvidéis incluir:

## Coste de licencias/suscripción.

<img width="1904" height="944" alt="image" src="https://github.com/user-attachments/assets/9f6de24b-7b29-478f-9f71-dda0195afdbe" />

## Coste de implantación (vuestras horas de desarrollo: estima 100h a 40€/h).

Cada desarrollador cobraria 40 € la hora sumando un total de 1.333 € cada uno para llegar a las 100 h entre los 3 desarrolladores

## Coste operativo (Hosting en Google Cloud, AWS, Huawei Cloud o similar).

Elegimos Google Cloud porque asumimos costes mínimos comparados con las demás suscripciones disponibles. Además, tiene un tiempo de lanzamiento más rápido, mayor flexibilidad y escalabilidad, ahorro de costes y seguridad avanzada.


# Bloque B: Diseño de Seguridad RBAC (CE f)

## 1. Diseña la matriz de permisos para los siguientes roles, asegurando el Principio de Mínimo Privilegio:
<img width="606" height="408" alt="image" src="https://github.com/user-attachments/assets/c7a55dcc-3039-4565-9bb6-36605ff54485" />

Administrador: Acceso total.

Comercial: Solo ve sus clientes y presupuestos (Record Rules).

Operario de Almacén: Solo ve stock y albaranes de entrada/salida.

Contable: Puede mirar facturas pero no puede modificar el stock


# Bloque C: Documentación de Explotación (CE i)
## 1. Siguiendo la norma ISO/IEC 26514, redacta un breve Manual de Despliegue para que el responsable de IT de la empresa pueda levantar el sistema en caso de caída. Debe incluir:

El fragmento de docker-compose.yml necesario.

# Versión de Docker Compose utilizada
version: '3.9'

services:

  # Servicio de base de datos PostgreSQL
  db:

    # Imagen oficial de PostgreSQL versión 15
    image: postgres:15

    # Nombre personalizado del contenedor
    container_name: odoo-db

    # Reinicia automáticamente el contenedor si falla
    restart: always

    # Variables de entorno para configurar PostgreSQL
    environment:

      # Nombre de la base de datos
      POSTGRES_DB: odoo

      # Usuario administrador de PostgreSQL
      POSTGRES_USER: odoo

      # Contraseña del usuario PostgreSQL
      POSTGRES_PASSWORD: odoo_password

    # Volumen persistente para no perder los datos
    # aunque el contenedor se elimine
    volumes:
      - postgres_data:/var/lib/postgresql/data

  # Servicio principal de Odoo
  odoo:

    # Imagen oficial de Odoo versión 17
    image: odoo:17

    # Nombre personalizado del contenedor
    container_name: odoo-app

    # Reinicio automático en caso de fallo
    restart: always

    # Odoo depende de PostgreSQL para funcionar
    depends_on:
      - db

    # Puerto publicado:
    # Puerto 8069 del servidor → Puerto 8069 del contenedor
    ports:
      - "8069:8069"

    # Variables de conexión con PostgreSQL
    environment:

      # Nombre del host del contenedor PostgreSQL
      HOST: db

      # Usuario de la base de datos
      USER: odoo

      # Contraseña del usuario PostgreSQL
      PASSWORD: odoo_password

    # Volumen persistente para conservar
    volumes:
      - odoo_data:/var/lib/odoo

    # Declaración de volúmenes persistentes
volumes:

     # Volumen para PostgreSQL
  postgres_data:

    # Volumen para Odoo
  odoo_data:


El comando para realizar un backup de la base de datos PostgreSQL.





