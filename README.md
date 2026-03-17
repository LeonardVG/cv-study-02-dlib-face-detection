# Estudo 02: Detecção Facial com Dlib (HOG & CNN) 

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat-square)
![Dlib](https://img.shields.io/badge/Library-Dlib-red?style=flat-square)
![Status](https://img.shields.io/badge/Status-Educational-orange)


O foco deste notebook é comparar duas tecnologias distintas:
1.  **HOG + SVM:** Método clássico baseado em gradientes.
2.  **CNN (MMOD):** Método moderno baseado em Deep Learning.

### 1. HOG (Histogram of Oriented Gradients)
* **Conceito:** Analisa a direção das bordas e formas geométricas.
* **Performance:** Rápido mesmo em CPUs.
* **Limitação:** Funciona bem apenas para rostos frontais. Sofre com rotações e oclusões.

### 2. CNN (Max-Margin Object Detection)
* **Conceito:** Rede Neural Convolucional treinada profundamente.
* **Performance:** Extremamente precisa, detecta rostos de perfil e em condições difíceis.
* **Limitação:** Muito pesada computacionalmente. Sem uma GPU dedicada (CUDA), o processamento torna-se inviável para tempo real (chegando a 40s+ em imagens de alta resolução com upsampling).

###  Resultados do Experimento (Resumo)
Em testes com múltiplos rostos pequenos (multidão), observou-se:

| Método | Upsampling | Tempo (CPU) | Detecções | Conclusão |
| :--- | :---: | :---: | :---: | :--- |
| **HOG** | 4x | ~9s | 5/9 | Rápido, mas perdeu faces difíceis. |
| **CNN** | 3x | ~44s | 7/9 | Mais preciso, mas 5x mais lento. |

> *A análise detalhada e o código de comparação encontram-se no notebook.*

## ⚠️ Pré-requisitos Importantes

### 1. Arquivo de Pesos da CNN
Ao contrário do HOG (que já vem no Dlib), a CNN precisa de um arquivo de modelo treinado ("o cérebro").
* Arquivo necessário: `mmod_human_face_detector.dat`
* Você pode pegar desse repositório ou baixá-lo no [repositório oficial do Dlib](http://dlib.net/files/mmod_human_face_detector.dat.bz2) (é necessário descompactar).
* **No código:** Certifique-se de apontar o caminho correto para onde você salvou este arquivo.

### 2. Imagens e Caminhos (Google Colab)
O código foi configurado para rodar no Google Colab lendo imagens do **Google Drive**.
* Se for rodar localmente, altere os caminhos das imagens (`cv2.imread`) e do modelo `.dat`.
* Lembre-se: O Dlib trabalha com imagens em **RGB**, enquanto o OpenCV carrega em **BGR**. A conversão é obrigatória para bons resultados na CNN.

##  Tecnologias
* Python
* Dlib
* OpenCV (`cv2`)
* Google Colab

##  Estrutura da Série
1.  [cv-study-01-haarcascade](https://github.com/LeonardVG/cv-study-01-haarcascade) - Detecção básica e rápida.
2.  **cv-study-02-dlib-face-detection** - Comparativo HOG vs CNN (Este repositório).

---
Desenvolvido para fins de estudo.
