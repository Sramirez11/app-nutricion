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
  Perfil) se trabaja en su propia sesión y en sus propios archivos.
  Los archivos hoy-v* (desde la v71) solo tienen el home y el
  registro (alimentos, agua y suplementos); Mi plan, Estadísticas
  y Milo no se dibujan ahí.
- Todas las secciones respetan el alcance de Hoy (hoy-v106, antes
  v69) descrito en este archivo. Cuando una pantalla muestra otra
  sección (por ejemplo, el recorrido del onboarding mostrando Hoy),
  usa el diseño más reciente de esa sección, sin reinventarlo. Si
  algo nuevo contradice Hoy, pregúntame antes.

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

## Arquitectura (referencia: wireframes/hoy-v106.html)
- Barra de navegación = solo lugares: Hoy, Mi plan, Estadísticas.
  A la derecha, el botón de Milo.
- Perfil vive en el avatar del encabezado, no en la barra.
- No hay botón flotante "+". Se registra desde los tabs de Hoy.
- Cada elemento tiene un solo trabajo.
- Onboarding: meta obligatoria y datos básicos; el plan de comidas
  es opcional y se puede crear después desde Mi plan.

## Onboarding (referencia: wireframes/onboarding-v33.html)
- La v33 reúne la experiencia completa: onboarding, armar el plan de
  comidas y el recorrido sobre el Hoy de la v93. Trae arriba un
  prototipo interactivo de "Tu meta". Las demás variantes están en
  la v15 y la v21 y no se han pasado a esta estructura.
- La cuenta se crea antes del onboarding (el login queda fuera). El
  aviso de que la app no reemplaza a un nutricionista va en los
  términos y condiciones de esa experiencia, no en el onboarding.
- Pasos: "¿Qué quieres lograr?" → "Cuéntanos sobre ti" → días de
  ejercicio a la semana → "Tu meta" → "¿Qué comidas haces al día?"
  (botón "Finalizar") → "Calculando tu plan" → "Tu plan está listo".
  Mantener: 4 pasos, sin "Tu meta".
- "Cuéntanos sobre ti": sexo, edad y estatura, en cascada y a todo
  el ancho. En Mantener también va aquí el peso actual.
- Días de ejercicio: la ayuda va en un callout con ícono informativo.
- "Tu meta": "Con estos pesos calculamos tu ritmo.", peso actual y
  "¿A qué peso quieres llegar?". Al tocar "Listo" con los dos pesos
  y una meta saludable aparecen la validación y "¿A qué ritmo
  quieres ir?" con 2 tarjetas (calorías al día, kilos por semana y
  cuándo llegas). Si la meta no es saludable (ver Reglas de datos),
  es igual a su peso o va en contra del objetivo, solo se muestra un
  callout informativo, sin ritmo y con "Continuar" desactivado.
- "¿Qué comidas haces al día?": checks con 4 marcadas (desayuno,
  almuerzo, snack de la tarde y cena) y un callout. Sin contador.
  Reparte las calorías por comida y define las filas de "Tus comidas" en Hoy.
- Números con teclado numérico, solo en cm y kg. Botones "Atrás" y
  "Continuar" del mismo tamaño, sin chevrones. Lenguaje sin siglas.
- "Tu plan está listo": un solo botón principal, "Ir al inicio". La
  tarjeta va en este orden: la meta y cuándo llega ("Perder 3 kg ·
  Llegas a mediados de diciembre") → "Para lograrlo, te recomendamos
  al día" con 2.000 kcal y nutrientes → acordeón cerrado "Calorías
  en tus 4 comidas". Debajo, una tarjeta opcional sin etiquetas:
  "¿Te ayudamos con qué comer?", 3 líneas cortas y el botón con
  borde "Armar mi plan".
- Armar el plan de comidas: formulario de 3 pasos (tu alimentación →
  lo que te gusta → cómo cocinas), porque las comidas ya se eligieron
  en el onboarding. Tiene barra de pasos arriba y una × a la derecha
  del título para salir en cualquier momento. Comidas posibles:
  desayuno, snack de la mañana, almuerzo, snack de la tarde y cena.
- Recorrido (opcional): al llegar a Hoy, una hoja "Así te ayuda
  Milo" con índice de 4 pasos, "Ver recorrido" y "Ahora no". Pasos:
  tu balance → Mi plan y Estadísticas → Milo AI → registrar (termina
  en "Registrar una comida", sin decir qué comida "toca"). Usa el Hoy más reciente
  sin cambios; se puede volver a ver desde Perfil.

## Hoy
- Tarjeta de balance: "Calorías consumidas X / 2.000 kcal" con
  barra, y Proteína, Carbos y Grasa en formato "actual / meta".
- Debajo del balance, 3 tabs solo con el nombre, en chips: Comidas,
  Agua y Suplementos, sin estado ni contador. Siempre abre en Comidas.
- Tab Comidas: no hay botón de Comidas. Cada comida marcada en el
  paso 5 del onboarding es una fila con aire. Vacía: solo imagen,
  nombre y un + oscuro, sin plato, sin "pendiente" ni resaltar según
  la hora. Registrada: lo que comió y un lápiz. Al final, una fila
  punteada "+ Agregar otra comida".
- Nombres de las comidas en toda la app, iguales al onboarding:
  Desayuno, Snack de la mañana, Almuerzo, Snack de la tarde y Cena.
- Registrar una comida: tocar la fila abre un drawer con el nombre
  de la comida y 3 opciones: "Comida del plan" (con el plato), "Nueva
  comida" y "Preparar algo con lo que tengo". Sin plan, las dos últimas.
  - Comida del plan (3 toques: fila → Comida del plan → Registrar):
    pantalla con el plato y sus ingredientes en lista, sin tarjeta
    (Proteína: 2 huevos pericos · Carbohidrato: 1 arepa mediana ·
    Fruta: 1 fruta). Solo si va bajo en proteína: una línea "Bajo en
    proteína · 62 de 140 g" con barra y "Elige tu porción" con dos
    tarjetas horizontales (Ajustada, recomendada, / De siempre), con
    la porción en gramos y el radio a la derecha; la elegida se
    resalta (borde de 2 px y fondo gris). Sin kcal. → snackbar con
    Deshacer. Cada comida se registra una vez al día.
  - Nueva comida: solo "Tomar foto" o "Buscar". Queda en la comida
    que tocó; no se elige el momento.
  - Buscar: resultados con su fuente (ICBF primero), incluidos platos
    completos si están en la base de datos → porción: imagen,
    información nutricional en bloques y "¿Cuánto comiste?" con − y +
    → "Registrar" o "+ Agregar otro alimento".
  - Tu plato (varios alimentos), Cámara, "Ya la comí" y Editar (lápiz)
    usan la misma revisión: total nutricional en bloques y cada
    alimento con su porción debajo ("1 pocillo · 5 kcal") y "✎ Editar",
    más "+ Agregar otro alimento" → Registrar (en Editar, "Guardar" y
    "Quitar esta comida"). Salir con la × con algo agregado pregunta
    "¿Salir sin guardar?".
  - Preparar: abre Milo sabiendo qué comida tocó. Milo propone la
    preparación y termina en "Ya la comí", que abre la revisión con
    los ingredientes llenos. Con la × no se registra nada.
  - "+ Agregar otra comida": drawer "Otra comida" con Tomar foto o
    Buscar y, si hay plan, el aviso "Queda fuera de tu plan y suma a
    tu día" (no restringe). Queda como fila con la etiqueta "Fuera
    del plan". Sin plan funciona igual, sin aviso.
  - Grabar (voz) queda fuera del MVP.
- Tab Agua: sin meta, estado vacío "Aún no defines tu agua" con
  "Definir mi meta", que abre un drawer con "¿Cuántos vasos quieres
  tomar al día?", la recomendación destacada ("Te recomendamos 8 vasos
  al día · Equivalen a 2 litros de agua"), contador y "Guardar". Con
  meta, una sola tarjeta: "6 / 8 vasos" con − y +, barra y abajo "Tu
  meta: 2 litros al día" con "✎ Editar". El + registra al momento con
  Deshacer; sin botón de guardar. Se puede pasar de la meta. Solo
  vasos de 250 ml. Editar la meta abre el mismo drawer sin botón: se
  guarda al cambiarla y confirma con "Meta actualizada".
- Los elementos de selección (radio y check) van a la derecha de la
  tarjeta, salvo los checks de listas para marcar.
- Todos los drawers tienen una × para cerrar y también se cierran
  tocando el fondo. En drawers y pantallas completas, la × va a la
  derecha del título.
- Suplementos tiene dos momentos, separados en el diseño.
- Suplementos, primera vez: su tab muestra el estado vacío "Aún no
  agregas suplementos" con "Agregar suplementos", que abre 3 pasos con el tracker del onboarding (‹ desde el paso 2,
  3 segmentos, "X de 3" y × a la derecha) y un título de 28 sin
  subtítulo.
  1) "¿Qué suplementos tomas?": buscador y "Los más comunes" (sin
     recomendar ninguno). Solo se eligen suplementos de la base de
     datos (no se crean nuevos). Un solo componente: el check.
     Marcar (en la lista o en el buscador) abre de inmediato el
     drawer de dosis; al tocar "Guardar" vuelve al paso 1 y el
     suplemento aparece en "Tus suplementos (X)" con su check, el
     nombre, debajo la dosis ("5 g por toma") y a la derecha un
     botón grande "✎ Editar". "Continuar" se activa con al menos uno.
     Si toca la × con algo añadido, se pregunta "¿Salir sin
     guardar?" (Seguir configurando / Salir).
  2) "¿Qué días los tomas?": arriba la lista de lo elegido (con su
     dosis) y abajo radios para todos: Todos los días / Lunes a
     viernes / Elegir días. Con "Elegir días" se marcan L M M J V S D.
  3) "¿Quieres un recordatorio?": viene activado y con hora por
     defecto (8:00 a. m.); se puede cambiar o apagar. Se pide
     permiso de notificaciones (en iPhone solo si la app está en la
     pantalla de inicio).
  "Confirmar": título y botón dicen "Confirmar"; resumen de
  suplementos, días y recordatorio. Vuelve al tab con el snackbar
  "Confirmamos tus 2 suplementos" y el avance en 0.
- Drawer de dosis (con aire): "Medida" (las unidades que aplican;
  ej.: creatina en gramos o scoop), luego "¿Cuánto tomas cada vez?"
  con − y + oscuros y el valor "5 g por toma" → "Guardar" (al
  editar, también "Quitar de mis suplementos").
- Suplementos, uso diario: en su tab, una sola tarjeta igual a la del
  agua: "1 / 2 suplementos" con barra, una fila con check por
  suplemento (nombre y "5 g por toma"; lo pendiente no viene marcado)
  y abajo "Lunes a viernes · 8:00 a. m." con "✎ Editar", que entra a
  los 3 pasos (solo ahí se agrega, cambia o quita). Marcar registra al
  momento con Deshacer, sin botón. Lo ya tomado se ve con check gris y
  la hora y no se desmarca. Si hoy no toca (ej.: sábado con "Lunes a
  viernes"), la tarjeta dice "Hoy no toca". Si un suplemento tiene
  calorías (ej.: proteína en polvo), suma al balance del día. La dosis
  "solo por hoy" queda fuera del MVP.
- Sin kcal por comida en el home ni en los snackbars de comidas ("Snack
  de la tarde registrado", con Deshacer): el total ya está en el
  balance. El lápiz abre la pantalla de revisión; su botón dice
  "Guardar".
- El botón de registrar solo dice "Registrar".

## Mi plan (alcance MVP, referencia: wireframes/plan-v3.html)
- Plan de comidas según la meta. Se crea con el mismo formulario de
  4 pasos del onboarding (cuáles comidas → tu alimentación → lo que
  te gusta → cómo cocinas) → "Armando tu plan" → resultado →
  "Guardar plan de comidas". No se crea en una conversación con Milo.
- Sin plan: la tarjeta de invitación del onboarding ("Arma con
  nosotros tu plan de comidas") con el botón principal "Armar mi
  plan de comidas", sin la etiqueta "Opcional".
- Con plan: una sola vista para todos (plan creado en el onboarding
  o en Mi plan). Arriba, la constancia de la semana y las comidas de
  hoy con imagen y estado. Abajo, "Tus elecciones" (sección
  informativa con lo elegido) con un solo "Editar", que abre el
  resumen "Tus respuestas" del onboarding.
- El plan tiene solo las comidas elegidas; lo que falte para la meta
  queda "Fuera de tu plan" y se puede registrar.
- Aquí viven las porciones caseras y las recetas de 3 a 5 pasos
  (solo en comidas que se cocinan), con 2 opciones por comida.
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
- Estadísticas muestra el progreso y es la fuente de verdad; Milo
  lo explica. No se elimina ni se reemplaza por Milo.
- El peso se registra aquí y, como atajo, también diciéndoselo a
  Milo ("Hoy peso 72,4"). Las dos vías guardan en el mismo lugar.

## Milo (asistente de IA, Beta)
- Se abre desde el botón de la barra.
- 3 opciones: Preparar comida con lo que tengo, Analizar lo que
  como y Analizar mi progreso. Además, un campo libre para
  cualquier pregunta de nutrición.
- En el campo, el + permite galería de fotos, tomar foto o cargar
  archivo.
- "Analizar mi progreso" interpreta los datos de Estadísticas (el
  porqué y qué sigue), sin mostrar cifras distintas. Milo no es un
  panel de estadísticas: lo básico no depende de la IA.
- "Preparar algo con lo que tengo" también se abre desde una comida
  en Hoy: es la misma conversación, sabe qué comida tocó y termina en
  "Ya la comí".
- Atajo: registrar el peso por chat, con confirmación de lo que Milo
  entendió; se guarda en Estadísticas.

## Reglas de datos
- Meta de ejemplo: 2.000 kcal. Los números deben ser coherentes.
- Fuentes nutricionales: ICBF (comida colombiana), USDA
  (genéricos), Open Food Facts (marcas). La IA estima porciones;
  los macros salen de la base de datos.
- La alerta de nutrición se activa pasada la hora del almuerzo si
  un macro va por debajo del 50 % de la meta. Se muestra al abrir
  "Comida del plan", no como fila en Hoy.
- Los ajustes de porción deben ser realistas y en gramos del
  alimento (ej.: yogur 100 g → 200 g).
- Ritmo para perder peso según el peso de cada persona: Constante
  (recomendado) ≈ 0,7 % del peso por semana y Suave ≈ 0,35 %
  (ej.: 75 kg → medio kilo y un cuarto de kilo). Con metas de más
  de 5 kg se muestra una primera etapa de 5 kg.
- No hay límite de kilos a perder o ganar. La meta se valida con el
  rango saludable del IMC de adultos (18,5 a 24,9) según la
  estatura (ej.: 1,75 m → 57 a 76 kg). Si al perder la meta queda
  por debajo del rango, o al ganar queda por encima, no se muestra
  "¿A qué ritmo quieres ir?": solo un texto informativo explica el
  riesgo y sugiere el peso recomendado, y "Continuar" queda
  desactivado hasta corregir la meta.
- Tope por comida del plan: desayuno 550 kcal, cada snack 300,
  almuerzo 700 y cena 600. Si las comidas elegidas no alcanzan la
  meta, la diferencia se muestra como "Fuera de tu plan".
- Calorías mínimas al día: 1.200 (mujeres) y 1.500 (hombres).
  Edad mínima: 18 años.

## Estilo de wireframe
- Aplica solo a los wireframes (carpeta wireframes/). La alta
  fidelidad sigue el DESIGN.md.
- Solo grises, blanco y negro. Sin colores. Cajas grises como
  placeholder de imágenes. Ancho de celular de 390 px.
- Escala tipográfica: 28 (título y cifra principal), 17 (título de
  pantalla), 15 (sección y elemento), 13 (secundario), 12
  (etiquetas).

## Línea visual de alta fidelidad (referencia: diseno/linea-visual-v6.html)
- Todo diseño en alta fidelidad (carpeta diseno/) sigue el DESIGN.md:
  colores, estados, tipografía, espaciados, radios, sombras,
  componentes y reglas de uso. Si algo nuevo lo contradice,
  pregúntame. La regla de "solo grises" aplica solo a los wireframes.
- El contexto de producto para Impeccable está en PRODUCT.md.
- Resumen del DESIGN.md:
- Acento: cobalto. Claro #2442D4 (texto blanco en botones). Oscuro
  #90A3FF (texto del botón #11131A). Cumple WCAG AA en los dos.
- Fondo cálido: claro #F5F2EC, oscuro #131210. El acento va solo en
  la barra de calorías, la pestaña activa, el radio, el cursor y el
  botón principal.
- Foco y selección: borde de 2 px en el color del texto, no en el
  acento.
- Base Apple, color Wise, datos MacroFactor, íconos 3D (Airbnb) solo
  en tipos de comida, estados vacíos y bienvenida, y animación
  (Revolut) solo al registrar.

## Documento de referencia
- La definición completa está en el documento "App de nutrición ·
  Fase 1: Definición" (fuera de este proyecto). Si algo aquí
  contradice una instrucción mía nueva, pregúntame.
