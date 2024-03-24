# Proyecto_final_G8

**Tema**: Anotación de genoma bacteriano.

**Problema**: La anotación genómica completa y precisa es crucial para inferir las funciones previstas de un organismo. Existen numerosas herramientas para anotar genes, grupos de genes, elementos genéticos móviles y otras características diversas. Sin embargo, estas herramientas y canales pueden ser difíciles de instalar y ejecutar, estar especializados para un elemento o característica particular, o carecer de anotaciones para elementos más grandes que proporcionen un contexto genómico importante (Jung, 2024).


**Antecedentes**: La anotación de secuencias procarióticas se puede separar en anotación estructural y funcional. La anotación estructural depende del interrogatorio algorítmico de la evidencia experimental para descubrir las características físicas de un gen. Esto se hace en un esfuerzo por construir modelos genéticos precisos, de modo que no se impida comprender la función o la evolución de los genes entre los organismos (Beckloff, 2012).

Las herramientas de software de anotación de línea de comandos han ganado continuamente popularidad en comparación con los servicios centralizados en línea debido al aumento mundial de genomas bacterianos secuenciados. Sin embargo, los resultados de los canales de software de línea de comandos existentes dependen en gran medida de bases de datos específicas de taxones o de genomas de referencia suficientemente bien anotados. Por esto nace Bakta, una herramienta de software de línea de comandos para la anotación robusta, independiente de taxones, exhaustiva y, no obstante, rápida de genomas bacterianos (Schwengers, 2021).

**Objetivos**: 

- Ejecute una serie de herramientas para anotar un borrador del genoma bacteriano para diferentes tipos de componentes genómicos.

- Evaluar la anotación

- Procese los resultados para formatearlos según las necesidades de visualización.

- Visualice un borrador del genoma bacteriano y sus anotaciones.

## **FastQC en virtual box**

BlastQC proporciona una herramienta simple, liviana y portátil que permite un fácil control de los resultados de BLAST y evita los incovenientes de otras opciones. BlastQC es ideal para su uso en flujos de trabajo y procesos de alto rendimiento que son comunes en la investigación bioinformatica y genómica (Torkian et al., 2020).

Se trabajará con un archivo tipo *fasta* y *fastq* para la anotación del genoma bacteriano, primero que nada debemos comrpobar la calidad de nuetra secuencia problema por lo que usaremos líneas de comando en una máquina virtual con el programa fastQC.

### Instalación y ejecución de FastQC

Debemos instalar el programa fastQC en nuestra máquina virtual, para eso se utulizan los siguientes comandos:

```
sudo apt-get update
```

```
sudo apt-get install fastqc
```

Para confirmar la versión instalada uso el comando:

```
fastqc - -version
```

Descargamos la secuancia en formato fastq

<img width="440" alt="image" src="https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/cf0da9ba-9085-45f9-a16f-21a7a0810e8e">

Para el control de calida por fastQC aplicamos el comando:

```
fastqc **archivo.fastq**
```

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/f092c48c-ca20-40da-a6ad-d351dbb67330)

Se nos generará un archivo .HTML donde podremos observar todos los resultados que nos da el analisis fastQC

<img width="409" alt="image" src="https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/382eb007-b038-43d8-809a-f9045b53eee4">

Al revisar nuestros resultados podemos concluir que, efectivamente, nustra secuencia tiene una buena calidad.

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/830c47ba-73a7-4e6e-8e78-ece2b6e6af94)

# Anotación del genoma bacteriano

la anotación de secuencias de organismos procariotas se separa en notación estructural y funcional. La anotación estructural depende del interrogatorio algoritmico de la evidnecia experimental para descubrir las caracteristicas físicas de un gen, la anotación funcional depende de la similitud de secuencia con genes o proteínas conocidos en un esfuerzo por evaluar la funsión de un gen. la combinación de anotaciones estructurales y funcionales entre genomas promueve niveles altos de anotaciones precisas (Beckloff, 2012).


Al tener el link directo de nuestra secuencia lo subimos con la sección *Paste/Fetch data* 

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/febf889a-1957-4107-bec8-e80085200a36)

## Para la anotación de los contings utilizaremos la herramienta **Bakta** 

Bakta es una herramienta para la anotación rápida y estandarizada de genomas y plásmidos bacterianos que implementa un flujo de trabajo integral capaz de utilizar metadatos de secuencia además del ensamblaje del genoma (Schwengers et al., 2021).

Prokka coordina un conjunto de herramientas de software existentes para lograr una anotación rica y confiable de secuencias bacterianas genómicas y se puede instalar en cualquier sistema Unix  ( Stewart et al. , 2009 ) . Es ampliamente utilizado en la investigación genómica bacteriana debido a su facilidad de uso, velocidad y precisión en la anotación automática de genoma ( Aziz et al. , 2008 ). Según lo recomendado según el mismo autor Seemann (2014) se debe de utilizar Bakta como sucesor del Prokka.

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/b5bed94d-9b34-40c8-a49e-6614a23e550c)

Elegimos los parametros:

En “Input/Output options”:

- En “The bakta database”: seleccionamos la última versión

- En “The amrfinderplus database”: Seleccionamos la última versión

- En “Select genome in fasta format”: Colocamos nuestro archivo de interes .fasta

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/59ccf117-cbbf-45b8-bd62-dda735d689fa)

En “Optional annotation”

- En “Keep original contig header (–keep-contig-headers)”: Seleccionamos "Yes"

<img width="383" alt="image" src="https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/38da2e7e-7f40-4aa9-9f54-bc50fbc2b565">

En “Selection of the output files”: selecionamos los siguientes archivos de salida:

- Annotation file in TSV

- Annotation and sequence in GFF3

- Feature nucleotide sequences as FASTA

- Summary as TXT

- Plot of the annotation result as SVG

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/df80b9b7-2df8-4477-b79a-c75916cc5220)

Los resultados que nos da **Bakta** son diversos, entre ellos tenemos:

### **Analysis_summary**: Es un resumen del analisis en forma de archivo de texo

Entre los resultados más importantes podemos destacar los siguiente: 

- Que se han proporcionado 44 contings como entrada "input" (El recuento se secuencias).

- El borrador del genoma tiene un largo de 2'911.349 pb siendo un poco más corto de los 2'914.567 esperados obtenidos por Hichiki *et al*. 2019.

- Se han encontrado 2.717 CDS's, un poco más que los 2.704 obtenidos por Hichiki *et al*. 2019.

- Contiene 5 proteínas pequeñas, no hay esta información en Hichiki *et al*. 2019.

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/677794ef-17b0-4e7c-a898-5c27f6003285)

### **Nucleotide sequence**: Son secuencuias de nucleotidos en archivo FASTA

Aquí podemos destacar el número de secuencias que me da este archivo, que son un total de 2.901 secuencias. 

Además, que aquí se almacenan:

- ARNt

- ARNtm

- ARNr

- ncARN

- CDS

- SORF

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/3681f10d-7ec3-4e0d-8148-6f6866d69c72)

### Annotation summary: Son anotaciones como TSV simples y legibles.

Es una tabla de nueve columnas que corresponden a: **Comuna1**: *Sequence ID*; **Columna2**: *Type*; **Columna3**: *Start*; **Columna4**: *Stop*; **Columna5**: *Strand*; **Columna6**: *Locus Tag*; **Columna7**: *gene*; **Columna8**: *Product*; **Columna9**: *DbXrefs*.

Aquí contiene 2.933 líneas de secuencia y la información de: ARNt, ARNtm, ARNr, ncARN, CDS's, sORF's, gaps, oriCs, oriVs, oriTs.

<img width="314" alt="image" src="https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/54a0302d-c873-4371-83a7-7fecd14484bb">

### Annotation and sequence: está en formato GFF

GFF es un formato de archivo porpular utilizado por porgramas de bioinformatica para representar e intercambiar información sobre diversas caracteristicas genomicas, como la ubicacion y la estructura de genes y trascripciones (Pertea, G., & Pertea, M. 2020).

Contiene los siguientes campos: seqid, source, type, start, end, score, strand, phase, attributes. Aqupi tenemos 51.563 líneas de secuencia.

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/3b699ac2-ad59-4538-a3f2-e7688a62fa33)

### Plot of the annotation: Gráfica de la anotación en forma de genoma circular

El primer anillo del centro de la figura representa el contenido de Guanina-Citocina (GC) por ventana deslizante en toda la secuencia o secuencias, con el GC en verde por encima y el GC en rojo por debajo de la media. El segundo anillo representa la desviación de GC en naranja y azul. Todas las características se representan en dos anillos que representan la cadena directa e inversa de exterior a interior con CDS en gris (los otros colores son difíciles de distinguir).

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/0d0a02a8-ffcf-4245-87e7-eeb959cc631d)

## Plásmidos

Para identificar plásmidos en nuestros contings utilizamos la herramienta **PlasmidFinger**. Aquí no hay parametros especiales que debamos seguir.

permite la identificación de motivos plasmídicos usando una base de datos no redundante de replicones (secuencias que activan o controlan la replicación del plásmido y son identificativas de un determinado tipo de plásmido) y los asigna a un determinado grupo Inc (grupo de incompatibilidad plasmídica) (Carattoli *et al*., 2014).

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/034df5a5-8b91-4007-89b0-41576da111c6)

Los resultados que nos da **PlasmidFinger** son diversos, entre ellos tenemos:

### raw results.txt: Es un archivo de texto que contiene la tabla de resultados y las alineaciones.

<img width="376" alt="image" src="https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/9661452c-58dd-48ea-8be3-0f54add91380">

### results.tsv: Es un archivo tabular con las siguientes columnas:

TSV Es un formato de archivo utilizado para almacenar datos tabulares en texto plano. En un archivo TSV, cada línea representa una fila de datos, y los valores de cada fila están separados por tabuladores

Es una tabla de nueve columnas que corresponden a: **Comuna1**: *Database*; **Columna2**: *Plasmid*; **Columna3**: *Identity*; **Columna4**: *Query/Template Length*; **Columna5**: *Conting*; **Columna6**: *Position in conting*; **Columna7**: *Note*; **Columna8**: *Accession number*.

En este output podemos destacar que nos indica la presencia de cinco secuencias de plásmidos localizados de la siguiente manera: tres en conting00019, uno en conting00002 y uno en 00024. 

Al observer el número de acceso de estos contings en NCBI podemos visualizar que:

- Tanto AP003139 como CP000737 corresponden a plásmidos de *Staphylococcus aureus*

- AF503772 corresponde a un plásmido de *Enterococcus faecalis*

- CP003584 corresponde a un plásmido de *Enterococcus faecium*

Todas las secuencias de plásmidos correspondientes a los plásmidos de Staphylococcus aureus están todas en contig00019, lo que hace que este cóntig probablemente sea un plásmido. Además, este contig tiene una longitud de 30.347 pb, que es similar a la longitud esperada del plásmido para KUN1163 en la Tabla 1 en Hikichi et al. 2019.

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/f44cc31a-708f-41b1-8bae-f7d36846a9f7)

### Plasmid.fasta: Es una archivo fasta que contiene las secuencias que mejor coinciden con el genoma de consulta.

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/8bec8058-0dd8-4aa9-a7be-92a6b5c3219a)

### Hit in genome.fasta: Es un archivo fasta que contiene los genes plasmidicos que mejor coinciden de la base de datos.

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/f0235d49-3602-458e-a417-f22a26ab5dae)

## Integrones

Para identificar integrones utilizaremos la herramienta **IntegronFinger**

Es capaz de identificar integrones con nuevos casetes y es complementario al uso de bases de datos como Integrall que almacenan integrones conocidos y permiten buscar homología de los casetes por similitud de secuencia (Nerón, B *et al*., 2022). 

Los parametros para el uso de esta herramienta son los siguintes:

- En *"Thorough local detection"* colocamos **Yes**

- En *“Search also for promoter and attI sites?”* colocamos **Yes**

- En *“Remove log file”* colocamos **Yes**

<img width="589" alt="image" src="https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/ae67c229-87ec-4c2f-befa-e81c9f534bbe">

La herramienta **IntegronFinger** nos da dos resultados "output".

Un resumen que contenga, para cada secuencia de la entrada, el número de elementos CALIN, elementos In0 e integrones completos identificados. Aquí podemos notar que no se han encontrado elementos integrones en ningún contig, Esto podría deberse a que el genoma es demasiado estable o a que la calidad del ensamblaje no es lo suficientemente buena y se eliminaron algunas partes útiles para la detección de integrones.

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/df909c1a-7374-4a29-9969-7a91ed7c4d9a)

El otro archivo obtenido es uno de anotación integrado como tabular.

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/199e76cf-f5c0-486c-99ce-4a5db89286e5)

## Para detectar elementos IS utilizaremos la herramienta **ISEScan** que nos generará siete resultados o "outputs":

Es una secuencia corta de ADN que actúa como un elemento transponible simple . Las secuencias de inserción tienen dos características principales: son pequeñas en relación con otros elementos transponibles y solo codifican proteínas implicadas en la actividad de transposición (Azziz R.K. *et al* 2010).

- Un resumen en forma de tabla

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/3306e611-3b1c-495e-9b58-2fd20a12f5dc)

- Los resultados en forma de tabla

Aquí podemos ver los elementos IS detectados, que son un total de 20. 

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/f7c41cac-a962-4a39-b788-a76bf9866a3b)

Para saber dónde están ubicados debemos de utilizar la herramienta **Group data by a column**

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/54cfaa0f-3925-4758-92f3-8e9869ac1df2)

Tenemos el número de elementos IS por cada conting:

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/9e4b5118-358a-46cd-ac7f-056fffe977ac)

Tenemos también el númeor de elementos IS identificados por cada familia de IS

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/f9f21794-a7c6-47c1-aa75-76aba4ed4547)

- Los resultados como un archivo GFF

  ![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/9c4fcb2b-07c1-4804-9f6d-d1a1be65413e)

- **Varios archivos FASTA**

- Secuencia de nucleotidos IS
  
![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/a646295e-d07b-4c5f-8074-af8d808dfbb4)

- Secuencia de nucleotidos ORF

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/3e976e21-d7bc-4a91-9acb-f4199ddb12a4)

- Secuencia de amonoacidos ORF

![image](https://github.com/BioRaul/Proyecto_final_G8/assets/163359448/ede80283-e61b-4b8a-bdd3-d16a053e96a3)


**Bibliografía**

- Aziz RK, et al. El servidor RAST: anotaciones rápidas utilizando tecnología de subsistemas, Genómica BMC, 2008, vol. 9 pág. 75

- Beckloff, N., Starkenburg, S., Freitas, T., & Chain, P. (2012). Bacterial genome annotation. Microbial Systems Biology: Methods and Protocols, 471-503.

- Carattoli, A., Zankari, E., García-Fernández, A., Voldby Larsen, M., Lund, O., Villa, L., ... & Hasman, H. (2014). In silico detection and typing of plasmids using PlasmidFinder and plasmid multilocus sequence typing. Antimicrobial agents and chemotherapy, 58(7), 3895-3903.

- Jung, J. M., Rahman, A., Schiffer, A. M., & Weisberg, A. J. (2024). Beav: A bacterial genome and mobile element annotation pipeline. bioRxiv, 2024-01.

- Néron, B., Littner, E., Haudiquet, M., Perrin, A., Cury, J., & Rocha, E. P. (2022). IntegronFinder 2.0: identification and analysis of integrons across bacteria, with a focus on antibiotic resistance in Klebsiella. Microorganisms, 10(4), 700.

- Schwengers, O., Jelonek, L., Dieckmann, M. A., Beyvers, S., Blom, J., & Goesmann, A. (2021). Bakta: rapid and standardized annotation of bacterial genomes via alignment-free sequence identification. Microbial genomics, 7(11), 000685.

- Seemann, T. (2014). Prokka: rapid prokaryotic genome annotation. Bioinformatics, 30(14), 2068-2069.

- Stewart C.A., et al. DIYA: un canal de anotación bacteriana para cualquier laboratorio de genómica, Bioinformática, 2009, vol. 25 (pág. 962-963)

- Pertea, G., & Pertea, M. (2020). GFF Utilities: GffRead and GffCompare. F1000Research, 9, ISCB Comm J-304. https://doi.org/10.12688/f1000research.23297.2

- Torkian, B., Hann, S., Preisner, E. et al. BLAST-QC: automated analysis of BLAST results. Environmental Microbiome 15, 15 (2020). https://doi.org/10.1186/s40793-020-00361-y
