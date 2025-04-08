# ⚙️ 1. Clonar o repositório DeOldify
!git clone https://github.com/jantic/DeOldify.git DeOldify
%cd DeOldify

# 📦 2. Instalar dependências específicas do Colab
!pip install -r requirements-colab.txt

# 📁 3. Criar pasta para modelos e baixar o modelo pré-treinado
!mkdir models
!wget https://data.deepai.org/deoldify/ColorizeArtistic_gen.pth -O ./models/ColorizeArtistic_gen.pth

# ⚡ 4. Configurar GPU
from deoldify import device
from deoldify.device_id import DeviceId
import torch

device.set(device=DeviceId.GPU0)

if not torch.cuda.is_available():
    print('⚠️ GPU não está disponível. Vá em "Ambiente de execução > Alterar tipo de hardware > GPU"')

# 🛠️ 5. Corrigir erro de segurança do PyTorch 2.6
from functools import partial
torch.serialization.add_safe_globals([partial])

# 🧠 6. Importar o colorizador de imagens
from deoldify.visualize import *
colorizer = get_image_colorizer(artistic=True)

# 🗂️ 7. Montar Google Drive
from google.colab import drive
drive.mount('/content/drive')

# 📷 8. Definir o caminho da sua imagem no Google Drive (ajuste conforme necessário)
# Exemplo: imagem dentro da pasta MyDrive
image_path = '/content/drive/MyDrive/sua_imagem.jpg'  # 🔁 Altere aqui se quiser usar outra

# 🖌️ 9. Colorizar imagem do seu Drive
colorizer.plot_transformed_image(
    path=image_path,
    render_factor=35,
    display_render_factor=True,
    figsize=(8,8)
)
