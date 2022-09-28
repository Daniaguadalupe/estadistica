# estadistica
Este repositorio contiene las evidencias de trabajo del semestre A en la licenciatura preescolar 2022

title: "Ejercicio 1"
author: "Dania Guadalupe González Roa"
date: "2022-09-22"
output: pdf_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```


# Reconocimiento de la matriz de datos.

1.- Indicar la ruta de trabajo

session/Set working Directory/ Choose Directory/Cloud/project/enter.

2.- Lectura de la matriz de datos.
Se copia la ruta de acceso que proporciona R y se le agrega el nombre del archivo.

```{r}
library("readxl")
```


```{r}
BX<-read_excel("/cloud/project/penguins.xlsx")
```

# Exploración de la matriz

1.- Visualización de los nombres de las variables.
```{r}
colnames(BD)
```

2.- Visualización del tipo de variable
```{r}
str(BD)
```


# Instalación de librerías

se va a instalar instalar el paquete ggplot2. No olvides declarar los argumentos warning=FALSE y message=FALSE

```{r, warning=FALSE, message=FALSE}
library(ggplot2)
```

# Generación de gráficos

## Boxplot
Se utiliza para visualizar variables cualitativas y cuantitativas simultáneamente. En el eje de la x se muestra la variable cualitativa codificada en factor. En el eje y se muestra la variable cuantitativa.

1.- Codificación de la variable cualitativa a factor.

```{r}
BD$genero<-factor(BD$genero, 
            levels=c("male", "female"))
```

2.- Creación de un vector de color
```{r}
color=c("cadetblue3","coral4")
```

3.- Creacion del grafico

```{r}
BX<-ggplot(BD, aes(x=genero, y=largo_pico_mm))+
  geom_boxplot(fill=color)+
  ggtitle("Boxplot")+
  xlab("Género")+
  ylab("largo de la aleta (mm)")+
  theme_bw()
```

```{r}
BX
```


4.- Visualización del boxplot

```{r}
BX
```



## Gráfico de barras

Se tiene que tener en cuenta que las variables agraficar tienen que ser cualitativas y deben estar configuradas en factores.

1.- Codificación de la variable en factores.
```{r}
BD$especie<-factor(BD$especie, 
            levels=c("Adelie", "Gentoo", "Chinstrap"))
```

2.- Creación de un vector de colores.
Dependiendo del número de factores que tenga nuestra variable, es el número de colores que vamos a crear. Los colores los puedes seleccionar desde el catálogo de RColors.

```{r}
color=c("darkcyan","aquamarine3", "cadetblue4")
```

3.- Creación del gráfico.

```{r}
GB1<-ggplot(BD, aes(x=especie))+
  geom_bar(colour= "green4", fill=color)+
  ggtitle("Gráfico de Barras")+
  xlab("Especie")+
  ylab("Frecuencias")+
  theme_minimal()
```

```{r}
GB1
```

4.- Visualización del Gráfico.

```{r}
GB1
```

## Histograma

Se tiene que cuenta que las variables que se van a graficar deben ser cuantitativas y se recomienda para más de 100 observaciones.

1.- Creación del gráfico.
```{r}
HG<-ggplot(BD, aes(x=largo_aleta_mm))+
  geom_histogram(col="lightcyan3",  fill="lightpink3")+
  ggtitle("Histograma")+
  xlab("Largo de la aleta (mm)")+
  ylab("Frecuencias")+
  theme_classic()
```

```{r}
HG
```

2.- Visualización del gráfico.
```{r}
HG
```

## Gráfico de dispersión.

Se utiliza para visualizar variables cuantitativas.

1.- Construcción del gráfico.
```{r}
GD<-ggplot(BD, aes(x=largo_pico_mm, y=grosor_pico_mm))+
  geom_point(aes(color=especie))+
  ggtitle("Gráfico de dispersión")+
  xlab("largo del pico (mm)")+
  ylab("grosor del pico (mm)")+
  theme_light()
```

2.- Visualización del gráfico.
```{r}
GD
```

# Organización de gráficos

Se pueden organizar los gráficos de tal forma que se puedan mostrar dos objetos en una sola fila y como mejor se aprecie la información.

1.- Instalación de paquetes.
No olvides declarar los argumentos warning=FALSE y message=FALSE

```{r, warning=FALSE, message=FALSE}
install.packages("gridExtra")
```


2.- Abrir librería.
```{r, warning=FALSE, message=FALSE}
library(gridExtra)
```

3.- Organizacion 2 gráficos en una fila y dos columnas.

```{r}
grid.arrange(BX,GB1, nrow=1, ncol=2)
```

4.- Organizacion 3 graficos en dos filas y dos columnas.

```{r}
grid.arrange(BX,GB1,HG, nrow=2, ncol=2)
```

5.- Organizacion 4 graficos en dos filas y dos columnas.

```{r}
grid.arrange(BX,GB1,HG,GD, nrow=2, ncol=2)
```

 
