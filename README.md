* Projeto de Redes Neurais (Cesar School) - Professor : Vitor Casadei
* Aluno: Ricardo José Nunes Fernandes
* Dataset - Lion ; Tiger ; Cow


## Overview

Foi utilizado um dataset composto por três classes ( Lion ; Tiger ; Cow ), retirados do google imagens, organizados e postados em meu github (Ricardojnf33) Os dados estão divididos em dois conjuntos: "train" e "val" e são compostos por 333 iamgens de cada classe, totalizando 999 imagens.

## Dependencies

* Google Coolab - Python versão 3.7.12
* Pytorch
* Resnet34 (Pré-treinada)

## Notebook

https://colab.research.google.com/drive/1WEAL3FJ0a9OPKrp-TVg3Qc2wWwIC7xhI?usp=sharing

# Estrutura de pastas

*PetImages/
*    train/
*        lion/ ### 333 fotos
*            ...
*        tiger/ ### 333 fotos
*            ...           
*        cow/ ### 333 fotos
*            ...
*    val/
*        lion/ ### 333 fotos
*           ...
*        tiger/ ### 333 fotos
*            ...
*        cow/ ### 333 fotos
*            ...

            
# Abaixo está a maneira de preparar os dados:

# Comando de remoção dos diretórios para restart do modelo

!rm -rf RedesNeurais_ClassificationImage/ val/ PetImages/ PetImagesPetImages/ PetImagesval/
Realizando o clone do repositório ( Github )

# Comando para clonar os dados do dataset salvo no github

!git clone https://github.com/Ricardojnf33/RedesNeurais_ClassificationImage.git

# Reorganizando pastas para criação de diretórios

import os
import shutil
import re

base_dir = "PetImages"
try:
    os.makedirs("PetImages")
except OSError:
    print ("Creation of the directory %s failed")
else:
    print ("Successfully created the directory %s ")
dataset_dir = "RedesNeurais_ClassificationImage/train"

# Criar pasta de treinamento
files = os.listdir(base_dir)

# Move todas as imagens de treinamento de leões para a pasta de leões, imagens de treinamento de tigres para a pasta de tigres e imagens de treinamento de vacas para a pasta vacas

def train_maker(name):
  try:
      path = f"{base_dir}/train/{name}"
      os.makedirs(path, exist_ok=True)
  except OSError:
      print ("Creation of the directory failed")
  else:
      print ("Successfully created the directory")
  print("here")
  train_dir = f"{base_dir}/train/{name}"
  print(train_dir)
  files = os.listdir(dataset_dir)
  print(files)
  
  for f in files:
        search_object = re.search(name.lower(), f)
        print(search_object)
        if search_object:
          shutil.move(f'{dataset_dir}/{f}', train_dir)

train_maker("lion")
train_maker("tiger")
train_maker("cow")

# Criando diretórios e pastas de validação

try:
    path = base_dir + "/val/lion"
    os.makedirs(path, exist_ok=True)
    path = base_dir + "/val/tiger"
    os.makedirs(path, exist_ok=True)
    path = base_dir + "/val/cow"
    os.makedirs(path, exist_ok=True)
except OSError:
    print ("Creation of the directory failed")
else:
    print ("Successfully created the directory")
Successfully created the directory

# Criando pasta de validação

lion_train = base_dir + "/train/lion"
lion_val = base_dir + "/val/lion/"
tiger_train = base_dir + "/train/tiger/"
tiger_val = base_dir + "/val/tiger/"
cow_train = base_dir + "/train/cow/"
cow_val = base_dir + "/val/cow/"
lion_files = os.listdir(lion_train)
tiger_files = os.listdir(tiger_train)
cow_files = os.listdir(cow_train)

# Retirando imagens das pastas de treino e inserindo nas suas respectivas pastas de validação

for f in lion_files:
    validationCatsSearchObj = re.search("\d\d\d", f)
    if validationCatsSearchObj:
        shutil.move(f'{lion_train}/{f}', lion_val)

for f in tiger_files:
    validationCatsSearchObj = re.search("\d\d\d", f)
    if validationCatsSearchObj:
        shutil.move(f'{tiger_train}/{f}', tiger_val)

for f in cow_files:
    validationCatsSearchObj = re.search("\d\d\d", f)
    if validationCatsSearchObj:
        shutil.move(f'{cow_train}/{f}', cow_val)


from __future__ import print_function, division

import torch
import torch.nn as nn
import torch.optim as optim
from torch.optim import lr_scheduler
import torchvision
from torchvision import datasets, models, transforms
import matplotlib.pyplot as plt
import numpy as np
import time
import os
import copy

# Definindo transformações para aumentar a variabilidade das imagens, através de re-cálcuco de tamanhos, recortes de pedaços, rotações, normalização e transformações em Tensor.

# Faça transformações e use carregadores de dados (data loaders)
# Usaremos muito isso, então faça com que sejam variáveis

mean_nums = [0.485, 0.456, 0.406]
std_nums = [0.229, 0.224, 0.225]

chosen_transforms = {'train': transforms.Compose([
        transforms.RandomResizedCrop(size=256),
        transforms.RandomRotation(degrees=15),
        transforms.RandomHorizontalFlip(),
        transforms.ToTensor(),
        transforms.Normalize(mean_nums, std_nums)
]), 'val': transforms.Compose([
        transforms.Resize(256),
        transforms.CenterCrop(224),
        transforms.ToTensor(),
        transforms.Normalize(mean_nums, std_nums)
]),
}
# Construção do dataset

# Defina o diretório para os dados

data_dir = 'PetImages/'

# Use a função de pasta de imagens para criar conjuntos de dados

chosen_datasets = {x: datasets.ImageFolder(os.path.join(data_dir, x), chosen_transforms[x]) for x in ['train', 'val']}
Criando dataloaders para obter imagens iteráveis
[16]
0s
 
# Faça iteráveis com os carregadores de dados

dataloaders = {x: torch.utils.data.DataLoader(chosen_datasets[x], batch_size=4,
  shuffle=True, num_workers=4)
              for x in ['train', 'val']}

dataloaders
{'train': <torch.utils.data.dataloader.DataLoader at 0x7fd70715d810>,
 'val': <torch.utils.data.dataloader.DataLoader at 0x7fd606e8dd90>}
Vamos precisar preservar algumas informações sobre nosso conjunto de dados, especificando o tamanho do conjunto de dados, nomes das classes e especificando o tipo de dispositivo ( GPU ).

dataset_sizes = {x: len(chosen_datasets[x]) for x in ['train', 'val']}
class_names = chosen_datasets['train'].classes

device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
Visualização de Datasets e Classes

print(dataset_sizes)
print(class_names)
{'train': 222, 'val': 776}
['cow', 'lion', 'tiger']

# Visualização de imagens com uma função. Pegando uma entrada, criando uma matriz Numpy a partir dela e a transpondo a mesma. Em seguida, normaliza-se a entrada usando média e desvio padrão. Por fim, recorta-se os valores entre 0 e 1 para que não haja um intervalo enorme nos valores possíveis do array e, em seguida, mostraremos a imagem:

def imshow(inp, title=None):
    inp = inp.numpy().transpose((1, 2, 0))
    mean = np.array([mean_nums])
    std = np.array([std_nums])
    inp = std * inp + mean
    inp = np.clip(inp, 0, 1)
    plt.imshow(inp)
    if title is not None:
        plt.title(title)
    plt.pause(0.001)  # Pause a bit so that plots are updated
Visualizando alguns dos dados

# Pegue alguns dos dados de treinamento para visualizar

inputs, classes = next(iter(dataloaders['train']))

# Agora construímos uma grade de lote

out = torchvision.utils.make_grid(inputs)

imshow(out, title=[class_names[x] for x in classes])

# Realizando set do modelo e o download da resnet34 (Pré-treinada) para utilização dos pesos para treinamento

# carregando modelo pré-treinado e reset final totalmente conectado

res_mod = models.resnet34(pretrained=True)

num_ftrs = res_mod.fc.in_features
res_mod.fc = nn.Linear(num_ftrs, 3)

# Visualização da composição do modelo

for name, child in res_mod.named_children():
    print(name)
    
conv1
bn1
relu
maxpool
layer1
layer2
layer3
layer4
avgpool
fc

# A parte final "fc" (Fully-Connected) é a camada que estamos modificando a forma, dando-a três classes de saída. Essencialmente, vamos alterar as saídas da parte final totalmente conectada para apenas duas classes e ajustar os pesos para todas as outras camadas.

# Agora precisamos enviar nosso modelo para nosso dispositivo de treinamento. Também precisamos escolher o critério de perda e o otimizador que queremos usar com o modelo. CrossEntropyLoss e o otimizador SGD são boas escolhas, embora existam muitos outros.

# Também escolheremos um agendador de taxa de aprendizado, que diminui a taxa de aprendizado do otimizador de horas extras e ajuda a evitar a não convergência devido a grandes taxas de aprendizado. Você pode aprender mais sobre programadores de taxa de aprendizado aqui se estiver curioso:

res_mod = res_mod.to(device)
criterion = nn.CrossEntropyLoss()

# Observe que todos os parâmetros estão sendo otimizados

optimizer_ft = optim.SGD(res_mod.parameters(), lr=0.001, momentum=0.9)

# Decay LR by a factor of 0.1 every 7 epochs

exp_lr_scheduler = lr_scheduler.StepLR(optimizer_ft, step_size=7, gamma=0.1)

# Definindo as funções que irão treinar o modelo e visualizar as previsões.Vamos começar com a função de treinamento. Levará em nosso modelo escolhido, bem como o otimizador, critério e escalonador que escolhemos. Também especificaremos um número padrão de épocas de treinamento.
# Cada época terá uma fase de treinamento e validação. Para começar, definimos os melhores pesos iniciais do modelo para aqueles do modo pré-treinado, usando state_dict.
# Agora, para cada época no número escolhido de épocas, se estivermos na fase de treinamento, iremos:
#  *Diminua a taxa de aprendizado
#  *Zere os gradientes
#  *Executar o passe de treinamento para a frente
#  *Calcule a perda
#  *Faça a "back-propagation" e atualize os pesos com o otimizador

    def train_model(model, criterion, optimizer, scheduler, num_epochs=10):
    since = time.time()

    best_model_wts = copy.deepcopy(model.state_dict())
    best_acc = 0.0

    for epoch in range(num_epochs):
        print('Epoch {}/{}'.format(epoch, num_epochs - 1))
        print('-' * 10)

   # Cada época tem uma fase de treinamento e validação
   
        for phase in ['train', 'val']:
            if phase == 'train':
                scheduler.step()
                model.train()  # Set model to training mode
            else:
                model.eval()   # Set model to evaluate mode

            current_loss = 0.0
            current_corrects = 0

   # Aqui é onde o treinamento acontece
   
            print('Iterating through data...')

            for inputs, labels in dataloaders[phase]:
                inputs = inputs.to(device)
                labels = labels.to(device)

   # Precisamos zerar os gradientes, não esqueça
   
                optimizer.zero_grad()

   # Hora de realizar o treinamento avançado poss
   # Só precisamos registrar as estatísticas de perda se estivermos em fase de treinamento
   
                with torch.set_grad_enabled(phase == 'train'):
                    outputs = model(inputs)
                    _, preds = torch.max(outputs, 1)
                    loss = criterion(outputs, labels)

   # backward + optimize somente se estiver em fase de treinamento
   
                    if phase == 'train':
                        loss.backward()
                        optimizer.step()

   # Queremos que as variáveis mantenham as estatísticas de perda
   
                current_loss += loss.item() * inputs.size(0)
                current_corrects += torch.sum(preds == labels.data)

            epoch_loss = current_loss / dataset_sizes[phase]
            epoch_acc = current_corrects.double() / dataset_sizes[phase]

            print('{} Loss: {:.4f} Acc: {:.4f}'.format(
                phase, epoch_loss, epoch_acc))

   # Make a copy of the model if the accuracy on the validation set has improved
            if phase == 'val' and epoch_acc > best_acc:
                best_acc = epoch_acc
                best_model_wts = copy.deepcopy(model.state_dict())

        print()

    time_since = time.time() - since
    print('Training complete in {:.0f}m {:.0f}s'.format(
        time_since // 60, time_since % 60))
    print('Best val Acc: {:4f}'.format(best_acc))

   # Now we'll load in the best model weights and return it
    model.load_state_dict(best_model_wts)
    return model
    
# Função para visualização das predições realizadas pelo modelo

    def visualize_model(model, num_images=12):
    was_training = model.training
    model.eval()
    images_handeled = 0
    fig = plt.figure()

    with torch.no_grad():
        for i, (inputs, labels) in enumerate(dataloaders['val']):
            inputs = inputs.to(device)
            labels = labels.to(device)

            outputs = model(inputs)
            _, preds = torch.max(outputs, 1)

            for j in range(inputs.size()[0]):
                images_handeled += 1
                ax = plt.subplot(num_images//2, 2, images_handeled)
                ax.axis('off')
                ax.set_title('predicted: {}'.format(class_names[preds[j]]))
                imshow(inputs.cpu().data[j])

                if images_handeled == num_images:
                    model.train(mode=was_training)
                    return
        model.train(mode=was_training)
        
# Treinando o modelo com as imagens e mostrando previsões

base_model = train_model(res_mod, criterion, optimizer_ft, exp_lr_scheduler, num_epochs=3)
visualize_model(base_model)
plt.show()

# Configurando o modelo
# Observe que os parâmetros dos modelos importados são definidos como "require_grad=True" por default

res_mod = models.resnet34(pretrained=True)
for param in res_mod.parameters():
    param.requires_grad = False

num_ftrs = res_mod.fc.in_features
res_mod.fc = nn.Linear(num_ftrs, 3)

res_mod = res_mod.to(device)
criterion = nn.CrossEntropyLoss()

# Aqui está outra mudança: em vez de todos os parâmetros serem otimizados
# Apenas os parâmetros das camadas finais estão sendo otimizados

optimizer_ft = optim.SGD(res_mod.fc.parameters(), lr=0.001, momentum=0.9)

exp_lr_scheduler = lr_scheduler.StepLR(optimizer_ft, step_size=7, gamma=0.1)

for name, child in res_mod.named_children():
    print(name)
    
conv1
bn1
relu
maxpool
layer1
layer2
layer3
layer4
avgpool
fc

for name, child in res_mod.named_children():
    if name in ['layer3', 'layer4']:
        print(name + 'has been unfrozen.')
        for param in child.parameters():
            param.requires_grad = True
    else:
        for param in child.parameters():
            param.requires_grad = False
layer3has been unfrozen.
layer4has been unfrozen.

optimizer_conv = torch.optim.SGD(filter(lambda x: x.requires_grad, res_mod.parameters()), lr=0.001, momentum=0.9)
 
base_model = train_model(res_mod, criterion, optimizer_conv, exp_lr_scheduler, num_epochs=3)
visualize_model(base_model)
plt.show()

!mkdir models/

torch.save(base_model.state_dict(), "/content/models/test.pt" )

base_model.load_state_dict(torch.load("/content/models/test.pt"))
base_model.eval()

ResNet(
  (conv1): Conv2d(3, 64, kernel_size=(7, 7), stride=(2, 2), padding=(3, 3), bias=False)
  (bn1): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
  (relu): ReLU(inplace=True)
  (maxpool): MaxPool2d(kernel_size=3, stride=2, padding=1, dilation=1, ceil_mode=False)
  (layer1): Sequential(
    (0): BasicBlock(
      (conv1): Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (1): BasicBlock(
      (conv1): Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (2): BasicBlock(
      (conv1): Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
  )
  (layer2): Sequential(
    (0): BasicBlock(
      (conv1): Conv2d(64, 128, kernel_size=(3, 3), stride=(2, 2), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (downsample): Sequential(
        (0): Conv2d(64, 128, kernel_size=(1, 1), stride=(2, 2), bias=False)
        (1): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      )
    )
    (1): BasicBlock(
      (conv1): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (2): BasicBlock(
      (conv1): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (3): BasicBlock(
      (conv1): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
  )
  (layer3): Sequential(
    (0): BasicBlock(
      (conv1): Conv2d(128, 256, kernel_size=(3, 3), stride=(2, 2), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (downsample): Sequential(
        (0): Conv2d(128, 256, kernel_size=(1, 1), stride=(2, 2), bias=False)
        (1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      )
    )
    (1): BasicBlock(
      (conv1): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (2): BasicBlock(
      (conv1): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (3): BasicBlock(
      (conv1): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (4): BasicBlock(
      (conv1): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (5): BasicBlock(
      (conv1): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
  )
  (layer4): Sequential(
    (0): BasicBlock(
      (conv1): Conv2d(256, 512, kernel_size=(3, 3), stride=(2, 2), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (downsample): Sequential(
        (0): Conv2d(256, 512, kernel_size=(1, 1), stride=(2, 2), bias=False)
        (1): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      )
    )
    (1): BasicBlock(
      (conv1): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (2): BasicBlock(
      (conv1): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
  )
  (avgpool): AdaptiveAvgPool2d(output_size=(1, 1))
  (fc): Linear(in_features=512, out_features=3, bias=True)
)

## Conclusão
# Foi implementado um modelo de redes neurais, salvo na pasta \models do painel do colab, com um dataset de três classes (lion-tiger-cow), contendo um total 999 imagens, postado em minha página do github https://github.com/Ricardojnf33, com o repositório de título RedesNeurais_ClassificationImage. O treinamento foi realizado em 12m 9s com os seguintes resultados:

# val Loss: 0.0429
# Best val Acc: 0.996134
