# Auditoría y Compatibilidad de Licencias

## Introducción

ElephanTalk hace uso de diversas bibliotecas, frameworks y herramientas de terceros tanto en el frontend como en el backend. Con el objetivo de verificar el cumplimiento de las licencias de software utilizadas por estas dependencias, se realizó una auditoría de licencias durante el desarrollo del proyecto.

Esta verificación permite mantener un inventario actualizado de las licencias utilizadas y facilitar futuras revisiones cuando se incorporen nuevas dependencias al sistema.


## Herramienta utilizada

La auditoría fue realizada utilizando **ScanCode Toolkit**, una herramienta de código abierto especializada en el análisis de licencias, derechos de autor y paquetes de software.

El análisis fue ejecutado sobre los componentes del frontend y backend con el fin de identificar las licencias presentes en las dependencias del proyecto y generar reportes para su posterior revisión.


## Principales tecnologías analizadas

Las tecnologías principales utilizadas por ElephanTalk emplean licencias ampliamente utilizadas dentro del ecosistema de software libre y de código abierto.

### Frontend

| Tecnología | Licencia |
|------------|----------|
| React | MIT |
| Vite | MIT |
| Tailwind CSS | MIT |

### Backend

| Tecnología | Licencia |
|------------|----------|
| NestJS | MIT |
| FastAPI | MIT |
| Mongoose | MIT |

### Inteligencia Artificial

| Tecnología | Licencia |
|------------|----------|
| Detoxify | Apache License 2.0 |


## Evidencias de la auditoría

Como evidencia del proceso de auditoría se incluyen los reportes generados durante el análisis con ScanCode Toolkit.

Los archivos pueden consultarse en el siguiente repositorio documental:

🔗 **[Auditoría de Licencias](https://ucaedusv-my.sharepoint.com/:f:/g/personal/00162622_uca_edu_sv/IgBRe9gkKkepRLlGaYVuOnrUAUEpLkqm14_l1EtbdGIKC-U?e=EHbMxe)**

Entre los archivos disponibles se encuentran:

- `floss-license-slide.pdf`
- `scan_frontend.json`
- `scan_backend.json`
- `scan_frontend.sqlite`
- `scan_backend.sqlite`
- `scan-frontend-summary.log.txt`

Estos archivos contienen el detalle completo del análisis realizado sobre las dependencias del proyecto.


## Recomendaciones

Para mantener actualizado el cumplimiento de licencias del proyecto se recomienda:

- Ejecutar nuevamente la auditoría después de agregar nuevas dependencias.
- Revisar las licencias antes de actualizar paquetes principales.
- Conservar los reportes de auditoría junto con la documentación técnica del sistema.
- Documentar cualquier cambio significativo relacionado con las licencias de las dependencias.


## Conclusión

La auditoría realizada proporciona un registro del estado de las licencias de las dependencias utilizadas por ElephanTalk y constituye una referencia técnica para el mantenimiento del proyecto y futuras actualizaciones.