# ATIVIDADE 1

```sql
SELECT 
  ano,
  raca_cor,
  populacao

FROM `basedosdados.br_ibge_pnadc.ano_brasil_raca_cor` 

WHERE ano = 2012
AND raca_cor = 'Preta'
AND sexo = 'Total'

```
# ATIVIDADE 2
```sql
SELECT 
  ano,
  raca_cor,
  populacao

FROM `basedosdados.br_ibge_pnadc.ano_brasil_raca_cor` 

WHERE raca_cor = 'Preta'
AND sexo = 'Total'
ORDER BY ano ASC
```
# ATIVIDADE 3
```sql
SELECT 
  ano,
  populacao

FROM `basedosdados.br_ibge_pnadc.ano_brasil_raca_cor` 

WHERE raca_cor = 'Total'
AND sexo = 'Mulheres'
ORDER BY ano ASC
```
# ATIVIDADE 4
```sql
SELECT
  id_municipio,
  COUNT (*) AS QTD
  
FROM `basedosdados.br_ibge_nomes_brasil.quantidade_municipio_nome_2010` 

GROUP BY id_municipio
ORDER BY QTD DESC

```

# ATIVIDADE 5
```sql
SELECT 
  id_municipio,
  COUNT (DISTINCT nome) AS QTD

FROM `basedosdados.br_ibge_nomes_brasil.quantidade_municipio_nome_2010` 
WHERE
LENGTH(nome) > 7
GROUP BY id_municipio
ORDER BY QTD DESC
```

# ATIVIDADE 6
```sql

SELECT 
COUNT (DISTINCT id_municipio) AS QTD_MUN, 
FROM `basedosdados.br_ibge_populacao.municipio`
```


# ATIVIDADE 7

```sql
SELECT 
  sigla_uf,
  COUNT (DISTINCT id_municipio) AS estados_municipios

FROM `basedosdados.br_ibge_populacao.municipio` 
GROUP BY sigla_uf
ORDER BY estados_municipios DESC
```

# ATIVIDADE 8

```sql
SELECT 
  sigla_uf,
  COUNT (DISTINCT id_municipio) AS populacao_estado

FROM `basedosdados.br_ibge_populacao.municipio` 

WHERE populacao > 100000
GROUP BY sigla_uf
ORDER BY populacao_estado DESC
```

# ATIVIDADE 9
```sql

SELECT 
  idade,
  ROUND (AVG (salario_mensal)) AS media_salarial,
  COUNT (*) AS qtd

FROM `basedosdados.br_me_caged.microdados_movimentacoes`  
GROUP BY idade
ORDER BY idade DESC
```

# ATIVIDADE 10
```sql

SELECT 
  sigla_uf,
  ROUND (AVG (salario_mensal)) AS media_salarial,
  COUNT (*) AS populacao

FROM `basedosdados.br_me_caged.microdados_movimentacoes`  
GROUP BY sigla_uf
ORDER BY media_salarial DESC
```

# ATIVIDADE 11
```sql
SELECT 
  idade,
  ROUND (MAX (salario_mensal)) AS maiores_salarios,
  COUNT (*) AS populacao

FROM `basedosdados.br_me_caged.microdados_movimentacoes` 

GROUP BY idade
ORDER BY maiores_salarios DESC
```

# ATIVIDADE 12
```sql
SELECT 
  ROUND (salario_mensal) AS salario_arredondado,
  COUNT (*) AS quantidade_registros

FROM `basedosdados.br_me_caged.microdados_movimentacoes` 

GROUP BY salario_arredondado
ORDER BY salario_arredondado ASC
```

```sql
SELECT 
  COUNT (*) AS totais,

CASE
WHEN salario_mensal <= 0 THEN 'Sem salário'
WHEN salario_mensal BETWEEN 0 AND 1212 THEN 'Até 1 salário mínimo'
WHEN salario_mensal BETWEEN 1212 AND 1212 * 5 THEN 'De 1 até 5 salários mínimos'
WHEN salario_mensal BETWEEN 5 * 1212 AND 10 * 1212 THEN 'De 5 até 10 salários mínimos'
WHEN salario_mensal >= 10 * 1212 THEN 'Maior que 10 salários mínimos'
ELSE 'Salário não especificado'
END AS faixa_salarial,

CASE
WHEN salario_mensal <= 0 THEN 1
WHEN salario_mensal BETWEEN 0 AND 1212 THEN 2
WHEN salario_mensal BETWEEN 1212 AND 1212 * 5 THEN 3
WHEN salario_mensal BETWEEN 5 * 1212 AND 10 * 1212 THEN 4
WHEN salario_mensal >= 10 * 1212 THEN 5
ELSE 0
END AS ordem

FROM `basedosdados.br_me_caged.microdados_movimentacoes` 

GROUP BY faixa_salarial, ordem
ORDER BY ordem
```


# ATIVIDADE 13
```sql
SELECT 
  ROUND (AVG(salario_mensal)) AS media_salarial,

CASE sexo

  WHEN '1' then 'Homem'
  WHEN '3' then 'Mulher'
  WHEN '9' then 'Nao_identiificado'
  END
  AS sexo 

FROM `basedosdados.br_me_caged.microdados_movimentacoes`

GROUP BY sexo
ORDER BY media_salarial
```


# ATIVIDADE 14
```sql
SELECT 
  id_municipio,
  nome

FROM `basedosdados.br_bd_diretorios_brasil.municipio` 
WHERE nome = 'Marília'
```
# ATIVIDADE 14.1
```sql
SELECT 
  id_escola,
  ano,
  id_municipio,
  nota_saeb_matematica
  
FROM `basedosdados.br_inep_ideb.escola` 

WHERE ano = 2019 and id_municipio = '3529005'
ORDER BY nota_saeb_matematica DESC

LIMIT 1
```

id_escola: 35033583

nota mental: MAX (nota_saeb_matematica) AS maior_nota_matematica


# ATIVIDADE 14.2
```sql
SELECT 
  id_escola,
  ano,
  id_municipio,
  nota_saeb_lingua_portuguesa
  
FROM `basedosdados.br_inep_ideb.escola` 

WHERE ano = 2019 and id_municipio = '3529005'
ORDER BY nota_saeb_lingua_portuguesa DESC

LIMIT 1
```
id_escola: 35033583

# ATIVIDADE 14.3
```sql
SELECT 
  id_escola,
  indicador_rendimento,
  ano
  
FROM `basedosdados.br_inep_ideb.escola` 
WHERE ano = 2019 and id_municipio = '3529005'
ORDER BY indicador_rendimento DESC

LIMIT 1
```
id_escola: 35033662

# ATIVIDADE 14.4
```sql
SELECT 
  id_escola,
  nome

FROM `basedosdados.br_bd_diretorios_brasil.escola` 
WHERE id_escola = '35033583' 
--
SELECT 
  id_escola,
  nome

FROM `basedosdados.br_bd_diretorios_brasil.escola` 
WHERE id_escola = '35033662'
```
ANTONIO DEVISATE ETEC
ANTONIO DEVISATE ETEC
BENTO DE ABREU SAMPAIO VIDAL

# ATIVIDADE 14.5
```sql
SELECT 
  
  ROUND (AVG (nota_saeb_matematica)) AS matematica,
  ROUND (AVG (nota_saeb_lingua_portuguesa)) AS portugues,
  ROUND (AVG (indicador_rendimento), 3) AS media_ideb
  
FROM `basedosdados.br_inep_ideb.escola` 
WHERE ano = 2019 and id_municipio = '3529005'
```

# ATIVIDADE 14.6
```sql

SELECT 
  
  ROUND (AVG (nota_saeb_matematica)) AS matematica,
  ROUND (AVG (nota_saeb_lingua_portuguesa)) AS portugues,
  ROUND (AVG (indicador_rendimento), 3) AS media_ideb
  
FROM `basedosdados.br_inep_ideb.escola` 
WHERE ano = 2019 and sigla_uf = 'SP'
```

# ATIVIDADE 14.7
```sql

SELECT 
  ROUND (AVG (indicador_rendimento), 3) AS media_ideb,
  ROUND (AVG (nota_saeb_lingua_portuguesa)) AS media_portugues,
  ROUND (AVG (nota_saeb_matematica)) AS media_matematica,
  sigla_uf,
  ano


FROM `basedosdados.br_inep_ideb.escola` 
WHERE ano = 2019
GROUP BY sigla_uf, ano
ORDER BY media_ideb DESC

--

SELECT 
  ROUND (AVG (indicador_rendimento), 3) AS media_ideb,
  ROUND (AVG (nota_saeb_lingua_portuguesa)) AS media_portugues,
  ROUND (AVG (nota_saeb_matematica)) AS media_matematica,
  id_municipio,
  ano


FROM `basedosdados.br_inep_ideb.escola` 
WHERE id_municipio = '3529005'
GROUP BY id_municipio, ano
ORDER BY ano DESC

--

SELECT 
  ROUND (AVG (indicador_rendimento), 3) AS media_ideb,
  ROUND (AVG (nota_saeb_lingua_portuguesa)) AS media_portugues,
  ROUND (AVG (nota_saeb_matematica)) AS media_matematica,
  sigla_uf,
  ano


FROM `basedosdados.br_inep_ideb.escola` 
WHERE sigla_uf = 'SP'
GROUP BY sigla_uf, ano
ORDER BY ano DESC

--

SELECT 
  ROUND (AVG (indicador_rendimento), 3) AS media_ideb,
  ROUND (AVG (nota_saeb_lingua_portuguesa)) AS media_portugues,
  ROUND (AVG (nota_saeb_matematica)) AS media_matematica,
  id_municipio,
  id_escola,
  ano


FROM `basedosdados.br_inep_ideb.escola` 
WHERE id_municipio = '3529005' AND ano = 2019
GROUP BY id_municipio, ano, id_escola
ORDER BY media_ideb DESC
```

O Índice de Desenvolvimento da Educação Básica (IDEB) é um indicador criado pelo Instituto Nacional de Estudos e Pesquisas Educacionais Anísio Teixeira (INEP), em 2007, para servir de referência da avaliação da educação básica no Brasil. Seu resultado é obtido a partir do rendimento escolar (que considera avaliações e evasão escolar) e pelas provas do Sistema Nacional de Avaliação Básica (SAEB). O objetivo do indicador é servir como uma referência estatística sobre o desempenho e progresso dos alicerces da educação básica, a saber, alfabetização e assimilalação de operações básicas da matemática.

Entendendo do que se trata o indicador, seu objetivo e como ele é operacionalizado, podemos refletir melhor sobre as diferenças entre a média do município de Marília e suas melhores escolas em comparação com a média do Estado de São Paulo. 

De modo geral, São Paulo apresentou, junto com o Estado do Ceará, um bom desempenho nos indicadores de avaliação básica do Governo Federal no ano de 2019 - último ano em que as provas foram realizadas, em virtude da pandemia. A média IDEB do Estado de são Paulo em 2019 foi de 9,56 e na cidade de Marília a média foi de 9,680. A pequena diferença positiva pode ser atribuída a uma política de valorização salarial dos profissionais da rede municipal, embora os atrasos nas realizações de concursos possam ter influenciado em uma nota menor em relação a 2017, quando Marília obteve 9,730. 

No caso da escola melhor colocada, ela está incluída em um seleto grupo de escolas públicas municipais com prioridade de gestão, prática que não é exclusiva do município de Marília. Por se tratar de uma política nacional, baseada em indicadores públicos, é de interesse do município que suas escolas figurem entre as mais bem avaliadas, pois isso confere legitimidade política em relação a gestão da educação na cidade. Isso posto, é uma prática comum que os executivos municipais orientem suas políticas de educação para que as escolas melhorem seus desempenhos nos indicadores de avaliação. No caso das escolas mais bem colacadas em Marília, elas fazem parte desse grupo que recebe prioridade de gestão, tanto estadual (como é o caso da ETEC Antonio Devisate), seja municipal, como é o caso da melhor colocada na média IDEB.

Contudo, não é possível considerar esse um fator determinante, haja visto que, de modo geral, as escolas de Marília figuraram todas bem e com notas próximas a média do Estado e do município, com a menor nota sendo 9,450.






















