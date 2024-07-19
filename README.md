
## Generando-Secuencias-de-Notas-Musicales-con-MusicVae-y-maquinas-preentrenadas
En ese repositorio se encuentra toda la explicación de nuestro proyecto final para generar secuencias de notas a partir de inteligencia artificial

>Cesar Maure, Bolivar Peña, Carlos 

## **Introducción**
>Se han desarrollado numerosos enfoques de aprendizaje automático generativo para la música simbólica, utilizando diversas arquitecturas de red y representaciones de notas musicales. Sin embargo, no existe un consenso sobre la mejor forma de representar la música simbólica ni sobre si transponer las secuencias de entrenamiento a una única tonalidad o a múltiples tonalidades mejora los resultados. Muchos investigadores eligen una opción sin explorar si otras podrían mejorar la calidad de la música generada o acelerar el entrenamiento.

>Para investigar este asunto, reimplementamos la arquitectura MusicVAE y la entrenamos con conjuntos de datos tratados de diferentes maneras. Descubrimos que nuestras dos modificaciones mejoraron tanto el tiempo de entrenamiento como el rendimiento en comparación con la implementación original. Obtuvimos resultados similares en secuencias de 2 compases y una prueba de escucha a ciegas confirmó que la música generada es indistinguible de la creada por humanos. Esto demuestra que las elecciones en la representación y tratamiento de los datos pueden influir significativamente en el rendimiento de las redes neuronales generativas y subraya la necesidad de más comparaciones con otras arquitecturas, además del Autoencoder Variacional que utilizamos.


## **EXPLICACIÓN DEL REPOSITORIO**
>Este repositorio contiene el código, una reimplementación del MusicVAE del equipo de Google Magenta. Se puede usar para generar nueva música e interpolar entre secuencias musicales existentes o generadas aleatoriamente mediante una interfaz de línea de comandos. Además, todo el código para generar conjuntos de datos de entrenamiento en varias configuraciones y entrenar el modelo también es accesible desde la CLI.
Esta versión solo admite melodías monofónicas y fue entrenada con secuencias musicales de 2, 4, 8 y 16 compases. Para las secuencias de 2 compases, se utilizaron todas las combinaciones posibles de las siguientes representaciones/tratamientos de datos:

## **CÓMO INSTALAR EL ENTORNO**
1. El primer paso para empezar a utilizar nuestro proyecto para generar notas es descargar el repositorio suministrado en la parte de arriba y dentro de nuestro IDE ubicar la carpeta: generando-melodías. Modificar el código suministrado abajo con la ruta de descarga de tu ordenador.
    `cd C:\Users\user\Downloads\generando-melodias`

2. Abrir el entorno virtual que se encuentra dentro de esta carpeta con el       
siguiente script:
    `.\tutorial-env\Scripts\Activate.ps1`

3. Instalar las librerias necesarias dentro del entorno virtual de ser necesario con el siguiente script.
     `pip install -r librerias.txt`

4. Con todo esto listo, solo faltaría cargar nuestros modelos preentrenados, aunque, para este proyecto solo utilizamos uno con notas de piano (pianoroll_train_4bars_1stride_tempo_computed_transposed.tar). Puedes descargar este modelo desde el siguiente [enlace](https://drive.google.com/drive/folders/18NdFzZqUMGpcQ3-6WFYjEHmcVvPYvdIC)

Este modelo debe ser colocado en el repositorio dentro de `Models/Final` sin       descomprimir.

## **EJEMPLO DE USO**
Dentro del CLI de nuestro IDE ingresaremos el siguiente comando.
>`python musicVAE.py sample 4 -p -t  `
  El archivo.midi con nuestro sonido se creará dentro de la carpeta samples de nuestro repositorio.

Tambié podemos interpolar una secuencia generada aleatoreamente para crear 5 archivos.midi
>`python musicVAE.py reconstruct 2 -ptv -n 5 --start_sequence=Sampled/manually_created_sequences/smoke.midi`

  Nuestros sonidos se guardarán dentro de la carpeta samples también.

