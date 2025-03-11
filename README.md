```plantuml
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
    int quantidade
    LocalDate dataCriacao
}

class RecebimentoDePedido {
    Long id
    int quantidadeRecebida
    LocalDate dataRecebimento
}

Usuario "1" -- "*" OrdemDeCompra : cria
Fornecedor "1" -- "*" OrdemDeCompra : fornece
Produto "1" -- "*" OrdemDeCompra : inclui
OrdemDeCompra "1" -- "*" RecebimentoDePedido : relacionado
Status "1" -- "*" OrdemDeCompra : possui

OrdemDeCompra "*" -- "1" Produto
OrdemDeCompra "*" -- "1" Fornecedor
RecebimentoDePedido "*" -- "1" OrdemDeCompra

@enduml
