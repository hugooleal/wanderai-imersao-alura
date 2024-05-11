# WanderAI - Gerador de Roteiros de Viagem com Google Gemini
## 1. Introdução
Este repositório contém um script Python que utiliza o poder do modelo de linguagem Google Gemini para gerar roteiros de viagem personalizados. Através de perguntas sobre suas preferências, o script constrói um roteiro detalhado, incluindo sugestões de atividades, restaurantes e dicas de transporte.
## 2. Explicação do Código
O código se divide nas seguintes etapas:
### 2.1 Instalação e Importações:
Instala a biblioteca google-generativeai.
Importa as bibliotecas necessárias: google.generativeai, pandas, numpy, pathlib, textwrap, IPython.display.
### 2.2 Funções Auxiliares:
to_markdown(text): Formata o texto da resposta para o formato Markdown.
### 2.3 Configuração do Modelo Gemini:
Define a chave da API do Google Gemini (api_key), que está guardada secretamente no Google Golab.
Lista os modelos disponíveis com suporte para geração de conteúdo.
Define as configurações do modelo (temperatura, top_p, top_k, max_output_tokens). Nessa etapa, criamos um dicionário contendo 3 configs diferentes cada uma com uma temperatura, sendo elas: 0.5, 0.75 e 1.
Configura parâmetros de segurança para evitar conteúdo inadequado.
### 2.4 Coleta de Informações do Usuário:
Solicita ao usuário as informações sobre o destino, estilo de viagem, duração, atividades preferidas e orçamento.
### 2.5 Geração do Roteiro:
Constrói um prompt detalhado com as informações fornecidas pelo usuário.
Com base no prompt gerado, fazemos uma iteração entre as 3 configurações criadas nos passos acima. Dessa forma, recebemos 3 respostas diferentes para o mesmo prompt, considerando temperaturas de 0.5, 0.75 e 1. Dessa forma conseguimos explorar diferentes níveis de criatividade.
### 2.6 Processamento das Respostas:
Em seguida, armazenamos as respostas em um DataFrame Pandas e criamos a função "embedFunction" para se utilizar dos modelos de embedding do Google Gemini para gerar embeddings para cada resposta, representando seu significado semanticamente.
### 2.7 Seleção da Melhor Resposta:
Posteriormente, criamos a função "consultarMelhorResposta" que compara o embedding do prompt inicial com os embeddings das respostas e
seleciona a resposta com o maior produto escalar, ou seja, aquela que indica maior similaridade semântica com o prompt.
Dessa forma, aplicamos um método de autovalidação pelo próprio Gemini, combinando tanto o modelo gerador de conteúdo quanto o modelo de embedding. 
### 2.8 Apresentação da Melhor Resposta:
A melhor resposta é formatada com Markdown e exibida ao usuário.
## 3. Conclusão
Este script demonstra o enorme potencial do Google Gemini nas mais diversas áreas que a imaginação pode chegar. A criação de roteiros de viagem personalizados e informativos é apenas uma das milhares de possibilidades. Ao ajustar as configurações do modelo e coletar informações detalhadas do usuário, o script oferece uma experiência de planejamento de viagem interativa e eficiente, de forma rápida.
