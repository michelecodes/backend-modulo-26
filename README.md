# Modulo 26
O PostgreSQL é um sistema de gerenciamento de banco de dados relacional (SGBDR) de código aberto e é conhecido por sua confiabilidade, extensibilidade e conformidade com os padrões ANSI SQL. Aqui estão algumas informações importantes sobre o PostgreSQL:

- História: O PostgreSQL teve início nos anos 1980 na Universidade da Califórnia, Berkeley, como um projeto chamado Ingres. Posteriormente, evoluiu para se tornar o PostgreSQL, sendo lançado pela primeira vez em 1996.
- Características Principais:Open Source: O PostgreSQL é um software de código aberto, o que significa que é gratuito para uso, distribuição e modificação. Extensibilidade: Suporta a adição de novas funcionalidades através de extensões e permite a criação de tipos de dados personalizados e operadores. Confiabilidade: Conhecido por sua estabilidade e robustez, sendo uma escolha popular para aplicações críticas. Padrões ANSI SQL: Oferece suporte significativo aos padrões SQL definidos pelo ANSI (American National Standards Institute).
- Linguagem SQL: Utiliza a linguagem SQL (Structured Query Language) para manipulação e consulta de dados.
- Tipos de Dados: Oferece uma ampla variedade de tipos de dados, incluindo inteiros, decimais, strings, datas, booleanos, arrays e tipos geométricos.
- Índices: Permite a criação de vários tipos de índices para otimizar consultas e melhorar o desempenho.
- Transações: Suporta transações ACID (Atomicidade, Consistência, Isolamento e Durabilidade) para garantir a integridade dos dados.
- Triggers e Stored Procedures: Permite a definição de gatilhos (triggers) e procedimentos armazenados (stored procedures) para automação de tarefas e execução de lógica do lado do servidor.
- Replicação: Oferece recursos avançados de replicação para garantir a disponibilidade e escalabilidade.
- Suporte a JSON: Integra funcionalidades para manipulação de dados em formato JSON, permitindo consultas e indexação de dados JSON.
- Comunidade Ativa: O PostgreSQL conta com uma comunidade ativa de desenvolvedores e usuários, resultando em suporte contínuo e atualizações frequentes.
- Ferramentas de Administração: Existem várias ferramentas de administração gráfica e de linha de comando disponíveis para gerenciar bancos de dados PostgreSQL, como pgAdmin e psql.
- Compatibilidade com Georreferenciamento: Possui suporte robusto para dados georreferenciados e é amplamente utilizado em aplicações GIS (Sistemas de Informação Geográfica).
Segurança: Oferece recursos avançados de segurança, incluindo autenticação, autorização e criptografia.

## Exemplos de comando

- Criar banco de dados
  
      CREATE DATABASE nome_do_banco;
- Conectar banco de dados

      \c nome_do_banco;
- Criar uma tabela

      CREATE TABLE usuarios (
      id SERIAL PRIMARY KEY,
      nome VARCHAR(50),
      idade INT
      );
- Inserir dados na tabela

      INSERT INTO usuarios (nome, idade) VALUES
      ('João', 25),
      ('Maria', 30),
      ('Carlos', 22);
- Consultar dados

      SELECT * FROM usuarios;
- Atualizar dados

      UPDATE usuarios SET idade = 26 WHERE nome = 'João';
- Excluir dados
  
      DELETE FROM usuarios WHERE nome = 'Carlos';
- Consulta de condições

      SELECT * FROM usuarios WHERE idade > 25;
- Criar indices

      CREATE INDEX idx_nome ON usuarios(nome);
- Criar uma função

      CREATE OR REPLACE FUNCTION aumentar_idade(p_id INT, p_valor INT)
      RETURNS VOID AS
      $$
      BEGIN
          UPDATE usuarios SET idade = idade + p_valor WHERE id = p_id;
      END;
      $$
      LANGUAGE plpgsql;
- Executar uma função

      SELECT aumentar_idade(1, 2);
- Criar um trigger

      CREATE OR REPLACE FUNCTION atualizar_data_modificacao()
      RETURNS TRIGGER AS
      $$
      BEGIN
          NEW.data_modificacao = NOW();
          RETURN NEW;
      END;
      $$
      LANGUAGE plpgsql;
      
      CREATE TRIGGER trigger_atualizar_data_modificacao
      BEFORE UPDATE ON usuarios
      FOR EACH ROW
      EXECUTE FUNCTION atualizar_data_modificacao();





