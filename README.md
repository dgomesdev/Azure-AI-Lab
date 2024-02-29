# Azure-AI-Lab

Entre no portal do Azure, pesquise Machine Learning e crie um novo recurso do Azure Machine Learning. Inicie o estúdio do Azure Machine Learning e selecione o espaço de trabalho criado.

Visualize a página ML automatizado. Crie um novo trabalho de ML automatizado. Depois que o conjunto de dados for criado, selecione o conjunto de dados de aluguel de bicicletas para continuar a enviar o trabalho de ML automatizado.

Aguarde a conclusão do trabalho. Revise o melhor modelo. Quando o trabalho de aprendizado de máquina automatizado for concluído, o melhor modelo treinado poderá ser revisado.

Na guia Overview (Visão geral) do trabalho de aprendizado de máquina automatizado, observe o resumo do melhor modelo. Selecione o texto em Algorithm name (Nome do algoritmo) para o melhor modelo para visualizar seus detalhes. Selecione a guia Metrics (Métricas) e selecione os gráficos residuals (resíduos) e predicted_true (previsto_verdadeiro) se eles ainda não estiverem selecionados. Revise os gráficos que mostram o desempenho do modelo.

Na guia Model (Modelo) do melhor modelo treinado pelo seu trabalho de aprendizado de máquina automatizado, selecione Deploy (Implantar) e use a opção Web service (Serviço da Web) para implantar o modelo.

Aguarde o início da implantação. Aguarde até que o status Deploy mude para Succeeded. Teste o serviço implantado

No menu à esquerda, selecione Endpoints e abra o endpoint em tempo real predict-rentals. Na página do endpoint em tempo real de predict-rentals, visualize a guia Test.

No painel Dados de entrada para testar o endpoint, substitua o modelo JSON pelos seguintes dados de entrada:

{
   "Inputs": { 
     "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]    
   },   
   "GlobalParameters": 1.0
}

Clique no botão Testar.

Revise os resultados do teste:

{
  "Results": [
    298.00910497656025
  ]
}
