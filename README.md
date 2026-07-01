# Proyecto QUBO-QAOA: matching bipartito 4x4

Qubit.mx — QMexico Summer School 2026, proyecto final.

> Estado: plantilla inicial. El dataset real todavía no ha sido elegido — ver
> `SPECIFICATION.md` y `data/README.md` para los siguientes pasos.

## Dataset
Nombre del dataset: TODO
Fuente oficial o confiable: TODO
Institución responsable: TODO
URL de la fuente: TODO
URL raw del CSV usado en data/: TODO (URL raw de GitHub una vez subido)
Licencia o condiciones de uso: TODO
Fecha de consulta: TODO
Dominio del problema: TODO (salud, vivienda, empleo, servicios urbanos, educación, ...)

## Modelado
Conjunto A: TODO
Criterio para elegir exactamente 4 elementos de A: TODO
Conjunto B: TODO
Criterio para elegir exactamente 4 elementos de B: TODO
Definición de x_ij = 1: TODO
Interpretación de x_ij = 0: TODO

## Matriz de score
Columnas usadas: TODO
Fórmula exacta de S_ij: TODO
Normalización aplicada: TODO
Matriz S 4x4: TODO (pegar tabla una vez calculada)

## Restricciones
Restricción por filas: cada elemento de A se asigna exactamente una vez.
Restricción por columnas: cada elemento de B recibe exactamente una asignación.
Otras restricciones, si existen: TODO
Justificación de por qué el problema es matching bipartito: TODO
Justificación de por qué es razonable modelarlo como QUBO: TODO

## Resultados
Solución clásica exacta: TODO
Resultado QAOA local: TODO
Comparación clásico vs QAOA local: TODO
Si se usó hardware real o pipeline híbrido, comparación adicional: TODO (opcional)

## Ética y limitaciones
Riesgos éticos: TODO
Medidas de mitigación: TODO
Limitaciones del modelo: TODO

## Ejecución
Instrucciones para abrir el archivo .ipynb en Google Colab: abrir
`proyecto_qubo_qaoa.ipynb` desde este repositorio con Colab (`Abrir en Colab` o
File → Open notebook → GitHub), o clonar el repositorio y abrirlo localmente.
Instrucciones para ejecutar todas las celdas sin errores: `Runtime → Run all`.
El CSV en `data/dataset_real_4x4.csv` debe poder leerse sin intervención manual.
