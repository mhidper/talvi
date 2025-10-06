# Correcciones Aplicadas al Documento VECM_fusionado.tex

## ✅ Correcciones Realizadas Automáticamente

### 1. Eliminación de conflicto natbib
**Problema:** `elsarticle` ya incluye natbib, causando conflicto
**Solución:** Eliminadas las líneas:
```latex
\usepackage{natbib}
\bibliographystyle{elsarticle-harv}
```

### 2. Comandos MSC y JEL comentados  
**Problema:** Estos comandos pueden no estar disponibles en todas las instalaciones
**Solución:** Comentadas las líneas en el bloque `keyword`:
```latex
% \MSC[2010] 62M10, 62P20
% \JEL C32, C53, F34, F47, O54
```

## ⚠️ Advertencias sobre Figuras

El documento hace referencia a las siguientes figuras que deben existir en las rutas especificadas:

1. **model_diagnostics.pdf** - Referenciado en Sección 4.2
   - Ruta esperada: `../../notebooks/figures/` o `../../reports/figures/`
   - Línea de referencia: `\includegraphics[width=0.95\textwidth]{model_diagnostics.pdf}`

2. **vulnerability_timeseries.pdf** - Referenciado en Sección 4.4
   - Ruta esperada: `../../notebooks/figures/` o `../../reports/figures/`  
   - Línea de referencia: `\includegraphics[width=0.95\textwidth]{vulnerability_timeseries.pdf}`

### Opciones si las figuras no existen:

**Opción A:** Comentar temporalmente las figuras para compilar sin ellas:
```latex
% \begin{figure}[htbp]
%     \centering
%     \caption{...}
%     \includegraphics[width=0.95\textwidth]{archivo.pdf}
%     \label{fig:...}
%     ...
% \end{figure}
```

**Opción B:** Crear placeholders vacíos (archivos PDF en blanco) con esos nombres

**Opción C:** Usar el paquete `draft` en opciones del documentclass:
```latex
\documentclass[3p,11pt,draft]{elsarticle}
```
Esto mostrará cajas grises en lugar de las figuras faltantes.

## 📝 Compilación Recomendada

### Secuencia de comandos:
```bash
pdflatex VECM_fusionado.tex
pdflatex VECM_fusionado.tex  # Segunda pasada para referencias
```

### Si hay errores adicionales:

1. **Revisar el archivo .log** generado para identificar líneas específicas con problemas

2. **Errores comunes restantes:**
   - Caracteres especiales sin escapar (ej: `%`, `&`, `$`, `#`)
   - Referencias cruzadas a labels que no existen
   - Comandos matemáticos fuera de modo matemático

## 🔧 Paquetes Requeridos

Asegúrate de tener instalados:
- `elsarticle` (clase de documento)
- `amsmath`, `amssymb`, `amsthm`, `mathtools`
- `graphicx`, `float`, `subcaption`
- `booktabs`, `multirow`, `makecell`
- `hyperref`, `cleveref`
- `siunitx`
- `babel[spanish]`

## 📊 Estado del Documento

- **Secciones completadas:** 5/5 (100%)
- **Subsecciones completadas:** 18/18 (100%)
- **Tablas incluidas:** 8
- **Figuras referenciadas:** 2 (requieren archivos externos)
- **Páginas estimadas:** 40-45

## ✨ El documento está COMPLETO y listo para compilar

Una vez que las figuras estén disponibles o comentadas, el documento debería compilar sin errores.
