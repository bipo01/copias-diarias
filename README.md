# copias-diarias

Cópia diária, **criptografada**, de um banco de dados PostgreSQL.

- O fluxo `.github/workflows/copia.yml` roda todo dia às 03:00 (Brasília), faz `pg_dump` por um usuário
  **só de leitura**, confere que as tabelas principais vieram e tranca o arquivo com [age](https://age-encryption.org)
  antes de guardar. Quem baixar o artefato sem a chave privada não lê nada.
- A chave privada nunca esteve neste repositório. A conexão com o banco é um segredo do repositório.
- Cada cópia fica 90 dias em *Actions › copia › Artifacts*.
- O repositório é público só para o GitHub não cobrar nem bloquear os minutos do fluxo.
  O arquivo `vivo.txt` muda uma vez por mês: sem atividade por 60 dias o GitHub desliga fluxos agendados.
