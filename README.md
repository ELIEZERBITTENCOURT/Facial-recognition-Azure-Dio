# Learning Facial recognition

Foi utilizado codigo em python e precisará instalar a biblioteca azure-cognitiveservices-vision-face para interagir com a API do Azure. Instalar essa biblioteca via pip:

```bash
pip install azure-cognitiveservices-vision-face
```

Aqui está o codigo utilizado:

```bash
from azure.cognitiveservices.vision.face import FaceClient
from msrest.authentication import CognitiveServicesCredentials
import os

# Credenciais do Azure
subscription_key = 'AQUI_SUA_CHAVE_DE_ASSINATURA'
endpoint = 'AQUI_SEU_ENDPOINT'

# Caminho para a imagem a ser analisada
image_path = 'caminho/para/sua/imagem.jpg'

# Inicialização do cliente da face
face_client = FaceClient(endpoint, CognitiveServicesCredentials(subscription_key))

# Carrega a imagem
with open(image_path, 'rb') as image_file:
    detected_faces = face_client.face.detect_with_stream(image=image_file)

# Mostra resultados
print('Rostos detectados na imagem:')
for face in detected_faces:
    print(f'ID: {face.face_id}')
    print(f'Posição do rosto: {face.face_rectangle}')
    print(f'Gênero: {face.face_attributes.gender}')
    print(f'Idade: {face.face_attributes.age}')
    print('---')

```
