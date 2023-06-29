# spring-guides-Accessing-Data-with-JPA

### dependencies 
- Spring Data JPA
- H2 Database

### JPA의 어노테이션 

@Entity : JPA의 entity임을 지정, Class 단계에 적용, @Table 어노테이션이 table명은 클래스명인 Customer를 반영한다 
@Table : DB의 table로 매핑될 것을 의미 
@Id : table의 id, JPA가 객체의 id값으로 처리 + @GeneratedValue : PK값 생성 전략 표시

JPA @Entity 클래스에 기본생성자를 추가해주어야 하는 이유 
- JPA는 DB 값을 스프링의 객체에 자동 변환해 주입해준다
- 이때, 기본 생성자를 이용하여 스프링 객체를 생성한 후 Reflection API를 사용하여 동적으로 값을 매핑한다
- 따라서 기본 생성자가 없다면 Reflection은 해당 객체를 생성할 수 없다
- 직접 사용하지 않고, JPA가 사용하므로 protected 타입으로 명시

### Repository 생성

Spring Data JPA의 핵심은 JPA를 이용하여 db에 정보를 저장하는 것 
이를 위해 CrudRepository 클래스를 상속받는 Repo를 생성한다 
CrudRepository<Entity 클래스, ID 데이터 타입>
어플 실행시 기본 db 접근 메서드들이 생성된다 

### 스프링부트 런타임 시점에 특정 코드 실행시키기 (CommandLineRunner)

- 런타임 시 실행되어야 하는 Bean을 표시한다
- SpringApplication 내부에 포함된 Bean들 중 실행되어야 하는 Bean을 가리키는 인터페이스 
- 만약 CommandLineRunner를 implements 받은 Bean 이 여러개라면  @Order 로 순서 지정 가능

### SQL 기초 개념

1) table : 비슷한 개념을 모아놓은 하나의 집합 ex) student
2)column : 세로 방향, 열, 테이블 내에서 더 작은 단위의 의미 집합 ex) age 
3) row : 가로 방향, 행, 테이블 내에서 column의 모든 정보를 각각 가진 개별 정보


### Lombok / @Data

@Getter @Setter
@RequiredArgsConstructor 
(final, @NotNull인 필드값만 받는 생성자를 만든다)
@ToString 모두 생성해준다

-> Lombok DTO 기본 세팅 : @Data @AllArgsConstructor @NoArgsConstructor

