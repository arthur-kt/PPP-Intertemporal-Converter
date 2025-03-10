# PPP-Intertemporal-Converter

Conversor de preços usando o método de Pariedade de Poder de Compra e ajustando pelo tempo usando a inflação americana.

## Funcinalidades
Primeiro, foram reunidos os dados de Paridade do Poder de Compra (PPP) para cada país e ano relevante, sendo eles retirados do Banco Mundial. O índice PPP representa o número de unidades da moeda local necessárias para comprar uma quantidade equivalente de bens e serviços que custaria 1 dólar nos EUA. Em seguida, cada gasto em moeda local é ajustado para dólares PPP do ano específico. Para isso, o valor do gasto em moeda local é divido pelo índice PPP daquele ano, convertendo assim o gasto para a moeda dos EUA ajustada pelo poder de compra. Por exemplo, se o gasto foi de 100 unidades em uma moeda local e o índice PPP é 0,8, o valor ajustado para dólares PPP seria 100 / 0,8, resultando em 125 dólares PPP.

Para expressar os valores em dólares correntes, é aplicado o ajuste pela inflação dos EUA, utilizando o índice de preços ao consumidor (CPI) disponível no Federal Reserve Economic Data (FRED). O valor em dólares PPP é multiplicado pelo índice de inflação acumulada dos EUA até o ano atual, ajustando-o pela taxa CPI do ano original, de modo que o cálculo final seja: valor ajustado = gasto em dólares PPP * (CPI atual / CPI do ano de referência). Para o caso de gastos realizados em diferentes anos, o programa calcula a média do PPP e do CPI entre os dois anos para efetuar o cálculo.

O ano de 2024 não conta com dados do PPP, logo a conversão de valores foi feita utilizando a taxa média de câmbio do ano de 2024 do país com dados em 2024 em relação ao dólar americano. Nos casos em que o gasto ocorre entre dois anos e o segundo ano é 2024, aplica-se uma abordagem combinada: primeiro, o valor é convertido pela taxa de câmbio de 2024 (sem ajuste por inflação); em seguida, é calculado o valor com base no PPP e CPI apenas do primeiro ano. A média entre os dois resultados é adotada como valor final, conciliando os dois métodos para compensar a ausência de dados de PPP em 2024.

## Instruções
Na seção "Insira seus dados", insira em 'País_Moeda' o país emissor da moeda utilizada (no caso de uso de moedas diferentes do país de origem), em 'País do Programa' o país de origem do Programa, em 'Ano' o ano da origem dos recursos, em 'Gasto_Local' a quantia dispendida, em 'Programa' o nome do Programa e em 'Descrição' uma breve descrição da função ou destinação dos valores. A coluna 'Ano2' serve para os programas que tem custos entre 2 diferentes anos, sendo necessário calcular a média do PPP e da inflação americana. Então, insira no 'Ano2' o último ano do programa, se não, preencha com 0.

## Fontes
- PPP conversion factor, GDP (LCU per international $): https://data.worldbank.org/indicator/PA.NUS.PPP?view=chart&year=2023
- Consumer Price Index for All Urban Consumers: All Items in U.S. City Average: https://fred.stlouisfed.org/series/CPIAUCSL
- Official exchange rate, LCU per USD, period average:  Global Economic Monitor (GEM) - https://databank.worldbank.org/source/global-economic-monitor-(gem)/Type/TABLE/preview/on#advancedDownloadOptions
