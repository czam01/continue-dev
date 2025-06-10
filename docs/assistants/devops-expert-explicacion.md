# 🚀 DevOps Expert Assistant

## 📋 Información General

Este asistente especializado está diseñado para guiar la transformación de organizaciones desde prácticas DevOps tradicionales hacia un modelo **NoOps** avanzado, incorporando **AIOps** (Artificial Intelligence for IT Operations) y automatización inteligente con IA generativa.

## 🎯 Propósito Principal

El DevOps Expert Assistant actúa como un arquitecto experto que ayuda a:
- Diseñar estrategias de transformación DevOps → AIOps → NoOps
- Implementar automatización inteligente y predictiva
- Minimizar la intervención humana en operaciones
- Incorporar IA generativa en pipelines y procesos

## 🏗️ Configuración del Asistente

### Metadatos
```yaml
name: DevOps Expert
version: 0.0.1
schema: v1
```

### Modelos Configurados

#### Claude 4 Sonnet (Modelo Principal)
```yaml
- name: 4 Sonnet
  provider: bedrock
  model: us.anthropic.claude-sonnet-4-20250514-v1:0
  env:
    region: us-east-1
    profile: aws-profile
  roles:
    - chat
    - edit
    - apply
```

**🎯 Uso Específico**:
- ✅ Diseño de arquitecturas complejas NoOps
- ✅ Análisis de madurez organizacional
- ✅ Estrategias de transformación detalladas
- ✅ Roadmaps de implementación

#### AWS Nova Premiere (Modelo Complementario)
```yaml
- name: AWS Nova Premiere
  provider: bedrock
  model: us.amazon.nova-premier-v1:0
  env:
    region: us-east-1
    profile: aws-profile
  roles:
    - chat
    - edit
    - apply
```

**🎯 Uso Específico**:
- ✅ Configuraciones específicas de AWS
- ✅ Servicios nativos de AWS para AIOps
- ✅ Integración con herramientas AWS DevOps

### Contexto Avanzado
```yaml
context:
  - provider: code          # Análisis de código actual
  - provider: docs          # Documentación del proyecto
  - provider: diff          # Cambios en desarrollo
  - provider: terminal      # Salida de comandos
  - provider: problems      # Issues identificados
  - provider: folder        # Estructura del proyecto
  - provider: codebase      # Análisis completo del código
  - provider: currentFile   # Archivo activo
  - provider: search        # Búsquedas en el proyecto
  - provider: url           # Referencias externas
  - provider: clipboard     # Contenido del portapapeles
  - provider: commit        # Historial de commits
  - provider: repo-map      # Mapa del repositorio
```
