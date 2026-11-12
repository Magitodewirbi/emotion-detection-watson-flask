# Final project

Detector de emociones con Watson NLP y Flask. Código breve, docstrings y Pylint sin reglas desactivadas. La interfaz y la licencia son las originales de IBM.

## Preparación y tarea 1

La API del curso requiere Skills Network Theia. Haz un fork **público** de https://github.com/ibm-developer-skills-network/oaqjp-final-project-emb-ai y clónalo allí:

```bash
git clone URL_DE_TU_FORK final_project
cd final_project
```

Descomprime este ZIP y copia su contenido sobre ese repositorio, conservando su carpeta .git. Ejecuta todos los comandos siguientes desde final_project:

```bash
python3 -m pip install -r requirements.txt
```

El README ya tiene el título exacto requerido: Final project.

## Tarea 2: función inicial que devuelve response.text

```bash
cp etapas/02_emotion_detection.py emotion_detection.py
python3 -c 'from emotion_detection import emotion_detector; print(emotion_detector("I love this new technology."))' | tee entregables/2b_application_creation.txt
```

Código para entregar: entregables/2a_emotion_detection.txt.

## Tarea 3: formato y emoción dominante

```bash
cp etapas/03_emotion_detection.py emotion_detection.py
python3 -c 'from emotion_detection import emotion_detector; r=emotion_detector("I am so happy I am doing this"); print(r); assert r["dominant_emotion"] == "joy"' | tee entregables/3b_formatted_output_test.txt
```

Código: entregables/3a_output_formatting.txt.

## Tarea 4: paquete EmotionDetection

El paquete y su __init__.py ya están creados.

```bash
rm emotion_detection.py
python3 -c 'from EmotionDetection import emotion_detector; r=emotion_detector("I hate working long hours"); print(r); assert r["dominant_emotion"] == "anger"' | tee entregables/4b_packaging_test.txt
```

## Tarea 5: pruebas de las cinco frases requeridas

```bash
python3 -m unittest -v test_emotion_detection 2>&1 | tee entregables/5b_unit_testing_result.txt
```

Una prueba parametrizada ejecuta cinco subcasos contra Watson real. Código: entregables/5a_unit_testing.txt.

## Tarea 6: Flask en puerto 5000

La versión de esta tarea se conserva en etapas/06_server.py. Ejecuta:

```bash
python3 -m flask --app etapas/06_server.py run --host=0.0.0.0 --port=5000
```

Abre la vista previa del puerto 5000, prueba **I think I am having fun** y guarda la captura real como **6b_deployment_test.png**. Detén el servidor con Ctrl+C. Código: entregables/6a_server.txt.

## Tarea 7: error 400 y texto vacío

El código final devuelve todas las claves con None al recibir HTTP 400 y muestra el mensaje requerido desde Flask:

```bash
python3 server.py
```

Envía el campo vacío y guarda la captura real como **7c_error_handling_interface.png**, mostrando **Invalid text! Please try again!**

Código: entregables/7a_error_handling_function.txt y entregables/7b_error_handling_server.txt.

## Tarea 8: análisis estático

En otra terminal, desde final_project:

```bash
python3 -m pylint server.py | tee entregables/8b_static_code_analysis.txt
```

Código: entregables/8a_server_modified.txt. El servidor final obtuvo **10.00/10** con Pylint 4.1.3 durante la preparación.

## Entrega

Los fragmentos de código ya están en entregables/. Los comandos anteriores generan las salidas reales de terminal. Si un comando falla, corrígelo antes de entregar: tee guarda lo que se imprima, pero no certifica que la prueba pasó.

Sube los archivos a tu fork:

```bash
git add .
git commit -m "Complete emotion detection final project"
git push
```

Para evaluación por IA, entrega los enlaces públicos de GitHub a README.md (tarea 1) y EmotionDetection/__init__.py (tarea 4), los fragmentos y salidas de terminal correspondientes y las dos capturas reales de las tareas 6 y 7.

Para evaluación por compañeros, toma las 16 capturas de código, estructura, terminal e interfaz con los nombres exactos de lab-instructions.md.

## Estado

Este ZIP incluye código final, versiones intermedias, interfaz original y fragmentos listos para copiar. El fork, la subida a GitHub, las predicciones reales y las capturas de Theia quedan pendientes de ejecutar en tu laboratorio. Las verificaciones locales usan respuestas simuladas y validan la lógica, no las predicciones de Watson.

