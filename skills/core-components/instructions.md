# Core Components

Construye una biblioteca de bloques CAD reutilizables en SVG usando `<symbol>` y `<use>`.
Define una vez, instancia en cualquier posición y escala. Equivalente al sistema de
bloques de AutoCAD pero en SVG nativo.

## El sistema de bloques CAD en SVG

```
<defs>
  <symbol id="nombre-bloque" viewBox="...">
    <!-- geometría del bloque en coordenadas locales centradas en 0,0 -->
  </symbol>
</defs>

<!-- Instanciar en cualquier posición -->
<use href="#nombre-bloque" x="posX" y="posY" width="escala" height="escala"/>
```

La clave: el `viewBox` del símbolo define un espacio de coordenadas propio.
`width` y `height` en el `<use>` controlan el tamaño de renderizado sin tocar el símbolo.

## Biblioteca de bloques estructurales

### Apoyo fijo (empotrado)
```svg
<symbol id="apoyo-fijo" viewBox="-15 -5 30 20">
  <line x1="0" y1="0" x2="0" y2="8" stroke="#000" stroke-width="1.5"/>
  <rect x="-12" y="8" width="24" height="4" fill="#444" stroke="#000" stroke-width="0.8"/>
  <!-- Líneas de sombreado -->
  <line x1="-12" y1="12" x2="-8" y2="16" stroke="#444" stroke-width="0.6"/>
  <line x1="-6" y1="12" x2="-2" y2="16" stroke="#444" stroke-width="0.6"/>
  <line x1="0" y1="12" x2="4" y2="16" stroke="#444" stroke-width="0.6"/>
  <line x1="6" y1="12" x2="10" y2="16" stroke="#444" stroke-width="0.6"/>
</symbol>
```

### Apoyo simple (articulado)
```svg
<symbol id="apoyo-simple" viewBox="-12 -5 24 20">
  <line x1="0" y1="0" x2="0" y2="8" stroke="#000" stroke-width="1.5"/>
  <polygon points="0,0 -8,12 8,12" fill="none" stroke="#000" stroke-width="1"/>
  <line x1="-12" y1="12" x2="12" y2="12" stroke="#000" stroke-width="1"/>
  <line x1="-12" y1="12" x2="-8" y2="16" stroke="#444" stroke-width="0.6"/>
  <line x1="-4" y1="12" x2="0" y2="16" stroke="#444" stroke-width="0.6"/>
  <line x1="4" y1="12" x2="8" y2="16" stroke="#444" stroke-width="0.6"/>
</symbol>
```

### Apoyo rodillo (deslizante)
```svg
<symbol id="apoyo-rodillo" viewBox="-12 -5 24 22">
  <line x1="0" y1="0" x2="0" y2="8" stroke="#000" stroke-width="1.5"/>
  <polygon points="0,0 -8,12 8,12" fill="none" stroke="#000" stroke-width="1"/>
  <circle cx="-5" cy="15" r="2" fill="none" stroke="#000" stroke-width="0.8"/>
  <circle cx="0" cy="15" r="2" fill="none" stroke="#000" stroke-width="0.8"/>
  <circle cx="5" cy="15" r="2" fill="none" stroke="#000" stroke-width="0.8"/>
  <line x1="-12" y1="18" x2="12" y2="18" stroke="#000" stroke-width="1"/>
</symbol>
```

### Cimentación superficial (zapata)
```svg
<symbol id="zapata" viewBox="-20 -5 40 30">
  <!-- Columna -->
  <rect x="-5" y="-5" width="10" height="15" fill="#ccc" stroke="#000" stroke-width="0.8"/>
  <!-- Zapata -->
  <rect x="-20" y="10" width="40" height="12" fill="url(#hatch-concreto)" stroke="#000" stroke-width="1"/>
</symbol>
```

### Perfil IPN/IPE (vista transversal)
```svg
<symbol id="perfil-ipn" viewBox="-10 -15 20 30">
  <!-- Ala superior -->
  <rect x="-10" y="-15" width="20" height="3" fill="#888" stroke="#000" stroke-width="0.5"/>
  <!-- Alma -->
  <rect x="-1.5" y="-12" width="3" height="24" fill="#888" stroke="#000" stroke-width="0.5"/>
  <!-- Ala inferior -->
  <rect x="-10" y="12" width="20" height="3" fill="#888" stroke="#000" stroke-width="0.5"/>
</symbol>
```

### Barra de refuerzo (vista transversal)
```svg
<symbol id="barra-acero" viewBox="-4 -4 8 8">
  <circle cx="0" cy="0" r="3.5" fill="#444" stroke="#000" stroke-width="0.5"/>
  <!-- Cruz central para indicar corte -->
  <line x1="-2" y1="-2" x2="2" y2="2" stroke="#000" stroke-width="0.4"/>
  <line x1="2" y1="-2" x2="-2" y2="2" stroke="#000" stroke-width="0.4"/>
</symbol>
```

## Proceso para construir una biblioteca de proyecto

```
1. INVENTARIO   → listar todos los elementos que se repiten en los planos del proyecto
2. NORMALIZAR   → definir tamaño canónico de cada bloque (viewBox centrado en 0,0)
3. CREAR        → escribir cada <symbol> en el <defs> del SVG maestro
4. PROBAR       → instanciar cada bloque una vez para verificar proporciones
5. DOCUMENTAR   → comentario sobre cada símbolo: nombre, viewBox, punto de inserción
```

## Instanciación con escala variable

```svg
<!-- Mismo símbolo a distintas escalas -->
<use href="#apoyo-fijo" x="100" y="200" width="30" height="30"/>   <!-- escala normal -->
<use href="#apoyo-fijo" x="300" y="200" width="20" height="20"/>   <!-- 66% del tamaño -->
<use href="#apoyo-fijo" x="500" y="200" width="40" height="40"/>   <!-- 133% del tamaño -->
```

## Reglas

- El viewBox de cada símbolo debe estar centrado en 0,0 o con el punto de inserción en 0,0
- Nunca poner `fill` o `stroke` hardcodeados en el `<symbol>` si el color puede variar — usar `currentColor`
- Los IDs de símbolos deben ser descriptivos y únicos: `apoyo-fijo`, no `s1`
- Si el símbolo requiere un pattern (como hatch), el pattern también debe estar en `<defs>` globales
- Un símbolo debe ser autocontenido: no debe depender de elementos fuera de su `<symbol>`

## Variaciones

**Biblioteca de proyecto:** un archivo SVG maestro con todos los `<defs>` del proyecto que se incluye en cada plano.

**Biblioteca por norma:** un set de símbolos conforme a NSR-10, ACI 318 o AISC para reutilizar entre proyectos.

**Componentes interactivos:** símbolos con IDs en sub-elementos para activar tooltips o highlights por JavaScript.
