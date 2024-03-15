Hand Gesture Prediction Model
 
O Dataset utilizado encontra-se em Classify gestures by reading muscle activity. (kaggle.com)
O objetivo é desenvolver um modelo que possa classificar com precisão diferentes gestos de mão usando leituras de sensores. Essa tecnologia tem aplicações potenciais em diversos campos, incluindo:
* Reconhecimento de linguagem gestual
* Melhorar os movimentos de próteses mecânicas
* Pode ser usada para uma nova forma de interagir com um “computador “ ou interface

O conjunto de dados contém mais de 11 mil instâncias, onde cada uma corresponde a uma medição obtida por um procedimento diagnóstico médico chamado Eletromiografia (EMG), no qual é recolhida a atividade elétrica dos músculos através de transdutores. O conjunto de dados atual contém medições para 4 classes diferentes, onde 0 representa o gesto de Pedra, 1 representa Tesoura, 2 representa Papel e 3 representa Ok. O objetivo é criar um modelo capaz de identificar corretamente o gesto realizado com base nas medições de EMG.

# Carregamento e Pré-processamento dos Dados
Nesta parte, os dados são carregados a partir de arquivos CSV (0.csv, 1.csv, 2.csv, 3.csv) e concatenados em um único DataFrame chamado gesto. Os recursos são armazenados na variável x e os rótulos são armazenados na variável y.

# Normalização dos Dados
Os dados de entrada x são normalizados usando o StandardScaler para garantir que todas as características tenham a mesma escala.

# Transformação dos Rótulos
Os rótulos y são convertidos em codificação one-hot usando a função np.eye().
A função np.eye() cria uma matriz de identidade, que é uma matriz quadrada com todos os elementos iguais a zero, exceto os elementos da diagonal principal, que são iguais a um.

# Divisão dos Dados em Conjuntos de Treino e Teste
Os dados são divididos em conjuntos de treino e teste usando a função train_test_split().

# Definição da Arquitetura do Modelo LSTM

Aqui é definida a arquitetura do modelo LSTM, composto por várias camadas LSTM com dropout e camadas densas. A camada de saída usa a função de ativação softmax para classificação multiclasse.
A definição da arquitetura do modelo LSTM refere-se à configuração das camadas e unidades que compõem a rede neural recorrente LSTM (Long Short-Term Memory). A arquitetura do modelo define como as camadas estão organizadas e conectadas entre si para processar os dados de entrada e gerar as saídas desejadas.
No caso específico da arquitetura LSTM, são definidas as seguintes camadas:
Camadas LSTM: São camadas que contêm unidades LSTM, que são células de memória capazes de lembrar informações ao longo do tempo. Cada camada LSTM pode ter várias unidades LSTM, que processam sequências de dados de entrada e propagam informações relevantes ao longo do tempo.
Camadas de Dropout: São camadas que aplicam o dropout, uma técnica de regularização que desativa aleatoriamente uma fração das unidades de entrada durante o treino. Isso ajuda a evitar o overfitting, onde o modelo ajusta-se em excesso aos dados de treino e não generaliza bem para novos dados.
Camadas Densas: São camadas totalmente conectadas, onde todas as unidades de entrada estão conectadas a todas as unidades de saída. Essas camadas realizam operações de transformação linear e podem ter uma função de ativação associada para introduzir não linearidade na rede.
Na definição da arquitetura do modelo LSTM, também são especificados parâmetros como o número de unidades em cada camada LSTM, a taxa de dropout e a função de ativação da camada de saída. Esses parâmetros são ajustados com base nas características dos dados e nos requisitos da tarefa de aprendizado.

# Compilação e Treino do Modelo

* O modelo é compilado com o otimizador Adam e a função de perda binary_crossentropy. Em seguida, é treinado usando os dados de treino e validação.
Otimizador Adam: Adam é um algoritmo de otimização popular usado para ajustar os pesos da rede neural durante o treino. Combina técnicas de momentum e gradiente descendente estocástico para atualizar os pesos de forma eficiente, levando em consideração tanto o gradiente atual como também o gradiente acumulado ao longo do tempo.
* Função de Perda Binary Crossentropy: É uma função de perda comumente usada em problemas de classificação binária. No entanto, neste contexto multiclasse, ela ainda é aplicada devido à forma como os rótulos foram codificados (one-hot encoding). A função binary crossentropy calcula a diferença entre as probabilidades previstas pelo modelo e as probabilidades reais dos rótulos, penalizando desvios significativos entre essas probabilidades.
Dados de treino e teste: Durante o treino o modelo é ajustado iterativamente usando os dados de treino. Além disso, a validação é realizada em um conjunto separado de dados chamado conjunto de teste. Isso ajuda a monitorar o desempenho do modelo em dados não vistos durante o treino e a evitar o overfitting. Durante o treino, os pesos do modelo são atualizados de acordo com a função de perda e o algoritmo de otimização, e o desempenho é avaliado usando a métrica de precisão (accuracy) e a métrica de perda (loss).
Os resultados do treino são visualizados por meio de gráficos de precisão (accuracy) e perda (loss).

# Conclusão

Este projeto explorou o uso machine learning, especificamente networks Long Short-Term Memory (LSTM), para o reconhecimento de gestos com base em dados de sensores. O conjunto de dados utilizado foi originalmente destinado ao desenvolvimento de próteses biónicas. Ao demonstrar a viabilidade de classificar diversos gestos de mão com alta precisão, este trabalho podia contribuir para os sistemas de controlo das próteses biónicas. 
Próximos passos:
* Ajuste de Hiperparâmetros: Otimizar o desempenho do modelo ajustando hiperparâmetros pode levar a um reconhecimento de gestos ainda mais preciso. 
* Integração próteses biónicas: Integrar o modelo de reconhecimento de gestos com próteses biónicas reais será um passo crucial rumo a aplicações do mundo real. Testes e refinamentos nesse contexto são essenciais. 
* Exploração de Sensores Adicionais: Investigar a incorporação de outras modalidades de sensores (por exemplo, sensores de força, eletromiografia) poderia fornecer informações mais ricas para o reconhecimento de gestos e melhorar as capacidades de controlo.
* Integração em leitura de imagens: Integrar o modelo para leitura de imagens ou vídeo juntamente com os sensores para conseguir analisar linguagem gestual.
Além das conquistas técnicas, este projeto despertou uma forte motivação em nós para explorar mais as redes neurais e o TensorFlow. A habilidade de construir sistemas inteligentes que podem aprender e se adaptar é verdadeiramente impressionante. No geral, este projeto demonstra o potencial de machine learning para o reconhecimento de gestos, contribuindo para o avanço das próteses biónicas e seu potencial de transformar diversos campos.
