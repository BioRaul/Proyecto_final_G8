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



**Bibliografía**

- Beckloff, N., Starkenburg, S., Freitas, T., & Chain, P. (2012). Bacterial genome annotation. Microbial Systems Biology: Methods and Protocols, 471-503.

- Jung, J. M., Rahman, A., Schiffer, A. M., & Weisberg, A. J. (2024). Beav: A bacterial genome and mobile element annotation pipeline. bioRxiv, 2024-01.

- Schwengers, O., Jelonek, L., Dieckmann, M. A., Beyvers, S., Blom, J., & Goesmann, A. (2021). Bakta: rapid and standardized annotation of bacterial genomes via alignment-free sequence identification. Microbial genomics, 7(11), 000685.

- Torkian, B., Hann, S., Preisner, E. et al. BLAST-QC: automated analysis of BLAST results. Environmental Microbiome 15, 15 (2020). https://doi.org/10.1186/s40793-020-00361-y
