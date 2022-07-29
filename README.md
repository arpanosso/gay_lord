
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Análise Preliminar

## Carregando pacotes exigidos

``` r
library(tidyverse)
#> -- Attaching packages --------------------------------------- tidyverse 1.3.1 --
#> v ggplot2 3.3.5     v purrr   0.3.4
#> v tibble  3.1.6     v dplyr   1.0.8
#> v tidyr   1.2.0     v stringr 1.4.0
#> v readr   2.1.2     v forcats 0.5.1
#> -- Conflicts ------------------------------------------ tidyverse_conflicts() --
#> x dplyr::filter() masks stats::filter()
#> x dplyr::lag()    masks stats::lag()
library(ExpDes.pt)
library(readxl)
library(janitor)
#> 
#> Attaching package: 'janitor'
#> The following objects are masked from 'package:stats':
#> 
#>     chisq.test, fisher.test
library(skimr)
```

## Entrada de dados

``` r
dados<- read_excel("data/Análise_Preliminar.xlsx") %>% 
  clean_names()
```

## Resumo rápido

``` r
glimpse(dados)
#> Rows: 32
#> Columns: 26
#> $ usina                          <chr> "Moema", "Moema", "Moema", "Moema", "Mo~
#> $ ensaio                         <dbl> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, ~
#> $ tratamento                     <dbl> 1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, ~
#> $ descritivo                     <chr> "Testemunha", "Testemunha", "Testemunha~
#> $ repeticao                      <dbl> 1, 2, 3, 4, 1, 2, 3, 4, 1, 2, 3, 4, 1, ~
#> $ number_parcela                 <dbl> 9, 10, 3, 12, 13, 2, 7, 8, 5, 14, 15, 4~
#> $ massa_8m                       <dbl> 234.85, 188.26, 187.15, 244.45, 253.75,~
#> $ number_perfilhos               <dbl> 153, 124, 212, 135, 147, 164, 125, 201,~
#> $ massa_10_canas                 <dbl> 14.50, 17.55, 15.60, 17.30, 18.10, 15.8~
#> $ espessura_media_10_canas       <dbl> 2.590000, 2.690000, 2.730000, 2.640000,~
#> $ number_entrenos_media_10_canas <dbl> 13.2, 17.7, 15.5, 16.9, 17.9, 15.8, 16.~
#> $ altura_planta_p_q              <dbl> 2.083000, 2.533000, 2.285000, 2.452000,~
#> $ populacao                      <dbl> 63753.19, 51669.25, 88337.75, 56252.81,~
#> $ tch_1_2_linhas_8m              <dbl> 97.85906, 78.44559, 77.98307, 101.85926~
#> $ tch_2_10_canas                 <dbl> 92.44212, 90.67953, 137.80689, 97.31737~
#> $ tch_3_media                    <dbl> 95.15059, 84.56256, 107.89498, 99.58831~
#> $ pol                            <dbl> 13.22972, 14.14185, 15.81475, 13.90952,~
#> $ fibra                          <dbl> 12.6016, 13.5336, 14.0968, 12.5584, 12.~
#> $ pza                            <dbl> 72.37, 77.40, 78.25, 73.09, 77.19, 74.6~
#> $ pcc                            <dbl> 11.08662, 11.65909, 12.90937, 11.66509,~
#> $ ar_percent_caldo               <dbl> 1.1586189, 0.9860165, 0.9569533, 1.1339~
#> $ ar_percent_cana                <dbl> 0.9709329, 0.8129102, 0.7811485, 0.9509~
#> $ atr                            <dbl> 114.40, 118.42, 130.05, 119.73, 115.68,~
#> $ tah_1                          <dbl> 11.195076, 9.289527, 10.141698, 12.1956~
#> $ tah_2                          <dbl> 10.575379, 10.738270, 17.921786, 11.651~
#> $ tah_3                          <dbl> 10.885228, 10.013899, 14.031742, 11.923~
```

## Estatística rápida

``` r
skim(dados)
```

|                                                  |       |
|:-------------------------------------------------|:------|
| Name                                             | dados |
| Number of rows                                   | 32    |
| Number of columns                                | 26    |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |       |
| Column type frequency:                           |       |
| character                                        | 2     |
| numeric                                          | 24    |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |       |
| Group variables                                  | None  |

Data summary

**Variable type: character**

| skim_variable | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:--------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| usina         |         0 |             1 |   5 |   5 |     0 |        1 |          0 |
| descritivo    |         0 |             1 |   7 |  10 |     0 |        5 |          0 |

**Variable type: numeric**

| skim_variable                  | n_missing | complete_rate |     mean |      sd |       p0 |      p25 |      p50 |      p75 |     p100 | hist  |
|:-------------------------------|----------:|--------------:|---------:|--------:|---------:|---------:|---------:|---------:|---------:|:------|
| ensaio                         |         0 |             1 |     1.50 |    0.51 |     1.00 |     1.00 |     1.50 |     2.00 |     2.00 | ▇▁▁▁▇ |
| tratamento                     |         0 |             1 |     2.50 |    1.14 |     1.00 |     1.75 |     2.50 |     3.25 |     4.00 | ▇▇▁▇▇ |
| repeticao                      |         0 |             1 |     2.50 |    1.14 |     1.00 |     1.75 |     2.50 |     3.25 |     4.00 | ▇▇▁▇▇ |
| number_parcela                 |         0 |             1 |     8.50 |    4.68 |     1.00 |     4.75 |     8.50 |    12.25 |    16.00 | ▇▆▆▆▆ |
| massa_8m                       |         0 |             1 |   207.71 |   29.99 |   154.00 |   183.16 |   205.65 |   233.91 |   263.05 | ▃▇▃▆▅ |
| number_perfilhos               |         0 |             1 |   152.91 |   22.81 |   116.00 |   134.25 |   152.00 |   165.25 |   212.00 | ▇▇▇▂▂ |
| massa_10_canas                 |         0 |             1 |    15.11 |    1.92 |    11.60 |    14.17 |    14.70 |    16.38 |    19.45 | ▅▇▅▃▂ |
| espessura_media_10_canas       |         0 |             1 |     2.62 |    0.13 |     2.35 |     2.55 |     2.64 |     2.70 |     2.87 | ▃▂▇▆▃ |
| number_entrenos_media_10_canas |         0 |             1 |    15.68 |    1.38 |    13.20 |    14.57 |    15.80 |    16.90 |    17.90 | ▆▂▇▅▅ |
| altura_planta_p\_q             |         0 |             1 |     2.32 |    0.14 |     2.08 |     2.20 |     2.33 |     2.45 |     2.54 | ▅▃▇▂▆ |
| populacao                      |         0 |             1 | 63714.12 | 9503.92 | 48335.75 | 55940.30 | 63336.50 | 68857.61 | 88337.75 | ▇▇▇▂▂ |
| tch_1\_2_linhas_8m             |         0 |             1 |    86.55 |   12.50 |    64.17 |    76.32 |    85.69 |    97.47 |   109.61 | ▃▇▃▆▅ |
| tch_2\_10_canas                |         0 |             1 |    96.71 |   21.95 |    61.87 |    83.68 |    94.30 |   106.46 |   162.90 | ▅▇▅▁▁ |
| tch_3\_media                   |         0 |             1 |    91.63 |   14.59 |    65.94 |    80.55 |    90.06 |   101.46 |   124.32 | ▅▇▆▅▂ |
| pol                            |         0 |             1 |    14.37 |    0.86 |    12.39 |    13.74 |    14.51 |    15.09 |    15.81 | ▂▅▇▇▆ |
| fibra                          |         0 |             1 |    13.18 |    0.53 |    12.34 |    12.84 |    13.13 |    13.42 |    14.93 | ▅▇▃▁▁ |
| pza                            |         0 |             1 |    76.65 |    2.34 |    70.79 |    74.65 |    77.21 |    78.14 |    80.81 | ▁▅▃▇▃ |
| pcc                            |         0 |             1 |    11.92 |    0.70 |    10.11 |    11.45 |    12.07 |    12.47 |    13.00 | ▁▂▇▇▇ |
| ar_percent_caldo               |         0 |             1 |     1.01 |    0.08 |     0.87 |     0.96 |     0.99 |     1.08 |     1.21 | ▃▇▃▅▁ |
| ar_percent_cana                |         0 |             1 |     0.84 |    0.07 |     0.71 |     0.80 |     0.83 |     0.90 |     0.99 | ▃▇▅▅▂ |
| atr                            |         0 |             1 |   121.11 |    6.15 |   105.28 |   117.18 |   122.14 |   125.55 |   130.95 | ▂▂▇▇▆ |
| tah_1                          |         0 |             1 |    10.47 |    1.54 |     7.82 |     9.25 |    10.28 |    11.69 |    13.24 | ▆▇▇▇▇ |
| tah_2                          |         0 |             1 |    11.74 |    2.92 |     7.30 |     9.87 |    11.21 |    12.62 |    20.09 | ▃▇▃▁▂ |
| tah_3                          |         0 |             1 |    11.11 |    1.95 |     8.04 |     9.80 |    10.80 |    12.54 |    15.44 | ▃▇▃▃▂ |

## Análise para Ensaio 01

``` r
ensaio_1 <- dados %>% 
  filter(ensaio == 1)
for(i in  7:length(ensaio_1)){
  print("************ Análise de Variância ***************")
  print(paste0("Variável: ",names(ensaio_1[,i])))
  print("*************************************************")
  
  # print("--------Análise de resíduos---------")
  trat <- ensaio_1 %>%  pull(tratamento)
  y <- data.frame(ensaio_1)[,i]
  # mod <- aov(y~as.factor(trat))
  # rs<-rstudent(mod)
  # hist(rs)
  # print(shapiro.test(rs))
  # 
  # plot(y ~ as.factor(trat))
  # print(lawstat::levene.test(y,trat))
  
  print("---------Teste F da ANOVA - DBC -----------")
  bl <- ensaio_1 %>% pull(repeticao)
  dbc(trat, bl, y)
}
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: massa_8m"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ      QM      Fc   Pr>Fc
#> Tratamento  3   267.5   89.18 0.10686 0.95396
#> Bloco       3  4200.2 1400.08 1.67760 0.24049
#> Residuo     9  7511.2  834.57                
#> Total      15 11978.9                        
#> ------------------------------------------------------------------------
#> CV = 13.8 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.7915836 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.9544917 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 213.6775
#> 2      2 213.1625
#> 3      3 204.8750
#> 4      4 205.6625
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: number_perfilhos"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ      QM      Fc   Pr>Fc
#> Tratamento  3   860.2  286.73 0.33186 0.80271
#> Bloco       3  4051.7 1350.56 1.56314 0.26496
#> Residuo     9  7776.1  864.01                
#> Total      15 12687.9                        
#> ------------------------------------------------------------------------
#> CV = 19.54 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.4201356 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.1366023 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis Medias
#> 1      1 156.00
#> 2      2 159.25
#> 3      3 142.00
#> 4      4 144.50
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: massa_10_canas"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ     QM     Fc    Pr>Fc
#> Tratamento  3  8.356 2.7854 1.8467 0.209015
#> Bloco       3 26.226 8.7421 5.7959 0.017348
#> Residuo     9 13.575 1.5083                
#> Total      15 48.158                       
#> ------------------------------------------------------------------------
#> CV = 7.65 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.9543917 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.04776347 
#> ATENCAO: a 5% de significancia, as variancias nao podem ser consideradas homogeneas!
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis  Medias
#> 1      1 16.2375
#> 2      2 16.8875
#> 3      3 14.9000
#> 4      4 16.2250
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: espessura_media_10_canas"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL       SQ       QM      Fc   Pr>Fc
#> Tratamento  3 0.001622 0.000541 0.04198 0.98778
#> Bloco       3 0.103110 0.034370 2.66879 0.11089
#> Residuo     9 0.115906 0.012878                
#> Total      15 0.220637                         
#> ------------------------------------------------------------------------
#> CV = 4.28 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.9862714 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.6400136 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 2.662500
#> 2      2 2.655000
#> 3      3 2.635000
#> 4      4 2.649528
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: number_entrenos_media_10_canas"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ     QM     Fc   Pr>Fc
#> Tratamento  3  9.335 3.1117 1.8406 0.21006
#> Bloco       3  7.890 2.6300 1.5557 0.26665
#> Residuo     9 15.215 1.6906               
#> Total      15 32.440                      
#> ------------------------------------------------------------------------
#> CV = 8.28 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.6853326 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.8308401 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis Medias
#> 1      1 15.825
#> 2      2 16.900
#> 3      3 15.050
#> 4      4 15.025
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: altura_planta_p_q"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ       QM     Fc   Pr>Fc
#> Tratamento  3 0.09484 0.031615 1.8782 0.20370
#> Bloco       3 0.08579 0.028595 1.6988 0.23625
#> Residuo     9 0.15149 0.016833               
#> Total      15 0.33212                        
#> ------------------------------------------------------------------------
#> CV = 5.58 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.4947776 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.7929306 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 2.338250
#> 2      2 2.443639
#> 3      3 2.258167
#> 4      4 2.254278
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: populacao"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL         SQ        QM      Fc   Pr>Fc
#> Tratamento  3  149353042  49784347 0.33186 0.80271
#> Bloco       3  703488312 234496104 1.56314 0.26496
#> Residuo     9 1350145855 150016206                
#> Total      15 2202987209                          
#> ------------------------------------------------------------------------
#> CV = 19.54 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.4201356 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.1366023 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 65003.25
#> 2      2 66357.48
#> 3      3 59169.62
#> 4      4 60211.34
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: tch_1_2_linhas_8m"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ      QM      Fc   Pr>Fc
#> Tratamento  3   46.45  15.484 0.10686 0.95396
#> Bloco       3  729.28 243.093 1.67760 0.24049
#> Residuo     9 1304.15 144.906                
#> Total      15 2079.88                        
#> ------------------------------------------------------------------------
#> CV = 13.8 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.7915836 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.9544917 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 89.03674
#> 2      2 88.82215
#> 3      3 85.36885
#> 4      4 85.69699
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: tch_2_10_canas"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ      QM      Fc  Pr>Fc
#> Tratamento  3  1318.8  439.61 0.79459 0.5271
#> Bloco       3  4749.9 1583.31 2.86179 0.0966
#> Residuo     9  4979.3  553.26               
#> Total      15 11048.1                       
#> ------------------------------------------------------------------------
#> CV = 23.16 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.2078563 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.2856511 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis    Medias
#> 1      1 104.56148
#> 2      2 113.92601
#> 3      3  88.89247
#> 4      4  98.85494
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: tch_3_media"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ     QM     Fc   Pr>Fc
#> Tratamento  3  447.0 149.00 1.0964 0.39964
#> Bloco       3 2070.3 690.12 5.0783 0.02500
#> Residuo     9 1223.0 135.89               
#> Total      15 3740.4                      
#> ------------------------------------------------------------------------
#> CV = 12.35 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.1618443 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.5649149 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis    Medias
#> 1      1  96.79911
#> 2      2 101.37408
#> 3      3  87.13066
#> 4      4  92.27597
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: pol"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ      QM      Fc   Pr>Fc
#> Tratamento  3  2.6417 0.88056 0.73659 0.55617
#> Bloco       3  3.0764 1.02545 0.85780 0.49719
#> Residuo     9 10.7591 1.19545                
#> Total      15 16.4771                        
#> ------------------------------------------------------------------------
#> CV = 7.64 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.5013209 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.8613202 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 14.27396
#> 2      2 13.67682
#> 3      3 14.75126
#> 4      4 14.56227
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: fibra"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ      QM      Fc   Pr>Fc
#> Tratamento  3 1.5049 0.50164 1.07525 0.40739
#> Bloco       3 1.0434 0.34781 0.74553 0.55158
#> Residuo     9 4.1988 0.46653                
#> Total      15 6.7471                        
#> ------------------------------------------------------------------------
#> CV = 5.13 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.4570751 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.847167 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis  Medias
#> 1      1 13.1976
#> 2      2 13.0002
#> 3      3 13.2540
#> 4      4 13.8246
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: pza"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ     QM      Fc   Pr>Fc
#> Tratamento  3  5.410 1.8032 0.23179 0.87199
#> Bloco       3 20.289 6.7631 0.86933 0.49192
#> Residuo     9 70.017 7.7797                
#> Total      15 95.716                       
#> ------------------------------------------------------------------------
#> CV = 3.67 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.5806142 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.791978 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis  Medias
#> 1      1 75.2775
#> 2      2 75.5700
#> 3      3 76.5050
#> 4      4 76.6250
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: pcc"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ      QM      Fc   Pr>Fc
#> Tratamento  3  1.4583 0.48610 0.66795 0.59265
#> Bloco       3  2.1510 0.71699 0.98522 0.44223
#> Residuo     9  6.5498 0.72775                
#> Total      15 10.1590                        
#> ------------------------------------------------------------------------
#> CV = 7.2 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.4033873 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.703461 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 11.83004
#> 2      2 11.38075
#> 3      3 12.21645
#> 4      4 11.94921
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: ar_percent_caldo"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL       SQ        QM      Fc   Pr>Fc
#> Tratamento  3 0.006367 0.0021222 0.23193 0.87189
#> Bloco       3 0.023860 0.0079532 0.86917 0.49200
#> Residuo     9 0.082354 0.0091504                
#> Total      15 0.112580                          
#> ------------------------------------------------------------------------
#> CV = 9.25 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.5791314 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.7911165 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 1.058878
#> 2      2 1.049034
#> 3      3 1.016814
#> 4      4 1.012742
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: ar_percent_cana"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL       SQ        QM      Fc   Pr>Fc
#> Tratamento  3 0.006549 0.0021829 0.31943 0.81128
#> Bloco       3 0.018483 0.0061610 0.90155 0.47753
#> Residuo     9 0.061504 0.0068338                
#> Total      15 0.086536                          
#> ------------------------------------------------------------------------
#> CV = 9.65 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.3476115 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.8923189 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis    Medias
#> 1      1 0.8789865
#> 2      2 0.8729498
#> 3      3 0.8428425
#> 4      4 0.8305283
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: atr"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ     QM      Fc   Pr>Fc
#> Tratamento  3 121.91 40.635 0.73049 0.55932
#> Bloco       3 175.31 58.438 1.05052 0.41665
#> Residuo     9 500.65 55.628                
#> Total      15 797.87                       
#> ------------------------------------------------------------------------
#> CV = 6.19 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.3983339 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.6121557 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 120.6500
#> 2      2 116.3175
#> 3      3 124.0025
#> 4      4 121.3475
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: tah_1"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ     QM      Fc   Pr>Fc
#> Tratamento  3  0.271 0.0904 0.04043 0.98843
#> Bloco       3 15.270 5.0900 2.27690 0.14857
#> Residuo     9 20.119 2.2355                
#> Total      15 35.660                       
#> ------------------------------------------------------------------------
#> CV = 14.21 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.9938142 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.3646106 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 10.70548
#> 2      2 10.34328
#> 3      3 10.54626
#> 4      4 10.48162
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: tah_2"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ      QM      Fc   Pr>Fc
#> Tratamento  3  11.855  3.9516 0.35593 0.78623
#> Bloco       3  90.731 30.2437 2.72410 0.10655
#> Residuo     9  99.921 11.1023                
#> Total      15 202.506                        
#> ------------------------------------------------------------------------
#> CV = 27.08 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.5947627 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.5202268 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 12.72181
#> 2      2 13.35016
#> 3      3 11.01247
#> 4      4 12.14077
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: tah_3"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ      QM     Fc   Pr>Fc
#> Tratamento  3  2.761  0.9205 0.2769 0.84073
#> Bloco       3 42.421 14.1402 4.2536 0.03955
#> Residuo     9 29.919  3.3243               
#> Total      15 75.101                       
#> ------------------------------------------------------------------------
#> CV = 15.98 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.5522805 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.5836564 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 11.71364
#> 2      2 11.84672
#> 3      3 10.77937
#> 4      4 11.31120
#> ------------------------------------------------------------------------
```

## Análise para Ensaio 02

``` r
ensaio_2 <- dados %>% 
  filter(ensaio == 2)
for(i in  7:length(ensaio_2)){
  print("************ Análise de Variância ***************")
  print(paste0("Variável: ",names(ensaio_2[,i])))
  print("*************************************************")
  
  # print("--------Análise de resíduos---------")
  trat <- ensaio_1 %>%  pull(tratamento)
  y <- data.frame(ensaio_2)[,i]
  # mod <- aov(y~as.factor(trat))
  # rs<-rstudent(mod)
  # hist(rs)
  # print(shapiro.test(rs))
  # 
  # plot(y ~ as.factor(trat))
  # print(lawstat::levene.test(y,trat))
  
  print("---------Teste F da ANOVA - DBC -----------")
  bl <- ensaio_2 %>% pull(repeticao)
  dbc(trat, bl, y)
}
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: massa_8m"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ      QM      Fc   Pr>Fc
#> Tratamento  3  6237.8 2079.28 2.09691 0.17092
#> Bloco       3   649.8  216.59 0.21843 0.88119
#> Residuo     9  8924.4  991.60                
#> Total      15 15812.0                        
#> ------------------------------------------------------------------------
#> CV = 15.28 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.2002677 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.6968564 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 221.4875
#> 2      2 228.5750
#> 3      3 180.1875
#> 4      4 194.0125
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: number_perfilhos"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ     QM      Fc   Pr>Fc
#> Tratamento  3  896.7 298.92 1.47593 0.28557
#> Bloco       3  524.2 174.75 0.86284 0.49488
#> Residuo     9 1822.8 202.53                
#> Total      15 3243.7                       
#> ------------------------------------------------------------------------
#> CV = 9.16 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.4636773 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.2410245 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis Medias
#> 1      1  162.5
#> 2      2  161.0
#> 3      3  143.5
#> 4      4  154.5
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: massa_10_canas"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ     QM     Fc   Pr>Fc
#> Tratamento  3 15.047 5.0158 2.8701 0.09604
#> Bloco       3  5.964 1.9879 1.1375 0.38509
#> Residuo     9 15.729 1.7476               
#> Total      15 36.740                      
#> ------------------------------------------------------------------------
#> CV = 9.34 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.957082 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.6293006 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis  Medias
#> 1      1 15.1125
#> 2      2 15.0625
#> 3      3 12.8625
#> 4      4 13.5625
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: espessura_media_10_canas"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL       SQ       QM     Fc   Pr>Fc
#> Tratamento  3 0.183606 0.061202 7.7410 0.00731
#> Bloco       3 0.014134 0.004711 0.5959 0.63342
#> Residuo     9 0.071156 0.007906               
#> Total      15 0.268896                        
#> ------------------------------------------------------------------------
#> CV = 3.43 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.4716963 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.6966582 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> Teste de Tukey
#> ------------------------------------------------------------------------
#> Grupos Tratamentos Medias
#> a     1   2.6925 
#> a     2   2.658889 
#> ab    4   2.595 
#>  b    3   2.415 
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: number_entrenos_media_10_canas"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ     QM     Fc   Pr>Fc
#> Tratamento  3  4.4619 1.4873 1.3259 0.32553
#> Bloco       3 11.9619 3.9873 3.5546 0.06065
#> Residuo     9 10.0956 1.1217               
#> Total      15 26.5194                      
#> ------------------------------------------------------------------------
#> CV = 6.76 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.4535779 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.5317119 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis Medias
#> 1      1 15.950
#> 2      2 16.375
#> 3      3 15.150
#> 4      4 15.150
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: altura_planta_p_q"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL       SQ       QM     Fc    Pr>Fc
#> Tratamento  3 0.050187 0.016729 1.4320 0.296660
#> Bloco       3 0.127414 0.042471 3.6355 0.057609
#> Residuo     9 0.105142 0.011682                
#> Total      15 0.282743                         
#> ------------------------------------------------------------------------
#> CV = 4.66 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.5141725 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.6081264 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 2.343200
#> 2      2 2.400333
#> 3      3 2.273500
#> 4      4 2.261750
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: populacao"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL        SQ       QM      Fc   Pr>Fc
#> Tratamento  3 155701333 51900444 1.47593 0.28557
#> Bloco       3  91024727 30341576 0.86284 0.49488
#> Residuo     9 316481299 35164589                
#> Total      15 563207358                         
#> ------------------------------------------------------------------------
#> CV = 9.16 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.4636773 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.2410245 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 67711.72
#> 2      2 67086.69
#> 3      3 59794.66
#> 4      4 64378.22
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: tch_1_2_linhas_8m"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ     QM      Fc   Pr>Fc
#> Tratamento  3 1083.07 361.02 2.09691 0.17092
#> Bloco       3  112.82  37.61 0.21843 0.88119
#> Residuo     9 1549.52 172.17                
#> Total      15 2745.41                       
#> ------------------------------------------------------------------------
#> CV = 15.28 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.2002677 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.6968564 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 92.29107
#> 2      2 95.24435
#> 3      3 75.08188
#> 4      4 80.84258
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: tch_2_10_canas"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ     QM     Fc   Pr>Fc
#> Tratamento  3 1701.94 567.31 3.8766 0.04957
#> Bloco       3  121.63  40.54 0.2770 0.84063
#> Residuo     9 1317.09 146.34               
#> Total      15 3140.66                      
#> ------------------------------------------------------------------------
#> CV = 13.17 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.3321523 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.2410109 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> Teste de Tukey
#> ------------------------------------------------------------------------
#> Grupos Tratamentos Medias
#> a     1   102.0259 
#> a     2   100.9389 
#> a     4   87.41062 
#> a     3   77.03041 
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: tch_3_media"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ     QM     Fc   Pr>Fc
#> Tratamento  3 1361.73 453.91 3.3196 0.07067
#> Bloco       3   23.39   7.80 0.0570 0.98099
#> Residuo     9 1230.62 136.74               
#> Total      15 2615.74                      
#> ------------------------------------------------------------------------
#> CV = 13.16 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.3382797 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.4395868 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 97.15850
#> 2      2 98.09162
#> 3      3 76.05615
#> 4      4 84.12660
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: pol"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ      QM      Fc   Pr>Fc
#> Tratamento  3 0.6439 0.21463 0.38204 0.76851
#> Bloco       3 0.8051 0.26836 0.47768 0.70565
#> Residuo     9 5.0561 0.56179                
#> Total      15 6.5051                        
#> ------------------------------------------------------------------------
#> CV = 5.2 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.1263727 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.9964091 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 14.20971
#> 2      2 14.22579
#> 3      3 14.55944
#> 4      4 14.66432
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: fibra"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL      SQ       QM      Fc   Pr>Fc
#> Tratamento  3 0.17931 0.059772 0.57585 0.64519
#> Bloco       3 0.28039 0.093465 0.90046 0.47801
#> Residuo     9 0.93417 0.103797                
#> Total      15 1.39388                         
#> ------------------------------------------------------------------------
#> CV = 2.47 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.9055244 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.9258031 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis  Medias
#> 1      1 13.0274
#> 2      2 12.9930
#> 3      3 13.2240
#> 4      4 12.9460
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: pza"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ     QM      Fc   Pr>Fc
#> Tratamento  3  5.364 1.7881 0.39446 0.76016
#> Bloco       3 14.882 4.9607 1.09435 0.40040
#> Residuo     9 40.797 4.5330                
#> Total      15 61.043                       
#> ------------------------------------------------------------------------
#> CV = 2.75 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.200617 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.1128048 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis  Medias
#> 1      1 76.8875
#> 2      2 76.7200
#> 3      3 78.2100
#> 4      4 77.3800
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: pcc"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ      QM      Fc   Pr>Fc
#> Tratamento  3 0.4286 0.14287 0.35294 0.78826
#> Bloco       3 0.6207 0.20690 0.51113 0.68455
#> Residuo     9 3.6431 0.40479                
#> Total      15 4.6924                        
#> ------------------------------------------------------------------------
#> CV = 5.31 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.2321141 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.9510094 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 11.82046
#> 2      2 11.84270
#> 3      3 12.06705
#> 4      4 12.21544
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: ar_percent_caldo"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL       SQ        QM      Fc   Pr>Fc
#> Tratamento  3 0.006293 0.0020978 0.39296 0.76116
#> Bloco       3 0.017506 0.0058354 1.09311 0.40085
#> Residuo     9 0.048045 0.0053383                
#> Total      15 0.071844                          
#> ------------------------------------------------------------------------
#> CV = 7.38 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.2016073 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.1122738 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis    Medias
#> 1      1 1.0037813
#> 2      2 1.0094073
#> 3      3 0.9584159
#> 4      4 0.9868720
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: ar_percent_cana"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL       SQ        QM      Fc   Pr>Fc
#> Tratamento  3 0.004911 0.0016371 0.43866 0.73087
#> Bloco       3 0.011153 0.0037178 0.99620 0.43781
#> Residuo     9 0.033588 0.0037320                
#> Total      15 0.049653                          
#> ------------------------------------------------------------------------
#> CV = 7.42 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.2285916 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.05026885 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis    Medias
#> 1      1 0.8347857
#> 2      2 0.8399694
#> 3      3 0.7947140
#> 4      4 0.8220474
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: atr"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ     QM      Fc   Pr>Fc
#> Tratamento  3  34.63 11.545 0.36470 0.78025
#> Bloco       3  44.98 14.994 0.47366 0.70822
#> Residuo     9 284.90 31.656                
#> Total      15 364.52                       
#> ------------------------------------------------------------------------
#> CV = 4.63 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.2928382 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.9046611 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis   Medias
#> 1      1 120.1575
#> 2      2 120.4175
#> 3      3 122.1475
#> 4      4 123.8100
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: tah_1"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ     QM      Fc   Pr>Fc
#> Tratamento  3 12.998 4.3327 1.68356 0.23928
#> Bloco       3  1.967 0.6556 0.25475 0.85610
#> Residuo     9 23.162 2.5735                
#> Total      15 38.127                       
#> ------------------------------------------------------------------------
#> CV = 15.38 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.3461738 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.5920857 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis    Medias
#> 1      1 11.124082
#> 2      2 11.426057
#> 3      3  9.172959
#> 4      4  9.987804
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: tah_2"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ     QM      Fc   Pr>Fc
#> Tratamento  3 21.402 7.1340 2.31447 0.14435
#> Bloco       3  1.557 0.5191 0.16842 0.91501
#> Residuo     9 27.741 3.0824                
#> Total      15 50.701                       
#> ------------------------------------------------------------------------
#> CV = 15.71 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.2540339 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.3650409 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis    Medias
#> 1      1 12.291721
#> 2      2 12.154901
#> 3      3  9.438497
#> 4      4 10.817488
#> ------------------------------------------------------------------------
#> [1] "************ Análise de Variância ***************"
#> [1] "Variável: tah_3"
#> [1] "*************************************************"
#> [1] "---------Teste F da ANOVA - DBC -----------"
#> ------------------------------------------------------------------------
#> Quadro da analise de variancia
#> ------------------------------------------------------------------------
#>            GL     SQ     QM     Fc   Pr>Fc
#> Tratamento  3 16.784 5.5947 2.2434 0.15245
#> Bloco       3  0.370 0.1232 0.0494 0.98454
#> Residuo     9 22.445 2.4939               
#> Total      15 39.599                      
#> ------------------------------------------------------------------------
#> CV = 14.62 %
#> 
#> ------------------------------------------------------------------------
#> Teste de normalidade dos residuos 
#> valor-p:  0.299818 
#> De acordo com o teste de Shapiro-Wilk a 5% de significancia, os residuos podem ser considerados normais.
#> ------------------------------------------------------------------------
#> 
#> ------------------------------------------------------------------------
#> Teste de homogeneidade de variancia 
#> valor-p:  0.1851713 
#> De acordo com o teste de oneillmathews a 5% de significancia, as variancias podem ser consideradas homogeneas.
#> ------------------------------------------------------------------------
#> 
#> De acordo com o teste F, as medias nao podem ser consideradas diferentes.
#>   Niveis    Medias
#> 1      1 11.707902
#> 2      2 11.790479
#> 3      3  9.305728
#> 4      4 10.402646
#> ------------------------------------------------------------------------
```
