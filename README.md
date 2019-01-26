Empieza por la parte de automatización, yo creo imho que es la primera puerta que abren los que venimos de sistemas.
Plantea una arquitectura cualquiera que brinde X servicio(s), ponle todo tipo de recursos y softwares.
Móntalo en AWS y no toques el dashboard web más que para crearte la cuenta y las credenciales para las llamadas a la API.
Escoge tu herramienta favorita (Terraform, Ansible, Chef, Puppet...) y describe toda tu infra cómo código.
VPCs, subredes, grupos de seguridad, usuarios, balanceadores, bases de datos, VPNs, etc... TODO.
Disfruta de lo que se siente crearla y destruirla cuantas veces quieras. 🙃
Luego con la infra creada, escoge tu gestor de configuración favorito (Ansible, Puppet, Chef, Salt...) y configura todos los servidores.
Como lo harías a mano. Pero todo a golpe de gestor de configuración. O sea... no cambies un archivo de configuración a mano.
Luego, reconfigurarlos muchas veces más.

Luego de eso diría que te pongas un pipeline en tu CI/CD favorito. Hazte una web app de prueba en un repo git. Y que tu pipeline compile si tiene que compilar, suba los artefactos al entorno de staging/pre, les haga pruebas y si las pasa que lo despliegue en el entorno de pro.

Estos entornos podrían ser diferentes instancias  o diferentes VPCs en tu cuenta de AWS.

Algo tan sencillo como un hello world, y probar que la llamada a la URL te devuelva eso. O un botón de X color. Lo que sea.

Luego de eso, me metería en el tema de contenedores, tanto montar la infra para contenedores como que tu CI/CD genere la imagen docker, la suba a un registry y tu orquestador de contenedores la despliegue.