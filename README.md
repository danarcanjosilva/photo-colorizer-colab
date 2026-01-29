🎨 Photo Colorizer — Google Colab

Colorize fotos antigas automaticamente usando DeOldify no Google Colab, com GPU grátis e sem precisar instalar nada no computador.

👉 Ideal para fotos antigas em preto e branco.

🚀 Executar no Google Colab

Clique no botão abaixo para abrir o notebook no Colab:

👉 **Open in Colab**  
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/danarcanjosilva/photo-colorizer-colab/blob/main/photo_colorizer.ipynb)

⚙️ Passo a passo (IMPORTANTE)
1️⃣ Ativar GPU

No Google Colab:

Ambiente de execução → Alterar tipo de hardware

Em Acelerador de hardware, selecione GPU

Clique em Salvar

2️⃣ Executar a instalação

Execute a primeira célula do notebook
(Ela instala versões compatíveis do PyTorch, FastAI e DeOldify)

⛔ Não pule essa etapa

🔴 3️⃣ Reiniciar a sessão (OBRIGATÓRIO)

Após a instalação, o Colab PRECISA ser reiniciado, senão ocorrem erros de carregamento de modelo.

Faça exatamente assim:

Ambiente de execução → Reiniciar sessão

Confirme

⚠️ Isso é normal no Colab e é necessário por causa das versões das bibliotecas.

4️⃣ Executar o restante do notebook

Depois do restart:

Execute as células a partir da célula de imports

Aguarde o modelo carregar

Faça upload da imagem em preto e branco

5️⃣ Colorizar a imagem

O script irá processar a imagem

O resultado colorido será exibido na tela 🎨✨


<img width="1024" height="1536" alt="0cc0c042-caca-4532-8faf-c9a7733cf0a3" src="https://github.com/user-attachments/assets/74ecb914-856d-4f02-bbd9-3d890fd4a066" />


<img width="1046" height="1560" alt="corenabonita" src="https://github.com/user-attachments/assets/4aeff08b-a1ba-411f-8875-9283067c87a9" />

## 📂 Estrutura

- `DeOldify_colab.ipynb` — Notebook principal para rodar no Colab.
- `README.md` — Este arquivo com instruções.
- `models/` — Pasta onde os modelos são salvos automaticamente.
- `DeOldify/` — Repositório clonado com o código original.

---

## 📌 Requisitos

- Conta no Google
- Acesso ao [Google Colab](https://colab.research.google.com)

---

## 📥 Modelos usados

- `ColorizeArtistic_gen.pth`  
- Armazenados automaticamente em `/models`

---

## 👨‍💻 Autor

Feito com 💙 por [Daniel Arcanjo da Silva](https://github.com/danarcanjosilva)

---

# 🎨 Colorizador de Imagens para Google Colab

---

Script adaptado para facilitar o uso do DeOldify no Google Colab com versões atualizadas das bibliotecas.

---

## 📦 Dependências
- **DeOldify**: Framework de colorização criado por [Jason Antic](https://github.com/jantic).
  
---

## ⚠️ Créditos e Licença
- O núcleo de colorização (`DeOldify/`) é propriedade de **Jason Antic** e está sob licença [MIT](LICENSE-DeOldify).
- Adaptação do script de configuração por **Daniel Arcanjo da Silva**.

