# Spring의 구조 (DAO, DTO, Entity, Controller, Service)
## 전체구조
![](../img/spring-gujo.png)

## DAO (Data Access Object)
**repository package**
:DB를 사용해 데이터를 조회하거나 조작하는 기능을 전담하도록 만든 Object
- 실제로 DB에 접근하는 객체
- Service와 DB를 연결하는 고리의 역할
- SQL을 사용 (개발자가 직접 코딩)하여 DB에 접근한 후 적절한 CRUD API제공 
    - JPA 대부분의 기본적인 CURD method를 제공하고있다.
- ex)  
```java
public interface BoardRepository extends CrudRepository<Board, Long>{}
```
>Board라는 도메인타입의 PKey의 Tpye은 Long

## DTO (Data Transfer Object)
:계층간 데이터 교환을 위한 객체를 말한다.  
여기서 계층이란 컨트롤러, 서비스, 퍼시스턴스 계층등의 계층을 말한다.   
**DTO package**
:**계층간 데이테 교환을 위한 JAVABeans**를 말한다. 여기서 계층이란 컨트롤러, 뷰, 비즈니스계층, 퍼시스턴스계층을 말한다.
- **계층간 데이터교환을 위한 객체**이다.
- DB에서 데이터를 얻어  `Service`나 `Contriller`등으로 보내는 객체
- 로직을 갖고있지 않은 순수한 객체이다 `getter/setter` 메서드만 가지고있다.
- Request와 Response용 DTO는 View를 위한 클래스
    - 자주 변경이 필요한 클래스
    - Persentaion Model
    - `toEntity()` 메서드를 통해서 DTO에서 필요한 부분을 이용하여 Entity로 만든다.
    - 또한 Controller Layer에서 `Response DTO` 형태로 Client에 전달

## Entity class
**Domain package**
- 실제 DB테이블과 매칭될 클래스
    - 가장 core한 클래스라고 불림
    - `@Entity`, `@Column`, `@Id`등 사용
- 최대한 외부에서 Entity 클래스의 getter method를 사용하지 않도록 해당 클래스 안에서 필요한 로직(method)을 구현

## Entity class 와 DTO class 를 분리하는 이유
- View Layer 와 DB Layer의 역활을 철저히 하기위해
- 테이블과 매핑되는 Entity 클래스가 변경되면 여러 클래스에 영향을 끼치게 되는 반면 View와 통신하는 DTO 클래스(Request / Response 클래스)는 자주 변경되므로 분리
- ex)
```java
import lombok.*;
import org.hibernate.annotations.CreationTimestamp;
import org.hibernate.annotations.UpdateTimestamp;

import javax.persistence.*;
import java.time.LocalDateTime;

@NoArgsConstructor(access= AccessLevel.PROTECTED)
@Getter
@Entity
public class Board {
    @Id
    @GeneratedValue(strategy= GenerationType.IDENTITY)
    private long id;

    @Column(nullable=false)
    private String title;

    @Column
    private String content;

    @Column(updatable=false)
    @CreationTimestamp
    private LocalDateTime createdDateTime;

    @Column(nullable=false)
    private String regUserId;

    @UpdateTimestamp
    private LocalDateTime modifiedDateTime;

    @Column
    private String editUserId;

    @Builder
    private Board(long id, String title, String content, String regUserId, String editUserId) {
        this.id = id;
        this.title = title;
        this.content = content;
        this.regUserId = regUserId;
        this.editUserId = editUserId;
    }

}
```

## controller (web)
- View Layer와 DB Layer의 역할을 철저히 하기 위해서
- 테이블과 매핑되어있는 Entity클래스가 변경되면 여러 클래스에 영향을 미친다. dto는 view에 반환 등을 하며 통신하고, 자주변경되므로 dto클래스는 분리한다.
## service
- `Repository`의 DI를 통해 repository의 method를 이용
- 적절한 business Logic 처리
- DAO로 DB에 접근하고 DTO로 데이터를 전달받은 다음, 비지니스 로직을 처리해 적절한 데이터를 반환