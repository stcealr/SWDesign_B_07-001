<<<<<<< HEAD
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
=======
```mermaid
classDiagram
    class 고객정보 {
        -주민번호: String
        -성명: String
        +고객등록(주민번호: String, 성명: String): boolean
        +고객수정(주민번호: String, 성명: String): boolean
        +고객삭제(주민번호: String): boolean
        +고객조회(주민번호: String): boolean
    }

    class 주택정보 {
        -주소: String
        -주택가격: double
        -대출여부: boolean
        +주택등록(주소: String, 주택가격: double): boolean
        +주택수정(주소: String, 주택가격: double): boolean
        +주택삭제(주소: String): boolean
        +주택조회(주소: String): boolean
        +대출여부확인(주소: String): boolean
        +주택가격조회(주소: String): boolean
    }

    class 대출정보 {
        -대출id: String
        -주민번호: String
        -주소: String
        -대출금액: double
        -상환금액: double
        -대출일: int
        -상환예정일: int
        -상환일: int
        +대출(주민번호: String, 주소: String, 대출일: int, 상환예정일: int): double
        +상환(주민번호: String, 주소: String, 상환일: int): double
        +연체확인(상환일: int): boolean
    }

    class HouseRoanUI {
        +대출메뉴(): boolean
        +상환메뉴(): boolean
    }

    %% 연관 관계 및 다중성 설정
    %% 대출정보(0..*) : 고객정보(1)
    대출정보 "0..*" --> "1" 고객정보 : 고객조회 목적으로 참조
    
    %% 대출정보(1) : 주택정보(1)
    대출정보 "1" --> "1" 주택정보 : 주택정보조회 목적으로 참조

    %% 의존 관계 설정
    HouseLoanUI ..> 대출정보 : 의존
>>>>>>> 4502af81455f4a602e5c5d675d0942485c810b37
