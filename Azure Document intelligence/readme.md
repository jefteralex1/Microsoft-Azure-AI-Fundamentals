# Extração de Dados de Formulários

Imagine uma empresa que atualmente exige que os funcionários preencham folhas de pedidos manualmente e insiram os dados em um banco de dados. Eles estão interessados em utilizar serviços de IA para aprimorar esse processo de entrada de dados. Nesse contexto, você decide desenvolver um modelo de aprendizado de máquina capaz de ler o formulário e produzir dados estruturados que possam ser utilizados para atualizar automaticamente o banco de dados.

## Azure AI Document Intelligence

O Azure AI Document Intelligence é um serviço da Azure AI que possibilita aos usuários criar software automatizado para processamento de dados. Esse software pode extrair texto, pares chave/valor e tabelas de documentos de formulários por meio do reconhecimento óptico de caracteres (OCR). O Azure AI Document Intelligence oferece modelos pré-construídos para reconhecimento de faturas, recibos e cartões de visita, além de capacidade para treinar modelos personalizados.

## Desenvolvimento do Aplicativo no Visual Studio Code

Para iniciar o desenvolvimento do aplicativo, é necessário utilizar o SDK de serviço no Visual Studio Code. Os arquivos de código do aplicativo estão disponíveis em um repositório GitHub.

**Clonando o Repositório:**
- Abra o Visual Studio Code.
- Execute o comando "Git: Clone" na paleta de comandos (SHIFT+CTRL+P) e clone o repositório https://github.com/MicrosoftLearning/mslearn-ai-document-intelligence em uma pasta local.

## Criação do Recurso Azure AI Document Intelligence

Antes de utilizar o serviço Azure AI Document Intelligence, é necessário criar um recurso na sua subscrição do Azure. Siga os passos abaixo:

1. Acesse o portal do Azure em [https://portal.azure.com](https://portal.azure.com).
2. Pesquise por "Document Intelligence" e selecione "Criar".
3. Configure o recurso com os detalhes necessários, como assinatura, grupo de recursos, região e nível de preços.

## Treinamento do Modelo e Uso do Document Intelligence Studio

Após criar o recurso, é hora de treinar o modelo usando o Document Intelligence Studio:

1. Acesse o Document Intelligence Studio em [https://documentintelligence.ai.azure.com/studio](https://documentintelligence.ai.azure.com/studio).
2. Selecione "Modelo de extração personalizado" na seção de "Modelos personalizados".
3. Siga as instruções para criar um projeto, configurar o recurso de serviço e conectar a fonte de dados de treinamento.

## Teste do Modelo Personalizado de Document Intelligence

Após treinar o modelo, é importante testá-lo para verificar sua eficácia:

1. Instale o pacote Azure.AI.FormRecognizer para sua preferência de linguagem (C# ou Python).
2. Edite o arquivo de configuração com os detalhes do ponto de extremidade, chave e ID do modelo.
3. Execute o programa para testar o modelo e observe a saída.

## Limpeza

Após concluir o uso do recurso Azure, lembre-se de removê-lo para evitar encargos adicionais.

## Mais Informações

Para obter mais informações sobre o serviço Document Intelligence, consulte a [documentação oficial](https://docs.microsoft.com/azure/cognitive-services/document-understanding/index).
