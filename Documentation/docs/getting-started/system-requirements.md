# Requisitos del Sistema

Para garantizar una experiencia óptima y el funcionamiento correcto de ElephanTalk, es esencial cumplir con los siguientes requisitos según tu caso de uso.

### Sistema operativo

**Recomendado:**

- Windows 10 o posterior
- macOS (versiones recientes)
- Distribuciones recientes de Linux

### Navegadores web requeridos

**Navegadores compatibles:**

- Google Chrome (versión más reciente)
- Mozilla Firefox (versión más reciente) 
- Safari (versión más reciente)
- Microsoft Edge (versión más reciente)

!!! warning "Importante"
    En otros navegadores, el proyecto podría no funcionar de forma correcta.
    Mantener el navegador actualizado es crucial no solo para la compatibilidad con ElephanTalk, sino también para beneficiarse de las últimas mejoras en seguridad y rendimiento.

---

## Para desarrolladores

### Entorno de desarrollo

Para desarrollar y mantener el sistema de ElephanTalk, se deben cumplir con los siguientes requisitos:

### Requisitos de software

#### Node.js
- **Versión**: Node.js 20.x
- **Uso**: Frontend en React y backend en NestJS
- **Descarga**: [Node.js 20.9.0 (LTS)](https://nodejs.org/en/blog/release/v20.9.0)
- **Recomendación**: Mantener actualizado a la versión estable más reciente de la serie 20.x

#### Python
- **Versión**: Python 3.10
- **Uso**: API de FastAPI para moderación
- **Descarga**: [Python 3.10.11](https://www.python.org/downloads/release/python-31011/)
- **Recomendación**: Mantener actualizado dentro de la serie 3.10

### Frameworks y herramientas

- **NestJS**: Versión estable más reciente compatible con Node.js 20.x
- **React**: Versión estable más reciente compatible con Node.js 20.x  
- **FastAPI**: Versión estable más reciente compatible con Python 3.10
- **GeoJson**: Tener registrado el geojson en el schema correspondiente de mongo db, respetando el modelo de dicho schema ejemplo:
````
[
    {
        "featureType": "department",
        "shapeName": "San Salvador",
        "shapeID": "SV-ADM1-01",
        "shapeGroup": "ElSalvadorMap",
        "adminLevel": "ADM1",
        "geometry": {
            "type": "Polygon",
            "coordinates": [
                [
                    [
                        -89.3,
                        13.7
                    ],
                    [
                        -89.2,
                        13.7
                    ],
                    [
                        -89.2,
                        13.6
                    ],
                    [
                        -89.3,
                        13.6
                    ],
                    [
                        -89.3,
                        13.7
                    ]
                ]
            ]
        },
        "properties": {
            "population": 1000000,
            "source": "gov-geojson"
        }
    },
    {
        "featureType": "municipality",
        "shapeName": "Municipio Ejemplo",
        "shapeID": "SV-MUN-001",
        "shapeGroup": "ExampleGroup",
        "adminLevel": "ADM2",
        "geometry": {
            "type": "MultiPolygon",
            "coordinates": [
                [
                    [
                        [
                            -89.25,
                            13.7
                        ],
                        [
                            -89.24,
                            13.7
                        ],
                        [
                            -89.24,
                            13.69
                        ],
                        [
                            -89.25,
                            13.69
                        ],
                        [
                            -89.25,
                            13.7
                        ]
                    ]
                ],
                [
                    [
                        [
                            -89.26,
                            13.71
                        ],
                        [
                            -89.255,
                            13.71
                        ],
                        [
                            -89.255,
                            13.705
                        ],
                        [
                            -89.26,
                            13.705
                        ],
                        [
                            -89.26,
                            13.71
                        ]
                    ]
                ]
            ]
        },
        "properties": {
            "population": 12345,
            "source": "example-data",
            "notes": "MultiPolígono compuesto por dos polígonos (islas/enclaves)"
        }
    }
]
````

### Herramientas de desarrollo

#### IDE/Editor de código
- Visual Studio Code
- WebStorm
- PyCharm
- Cualquier editor que soporte JavaScript y Python

#### Control de versiones
- Git (versión más reciente)

#### Gestores de paquetes
- **npm**: Para dependencias de Node.js
- **pip**: Para dependencias de Python

#### Contenedores
- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

> Nota:
    Estos requisitos aseguran que los desarrolladores cuenten con un entorno de trabajo adecuado para implementar, probar y mantener las aplicaciones de ElephanTalk de manera eficiente.