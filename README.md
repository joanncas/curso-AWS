# Plan de estudios AWS

Distintas certificaciones según el path. https://d1.awsstatic.com/training-and-certification/docs/AWS_certification_paths.pdf

Curso Cloud practitioner - https://www.udemy.com/course/certified-cloud-practitioner-aws/?couponCode=24T4FS22124

Curso Solutions Architect Associate - https://www.udemy.com/course/certified-solutions-architect-associate-aws/?couponCode=24T4FS22124

Curso Developer Associate - https://www.udemy.com/course/aws-certified-developer-associate-dva/?couponCode=24T4FS22124

Curso DevOps Professional - https://www.udemy.com/course/aws-certified-devops-engineer-professional-hands-on/?couponCode=24T4FS22124

Curso Solutions Architect Professional - https://www.udemy.com/course/aws-solutions-architect-professional/?couponCode=24T4FS22124


Documentación:
- https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html
- https://docs.aws.amazon.com/vpc/latest/userguide/configure-your-vpc.html
- https://docs.aws.amazon.com/IAM/latest/UserGuide/when-to-use-iam.html
- https://docs.aws.amazon.com/IAM/latest/UserGuide/intro-structure.html#intro-structure-authentication
- https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege
- https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html
- https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instances-and-amis.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html
- https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingBucket.html
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html
- https://docs.aws.amazon.com/lambda/latest/dg/welcome.html
- https://docs.aws.amazon.com/lambda/latest/dg/lambda-runtime-environment.html#runtimes-lifecycle
  

## Ejercicios:
1. General
   1. ¿Cuál es la diferencia entre TCP y UDP?
   2. ¿Cuál es la diferencia entre una llave de encriptación asimétrica y simétrica?
2. VPC y subnets
   1. Tendiendo una VPC con CIDR 172.16.0.0/24, distribuirlo equitativamente en 4 subnets.
   2. ¿Puedo conectar una subnet a múltiples Availability zones?
   3. ¿Puedo desplegar una VPC entre múltiples regiones?
   4. ¿Qué diferencia una subnet pública de una privada?
   5. ¿Cómo doy acceso a una subnet privada a internet? Explicar paso a paso.
3. IAM. 
    1. Necesito asignarle permisos a una instancia EC2 para acceder a otros servicios de AWS. ¿Qué debería usar, una policy, un rol o un usuario? ¿Por qué?
    2. Tengo un código de Python que utiliza Boto3 desplegado en mi máquina local, necesito autenticar el Boto3 para acceder a los servicios de AWS. ¿Qué debería usar, una policy, un rol o un usuario? ¿Por qué?
    3.  ¿Por qué usar Least Privilege? 
    4.  ¿IAM puede autenticar y autorizar? Explicar la diferencia entre autenticar y autorizar. Dar un ejemplo y especificar el componente de IAM.
4. Security groups y NACL
    1. Nombra 3 diferencias claves entre Security groups y NACL. 
    2. ¿Puedo asignar un Security group a una subnet?
    3. ¿Puedo asignar un NACL a una instancia EC2?
    4. Se detecta un ataque desde un rango de IP 12.74.128.0/26, ¿Cómo se bloquearía este rango de IP tanto en el NACL como en el Security group?
    5.  Dentro de una instancia EC2 desplegada en una subnet pública, no puedo descargar paquetes de internet. Ya validé y las route tables están correctas. Por favor modificar las tablas con los cambios necesarios para solucionar el problema y resaltarlos (No es necesario remover ninguna regla). 
         
        Tengo el siguiente Security group:
   
        | Source         | Protocol | Port |
        |----------------|----------|------|
        | 192.168.0.0/24 | HTTP     | 8080 |

        | Destination | Protocol | Port |
        |-------------|----------|------|
        | 0.0.0.0/0   | All      | All  |
        
        Y el siguiente NACL:

        **Inbound:**
        | Rule # | Type             | Protocol | Port Range | Source    | Allow/Deny |
        |--------|------------------|----------|------------|-----------|------------|
        | 100    | All IPv4 traffic | All      | All        | 0.0.0.0/0 | ALLOW      |
        | *      | All traffic      | All      | All        | 0.0.0.0/0 | DENY       |

        **Outbound:**
        | Rule # | Type        | Protocol | Port Range  | Source         | Allow/Deny |
        |--------|-------------|----------|-------------|----------------|------------|
        | 100    | HTTP        | TCP      | 32768-65535 | 192.168.0.0/24 | ALLOW      |
        | *      | All traffic | All      | All         | 0.0.0.0/0      | DENY       |

5. EC2.
   1. Necesitas crear múltiples instancias EC2 que requieren tener instalados unos servicios, por ejemplo, Docker, Htop, Python, etc. Al ser múltiples, no puedes usar la consola de AWS ya que sería una carga operacional muy alta. ¿Cuáles son las dos formas de hacerlo y cuál es la más rápida?
   2. ¿Por qué es necesario crear una llave de encriptación simétrica para conectarse a SSH?
   3. ¿Cuál es la diferencia entre instance store y EBS? 
6. Elastic Load Balancer
   1. ¿Cuál es la diferencia entre NLB y ALB?
   2. En un escenario de cliente-servidor con un ELB en medio, ¿qué balanceador usar para lograr end-to-end encryption (terminar la sesión SSL en el servidor)? 
   3. En un escenario de cliente-servidor con un ELB en medio, ¿es posible terminar la sesión SSL y estaría encriptada la comunicación del balanceador al servidor?
   4. Necesito crear un ALB y que me distribuya a dos distintas instancias, donde cada instancia espera un path en específico (por ejemplo, /api/signals y /api/emergency), ¿qué debo crear y configurar?
7. Simple Storage Service (S3)
   1. ¿Cómo hacer la transición de objetos de su storage type una vez cumplan determinado tiempo para reducir costos?
   2. Si necesito guardar multiples veces el mismo archivo, pero sin sobreescribir y en un futuro recuperar una versión antigua, ¿qué tengo que habilitar en el bucket?
   3. ¿Cómo evitar que mi bucket sea público y definirlo solo para un IAM group?
8. Lambda
   1. ¿Cuál es la principal ventaja y desventaja de usar serverless a comparación de EC2?
   2. ¿Qué es el cold start?
   3. Tengo una lambda que debe ser invocada a través de un S3 trigger (ya está configurado) y esta lambda debe acceder a otro bucket de S3. ¿Cuántos y cuáles permisos debo crear y dónde se asignan para que funcione?  
   4. Tengo una lambda X que se invoca de forma sincrona y otra lambda Y asíncrona. ¿Qué diferencias hay cuando fallan las funciones?                      

