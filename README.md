# PhotoArt

App Android (Kotlin + Compose): carrusel de plantillas, elegir foto, sliders y estilizado con IA en tu servidor.

## App
1. Sube esta carpeta a un repositorio de GitHub (rama main).
2. Actions > "Build APK" > descarga el artefacto `PhotoArt-apk`.
3. En la app, escribe la URL de tu servidor y la API key.

## Servidor (`server/`)
Necesita GPU NVIDIA. Ver instrucciones en `server/main.py`.
Para el estilo exacto de tu ejemplo, entrena un LoRA con 20-50 imágenes similares y pásalo con `LORA_PATH`.

## Mejorar y ampliar (Real-ESRGAN)
Los botones "Mejorar 2x" y "Ampliar 4x" usan el endpoint `/upscale` del servidor.
El resultado se limita a 4096 px por lado.

Si al instalar `basicsr` falla con `functional_tensor`, ejecuta una vez:

    sed -i 's/torchvision.transforms.functional_tensor/torchvision.transforms.functional/' \
      $(python -c "import basicsr,os;print(os.path.dirname(basicsr.__file__))")/data/degradations.py

El modelo se descarga solo la primera vez (o define `ESRGAN_PATH` con la ruta del .pth).
