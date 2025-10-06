# Instrucciones para Compilar el Documento con Bibliografía

## Archivos Creados

1. **references.bib** - Archivo con 67 referencias bibliográficas en formato BibTeX
2. **VECM_fusionado.tex** - Documento principal actualizado con:
   - Configuración de biblatex en formato APA
   - Citas integradas usando comandos \\citet{} y \\citep{}
   - Comando \\printbibliography para generar la lista de referencias

## Cómo Compilar el Documento

Para generar el PDF con la bibliografía correctamente formateada, debes ejecutar la siguiente secuencia de comandos:

```bash
# 1. Compilación inicial con pdflatex
pdflatex VECM_fusionado.tex

# 2. Procesamiento de la bibliografía con biber
biber VECM_fusionado

# 3. Segunda compilación para actualizar referencias
pdflatex VECM_fusionado.tex

# 4. Tercera compilación para finalizar cross-references
pdflatex VECM_fusionado.tex
```

### Alternativa con latexmk (recomendado)

Si tienes latexmk instalado, puedes usar:

```bash
latexmk -pdf -bibtex VECM_fusionado.tex
```

## Formato de Citas

El documento usa el estilo APA con dos tipos de citas:

- **\\citet{key}** - Cita narrativa: "Engle y Granger (1987) establecieron..."
- **\\citep{key}** - Cita parentética: "...desarrollado previamente (Engle & Granger, 1987)"

Para citas múltiples: \\citet{key1,key2}

## Verificación

Para verificar que las citas funcionan correctamente:

1. Busca advertencias de "Citation ... undefined" en el log
2. Revisa que el archivo VECM_fusionado.bbl se genere correctamente
3. Confirma que la sección "Referencias" aparece al final del PDF
4. Verifica que las citas en el texto tengan hipervínculos a la bibliografía
