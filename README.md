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




El comando para realizar un backup de la base de datos PostgreSQL.


MANUAL PARA RECUPERAR EL SISTEMA:
1- Tener previamente Docker y Docker compose
2- Guarda el docker-compose.yml  y ejecuta docker-compose up -d en CMD
3- accede al localhost: 8200
4-docker exec -t db pg_dump -U odoo odoo > backup_odoo.sql 
5- cat backup_odoo.sql | docker exec -i db psql -U odoo odoo



