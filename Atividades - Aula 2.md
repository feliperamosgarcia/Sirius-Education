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
WHEN salario_mensal <= 0 THEN 'Sem sal??rio'
WHEN salario_mensal BETWEEN 0 AND 1212 THEN 'At?? 1 sal??rio m??nimo'
WHEN salario_mensal BETWEEN 1212 AND 1212 * 5 THEN 'De 1 at?? 5 sal??rios m??nimos'
WHEN salario_mensal BETWEEN 5 * 1212 AND 10 * 1212 THEN 'De 5 at?? 10 sal??rios m??nimos'
WHEN salario_mensal >= 10 * 1212 THEN 'Maior que 10 sal??rios m??nimos'
ELSE 'Sal??rio n??o especificado'
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
WHERE nome = 'Mar??lia'
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

O ??ndice de Desenvolvimento da Educa????o B??sica (IDEB) ?? um indicador criado pelo Instituto Nacional de Estudos e Pesquisas Educacionais An??sio Teixeira (INEP), em 2007, para servir de refer??ncia da avalia????o da educa????o b??sica no Brasil. Seu resultado ?? obtido a partir do rendimento escolar (que considera avalia????es e evas??o escolar) e pelas provas do Sistema Nacional de Avalia????o B??sica (SAEB). O objetivo do indicador ?? servir como uma refer??ncia estat??stica sobre o desempenho e progresso dos alicerces da educa????o b??sica, a saber, alfabetiza????o e assimilala????o de opera????es b??sicas da matem??tica.

Entendendo do que se trata o indicador, seu objetivo e como ele ?? operacionalizado, podemos refletir melhor sobre as diferen??as entre a m??dia do munic??pio de Mar??lia e suas melhores escolas em compara????o com a m??dia do Estado de S??o Paulo. 

De modo geral, S??o Paulo apresentou, junto com o Estado do Cear??, um bom desempenho nos indicadores de avalia????o b??sica do Governo Federal no ano de 2019 - ??ltimo ano em que as provas foram realizadas, em virtude da pandemia. A m??dia IDEB do Estado de s??o Paulo em 2019 foi de 9,56 e na cidade de Mar??lia a m??dia foi de 9,680. A pequena diferen??a positiva pode ser atribu??da a uma pol??tica de valoriza????o salarial dos profissionais da rede municipal, embora os atrasos nas realiza????es de concursos possam ter influenciado em uma nota menor em rela????o a 2017, quando Mar??lia obteve 9,730. 

No caso da escola melhor colocada, ela est?? inclu??da em um seleto grupo de escolas p??blicas municipais com prioridade de gest??o, pr??tica que n??o ?? exclusiva do munic??pio de Mar??lia. Por se tratar de uma pol??tica nacional, baseada em indicadores p??blicos, ?? de interesse do munic??pio que suas escolas figurem entre as mais bem avaliadas, pois isso confere legitimidade pol??tica em rela????o a gest??o da educa????o na cidade. Isso posto, ?? uma pr??tica comum que os executivos municipais orientem suas pol??ticas de educa????o para que as escolas melhorem seus desempenhos nos indicadores de avalia????o. No caso das escolas mais bem colacadas em Mar??lia, elas fazem parte desse grupo que recebe prioridade de gest??o, tanto estadual (como ?? o caso da ETEC Antonio Devisate), seja municipal, como ?? o caso da melhor colocada na m??dia IDEB.

Contudo, n??o ?? poss??vel considerar esse um fator determinante, haja visto que, de modo geral, as escolas de Mar??lia figuraram todas bem e com notas pr??ximas a m??dia do Estado e do munic??pio, com a menor nota sendo 9,450.






















