WITH IDEB AS (SELECT
  id_municipio,
  ROUND (AVG(ideb), 2) AS media_ideb
  FROM `basedosdados.br_inep_ideb.municipio`
  WHERE ano = 2019
  GROUP BY id_municipio) 

SELECT 
  nome AS Cidade,
  nome_uf AS Estado,
  populacao.populacao,
  populacao.ano,
  pib.pib,
  media_ideb,
  ROUND (AVG (media_ideb) OVER (PARTITION BY nome_uf), 2) AS ideb_estado,
  SUM (populacao.populacao) OVER (PARTITION BY nome_uf) AS populacao_estado,
  ROUND (populacao.populacao/SUM (populacao.populacao) OVER (PARTITION BY nome_uf)*100,4) AS percent

FROM `basedosdados.br_bd_diretorios_brasil.municipio` AS DIRETORIOS
LEFT JOIN `basedosdados.br_ibge_populacao.municipio` AS populacao ON DIRETORIOS.id_municipio = populacao.id_municipio AND populacao.ano = 2019
LEFT JOIN `basedosdados.br_ibge_pib.municipio` AS pib ON pib.id_municipio = DIRETORIOS.id_municipio AND pib.ano = 2019
LEFT JOIN IDEB ON IDEB.id_municipio = DIRETORIOS.id_municipio
