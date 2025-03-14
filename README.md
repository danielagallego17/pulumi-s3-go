# Proyecto Pulumi S3 en Go

# Creación de un Bucket en AWS con Pulumi y Go

Este proyecto utiliza **Pulumi** con **Go** para crear un bucket en **AWS S3**.

## Requisitos previos

Antes de comenzar, asegúrate de tener instalados los siguientes elementos:

- [Pulumi CLI](https://www.pulumi.com/docs/install/)
- [Go](https://go.dev/doc/install)
- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) y configurado con credenciales válidas
- Una cuenta de **AWS**
- Git (opcional, pero recomendado)

---

## Pasos para la construcción del bucket

### 1. Inicializar un nuevo proyecto de Pulumi

Si no lo has hecho, inicia un nuevo proyecto en Pulumi:

```sh
pulumi new aws-go

### definir el bucket en el codigo

Abre el archivo main.go y agrega la configuración para crear un bucket en S3: reemplazar el codigo que habia por el codigo siguiente 

package main

import (
	"github.com/pulumi/pulumi-aws/sdk/v5/go/aws/s3"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		// Crear un bucket de S3
		bucket, err := s3.NewBucket(ctx, "myBucket", nil)
		if err != nil {
			return err
		}

		// Exportar el nombre del bucket
		ctx.Export("bucketName", bucket.ID())

		return nil
	})
}

#### instalar dependencias 
Ejecutar el siguiente comando para instalar las dependencias de AWS en Pulumi
(go mod tidy)

configurar pulumi para aws 
Ejecutar el siguiente comando para autenticarte en AWS con Pulumi
(pulumi config set aws:region us-east-1)

Desplegar la infraestructura
Ejecutar el siguiente comando para crear el bucket en AWS:
(pulumi up)
Pulumi te pedirá confirmación antes de aplicar los cambios. Escribe yes y presiona Enter

Verificar el bucket en AWS
Una vez finalizado el despliegue, puedes verificar el bucket en la consola de AWS o con:
(aws s3 ls)

(Opcional) Eliminar el bucket
Si deseas eliminar el bucket creado, puedes ejecutar  el siguiente comando
(pulumi destroy)

¡Listo! Con estos pasos, ya puedes haber creado un bucket S3 en AWS con Pulumi y Go.

todo esto usando visual estudio code y git hub para el repositorio y aws para la creacion del bucket 


