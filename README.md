# 🎨 Photo Colorizer — DeOldify + Google Colab

Colorização de fotografias em preto e branco usando **DeOldify** em um ambiente **Google Colab com GPU**.

O projeto foi organizado para funcionar com runtimes modernos do Colab sem fazer downgrade do **PyTorch** e do **NumPy** já fornecidos pelo ambiente. O notebook também aplica ajustes de compatibilidade para executar o DeOldify, que utiliza APIs mais antigas.

## 🚀 Abrir no Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/danarcanjosilva/photo-colorizer-colab/blob/main/photo_colorizer.ipynb)

Ou abra diretamente:

**[📓 photo_colorizer.ipynb](./photo_colorizer.ipynb)**

## ✨ O que o projeto faz

* Configura o ambiente do Google Colab para o DeOldify.
* Verifica Python, NumPy, PyTorch e disponibilidade de CUDA.
* Instala `fastai==1.0.61` sem alterar as dependências principais do Colab.
* Instala `ffmpeg-python` e `yt-dlp`.
* Baixa automaticamente o repositório do [DeOldify](https://github.com/jantic/DeOldify).
* Baixa o modelo artístico `ColorizeArtistic_gen.pth` quando necessário.
* Aplica ajustes de compatibilidade para versões atuais do PyTorch e Pillow.
* Usa a GPU do Colab para executar a colorização.
* Permite fazer upload da fotografia diretamente pelo navegador.
* Salva o resultado no diretório de resultados do DeOldify.

## 🧠 Tecnologia

O projeto utiliza principalmente:

* **Python**
* **Google Colab**
* **PyTorch**
* **CUDA**
* **fastai v1**
* **DeOldify**
* **Pillow**
* **NumPy**
* **ffmpeg-python**
* **yt-dlp**

A colorização é realizada com o modelo artístico do DeOldify através de `get_image_colorizer(artistic=True)`.

## 💻 Requisitos

O notebook foi desenvolvido para execução no **Google Colab** e exige um runtime com **GPU**.

No Colab:

1. Abra o notebook.
2. Acesse **Runtime → Change runtime type**.
3. Selecione **GPU** em **Hardware accelerator**.
4. Execute as células na ordem.

O notebook inclui uma verificação que interrompe a execução caso CUDA/GPU não esteja disponível.

## ▶️ Como usar

### 1. Abra o notebook

Clique no botão **Open in Colab** acima.

### 2. Ative a GPU

Confirme que o runtime do Colab está utilizando uma GPU.

### 3. Execute o setup

A primeira etapa verifica o NumPy e instala somente o que é necessário para o DeOldify. O objetivo é preservar o PyTorch e o NumPy fornecidos pelo runtime atual do Colab.

### 4. Baixe o DeOldify e o modelo

O notebook clona automaticamente o DeOldify em:

```text
/content/DeOldify
```

E utiliza o modelo:

```text
/content/DeOldify/models/ColorizeArtistic_gen.pth
```

O download do modelo é feito apenas quando ele ainda não está presente ou está incompleto.

### 5. Envie sua fotografia

A célula de upload abre o seletor de arquivos do Colab. A imagem enviada é salva em:

```text
/content/DeOldify/test_images/
```

### 6. Execute a colorização

O notebook inicializa o colorizador artístico e processa a imagem com:

```python
result_path = colorizer.plot_transformed_image(
    target,
    render_factor=35,
    display_render_factor=True,
    figsize=(20, 20)
)
```

O caminho do resultado é exibido ao final da execução.

## 📁 Estrutura do projeto

```text
photo-colorizer-colab/
├── photo_colorizer.ipynb
└── README.md
```

Durante a execução no Colab, o DeOldify e os arquivos gerados ficam no ambiente temporário de `/content`.

## 🔧 Compatibilidade

O DeOldify utiliza componentes de versões antigas do ecossistema Python. Por isso, o notebook inclui algumas adaptações:

### `fastai`

O projeto instala explicitamente:

```bash
fastai==1.0.61
```

com `--no-deps`, evitando que o instalador substitua automaticamente o PyTorch, torchvision ou NumPy do runtime do Colab.

### PyTorch

O notebook ajusta a chamada de `torch.load()` para permitir o carregamento dos pesos legados usados pelo DeOldify.

> ⚠️ Esse ajuste deve ser usado somente com arquivos/modelos de origem confiável, pois o carregamento tradicional de pesos PyTorch pode utilizar mecanismos de serialização baseados em pickle.

### Pillow

Caso necessário, o notebook recria o alias `Image.ANTIALIAS` usando `Image.Resampling.LANCZOS`, mantendo compatibilidade com trechos antigos do DeOldify sem exigir downgrade do Pillow.

## ✅ Ambiente testado

Uma execução registrada no notebook foi realizada com:

```text
Python: 3.13.15
NumPy: 2.1.3
PyTorch: 2.11.0+cu128
CUDA: 12.8
GPU: Tesla T4
```

Esses valores representam o runtime utilizado na execução registrada do notebook e podem variar conforme a imagem de runtime disponibilizada pelo Google Colab.

## 📌 Observações

* O projeto depende de acesso à Internet para baixar o DeOldify, o modelo e alguns pesos adicionais quando necessário.
* O ambiente do Colab é temporário; arquivos armazenados em `/content` podem ser perdidos quando a sessão for encerrada.
* A primeira execução pode demorar mais porque precisa baixar o modelo e outros arquivos.
* O parâmetro `render_factor=35` está definido no notebook e pode ser ajustado conforme o resultado desejado e os recursos disponíveis.

## 🙏 Créditos

Este projeto utiliza o trabalho do **DeOldify** como base para a colorização.

* DeOldify: https://github.com/jantic/DeOldify
* Repositório deste projeto: https://github.com/danarcanjosilva/photo-colorizer-colab

## 📄 Licença

Este repositório contém o notebook de integração e execução no Google Colab. Para informações de licença, direitos de uso e redistribuição do **DeOldify** e dos modelos utilizados, consulte os termos e arquivos de licença dos respectivos projetos de origem.

---

⭐ Se este projeto foi útil para você, considere deixar uma estrela no repositório.
