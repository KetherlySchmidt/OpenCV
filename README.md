# Computacao-Grafica-Opencv

Nome  dos desenvolvedores: Guilherme Cardozo e Ketherly Schmidt

# Opencv_annotations

A ferramenta opencv_annotations ajuda a capturar todas as coordenadas retangulares (x,y,w,h) de todas as amostras positivas que você gostaria de usar no treinamento em cascata, o programa irá gerar um arquivo de texto com o caminho do arquivo para a imagem positiva, o número de imagens e as coordenadas retangulares (x,y,w,h), é chamado de opencv_annotations porque descreve algumas informações sobre cada imagem positiva em suas amostras positivas.

**opencv_annotation --annotations=saida.txt --images=positivas/**

O programa será executado e tentará abrir todos os arquivos do diretório positivas e se encontrar qualquer coisa que não seja uma imagem ou que esteja corrompida, ele passará por uma exceção e será encerrado.

Quando iniciado corretamente, o programa exibe uma visualização da imagem. 

⇒ Usa-se o mouse para clicar no ponto onde estão as coordenadas de retângulo e arrastar até que a imagem positiva completa seja selecionada;

⇒ Em seguida pressione a tecla “c” para confirmar a gravação das coordenadas do retângulo;

⇒ E por último pressione a tecla “n” para passar para a próxima imagem;

⇒ Caso tenha marcado as coordenadas erradas aperte “b” para desfazer;

**Repita as etapas para todas as imagens que deseja anotar.**

O programa termina quando não há mais imagens a serem exibidas ou quando você pressiona o botão “esc”. É nesse momento que ele grava o nome do arquivo de imagem positivo e as coordenadas retangulares selecionadas para cada imagem no arquivo de anotações que você especificou.

# opencv_createsamples 
	
Cria amostra de treinamento e teste, os esquemas de criação de amostra de teste é semelhante à criação de amostra de treinamento, pois cada amostra de teste é uma imagem de fundo em que uma imagem distorcida e dimensionada aleatoriamente instância da imagem do objeto é colada em uma posição aleatória.

O **opencv_createsamples** suporta as seguintes opções:

👉 Info – usa-se conjunto com o img para criar teste

👉 Img – usa-se junto com o info para criar amostra de teste

👉 Vec – nome do arquivo de saída contendo as amostras positivas geradas para treinamento

👉 Bg - O arquivo de descrição do plano de fundo (o conjunto de amostra negativa). Ele contém uma lista de imagens nas quais versões distorcidas aleatoriamente do objeto são coladas de forma positiva para a geração de amostra.

👉 Num - O número de amostras positivas para gerar / treinar. 

👉 Bgcolor - A cor de fundo (atualmente, imagens em tons de cinza são assumidas); a cor de fundo denota a cor transparente. O padrão é 0.

👉 Inv - Inverte as cores.

👉 Maxidev - O desvio de intensidade máximo desejado dos pixels das amostras de primeiro plano. O padrão é 40.

👉 Maxxangle - O ângulo de rotação máximo na direção x em radianos. O padrão é 1,1.

👉 Maxyangle - O ângulo de rotação máximo na direção y em radianos. O padrão é 1,1.

👉 Maxzangle - O ângulo de rotação máximo na direção z em radianos. O padrão é 0,5.

👉 Mostra - Mostra cada amostra criada durante o processo de criação. Opcionalmente, um fator de escala pode ser definido. O padrão é 4.0. Se < ESC > for pressionado, o processo de criação continuará sem mostrar amostras. Isso pode ser útil para fins de depuração.

👉 H - Para a criação de amostras de treinamento, é a altura da amostra resultante. O padrão é 24. No caso de criar amostras de teste, é a altura mínima do objeto colocado cenário.

👉 W - Para a criação de amostras de treinamento, é a largura de amostra resultante. O padrão é 24. No caso de criar amostras de teste, é a largura mínima da imagem do objeto colocado.

Exemplos:

Para criar amostras de treinamento de uma imagem aplicando distorções e mostrar os resultados:

**opencv_createsamples -info saida.txt -bg negativas.txt -vec vetor.vec -w 24 -h 24**

Para criar amostras de treinamento de tamanho 40 x 40 a partir de algumas imagens sem aplicar distorções:

**opencv_creasamples  -info  source.dat  -vec  samples_out.vec  -w  40  -H  40**

# opencv_traincascade 
	
A ferramenta opencv_traincascade é uma versão mais recente, escrita em C ++ de acordo com a API OpenCV 2.x e OpenCV 3.x. O opencv_traincascade suporta HAAR como características wavelet e LBP (Local Binary Patterns) características. Os recursos LBP produzem precisão inteira em contraste com os recursos HAAR, produzindo precisão de ponto flutuante, de modo que o treinamento e a detecção com LBP são várias vezes mais rápidos do que os recursos HAAR. Quanto à qualidade da detecção de LBP e HAAR, depende principalmente dos dados de treinamento usados e dos parâmetros de treinamento selecionados. É possível treinar um classificador baseado em LBP que fornecerá quase a mesma qualidade que um baseado em HAAR, dentro de uma porcentagem do tempo de treinamento.

A interface de detecção do classificador em cascata mais recente do OpenCV 2.x e OpenCV 3.x ( cv :: CascadeClassifier ) suporta trabalhar com formatos de modelo novos e antigos. O opencv_traincascade pode até salvar (exportar) uma cascata treinada no formato antigo se por algum motivo você estiver travado usando a interface antiga.

# Tutorial 

O OpenCV é uma biblioteca de programação, de código aberto e inicialmente desenvolvida pela Intel com o objetivo de tornar a visão computacional mais acessível a desenvolvedores. Atualmente possui mais de 500 funções, pode ser utilizada em diversas linguagens de programação (C++, Python, Ruby, Java…) e é usada para diversos tipos de análise em imagens e vídeos, como  detecção, tracking e reconhecimento facial, edição de fotos e vídeos, detecção e análise de textos, etc. 

Com esta documentação, você será capaz de realizar o treinamento da sua IA para o reconhecimento e detecção por meio dos seguintes aplicativos Opencv: **opencv_createsamples, opencv_annotations e opencv_traincascade**. Além disso, será apresentada as diferentes etapas do processo de treinamento, desde a configuração do ambiente, coleta de dados, preparação e execução do treinamento de um modelo real.

Preparação do ambiente

👉 Baixar Python 32bit (durante o processo de instalação é fundamental que a seleção do pip seja realizada)

👉 Instalar opencv no python inserindo o seguinte código na linha de comando: **pip install opencv_python**

👉 Verificar se foi instalado corretamente abrindo o prompt de comando e digitando os códigos descritos abaixo: 

👆 **“python”** – para verificar se a instalação foi realizada na versão correta

👆 **“import cv2”**  – para verificar se foi instalado corretamente o Opencv

👉 Baixar opencv pelo link: **https://opencv.org/releases/** ⇒(atente-se para baixar a versão que seja compatível com as funcionalidades do Python)

👆 Descompactar os arquivos no diretório desejado

👉 Adicionar o seguinte caminho na variável de ambiente: **C:\Users\ + seu users\ + pasta que descompactou\opencv\build\x64\vc14\bin**
Esse endereço pode ser obtido copiando na barra de endereço da pasta que foi descompactado o OpenCV em seu computador. 

👆 Para configurar a variável de ambiente vá em: configurações avançadas do sistema ▷ variáveis de ambiente ▷ selecione o Path ▷ editar ▷ novo ▷ colar ▷ Ok

👉 Criar um diretório com as pastas:  positivas, negativas e treinamento. Atente-se para que o nome das imagens inseridas nas pastas esteja sem espaçamento. Abaixo você confere as funções de cada pasta descrita anteriormente: 

👆 Positivas – conjunto de imagens com o objeto que você deseja detectar

👆 Negativas – conjunto de imagens ao qual não contêm o objeto que você deseja detectar.

👆 Treinamento – pasta onde o processo de treinamento da IA irá criar os estágios.

# Treinamento da IA
👉 Realizar a execução do código buildListNegative.py para criar a lista das imagens inseridas dentro da pasta negativas.

👉 Aplicar o comando: **opencv_annotation --annotations=saida.txt --images=positivas/** no prompt de comando. Será aberta uma janela para que seja realizada a seleção das coordenadas das imagens adicionadas na pasta positivas.

👉 Inserir no prompt de comando: **opencv_createsamples -info saida.txt -bg negativas.txt -vec vetor.vec -w 24 -h 24 para criar o arquivo de vetor.vec**

👉 Aplicar a ferramenta traincascade seguindo o comando: **opencv_traincascade -data treinamento -vec vetor.vec -bg negativas.txt -numPos (número de imagens inseridas na pasta positivas) -numNeg (número de imagens inseridas na pasta negativas) -w 24 -h 24 -precalcValBufSize 1024 -precalcIdxBufSize 1024 -numStages 30 -acceptanceRatioBreakValue 1.0e-5**

👉 Aguardar que o processo de treinamento da IA seja finalizado.

👉 Realizar testes com imagens a fim de analisar o nível de sucesso do treinamento com a ferramenta do código analiseTreinamento.py
