# Projeto-de-Data-Analytics-com-Power-BI

Como podemos realizar uma análise estatística e criar visualizações de dados no Power BI. 

Exemplos de código DAX para análise estatística:

---

## **Carregar Dados**
No Power BI Desktop, siga estes passos para carregar seus dados:
1. Clique em **"Obter Dados"** no menu **Início**.
2. Selecione o tipo de fonte de dados que deseja importar.

## **Transformar Dados**
Após carregar os dados, utilize o **Editor de Consultas** para:
- Limpar dados desnecessários.
- Transformar formatos de dados.

## **Criar Modelo de Dados**
Na janela **"Relações"**, crie um modelo de dados:
- Arraste campos para criar relações entre tabelas.

## **Análise Estatística com DAX**
Utilize o painel **"Campos"** para:
- Arrastar e soltar campos e criar visualizações.
- Usar funções DAX para análise, como:

```dax
MedidaDeVendas = SUM(Vendas[Valor])
```

## **Criar Visualizações**
No painel **"Visualizações"**, selecione o tipo de gráfico e arraste os campos relevantes.

## **Publicar Relatório**
Publique seu relatório no serviço Power BI para compartilhamento.

---

## **Modificações no Power BI com Base em Sugestões de Especialistas**

### **Entenda as Sugestões do Especialista**
Certifique-se de compreender as sugestões, que podem incluir:
- Criação de novas visualizações.
- Alteração de visualizações existentes.

### **Abra o Relatório no Power BI Desktop**
Faça as modificações necessárias no relatório aberto.

### **Faça as Modificações**
Baseado nas sugestões, altere gráficos ou adicione novos campos, como:

```dax
TaxaDeCrescimento = (SUM(Vendas[ValorAnoAtual]) - SUM(Vendas[ValorAnoAnterior])) / SUM(Vendas[ValorAnoAnterior])
```

### **Verifique Seu Trabalho**
Confirme se as visualizações e análises estão corretas.

### **Salve e Publique Seu Trabalho**
Após a verificação, salve e publique o relatório.

Lembre-se de que estas são diretrizes gerais e o processo pode variar conforme as sugestões específicas e os dados em questão.

Aqui estão mais alguns exemplos de funções DAX que podemos usar para enriquecer as análises no Power BI:

### **Exemplos de Funções DAX**

#### **Cálculo de Média**
Para calcular a média de vendas, você pode usar a função `AVERAGE`:
```dax
MediaDeVendas = AVERAGE(Vendas[Valor])
```

#### **Cálculo de Percentual**
Para calcular o percentual de vendas realizadas por um segmento específico, use a função `CALCULATE` junto com `FILTER`:
```dax
PercentualDeVendasSegmento = CALCULATE(
    DIVIDE(
        SUM(Vendas[Valor]),
        CALCULATE(SUM(Vendas[Valor]), ALL(Vendas))
    ),
    Vendas[Segmento] = "Tecnologia"
)
```

#### **Crescimento Ano a Ano**
Para analisar o crescimento ano a ano, você pode utilizar a função `SAMEPERIODLASTYEAR`:
```dax
CrescimentoAnoAAno = DIVIDE(
    SUM(Vendas[Valor]) - CALCULATE(SUM(Vendas[Valor]), SAMEPERIODLASTYEAR('Calendário'[Data])),
    CALCULATE(SUM(Vendas[Valor]), SAMEPERIODLASTYEAR('Calendário'[Data]))
)
```

#### **Ranking de Vendas**
Para criar um ranking de vendas entre os vendedores, use a função `RANKX`:
```dax
RankingDeVendas = RANKX(ALL(Vendedores), SUM(Vendas[Valor]))
```

#### **Total Acumulado**
Para calcular o total acumulado de vendas ao longo do tempo, você pode usar a função `TOTALYTD`:
```dax
TotalAcumuladoAnual = TOTALYTD(SUM(Vendas[Valor]), 'Calendário'[Data])
```

Esses são apenas alguns exemplos das poderosas funções DAX disponíveis no Power BI para ajudar na realização de análises complexas e criar relatórios dinâmicos.
