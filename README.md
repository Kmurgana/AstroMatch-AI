-----

# AstroMatch AI ✨

**Donde la astrología y los datos se encuentran para crear conexiones cósmicas.**

AstroMatch AI es una aplicación backend diseñada para calcular la compatibilidad entre personas utilizando sus cartas astrales. El proyecto ingiere datos de nacimiento, genera las cartas natales correspondientes, las almacena de forma estructurada y utiliza algoritmos de matching y un modelo de IA para ofrecer interpretaciones y recomendaciones sobre las relaciones.

## 📜 Concepto

La sinastría, o el estudio de las relaciones a través de la astrología, es una práctica compleja. Este proyecto busca modernizar y escalar este análisis a través de un **pipeline de datos astrológicos**. La idea es simple: transformar la información astral en un formato estructurado (JSON) que pueda ser analizado cuantitativamente, permitiendo un sistema de matching robusto y, finalmente, una capa de inteligencia artificial que pueda "dialogar" e interpretar estos hallazemarks cósmicos.

-----

## 🚀 Características Principales

  * **Generación de Cartas Natales**: A partir de la fecha, hora y lugar de nacimiento, se genera una carta astral completa utilizando la librería `natal`.
  * **Almacenamiento Estructurado**: Cada carta astral se guarda como un objeto JSON en una base de datos, permitiendo consultas complejas y eficientes.
  * **Algoritmo de Matching**: Un sistema de puntuación que analiza la sinastría entre dos cartas, evaluando aspectos clave como las posiciones de los planetas, las casas y los aspectos angulares.
  * **Interpretación con IA**: Una vez que se establece un "match", un modelo de lenguaje (LLM) analiza los puntos fuertes y débiles de la relación y ofrece recomendaciones y diálogos personalizados.

-----

## 🛠️ Stack Tecnológico

  * **Backend**: **Python**
  * **Framework API**: **FastAPI** (Recomendado por su rendimiento y facilidad de uso)
  * **Librería Astrológica**: **natal**
  * **Base de Datos**: **PostgreSQL** (para datos relacionales de usuarios) y **MongoDB** (ideal para almacenar los JSON de las cartas)
  * **IA & LLM**: Integración con APIs como **Google Gemini** o **OpenAI GPT**.
  * **Contenerización**: **Docker**

-----

## 🏗️ Arquitectura del Proyecto

El flujo de datos está diseñado para ser modular y escalable:

1.  **Ingesta de Datos**: Un endpoint de la API recibe los datos de nacimiento del usuario (`/users/register`).
2.  **Procesamiento Asíncrono**: Se dispara una tarea en segundo plano (con Celery, por ejemplo) que utiliza la librería `natal` para generar la carta astral.
3.  **Almacenamiento**: La carta generada se guarda como un documento JSON en la base de datos no relacional, asociada al ID del usuario.
4.  **Motor de Matching**: Otro servicio se encarga de ejecutar periódicamente o bajo demanda el algoritmo de compatibilidad entre los perfiles de la base de datos.
5.  **Capa de IA**: Cuando un usuario consulta un match, la API recopila los datos de ambas cartas y los resultados del matching, los envía a un modelo de IA con un prompt diseñado para la interpretación y recibe la respuesta para mostrarla al usuario.

-----

## 🏁 Cómo Empezar

Sigue estos pasos para levantar el entorno de desarrollo local.

### Prerrequisitos

  * Python 3.9+
  * Docker y Docker Compose (recomendado)
  * Una cuenta de API para el servicio de IA que elijas.

### Instalación

1.  **Clona el repositorio:**

    ```bash
    git clone https://github.com/tu-usuario/astromatch-ai.git
    cd astromatch-ai
    ```

2.  **Crea y activa un entorno virtual:**

    ```bash
    python -m venv venv
    source venv/bin/activate  # En Windows: venv\Scripts\activate
    ```

3.  **Instala las dependencias:**

    ```bash
    pip install -r requirements.txt
    ```

4.  **Configura las variables de entorno:**
    Crea un archivo `.env` a partir del `.env.example` y añade tus credenciales de base de datos y la API key de la IA.

    ```bash
    cp .env.example .env
    ```

5.  **Inicia el servidor:**

    ```bash
    uvicorn app.main:app --reload
    ```

-----

## 🗺️ Roadmap del Proyecto

  * [x] **Fase 1: Core Engine** - Generación y almacenamiento de cartas natales.
  * [ ] **Fase 2: Matching v1** - Implementación de un algoritmo de sinastría básico basado en Sol, Luna y Ascendente.
  * [ ] **Fase 3: Integración con IA** - Conexión con un LLM para generar descripciones básicas de compatibilidad.
  * [ ] **Fase 4: Matching v2** - Algoritmo avanzado que incluya aspectos mayores (conjunción, oposición, etc.) y posiciones en casas.
  * [ ] **Fase 5: Frontend** - Desarrollo de una interfaz de usuario para interactuar con la aplicación.
  * [ ] **Fase 6: Autenticación y Perfiles** - Sistema completo de usuarios.

-----

## 🙌 Contribuciones

¡Las contribuciones son bienvenidas\! Si tienes ideas para mejorar el algoritmo de matching, optimizar las consultas o cualquier otra sugerencia, por favor abre un *issue* para discutirlo o envía directamente un *pull request*.

-----

## 📄 Licencia

Este proyecto está bajo la Licencia MIT.

-----

Espero que esta descripción te sea de gran ayuda, Kevin. ¡Es un proyecto con un enfoque muy original que combina dos mundos apasionantes\! ¡Mucho éxito y que los astros guíen tu código\! 🌌
