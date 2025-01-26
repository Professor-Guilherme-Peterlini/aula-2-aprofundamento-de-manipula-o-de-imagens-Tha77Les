# Questionário Teórico: Processamento de Imagens com Python

## Instruções
* Responda todas as questões de forma clara e concisa
* Justifique suas respostas quando solicitado
* Tempo estimado: 45 minutos

## Questões

### Parte 1: Conceitos Básicos

1. (2,0 pontos) Explique a diferença entre os métodos de redimensionamento de imagem:
   * Nearest Neighbor
   R: É o método mais simples de redimensionamento de imagem, ele copia o valor do pixel mais próximo na hora de redimensionar, um serviço mais rápido que pode acabar gerando uma imagem mais pixelada.

   * Bilinear
   R: O método bilinear realiza um cálculo médio entre 4 pixels para gerar uma imagem com mais detalhes, porém um pouco mais pesada que a Nearest Neighbor.
   
   * Bicubic
   R: O método Bicubic realiza um cálculo médio entre 16 pixels, realizando uma imagem bem mais detalhada e pesada do que os outros métodos.
   
2. (1,5 pontos) Por que é importante fazer backup das imagens originais antes de aplicar transformações? Cite dois cenários onde isso é crítico.
   R: É importante realizar backups caso a imagem seja corrompida, ou caso o resultado não seja o esperado, podendo assim retornar ao seu estado original.

### Parte 2: Escala de Cinza

3. (2,0 pontos) Compare os dois métodos de conversão para escala de cinza vistos em aula:
   * Média simples dos canais RGB
   * Método por luminosidade (Y = 0.299R + 0.587G + 0.114B)
   
   Por que o segundo método é considerado mais preciso para a percepção humana?
   R: Pois o olho humano é mais sensível ao verde.

4. (1,5 pontos) Em processamento de imagens, por que frequentemente convertemos uma imagem para escala de cinza antes de aplicar outros algoritmos?
R: Imagens em escala de cinza possuem se tornam bidimensionais, diferente das imagens coloridas que, além de largura e altura, possuem os canais de cor.

### Parte 3: Detecção de Bordas

5. (2,0 pontos) Explique o funcionamento dos seguintes operadores de detecção de bordas:
   * Sobel
   R: Utiliza duas matrizes 3x3, uma para bordas verticais e outras para verticais, calculando as mudanças em cada direção, que geralmente correspondem a bordas ou contornos.

   * Prewitt
   R: Funciona de maneira semelhante ao Sobel, porém é mais suave.

   * Laplaciano
   O laplace indica mudanças em qualquer dureção, porém, é mais sensíveis a ruído, já que ruídos também variam das cores originais da imagem.

6. (1,5 pontos) Na função `pipeline_processamento()` implementada, por que aplicamos equalização de histograma antes da detecção de bordas?
R: Pois o processo de equalização de histograma melhora o contraste da imagem, tornando as diferenças mais visíveis, facilitando o serviço dos detectores de bordas.

### Parte 4: Aplicação Prática

7. (2,0 pontos) Considere o seguinte trecho de código:
```python
img_bordas = img_equalizada.filter(ImageFilter.FIND_EDGES)
img_final = img_bordas.point(lambda x: 255 if x > limiar else 0)
```
   * Qual o propósito da segunda linha?
   * Como a escolha do valor de limiar afeta o resultado final?

8. (2,5 pontos) Descreva um pipeline completo para:
   * Detectar bordas em uma imagem com ruído
   R:
   def pipeline(imagem, limiar=128):
    img_cinza = imagem.convert('L')
    
    img_equalizada = ImageOps.equalize(img_cinza)
    
    img_bordas = img_equalizada.filter(ImageFilter.FIND_EDGES)

   * Justifique cada etapa do processo
   R: Na variável img_cinza a imagem é passada para a escala de cinza, na img_equalizada, o processo de equalização de histograma é feito, e em img_bordas, as bordas são identificadas.

   * Explique como você escolheria os parâmetros


## Bônus (1,0 ponto extra)
Proponha uma modificação no pipeline de processamento que poderia melhorar os resultados em imagens com baixo contraste.
---
**Autor**: [Guilherme Tavares]  
**Data**: [24/01/2025]  
**Versão**: 1.1
