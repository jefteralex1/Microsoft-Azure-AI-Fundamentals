# Extraia dados de formulários com Azure AI Document Intelligence

Imagine uma empresa que atualmente requer que os funcionários comprem folhas de pedidos manualmente e insiram os dados em um banco de dados. Eles estão interessados em usar serviços de IA para melhorar esse processo. Aqui está um passo a passo sobre como construir um modelo de aprendizado de máquina para ler formulários e produzir dados estruturados que podem ser usados para atualizar automaticamente um banco de dados.

## Azure AI Document Intelligence

O Azure AI Document Intelligence é um serviço da Azure AI que permite aos usuários criar software automatizado de processamento de dados. Ele pode extrair texto, pares chave/valor e tabelas de documentos de formulário usando reconhecimento óptico de caracteres (OCR). O serviço oferece modelos pré-construídos para reconhecimento de faturas, recibos e cartões de visita, além de permitir a criação de modelos personalizados.

## Preparação do Ambiente de Desenvolvimento

1. Clone o repositório `mslearn-ai-document-intelligence` do GitHub.
2. Abra o Visual Studio Code.
3. Na paleta (SHIFT+CTRL+P), execute o comando Git: Clone para clonar o repositório.
4. Abra a pasta no Visual Studio Code e aguarde a instalação de arquivos adicionais.

## Criação de Recurso Azure AI Document Intelligence

5. Acesse o portal do Azure e navegue até Document Intelligence.
6. Selecione Criar e configure seu recurso.
7. Após a criação, acesse o recurso para visualizar a página de Visão Geral.

## Preparação de Dados e Ambiente de Desenvolvimento

8. Reúna os formulários de amostra necessários para treinamento.
9. Abra a pasta `Labfiles/02-custom-document-intelligence` no Visual Studio Code.
10. Execute o script `setup.cmd` para criar recursos adicionais no Azure.
11. Verifique se os arquivos foram carregados com sucesso na conta de armazenamento.

## Treinamento do Modelo

12. Acesse o Document Intelligence Studio.
13. Crie um projeto de modelo de extração personalizado.
14. Configure o recurso de serviço e conecte a fonte de dados de treinamento.
15. Inicie o treinamento do modelo.

## Teste do Modelo Personalizado

16. Instale o pacote Document Intelligence no Visual Studio Code.
17. Edite o arquivo de configuração com os valores necessários.
18. Abra o arquivo de código do seu aplicativo cliente e revise-o.
19. Execute o programa e observe a saída do modelo.

## Limpeza

20. Se necessário, exclua o recurso no portal do Azure para evitar encargos adicionais.

## Mais Informações

- Para mais detalhes sobre o serviço Document Intelligence, consulte a [documentação oficial](https://docs.microsoft.com/azure/applied-ai-services/document-understanding/index).
