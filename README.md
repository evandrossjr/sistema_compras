@startuml

class Usuario {
    Long id
    String nome
    String email
    String senha
}

class Fornecedor {
    Long id
    String nome
    String cnpj
    String contato
}

class Produto {
    Long id
    String nome
    String marca
    Double preco
}

class Status {
    Long id
    String descricao
}

class OrdemDeCompra {
    Long id
    Fornecedor fornecedor
    Produto produto
    int quantidade
    Status status
    LocalDate dataCriacao
}

class RecebimentoDePedido {
    Long id
    OrdemDeCompra ordemCompra
    int quantidadeRecebida
    LocalDate dataRecebimento
}

Usuario "1" -- "*" OrdemDeCompra : cria
Fornecedor "1" -- "*" OrdemDeCompra : fornece
Produto "1" -- "*" OrdemDeCompra : incluído
OrdemDeCompra "1" -- "*" RecebimentoDePedido : relacionado
Status "1" -- "*" OrdemDeCompra : possui

@enduml
