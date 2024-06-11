# Algoritmo de Colonia de Hormigas (ACO) en una Red de Logística en Bogotá

Este repositorio contiene la implementación y comparación del algoritmo de colonia de hormigas (ACO) junto con otros enfoques de búsqueda, como A* y Dijkstra, para la optimización de rutas de vehículos autónomos de entrega en la ciudad de Bogotá.

## Contenido

1. [Abstract](#abstract)
2. [Introducción](#introducción)
3. [Fundamentos del Algoritmo de Colonia de Hormigas](#fundamentos-del-algoritmo-de-colonia-de-hormigas)
4. [Metodología de Implementación del Algoritmo en la Solución del Problema](#metodología-de-implementación-del-algoritmo-en-la-solución-del-problema)
5. [Desarrollo: Exploración de los Datos](#desarrollo-exploración-de-los-datos)

## Abstract

El algoritmo de colonia de hormigas (ACO) es una estrategia de optimización inspirada en el comportamiento de las hormigas que ha demostrado eficacia en la resolución de problemas combinatorios. A través de la deposición y seguimiento de feromonas, las "hormigas artificiales” construyen soluciones potenciales, actualizando dinámicamente las feromonas para guiar la exploración del espacio de búsqueda. Aplicado en la optimización de rutas para vehículos autónomos en entornos urbanos, el ACO ha destacado por su capacidad para reducir tiempos de entrega y costos operativos.

## Introducción

La implementación y comparación de algoritmos de búsqueda como A* y Dijkstra junto con el algoritmo de colonia de hormigas (ACO) constituye un enfoque crucial para evaluar la eficacia computacional en la optimización de rutas de vehículos autónomos de entrega en la ciudad de Bogotá. Mientras que A* y Dijkstra son reconocidos por su capacidad para encontrar caminos más cortos en grafos ponderados, ACO se inspira en el comportamiento colectivo de las colonias de hormigas para abordar problemas de optimización combinatoria.

Esta investigación se propone comparar el rendimiento de estos enfoques en términos de tiempo de ejecución y calidad de las rutas generadas, así como la distancia recorrida, el número de iteraciones del algoritmo y el tiempo empleado aproximado en encontrar la solución. Al considerar factores como la velocidad y direccionalidad de las calles, carreras y avenidas, se busca optimizar el tiempo y la distancia empleados en la entrega de mercancías. La implementación y evaluación de estos algoritmos ofrecerá información valiosa para mejorar la eficiencia logística y el abastecimiento en la dinámica urbe de Bogotá.

## Fundamentos del Algoritmo de Colonia de Hormigas

El algoritmo de la colonia de hormigas se basa en el comportamiento natural de las hormigas para encontrar la mejor ruta entre un punto de inicio (colonia) y una fuente de alimento (comida). En el contexto del proyecto de optimización de rutas de entrega en Bogotá, el nodo inicial se consideraría el centro de abastecimiento principal y los nodos de entrega serían los destinos de los paquetes.

El funcionamiento del algoritmo implica que las hormigas (representadas como agentes virtuales) exploran diferentes caminos desde el centro de abastecimiento hacia los nodos de entrega. Durante esta exploración, las hormigas depositan feromonas en los caminos recorridos. La cantidad de feromona depositada es proporcional a la calidad del camino (en este caso, la eficiencia en términos de tiempo y distancia).

A medida que más hormigas recorren un camino específico, la concentración de feromonas en ese camino aumenta, lo que lo hace más atractivo para las siguientes hormigas. Este proceso se repite iterativamente, permitiendo que las mejores rutas acumulen más feromonas y, por lo tanto, se conviertan en las preferidas por las hormigas.

Al final de múltiples iteraciones, las rutas con mayor concentración de feromonas representan las mejores opciones de entrega de paquetes, ya que indican los caminos más eficientes en términos de tiempo y distancia. En resumen, el algoritmo de la colonia de hormigas encuentra la mejor ruta entre el centro de abastecimiento y los nodos de entrega mediante la simulación del comportamiento de las hormigas y la aplicación de principios de optimización basados en feromonas.

## Metodología de Implementación del Algoritmo en la Solución del Problema

En este contexto, cada ubicación de entrega (destino) y los puntos clave de la ciudad (intersecciones, centros logísticos, etc.) son considerados como nodos en un grafo. Las conexiones entre los nodos representan las rutas posibles que los vehículos pueden tomar, con una distancia (o tiempo de viaje estimado) y posiblemente otros factores como el tráfico actual asociados a cada arista.

Cada arista en el grafo tiene asociado un nivel de feromonas que indica la calidad de esa ruta en términos de eficiencia y confiabilidad. Estos niveles de feromona pueden ser inicializados con un valor arbitrario o calculados dinámicamente en función de la experiencia pasada de los vehículos en esas rutas. Además, se considera la capacidad limitada de los vehículos para llevar paquetes al planificar las rutas, asegurándose de que no sobrepasen su capacidad durante el viaje.

El algoritmo de las hormigas guía a los vehículos autónomos en la selección de rutas óptimas. Las hormigas (o vehículos) construyen rutas visitando nodos y seleccionando aristas basadas en las feromonas depositadas y en heurísticas locales, como la distancia restante al destino o la capacidad actual del vehículo. Después de que todas las hormigas hayan construido sus rutas, se actualizan los niveles de feromonas en las aristas en función de la calidad de las soluciones encontradas.

La actualización de las feromonas sigue una regla de "evaporación-deposición", donde se considera la tasa de evaporación de la feromona y la cantidad de feromona depositada por cada hormiga. El proceso de búsqueda se repite hasta que se cumple un criterio de terminación, como un número máximo de iteraciones o la convergencia a una solución aceptable.

Finalmente, las rutas obtenidas por los vehículos autónomos se evalúan en función de criterios como la eficiencia en la entrega de paquetes, el tiempo total de viaje y la capacidad utilizada de los vehículos. Estos resultados se comparan con otras técnicas de optimización o con soluciones manuales para validar la efectividad del enfoque propuesto.

## Desarrollo: Exploración de los datos

En el proceso de optimización de rutas de entrega utilizando el algoritmo de las hormigas en el contexto de Bogotá, Colombia, se emplea la herramienta OSMnx, una biblioteca de Python que facilita la interacción con datos geoespaciales de OpenStreetMap (OSM), una plataforma colaborativa de datos cartográficos de acceso libre.

OSMnx simplifica la descarga, manipulación y análisis de datos geográficos, convirtiéndolos en estructuras de datos manejables en Python. Esta biblioteca proporciona acceso a una amplia gama de información geográfica detallada, incluyendo redes de carreteras, nodos y atributos asociados, lo que resulta fundamental para analizar y visualizar redes urbanas.

Al integrar el análisis urbano con algoritmos de optimización como el de las hormigas, se puede abordar eficazmente el estudio del sistema vial de Bogotá. Esta ciudad, una de las más grandes de América Latina, presenta una infraestructura vial compleja que puede ser estudiada con datos geoespaciales proporcionados por OSM.

Utilizando OSMnx, es posible obtener un mapa interactivo que representa la infraestructura vial de Bogotá. Este mapa sirve como base para aplicar el algoritmo de las hormigas, una técnica de optimización inspirada en el comportamiento de las hormigas reales para encontrar el camino más corto entre la colonia y una fuente de alimento.

El algoritmo de las hormigas puede ser aplicado para encontrar rutas óptimas entre puntos de interés en Bogotá, como centros de almacenamiento y puntos de entrega, considerando factores como la distancia, el tiempo de viaje y las condiciones del tráfico.

Para ello, se generan nodos sobre el mapa de Bogotá representando puntos de interés y posibles destinos. Luego, se aplica el algoritmo de las hormigas para determinar las rutas más eficientes para desplazarse entre estos nodos. Este proceso implica simular múltiples "hormigas" virtuales que exploran y seleccionan rutas basadas en criterios predefinidos, como la distancia y la cantidad de feromonas.

## Requisitos de Instalación

Para poder ejecutar este código, necesitarás instalar las siguientes dependencias utilizando pip:

pip install osmnx
pip install networkx
pip install matplotlib

## Contacto

Para cualquier pregunta o sugerencia, no dudes en ponerte en contacto con el equipo de desarrollo:

- Laura Ojeda - [sofojedal@gmail.com](mailto:sofojedal@gmail.com)
- Daniel Velásquez - [danielfvr01@gmail.com](mailto:danielfvr01@gmail.com)
- Santiago Niño - [santiago.nino02.usa@gmail.com](mailto:santiago.nino02.usa@gmail.com)

