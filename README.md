## Pre-requisitos

1. Tener una cuenta en AWS. Si es la primera vez que usa AWS puede aprovechar la [capa gratuita](https://aws.amazon.com/es/free/) durante un año.
2. Crear un par de claves de acceso (Programmatic access) que correspondan a un usuario con privilegios de Admin[¹] para poder crear recursos.

## Infraestructura


1. Escoge de las herramientas de aprovisionamiento de infraestructura del DevOps roadmap tu elegida, Terraform o Cloud Formation.
2. Crea un nuevo proyecto y define tres entornos: DEV, STAGING, PROD, cada entorno tendrá los mismos componentes de la arquitectura elegida. Cada entorno se engloba dentro de un VPC
3. Describe en infraestructura como código (IaC) lo necesario para crear desde cero y sin interveción manual la siguiente arquitectura propuesta: ([PDF](https://media.amazonwebservices.com/architecturecenter/AWS_ac_ra_web_01.pdf))

![arquitectura-alojamiento-aplicaciones-web](images/aws-web-hosting-architecture.png  "Arquitectura de Alojamiento de aplicaciones web")

Disfruta de lo que se siente crearla y destruirla cuantas veces quieras. 🙃

## Gestión de la configuración
Luego con la infra creada, escoge tu gestor de configuración favorito (Ansible, Puppet, Chef, Salt...) y configura todos los servidores.
Como lo harías a mano. Pero todo a golpe de gestor de configuración. O sea... no cambies un archivo de configuración a mano.
Luego, reconfigurarlos muchas veces más.

## CI / CD

Luego de eso diría que te pongas un pipeline en tu CI/CD favorito. Hazte una web app de prueba en un repo git. Y que tu pipeline compile si tiene que compilar, suba los artefactos al entorno de staging/pre, les haga pruebas y si las pasa que lo despliegue en el entorno de pro.

Estos entornos podrían ser diferentes instancias  o diferentes VPCs en tu cuenta de AWS.

Algo tan sencillo como un hello world, y probar que la llamada a la URL te devuelva eso. O un botón de X color. Lo que sea.

## Contenedores

Luego de eso, me metería en el tema de contenedores, tanto montar la infra para contenedores como que tu CI/CD genere la imagen docker, la suba a un registry y tu orquestador de contenedores la despliegue.

#### Notas

[¹]: Para iniciación rápida a _IaC_ esta es una forma de no tener problemas de permisos pero es una **MUY MALA** práctica. Las cuentas con _Programmatic access_ deben de tener permisos bien pensados. Un par de credenciales filtradas pueden resultar en una cuenta comprometida, destrucción de recursos y facturas sorpresas.