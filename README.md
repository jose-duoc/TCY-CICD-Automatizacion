# 🧪 Ejecución de Pruebas Automatizadas con Selenium

![Python](https://img.shields.io/badge/Python-3.10-blue?style=for-the-badge&logo=python)
![Selenium](https://img.shields.io/badge/Selenium-4.0+-green?style=for-the-badge&logo=selenium)
![GitHub%20Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-black?style=for-the-badge&logo=githubactions)

Este repositorio contiene el ecosistema de pruebas automatizadas basadas en **Selenium WebDriver** y **Python 3.10**. Está estructurado para ejecutar validaciones e integraciones del sistema de forma tanto local como remota mediante pipelines automatizados de CI/CD.

---

## 📂 Estructura del Proyecto

El repositorio se compone de los siguientes módulos y archivos clave:

* **`.github/workflows/`**: Contiene las definiciones de automatización para la integración continua (GitHub Actions).
* **`integraciones/`**: Módulos encargados de conectar las pruebas con servicios de terceros o endpoints del ecosistema.
* **`tests/`**: Suite de casos de prueba organizados y preparados para su ejecución unitaria o funcional.
* **`main.py`**: Orquestador principal y punto de entrada que inicializa el Driver de Selenium y dispara la suite de pruebas completa.
* **`requeriments.txt`**: Archivo de manifiesto con todas las dependencias y librerías de Python requeridas.
* **`Evidencia.png`**: Captura de pantalla estática que sirve como testigo visual del correcto funcionamiento de las pruebas de interfaz de usuario.
* **`LICENSE`**: Licencia formal del repositorio.

---

## 🛠️ Configuración e Instalación Local

Para clonar y ejecutar estas pruebas en tu entorno de desarrollo local, sigue estos pasos:

1.  **Clonar el repositorio:**
    ```bash
    git clone [https://github.com/tu-usuario/tu-repositorio.git](https://github.com/tu-usuario/tu-repositorio.git)
    cd tu-repositorio
    ```

2.  **Crear y activar un entorno virtual (Recomendado):**
    ```bash
    python -m venv venv
    # En Windows:
    .\venv\Scripts\activate
    # En Linux/macOS:
    source venv/bin/activate
    ```

3.  **Instalar las dependencias:**
    ```bash
    pip install -r requeriments.txt
    ```

4.  **Ejecutar la suite de pruebas:**
    ```bash
    python main.py
    ```

---

## 🚀 Integración Continua (GitHub Actions)

El repositorio incluye un Workflow automatizado llamado **"Ejecución de pruebas de Selenium"** configurado para ejecutarse en entornos limpios de Ubuntu.

### Detalles del Pipeline (`workflow_dispatch`)
Este flujo se activa de forma **manual** mediante el botón de despacho en la pestaña *Actions* de GitHub o puede ser gatillado de manera remota a través de una llamada API (`POST /repos/{owner}/{repo}/dispatches`) desde servidores externos.

#### Pasos del Job (`pruebas`):
1.  **Descargar código:** Descarga el código fuente usando la acción oficial `actions/checkout@v4`.
2.  **Configurar PYTHONPATH:** Inyecta la raíz del espacio de trabajo en el entorno global para evitar fallos de importación interna entre `tests/` e `integraciones/`.
3.  **Configurar Python:** Despliega un entorno aislado de **Python 3.10** mediante `actions/setup-python@v5`.
4.  **Instalar Dependencias:** Actualiza `pip` e instala de forma limpia todos los requerimientos listados en el archivo `requeriments.txt`.
5.  **Ejecutar Test:** Lanza el script ejecutor principal `python main.py`.

---

## 📊 Evidencias de Ejecución

El script está diseñado para interactuar con la interfaz gráfica del navegador de manera "headless" (sin interfaz visible) en el servidor de GitHub. Cualquier falla o éxito crítico genera registros detallados, tomando capturas de interfaz como la muestra almacenada en `Evidencia.png`.
