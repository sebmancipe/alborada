# Mosaico de emociones (prototipo)

Un mosaico de 6 fotos de un mismo protagonista. La cámara detecta hacia dónde mira la persona y, después de 1,2 s mirando una foto, la música cambia con un crossfade hacia la capa de esa emoción.

## Cómo abrirlo

1. Haz doble clic en **`iniciar.command`**. La primera vez, macOS puede bloquearlo: clic derecho → Abrir → Abrir.
   Se abre Chrome en `http://localhost:8000`.
2. Elige **"Empezar con la mirada"** y acepta el permiso de cámara.
3. Calibra: haz clic 5 veces en cada uno de los 9 puntos **mirándolo fijamente**.
4. Presiona **F** para ver en pantalla completa y **H** para ocultar la interfaz.

Si no quieres usar la cámara, "Probar con el mouse" funciona igual y sirve para revisar fotos y música.

WebGazer (3.5.3) viene incluido en la carpeta (`webgazer.js` y `mediapipe/`), así que funciona sin internet. Si en la barra de abajo aparece "Seguimiento: sin datos", revisa que tu cara se vea bien y recalibra con C.

**Teclas:** I muestra la leyenda · G muestra el punto de mirada · C recalibra · M cambia entre mirada y mouse · H oculta todo · F pantalla completa

## Emociones (orden del mosaico)

| # | Emoción | Foto (qué fotografiar) | Música de prueba |
|---|---------|------------------------|------------------|
| 1 | Calma | Luz suave de mañana, mucho espacio vacío, tonos fríos claros | Pad ambient Lam9 → Fa maj7 con campanas lejanas |
| 2 | Alegría | Luz cálida, movimiento, color saturado, brazos abiertos | Arpegio brillante Do–Sol–Lam–Fa con bombo suave |
| 3 | Ansiedad | Encuadre apretado, diagonales, desenfoque de movimiento | Dron grave en La + Si♭ disonante, tic-tac, latido |
| 4 | Tristeza | Contraluz, desaturado, sujeto pequeño en el cuadro | Piano escaso y descendente Lam–Fa–Rem–Mi |
| 5 | Ira | Contraste duro, rojos, luz lateral, primer plano | Bajo distorsionado con bombo pesado |
| 6 | Esperanza | Luz que entra (ventana o amanecer), gesto hacia afuera | Progresión ascendente Fa–Do–Sol–Lam con brillo |

El arco narrativo es: calma → alegría → ansiedad → tristeza → ira → esperanza.

**Integración:** todas las fotos comparten la **línea de horizonte al 62 % de la altura**. Mantén ese recurso cuando dispares las fotos reales: una mesa, un borde o el horizonte a la misma altura, el mismo protagonista y una prenda o color que se repita.

Las 6 pistas de música las generé yo y son libres de derechos. Todas están en **72 BPM y en la misma tonalidad (La menor / Do mayor)**, con loops de 40 s que suenan siempre sincronizados; solo cambia el volumen. Por eso el cambio entre emociones suena como una sola pieza.

## Cómo reemplazar con tus fotos y música

- **Fotos:** reemplaza los archivos de `fotos/` usando los mismos nombres, en formato horizontal 3:2 (por ejemplo 1200×800 o más).
- **Música:** reemplaza los archivos de `musica/`. Para que las transiciones suenen bien, conviene que todas tengan el mismo tempo, la misma tonalidad y la misma duración de loop.
- **Nombres, textos y tiempos:** se cambian en el bloque `CONFIGURACIÓN` al inicio del `<script>` en `index.html`, con estas variables: `DWELL_MS`, `FADE_MS`, `SMOOTH_N` y `BED_VOL` (pon 0.05 si quieres que las otras emociones se escuchen muy bajito de fondo).

## Montaje para la exposición

- Usa una pantalla grande en lugar de un proyector, una webcam a la altura de los ojos sobre la pantalla, luz frontal suave sobre la cara del espectador y audífonos.
- Funciona con **una persona a la vez**, a unos 50–70 cm de distancia. Calibra con cada persona nueva (tecla C).
- Si la precisión no alcanza, sube `DWELL_MS` a 1500–2000. Otra opción es pasar a seguimiento por orientación de la cabeza con MediaPipe, que es más robusto.
