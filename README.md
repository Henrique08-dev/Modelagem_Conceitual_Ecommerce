Modelagem de Banco de Dados - E-Commerce

📋 Descrição do Projeto

Este repositório contém a modelagem entidade-relacionamento estendida (MER) para um sistema de e-commerce, desenvolvida com refinamentos avançados para atender às necessidades complexas de um ambiente de vendas online.

🎯 Objetivo

Criar uma modelagem robusta e escalável que represente adequadamente as entidades, relacionamentos e regras de negócio de um sistema e-commerce completo.

🏗️ Estrutura da Modelagem

Entidades Principais

**Cliente** (`Cliente`)
- `idCliente` (PK)
- `Nome`, `Identificação`, `Endereço`, `TipoCliente`
- Relacionamentos: 1:1 com `ClientePF` e `ClientePJ`

**Pedido** (`Pedido`)
- `idPedido` (PK)
- `StatusPedido`, `Descrição`, `Frete`
- Relacionamento: N:1 com `Cliente`

**Produto** (`Produto`)
- `idProduto` (PK)
- `Descricao`, `Valor`
- Relacionamentos: N:M com `Fornecedor`, `Estoque`, `Pedido`, `Terceirizado`

**Fornecedor** (`Fornecedor`)
- `idFornecedor` (PK)
- `RazaoSocial`, `CNPJ`

🔧 Refinamentos Implementados

1. **Especialização de Cliente**
- **ClientePF** (`ClientePF`): Para pessoas físicas
  - `CPF`, `DataNascimento`
- **ClientePJ** (`ClientePJ`): Para pessoas jurídicas  
  - `CNPJ`, `RazaoSocial`

2. **Gestão de Endereços** (`Endereco`)
- Entidade independente para múltiplos endereços por cliente
- Campos: `Logradouro`, `Numero`, `Cidade`, `Estado`, `CEP`
- Relacionamento: N:1 com `Cliente`

3. **Sistema de Categorias** (`CategoriaProduto`)
- `idCategoriaProduto` (PK)
- `Nome`
- Organização hierárquica de produtos

4. **Controle de Pagamentos** (`Pagamento`)
- `idPagamento` (PK)
- `tipoPagamento`, `Detalhes`
- Relacionamento: N:M com `Pedido` através de tabela associativa

5. **Rastreamento de Entregas** (`Entrega`)
- `idEntrega` (PK)
- `codigoRastreio`, `statusEntrega`, `dataEnvio`, `dataEntrega`
- Relacionamento: 1:1 com `Pedido`

📊 Cardinalidades Principais

- **Cliente → Pedido**: 1:N (Um cliente faz muitos pedidos)
- **Pedido → Produto**: N:M (Um pedido contém muitos produtos, um produto está em muitos pedidos)
- **Fornecedor → Produto**: N:M (Um fornecedor fornece muitos produtos, um produto pode ser fornecido por muitos fornecedores)
- **Produto → Estoque**: N:M (Um produto está em muitos estoques, um estoque contém muitos produtos)
- **Cliente → Endereco**: 1:N (Um cliente tem muitos endereços)

🚀 Pontos de Melhoria Implementados
**Normalização Avançada**
- Eliminação de redundâncias através de especialização (ClientePF/ClientePJ)
- Separação de entidades complexas (Endereco como entidade independente)

**Flexibilidade no Catálogo**
- Sistema de categorias expansível
- Múltiplos fornecedores por produto
- Controle de estoque por localização física

**Gestão Financeira**
- Múltiplas formas de pagamento por pedido
- Rastreamento completo do processo de entrega
- Histórico de status de pedidos

**Escalabilidade**
- Modelagem preparada para crescimento
- Estrutura que suporta múltiplos canais de venda
- Gestão de fornecedores terceirizados

---

Desenvolvido como parte da Formação Suzano - Análise de Dados com Power BI - Digital Innovation One
