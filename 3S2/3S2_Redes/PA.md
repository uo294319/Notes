
---
# Cableado Estructurado
---

## Jerarquía
1. Subsistema troncal
	1. Repartidor de Interconexion
	2. Repartidor de Campus
	3. Repartidor de Edificio
2. Subsistema de cableado horizontal (Areas de 90m máximo)
	1. Repartidor de Planta
	2. Punto de consolidación (+15m del RP y +5m del TT) (max. 12 TT dobles)
	3. Toma de Telecomunicaciones 
3. Subsistema de área de trabajo
	1. Equipo terminal
---
## Componentes
## Tipos de redes
- Redes pequeñas (< 100 TT) usan cobre
- Redes grandes (> 100 TT)
	- Cobre subsistema horizontal
	- Fibra optica subsistema troncal
### Cobre
- Cable de 4 pares trenzados (UTP, STP)
- Manguera multipar (25, 50, 100 pares)
- Conectores RJ45
- Latiguillos (110-RJ45)
- Categorias. CAT 3, CAT 5e, CAT 6, CAT 6A, CAT 7, CAT 7A
### Fibra
- Cables fibra (monomodo, multimodo de salto de indice, multimodo de indice gradual)
- Conectores de fibra optica (ST, SC, LC)
- Latiguillos, bandejas y acopladores
### Armarios
- Medidos en unidades de rack  1U = 4.45cm
- 19" de ancho
---
## Relación sedes-subsistemas
- RP siempre
- RE si +2 plantas o 2 plantas de mas de $500m$ o 1 planta de más de $1000m$
- RC si más de 1 edificio
---
## Subsistema horizontal
- TT
	- Al menos 1 toma doble por usuario y despacho
	- Al menos 1 toma doble cada $10m^2$ útiles.
	- Al menos 1 toma inalámbrica cada $200m^2$
- RP
	- Distancia máxima de $90m$ entre TT y repartidor de planta
	- Cerca de vertical de edificio. Preferible misma posición en todas plantas.
- Armarios. Al menos 1 unidad para cada:
	- 24 tomas (de 4 pares, para guía pasacable o datos)
	- 12 enlaces de fibra
	- Al menos uno para cada 6 tomas eléctricas a instalar.
	- Al menos 30% de tomas libres para futuros usos.
---
## Subsistema troncal de edificio
- Distancia RE a RP dada por cable.
- Al menos 1 par de fibras por cada 10 TT
- Armarios.A l menos uno para cada 
	- Panel o bandeja.
	- 8 enlaces de fibra para commutadores edificio.
	- 12 enlaces de fibra para bandejas de fibra.
	- 6 tomas eléctricas a instalar.
	- 30% de tomas libres para futuros usos.
---
## Subsistema troncal de Campus
- Distancia maxima RC a RE de $1Km$
- Al menos 1 par de fibras por cada 5 pares de fibra
- Armarios. Al menos uno para cada 
	- panel o bandeja.
	- 12 puntos de fibra.
	- 6 tomas eléctricas a instalar.
	- Al menos 10 para electronica de red y equipos de proveedores
	- Al menos 30% de tomas libres para futuros usos.