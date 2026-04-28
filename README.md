classDiagram
    class User {
        -id: String
        -pw: String
        -userName: String
        -phone: String
        -address: String
        +registerUser(id: String, pw: String, userName: String, phone: String, address: String) void
        +updateUser(id: String, pw: String, userName: String, phone: String, address: String) void
        +deleteUser(id: String) void
        +searchUser(id: String) User
    }

    class Account {
        -number: String
        -balance: long
        +deposit(id: String, amount: long) void
        +withdraw(id: String, amount: long) void
        +transfer(id: String, targetNumber: String, amount: long) void
        +computeBalance() long
    }

    class BankUI {
        <<Boundary>>
    }

    %% 관계 설정
    BankUI ..> Account : 의존 (계좌 서비스 호출)
    Account ..> User : 의존 (입출금 시 searchUser 호출)