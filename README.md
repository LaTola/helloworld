# HelloWorld Calculator - Proyecto DevOps & Cloud

## Descripción

Este repositorio contiene una aplicación web sencilla de calculadora desarrollada en Python con Flask, diseñada para demostrar conceptos fundamentales de DevOps y testing:

- **Pruebas unitarias** con pytest
- **Pruebas de API/servicio** con mocking
- **Integración con Wiremock** para simulación de servicios
- **Pruebas de rendimiento** con JMeter
- **Pipeline de CI/CD** con Jenkins

## Estructura del Proyecto

```
helloworld/
├── app/                    # Código fuente de la aplicación
│   ├── api.py             # API Flask con endpoints REST
│   ├── calc.py            # Lógica de la calculadora
│   └── util.py            # Utilidades y conversiones
├── test/                   # Suite de pruebas
│   ├── unit/              # Pruebas unitarias
│   ├── rest/              # Pruebas de API
│   ├── wiremock/          # Configuración de mocks
│   └── jmeter/            # Pruebas de rendimiento
├── Jenkinsfile*           # Pipelines de CI/CD
├── pyproject.toml         # Configuración de Poetry
├── pytest.ini            # Configuración de pytest
└── requirements.txt       # Dependencias Python
```

## Funcionalidades

### API REST
La aplicación expone los siguientes endpoints:

- `GET /` - Mensaje de bienvenida
- `GET /calc/add/{op1}/{op2}` - Suma dos números
- `GET /calc/substract/{op1}/{op2}` - Resta dos números

### Operaciones Matemáticas
La clase `Calculator` implementa:
- Suma (`add`)
- Resta (`substract`)
- Multiplicación (`multiply`)
- División (`divide`)
- Potencia (`power`)

## Instalación y Configuración

### Requisitos
- Python 3.10+
- Flask
- pytest
- Poetry (opcional)

### Instalación

```bash
# Clonar el repositorio
git clone <repository-url>
cd helloworld

# Instalar dependencias
pip install -r requirements.txt

# O usando Poetry
poetry install
```

## Ejecución

### Ejecutar la aplicación

```bash
# Configurar Flask
export FLASK_APP=app/api.py
export FLASK_ENV=development

# Ejecutar servidor
flask run
```

La aplicación estará disponible en `http://localhost:5000`

### Ejecutar pruebas

```bash
# Todas las pruebas
pytest

# Solo pruebas unitarias
pytest test/unit -m unit

# Solo pruebas de API (requiere servidor ejecutándose)
pytest test/rest -m api

# Con reporte XML
pytest --junitxml=result-unit.xml test/unit
```

## Testing

### Pruebas Unitarias
Ubicadas en `test/unit/`, cubren:
- Operaciones matemáticas básicas
- Validación de tipos
- Manejo de errores
- Casos límite (división por cero, etc.)

### Pruebas de API
Ubicadas en `test/rest/`, verifican:
- Endpoints REST
- Códigos de respuesta HTTP
- Formato de respuestas
- Integración con servicios mock

### Wiremock
Configuración en `test/wiremock/mappings/` para simular servicios externos como el endpoint de raíz cuadrada.

### JMeter
Pruebas de rendimiento configuradas en `test/jmeter/flask.jmx` para evaluar el comportamiento bajo carga.

## Pipeline CI/CD

El proyecto incluye múltiples configuraciones de Jenkins:

- `Jenkinsfile` - Pipeline principal
- `Jenkinsfile-P22-T4` - Configuración específica
- `Jenkinsfile-P22-T6` - Configuración avanzada
- `Jenkinsfile2` - Pipeline alternativo

### Etapas del Pipeline
1. **Get Code** - Obtención del código fuente
2. **Build** - Preparación del entorno
3. **Tests** - Ejecución paralela de pruebas unitarias y de servicio
4. **Results** - Recopilación y publicación de resultados

## Configuración de Desarrollo

### Variables de Entorno
```bash
FLASK_APP=app/api.py
FLASK_ENV=development
PYTHONPATH=.
```

### Marcadores de Pytest
- `@pytest.mark.unit` - Pruebas unitarias
- `@pytest.mark.api` - Pruebas de API
- `@pytest.mark.security` - Pruebas de seguridad

## Contribución

Este proyecto está diseñado con fines educativos para demostrar:
- Buenas prácticas de testing
- Integración continua
- Automatización de pruebas
- Uso de herramientas DevOps

## Autor

**Mantenedor:** Wilbert Iglesias <wiglesias@gmail.com>

---

*Proyecto desarrollado para el curso EU - DevOps & Cloud - UNIR*
