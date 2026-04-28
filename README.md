```mermaid
classDiagram
    class User {
        -id: String
        -pw: String
        -name: String
        -phone: String
        -address: String

        +registerUser(id: String, name: String, phone: String, address: String) boolean
        +updateUser(id: String, name: String, phone: String, address: String) boolean
        +deleteUser(id: String) boolean
        +searchUser(id: String) boolean
    }

    class Account {
        -number: String
        -balance: double
        +deposit(id: String, amount: double) boolean
        +withdraw(id: String, amount: double) boolean
        +transfer(id: String, targetNumber: String, amount: double) boolean
        +computeBalance(id: String) double
    }

    Account "0..*" --> "1" User : 사용자 조회