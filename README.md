# Resposta-da-Questao-4
Levantamento de atendimentos por assunto e por ano em uma tabela.


Para resolver essa questão, eu utilizei um **comando SQL com agrupamento** e **filtragem** da seguinte forma:

1. **Agrupei os dados** por "assunto" e "ano" usando o `GROUP BY` para contar quantas vezes cada combinação aparece.
2. **Filtrei** os resultados com `HAVING COUNT(*) > 3`, exibindo apenas aqueles grupos com mais de 3 ocorrências.
3. Por fim, **ordenei os resultados** usando `ORDER BY` de forma decrescente, primeiro por "ano" e depois pela quantidade de ocorrências.

Isso permitiu listar os assuntos com mais de 3 atendimentos, organizados conforme solicitado.

```sql
SELECT assunto, ano, COUNT(*) AS quantidade
FROM atendimentos
GROUP BY assunto, ano
HAVING COUNT(*) > 3
ORDER BY ano DESC, quantidade DESC;
```

### Explicação:
- **`GROUP BY assunto, ano`**: Agrupa os registros por "assunto" e "ano" para contar as ocorrências de cada combinação.
- **`COUNT(*) AS quantidade`**: Conta o número de registros em cada grupo (combinação de "assunto" e "ano").
- **`HAVING COUNT(*) > 3`**: Filtra apenas os grupos que têm mais de 3 ocorrências.
- **`ORDER BY ano DESC, quantidade DESC`**: Ordena o resultado por "ano" em ordem decrescente e, dentro de cada ano, por quantidade de ocorrências também de forma decrescente.

### Resultado esperado (com base nos dados fornecidos):

| Assunto              | Ano  | Quantidade |
|----------------------|------|------------|
| Reclamacao cadastro   | 2022 | 8          |
| Reclamacao produto    | 2021 | 6          |
| Reclamacao atendimento| 2021 | 4          |
