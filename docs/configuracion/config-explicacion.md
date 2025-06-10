# 🔧 Explicación Detallada de config.yml

## 📋 Información General

Este archivo de configuración define cómo Continue.dev se conecta con Amazon Bedrock para acceder a múltiples modelos de IA. La configuración está optimizada para el trabajo de un Cloud Engineer, proporcionando acceso a diferentes modelos especializados según el tipo de tarea.

## 🏗️ Estructura del Archivo

### Metadatos del Proyecto
```yaml
name: Local Assistant
version: 1.0.0
schema: v1
```

- **name**: Nombre identificativo de tu configuración
- **version**: Versión de tu configuración (útil para control de cambios)
- **schema**: Versión del esquema de Continue.dev (siempre usar `v1`)

## 🤖 Configuración de Modelos

### Modelo Principal: Claude 4 Sonnet
```yaml
- name: Sonnet 4
  provider: bedrock
  model: us.anthropic.claude-sonnet-4-20250514-v1:0 
  env:
    region: us-east-1
    profile: aws-profile
  roles:
    - chat
    - edit
    - apply
    - summarize
    - autocomplete
```

**🎯 Uso Recomendado**: Modelo principal para tareas complejas
- ✅ Revisión de código avanzada
- ✅ Diseño de arquitecturas
- ✅ Análisis de seguridad
- ✅ Documentación técnica

**Roles Habilitados**:
- `chat`: Conversaciones generales
- `edit`: Edición de código
- `apply`: Aplicación automática de cambios
- `summarize`: Resúmenes de código/documentos
- `autocomplete`: Autocompletado inteligente

### Modelo Premium: Claude 4 Opus
```yaml
- name: Opus 4
  provider: bedrock
  model: us.anthropic.claude-opus-4-20250514-v1:0
```

**🎯 Uso Recomendado**: Tareas que requieren máxima precisión
- ✅ Arquitecturas críticas
- ✅ Revisiones de seguridad complejas
- ✅ Análisis de performance

### Modelo AWS Nativo: Nova Premiere
```yaml
- name: AWS Nova Premiere
  provider: bedrock
  model: us.amazon.nova-premier-v1:0
  roles:
    - chat
    - edit
    - apply
```

**🎯 Uso Recomendado**: Especializado en servicios AWS
- ✅ Configuración de servicios AWS
- ✅ Troubleshooting de AWS
- ✅ Optimización de costos
- ⚠️ **Nota**: No incluye `autocomplete` ni `summarize`

### Modelo de Razonamiento: DeepSeek R1
```yaml
- name: DeepSeek
  provider: bedrock
  model: us.deepseek.r1-v1:0
  roles:
    - chat
    - edit
    - apply
```

**🎯 Uso Recomendado**: Problemas complejos de lógica
- ✅ Debugging complejo
- ✅ Algoritmos avanzados
- ✅ Análisis matemático


**Configuración Requerida**:

1. **Región AWS**: `us-east-1`
   - Región donde están disponibles los modelos de Bedrock
   - Verificar disponibilidad de modelos en [AWS Bedrock Console](https://console.aws.amazon.com/bedrock/)

2. **Perfil AWS**: `aws-profile`
   - Debe estar configurado en `~/.aws/credentials`
   - Requiere permisos para Amazon Bedrock

### Permisos IAM Necesarios
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "bedrock:InvokeModel",
                "bedrock:InvokeModelWithResponseStream"
            ],
            "Resource": [
                "arn:aws:bedrock:us-east-1::foundation-model/us.anthropic.claude-*",
                "arn:aws:bedrock:us-east-1::foundation-model/us.amazon.nova-*",
                "arn:aws:bedrock:us-east-1::foundation-model/us.deepseek.*"
            ]
        }
    ]
}
```

## 📚 Configuración de Contexto

```yaml
context:
  - provider: code
  - provider: docs
  - provider: diff
  - provider: terminal
  - provider: problems
  - provider: folder
  - provider: codebase
```

### Proveedores de Contexto Explicados

| Proveedor | Descripción | Beneficio para Cloud Engineers |
|-----------|-------------|-------------------------------|
| `code` | Código actual en el editor | Análisis del archivo activo |
| `docs` | Documentación del proyecto | Contexto de arquitectura |
| `diff` | Cambios en Git | Revisión de modificaciones |
| `terminal` | Salida de comandos | Debugging de deployments |
| `problems` | Errores del IDE | Solución de problemas |
| `folder` | Estructura de directorios | Comprensión del proyecto |
| `codebase` | Todo el código del proyecto | Análisis completo |

## 🚀 Cómo Replicar Esta Configuración

### Paso 1: Configurar AWS CLI
```bash
# Instalar AWS CLI
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install

# Configurar perfil
aws configure --profile aws-profile
```

### Paso 2: Habilitar Modelos en Bedrock
1. Ir a [AWS Bedrock Console](https://console.aws.amazon.com/bedrock/)
2. Navegar a "Model access"
3. Solicitar acceso a los modelos:
   - Anthropic Claude 4 Sonnet
   - Anthropic Claude 4 Opus
   - Amazon Nova Premiere
   - DeepSeek R1

### Paso 3: Copiar Configuración
```bash
# Ubicación del archivo de configuración
# macOS/Linux: ~/.continue/config.yml
# Windows: %USERPROFILE%\.continue\config.yml

cp config/config.yml ~/.continue/config.yml
```

### Paso 4: Verificar Conexión
1. Reiniciar VS Code
2. Abrir Continue.dev
3. Probar con un comando simple: "¿Qué modelos tienes disponibles?"