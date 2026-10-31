# App de nutrición · contexto del proyecto

## Quién soy y cómo trabajamos
- Soy Santiago, product designer. No sé programar: explícame todo
  en palabras simples y en español.
- Yo hago la curaduría de diseño; tú propones, construyes y
  cuestionas mis decisiones si no tienen lógica.
- Respuestas cortas y directas.
- Nunca subas cambios a GitHub sin que yo lo pida.
- Cada wireframe nuevo va en un archivo nuevo dentro de
  wireframes/ (hoy-v1, hoy-v2...). No sobrescribas versiones.
- Cada sección (Hoy, Mi plan, Estadísticas, Milo, Onboarding,
  Perfil) se trabaja en su propia sesión.
- Todas las secciones respetan el alcance de la v69 descrito en
  este archivo. Cuando una pantalla muestra otra sección (por
  ejemplo, el recorrido del onboarding mostrando Hoy), usa el
  diseño más reciente de esa sección, sin reinventarlo. Si algo
  nuevo contradice la v69, pregúntame antes.

## Producto
- Web app de nutrición para portafolio. Usuarios en Colombia que
  empiezan su camino fitness. Comen comida local y productos
  importados.
- Problema: no saben cuánto ni qué comer, y medir y registrar es
  tan complejo que abandonan.
- Enfoque: bienestar, sin dietas rígidas. Progreso gradual (mito
  de Milón de Crotona). Lenguaje de recomendación, nunca de
  restricción ni de culpa ("Te recomendamos", nunca "debes").
- Objetivos: perder peso, mantenerlo o ganar masa (sin dirty bulk).
- La app no reemplaza a un nutricionista.

## Arquitectura (referencia: wireframes/hoy-v69.html)
- Barra de navegación = solo lugares: Hoy, Mi plan, Estadísticas.
  A la derecha, el botón de Milo.
- Perfil vive en el avatar del encabezado, no en la barra.
- No hay botón flotante "+". Se registra desde las tarjetas de Hoy.
- Cada elemento tiene un solo trabajo.
- Onboarding: meta obligatoria y datos básicos; el plan de comidas
  es opcional y se puede crear después desde Mi plan.

## Onboarding (referencia: wireframes/onboarding-v23.html)
- La v23 reúne la experiencia completa: onboarding (v15), armar el
  plan de comidas (v21) y el recorrido (v22 ajustado). Las
  variantes están en la v15 y la v21.
- La cuenta se crea antes del onboarding (el login queda fuera).
- Pasos: objetivo → datos básicos (sexo y edad) → medidas
  (estatura, peso actual y "¿A qué peso quieres llegar?") → días de
  ejercicio a la semana → ritmo (botón "Finalizar") → "Calculando
  tu plan" → "Tu plan está listo". Mantener: 4 pasos, sin peso
  meta ni ritmo.
- Números con teclado numérico, solo en cm y kg. Botones "Atrás" y
  "Continuar" del mismo tamaño, sin chevrones. Lenguaje sin siglas.
- "Tu plan está listo": un solo botón principal, "Ir al inicio";
  "Armar mi plan de comidas" es una tarjeta opcional.
- Armar el plan de comidas: formulario de 4 pasos (cuáles comidas →
  tu alimentación → lo que te gusta → cómo cocinas), con barra de
  pasos y una × para salir en cualquier momento. Comidas posibles:
  desayuno, snack de la mañana, almuerzo, snack de la tarde y cena.
  Pendiente: cómo se relaciona con la conversación de Milo en Mi
  plan.
- Recorrido (opcional): al llegar a Hoy, una hoja "Así te ayuda
  Milo" con índice de 4 pasos, "Ver recorrido" y "Ahora no". Pasos:
  tu balance → Mi plan y Estadísticas → Milo AI → registrar (termina
  en "Registrar mi [comida según la hora]"). Usa el Hoy más reciente
  sin cambios; se puede volver a ver desde Perfil.

## Hoy
- Tarjeta de balance: "Calorías consumidas X / 2.000 kcal" con
  barra, y Proteína, Carbos y Grasa en formato "actual / meta".
- "¿Qué quieres registrar hoy?": 3 tarjetas horizontales (Comidas,
  Agua, Suplementos) con título, cantidad ("3 de 5") y un botón
  oscuro con + blanco. Toda la tarjeta es táctil.
- Comidas: drawer con "Del plan" (sin plan: "Lo frecuente") o
  "Algo nuevo".
  - Del plan sin alerta: se registra al tocar y aparece un
    snackbar con Deshacer.
  - Del plan con alerta: pantalla completa con el porqué visible y
    dos opciones: porción ajustada o lo de siempre.
  - Algo nuevo: Cámara, Buscar o Grabar, más recientes en chips.
    Grabar: transcripción editable → análisis → revisar alimentos
    → registrar.
- Agua y suplementos: pantalla completa con el estado actual y la
  medida (vaso o botella; cápsulas).
- "Comidas de hoy": lo registrado, con kcal y lápiz para editar.
- El botón de registrar solo dice "Registrar".

## Mi plan (alcance MVP)
- Plan de comidas según la meta. Se crea en una conversación con
  Milo: cuántas comidas (1, 3 o 5), cuáles, gustos y
  restricciones. Máximo 3 opciones por pregunta.
- Plan activo: comidas con imagen, estado de hoy y constancia de
  la semana. El plan tiene solo las comidas elegidas; lo que falte
  para la meta queda "Fuera de tu plan" y se puede registrar.
- Aquí viven las porciones caseras y las recetas de 3 a 5 pasos
  (solo en comidas que se cocinan), con 2 opciones por comida.
- Sin plan: estado vacío con "Crear mi plan".
- Fuera del MVP: semana variada, meal prep, lista de mercado y
  catálogo de recetas.

## Estadísticas (alcance MVP)
- Meta con plazo calculado (perder según el peso, ver Reglas de
  datos; ganar unos 0,25 kg por semana) y peso una vez por semana.
  El peso vive aquí.
- Tu semana: lunes a domingo (días futuros atenuados), días cerca
  de la meta (±10 %) y una línea de atención sin invitar a
  compensar. Sin rachas.
- Días anteriores en solo lectura.

## Milo (asistente de IA, Beta)
- Se abre desde el botón de la barra.
- 3 opciones: Preparar comida con lo que tengo, Analizar lo que
  como y Analizar mi progreso. Además, un campo libre para
  cualquier pregunta de nutrición.
- En el campo, el + permite galería de fotos, tomar foto o cargar
  archivo.

## Reglas de datos
- Meta de ejemplo: 2.000 kcal. Los números deben ser coherentes.
- Fuentes nutricionales: ICBF (comida colombiana), USDA
  (genéricos), Open Food Facts (marcas). La IA estima porciones;
  los macros salen de la base de datos.
- La alerta de nutrición se activa pasada la hora del almuerzo si
  un macro va por debajo del 50 % de la meta. Se muestra al
  registrar una comida del plan, no como fila en Hoy.
- Los ajustes de porción deben ser realistas y en gramos del
  alimento (ej.: yogur 100 g → 200 g).
- Ritmo para perder peso según el peso de cada persona: Constante
  (recomendado) ≈ 0,7 % del peso por semana y Suave ≈ 0,35 %
  (ej.: 75 kg → medio kilo y un cuarto de kilo). Con metas de más
  de 5 kg se muestra una primera etapa de 5 kg.
- No hay límite de kilos a perder o ganar. La meta se valida con el
  rango saludable del IMC de adultos (18,5 a 24,9) según la
  estatura (ej.: 1,75 m → 57 a 76 kg). Si queda por debajo, una
  alerta explica el riesgo y sugiere el mínimo, sin bloquear.
- Tope por comida del plan: desayuno 550 kcal, cada snack 300,
  almuerzo 700 y cena 600. Si las comidas elegidas no alcanzan la
  meta, la diferencia se muestra como "Fuera de tu plan".
- Calorías mínimas al día: 1.200 (mujeres) y 1.500 (hombres).
  Edad mínima: 18 años.

## Estilo de wireframe
- Solo grises, blanco y negro. Sin colores. Cajas grises como
  placeholder de imágenes. Ancho de celular de 390 px.
- Escala tipográfica: 28 (título y cifra principal), 17 (título de
  pantalla), 15 (sección y elemento), 13 (secundario), 12
  (etiquetas).

## Documento de referencia
- La definición completa está en el documento "App de nutrición ·
  Fase 1: Definición" (fuera de este proyecto). Si algo aquí
  contradice una instrucción mía nueva, pregúntame.
