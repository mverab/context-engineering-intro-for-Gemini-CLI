# Plantilla de Ingeniería de Contexto

Una plantilla completa para empezar con la Ingeniería de Contexto, la disciplina de diseñar contexto para asistentes de codificación de IA para que tengan la información necesaria para realizar el trabajo de principio a fin.

> **La Ingeniería de Contexto es 10 veces mejor que la ingeniería de prompts y 100 veces mejor que la codificación por intuición. Esta versión ha sido optimizada para su uso con Gemini CLI.**

## 🚀 Inicio Rápido

```bash
# 1. Clona esta plantilla
git clone https://github.com/mverab/context-engineering-intro-for-Gemini-CLI
cd context-engineering-intro-for-Gemini-CLI

# 2. Instala y Autentica Gemini CLI
npm install -g @google/gemini-cli
gemini auth

# 3. Configura las reglas de tu proyecto (opcional - se provee plantilla)
# Edita GEMINI_CLI.md para añadir tus directrices específicas del proyecto

# 4. Añade ejemplos (muy recomendado)
# Coloca ejemplos de código relevantes en la carpeta examples/

# 5. Crea tu solicitud de funcionalidad inicial
# Edita INITIAL.md con los requisitos de tu funcionalidad

# 6. Genera un PRP (Prompt de Requisitos de Producto) completo
# En Gemini CLI, ejecuta:
gemini -p "@./.gemini/commands/generate-prp.md" "INITIAL.md"

# 7. Ejecuta el PRP para implementar tu funcionalidad
# En Gemini CLI, ejecuta:
gemini -p "@./.gemini/commands/execute-prp.md" "PRPs/tu-funcionalidad.md"
```

## 📚 Tabla de Contenidos

- [¿Qué es la Ingeniería de Contexto?](#qué-es-la-ingeniería-de-contexto)
- [Estructura de la Plantilla](#estructura-de-la-plantilla)
- [Guía Paso a Paso](#guía-paso-a-paso)
- [Cómo Escribir Archivos INITIAL.md Efectivos](#cómo-escribir-archivos-initialmd-efectivos)
- [El Flujo de Trabajo PRP](#el-flujo-de-trabajo-prp)
- [Uso Efectivo de Ejemplos](#uso-efectivo-de-ejemplos)
- [Mejores Prácticas](#mejores-prácticas)

## ¿Qué es la Ingeniería de Contexto?

La Ingeniería de Contexto representa un cambio de paradigma respecto a la ingeniería de prompts tradicional:

### Ingeniería de Prompts vs. Ingeniería de Contexto

**Ingeniería de Prompts:**
- Se enfoca en redacciones ingeniosas y frases específicas
- Se limita a cómo formulas una tarea
- Es como darle a alguien una nota adhesiva

**Ingeniería de Contexto:**
- Un sistema completo para proporcionar un contexto exhaustivo
- Incluye documentación, ejemplos, reglas, patrones y validación
- Es como escribir un guion completo con todos los detalles

### ¿Por Qué es Importante la Ingeniería de Contexto?

1.  **Reduce los Fallos de la IA**: La mayoría de los fallos de los agentes no son fallos del modelo, son fallos de contexto.
2.  **Asegura la Consistencia**: La IA sigue los patrones y convenciones de tu proyecto.
3.  **Permite Funcionalidades Complejas**: La IA puede manejar implementaciones de varios pasos con el contexto adecuado.
4.  **Autocorrección**: Los bucles de validación permiten a la IA corregir sus propios errores.

## Estructura de la Plantilla

```
context-engineering-intro/
├── .gemini/
│   ├── commands/
│   │   ├── generate-prp.md    # Genera PRPs completos
│   │   └── execute-prp.md     # Ejecuta PRPs para implementar funcionalidades
│   └── settings.local.json    # Permisos de Gemini CLI
├── PRPs/
│   ├── templates/
│   │   └── prp_base.md       # Plantilla base para PRPs
│   └── EXAMPLE_multi_agent_prp.md  # Ejemplo de un PRP completo
├── examples/                  # Tus ejemplos de código (¡crítico!)
├── GEMINI_CLI.md              # Reglas globales para el asistente de IA
├── INITIAL.md               # Plantilla para solicitudes de funcionalidad
├── INITIAL_EXAMPLE.md       # Ejemplo de solicitud de funcionalidad
└── README.md                # Este archivo
```

Esta plantilla no se enfoca en RAG y otras herramientas con ingeniería de contexto porque tengo MUCHO más preparado para eso pronto. ;)

## Guía Paso a Paso

### 1. Configura las Reglas Globales (GEMINI_CLI.md)

El archivo `GEMINI_CLI.md` contiene reglas para todo el proyecto que el asistente de IA seguirá en cada conversación. La plantilla incluye:

- **Conciencia del proyecto**: Leer documentos de planificación, revisar tareas.
- **Estructura del código**: Límites de tamaño de archivo, organización de módulos.
- **Requisitos de testing**: Patrones de pruebas unitarias, expectativas de cobertura.
- **Convenciones de estilo**: Preferencias de lenguaje, reglas de formato.
- **Estándares de documentación**: Formatos de docstrings, prácticas de comentarios.

**Puedes usar la plantilla proporcionada tal cual o personalizarla para tu proyecto.**

### 2. Crea Tu Solicitud de Funcionalidad Inicial

Edita `INITIAL.md` para describir lo que quieres construir:

```markdown
## FUNCIONALIDAD:
[Describe lo que quieres construir - sé específico sobre la funcionalidad y los requisitos]

## EJEMPLOS:
[Lista cualquier archivo de ejemplo en la carpeta examples/ y explica cómo deben ser usados]

## DOCUMENTACIÓN:
[Incluye enlaces a documentación relevante, APIs o recursos de servidores MCP]

## OTRAS CONSIDERACIONES:
[Menciona cualquier trampa, requisito específico o cosas que los asistentes de IA suelen pasar por alto]
```

**Consulta `INITIAL_EXAMPLE.md` para un ejemplo completo.**

### 3. Genera el PRP

Los PRPs (Prompts de Requisitos de Producto) son planos de implementación exhaustivos que incluyen:

- Contexto y documentación completos
- Pasos de implementación con validación
- Patrones de manejo de errores
- Requisitos de pruebas

Son similares a los PRDs (Documentos de Requisitos de Producto) pero están diseñados más específicamente para instruir a un asistente de codificación de IA.

Ejecuta en Gemini CLI:
```bash
gemini -p "@./.gemini/commands/generate-prp.md" "INITIAL.md"
```

Este comando hará lo siguiente:
1.  Leer tu solicitud de funcionalidad
2.  Investigar el código base en busca de patrones
3.  Buscar documentación relevante
4.  Crear un PRP completo en `PRPs/tu-funcionalidad.md`

### 4. Ejecuta el PRP

Una vez generado, ejecuta el PRP para implementar tu funcionalidad:

```bash
gemini -p "@./.gemini/commands/execute-prp.md" "PRPs/tu-funcionalidad.md"
```

El asistente de codificación de IA hará lo siguiente:
1.  Leer todo el contexto del PRP
2.  Crear un plan de implementación detallado
3.  Ejecutar cada paso con validación
4.  Ejecutar pruebas y corregir cualquier problema
5.  Asegurar que se cumplan todos los criterios de éxito

## Cómo Escribir Archivos INITIAL.md Efectivos

### Explicación de las Secciones Clave

**FUNCIONALIDAD**: Sé específico y exhaustivo
- ❌ "Construir un web scraper"
- ✅ "Construir un web scraper asíncrono usando BeautifulSoup que extraiga datos de productos de sitios de comercio electrónico, maneje la limitación de velocidad y almacene los resultados en PostgreSQL"

**EJEMPLOS**: Aprovecha la carpeta `examples/`
- Coloca patrones de código relevantes en `examples/`
- Haz referencia a archivos y patrones específicos a seguir
- Explica qué aspectos deben ser imitados

**DOCUMENTACIÓN**: Incluye todos los recursos relevantes
- URLs de documentación de API
- Guías de bibliotecas
- Documentación de servidores MCP
- Esquemas de bases de datos

**OTRAS CONSIDERACIONES**: Captura detalles importantes
- Requisitos de autenticación
- Límites de velocidad o cuotas
- Errores comunes
- Requisitos de rendimiento

## El Flujo de Trabajo PRP

### Cómo Funciona /generate-prp

El comando sigue este proceso:

1.  **Fase de Investigación**
    - Analiza tu código base en busca de patrones
    - Busca implementaciones similares
    - Identifica convenciones a seguir

2.  **Recopilación de Documentación**
    - Obtiene documentos de API relevantes
    - Incluye documentación de bibliotecas
    - Añade trampas y peculiaridades

3.  **Creación del Plano**
    - Crea un plan de implementación paso a paso
    - Incluye puertas de validación
    - Añade requisitos de pruebas

4.  **Control de Calidad**
    - Califica el nivel de confianza (1-10)
    - Asegura que todo el contexto esté incluido

### Cómo Funciona /execute-prp

1.  **Cargar Contexto**: Lee todo el PRP
2.  **Planificar**: Crea una lista de tareas detallada
3.  **Ejecutar**: Implementa cada componente
4.  **Validar**: Ejecuta pruebas y linting
5.  **Iterar**: Corrige cualquier problema encontrado
6.  **Completar**: Asegura que se cumplan todos los requisitos

Consulta `PRPs/EXAMPLE_multi_agent_prp.md` para un ejemplo completo de lo que se genera.

## Uso Efectivo de Ejemplos

La carpeta `examples/` es **crítica** para el éxito. Los asistentes de codificación de IA funcionan mucho mejor cuando pueden ver patrones a seguir.

### Qué Incluir en los Ejemplos

1.  **Patrones de Estructura de Código**
    - Cómo organizas los módulos
    - Convenciones de importación
    - Patrones de clases/funciones

2.  **Patrones de Pruebas**
    - Estructura de archivos de prueba
    - Enfoques de mocking
    - Estilos de aserción

3.  **Patrones de Integración**
    - Implementaciones de clientes de API
    - Conexiones a bases de datos
    - Flujos de autenticación

4.  **Patrones de CLI**
    - Análisis de argumentos
    - Formato de salida
    - Manejo de errores

### Estructura de Ejemplo

```
examples/
├── README.md           # Explica qué demuestra cada ejemplo
├── cli.py             # Patrón de implementación de CLI
├── agent/             # Patrones de arquitectura de agentes
│   ├── agent.py      # Patrón de creación de agentes
│   ├── tools.py      # Patrón de implementación de herramientas
│   └── providers.py  # Patrón de múltiples proveedores
└── tests/            # Patrones de pruebas
    ├── test_agent.py # Patrones de pruebas unitarias
    └── conftest.py   # Configuración de Pytest
```

## Mejores Prácticas

### 1. Sé Explícito en INITIAL.md
- No asumas que la IA conoce tus preferencias
- Incluye requisitos y restricciones específicas
- Haz referencia a ejemplos abundantemente

### 2. Proporciona Ejemplos Completos
- Más ejemplos = mejores implementaciones
- Muestra tanto qué hacer COMO qué no hacer
- Incluye patrones de manejo de errores

### 3. Usa Puertas de Validación
- Los PRPs incluyen comandos de prueba que deben pasar
- La IA iterará hasta que todas las validaciones tengan éxito
- Esto asegura código funcional al primer intento

### 4. Aprovecha la Documentación
- Incluye documentos oficiales de API
- Añade recursos de servidores MCP
- Haz referencia a secciones específicas de la documentación

### 5. Personaliza GEMINI_CLI.md
- Añade tus convenciones a `GEMINI_CLI.md`
- Incluye reglas específicas del proyecto
- Define estándares de codificación

## Recursos

- [Documentación de Gemini CLI](https://github.com/google/gemini-cli)
- [Mejores Prácticas de Ingeniería de Contexto](https://www.philschmid.de/context-engineering)
