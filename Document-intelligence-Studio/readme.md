Criar um recurso de Pesquisa de IA do Azure

Criar um recurso de serviços de IA do Azure

Criar uma conta de armazenamento

No painel do menu à esquerda do Armazenamento do Azure, selecione Contêineres.

Selecione + Contêiner. Um painel do lado direito é aberto.

Em uma nova guia do navegador, baixe as avaliações de café compactadas de https://aka.ms/mslearn-coffee-reviews e extraia os arquivos para a pasta de avaliações.

No portal do Azure, selecione o contêiner coffee-reviews. No contêiner, selecione Upload.

No painel Upload blob, selecione Select a file (Selecionar um arquivo).

Na janela Explorer, selecione todos os arquivos na pasta de análises, selecione Abrir e, em seguida, selecione Carregar.

Após a conclusão do upload, você pode fechar o painel Upload blob. Seus documentos estão agora no contêiner de armazenamento do coffee-reviews.

Depois de ter os documentos no armazenamento, você pode usar o Azure AI Search para extrair insights dos documentos. O portal do Azure fornece um assistente de importação de dados. Com esse assistente, você pode criar automaticamente um índice e um indexador para as fontes de dados compatíveis. Você usará o assistente para criar um índice e importar seus documentos de pesquisa do armazenamento para o índice do Azure AI Search.

No portal do Azure, navegue até seu recurso do Azure AI Search. Na página Visão geral, selecione Importar dados.

Na página Conectar aos seus dados, na lista Fonte de dados, selecione Armazenamento de Blobs do Azure.

Na seção Anexar Serviços Cognitivos, selecione seu recurso de serviços de IA do Azure.

Na seção Adicionar enriquecimentos:

Altere o nome do Skillset para coffee-skillset.

Marque a caixa de seleção Enable OCR (Ativar OCR) e mescle todo o texto no campo merged_content (conteúdo mesclado).

Observação É importante selecionar Enable OCR para ver todas as opções de campo enriquecido.

Certifique-se de que o campo Source data esteja definido como merged_content.

Altere o nível de granularidade do enriquecimento para Páginas (blocos de 5.000 caracteres).

Não selecione Habilitar enriquecimento incremental

Selecione Choose an existing connection (Escolher uma conexão existente). Escolha a conta de armazenamento que você criou anteriormente.

Clique em + Container (Contêiner) para criar um novo contêiner chamado knowledge-store (armazenamento de conhecimento) com o nível de privacidade definido como Private (Privado) e selecione Create (Criar).

Selecione o contêiner de armazenamento de conhecimento e clique em Selecionar na parte inferior da tela.

Selecione Projeções de blob do Azure: Document. É exibida uma configuração para Nome do contêiner com o contêiner da loja de conhecimento preenchido automaticamente. Não altere o nome do contêiner.

Selecione Avançar: Customize target index (Personalizar índice de destino). Altere o nome do índice para coffee-index.

Certifique-se de que a Chave esteja definida como metadata_storage_path. Deixe o nome do Sugeridor em branco e o Modo de pesquisa preenchido automaticamente.

Revise as configurações padrão dos campos do índice. Selecione filterable (filtrável) para todos os campos que já estão selecionados por padrão.

Selecione Avançar: Criar um indexador.

Altere o nome do indexador para coffee-indexer.

Deixe a Programação definida como Uma vez.

Expanda as opções avançadas. Certifique-se de que a opção Chaves de codificação Base-64 esteja selecionada, pois as chaves de codificação podem tornar o índice mais eficiente.

Selecione Enviar para criar a fonte de dados, o conjunto de habilidades, o índice e o indexador. O indexador é executado automaticamente e executa o pipeline de indexação, que:

Extrai os campos de metadados do documento e o conteúdo da fonte de dados.

Executa o conjunto de habilidades cognitivas para gerar campos mais enriquecidos.

Mapeia os campos extraídos para o índice.

Retorne à sua página de recursos do Azure AI Search. No painel esquerdo, em Gerenciamento de pesquisa, selecione Indexadores. Selecione o indexador de café recém-criado. Aguarde um minuto e selecione ↻ Refresh (Atualizar) até que o Status indique sucesso.

Selecione o nome do indexador para ver mais detalhes.

Captura de tela que mostra o indexador coffee-indexer criado com sucesso.

Use o Search explorer para escrever e testar consultas. O Search explorer é uma ferramenta incorporada ao portal do Azure que oferece uma maneira fácil de validar a qualidade do seu índice de pesquisa. Você pode usar o Search Explorer para escrever consultas e revisar os resultados em JSON.

Na página Visão geral do seu serviço de pesquisa, selecione Search explorer na parte superior da tela.

Observe como o índice selecionado é o índice de café que você criou. Abaixo do índice selecionado, altere a visualização para visualização JSON.

Selecione Search (Pesquisar). A consulta pesquisa todos os documentos no índice e filtra as avaliações com um sentimento negativo. Você deverá ver 1 no campo @odata.count.

Observação: veja como os resultados são classificados por @search.score. Essa é a pontuação atribuída pelo mecanismo de pesquisa para mostrar a proximidade da correspondência dos resultados com a consulta fornecida.

No portal do Azure, navegue de volta para sua conta de armazenamento do Azure.

No painel do menu à esquerda, selecione Contêineres. Selecione o contêiner do armazenamento de conhecimento.

Selecione qualquer um dos itens e, em seguida, clique no arquivo objectprojection.json.

Selecione Editar para ver o JSON produzido para um dos documentos de seu armazenamento de dados do Azure.

Selecione o breadcrumb de blob de armazenamento no canto superior esquerdo da tela para retornar aos contêineres da conta de armazenamento.

Nos contêineres, selecione o contêiner coffee-skillset-image-projection. Selecione qualquer um dos itens.

Selecione qualquer um dos arquivos .jpg. Selecione Edit (Editar) para ver a imagem armazenada do documento. Observe como todas as imagens dos documentos são armazenadas dessa maneira.

Selecione o breadcrumb da bolha de armazenamento no canto superior esquerdo da tela para retornar aos contêineres da conta de armazenamento.

Selecione Navegador de armazenamento no painel esquerdo e selecione Tabelas. Há uma tabela para cada entidade no índice. Selecione a tabela coffeeSkillsetKeyPhrases.

Observe as frases-chave que o armazenamento de conhecimento conseguiu capturar do conteúdo das revisões. Muitos dos campos são chaves, portanto, você pode vincular as tabelas como em um banco de dados relacional. O último campo mostra as frases-chave que foram extraídas pelo conjunto de habilidades.
