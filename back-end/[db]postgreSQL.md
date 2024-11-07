## [생활코딩] PostgreSQL 입문

개발자들은 저장된 데이터를 가공해 사용자에게 보여주고, 또 새로운 데이터를 저장하기 위해 데이터베이스를 사용합니다. 시중 많이 사용하는 데이터베이스중 하나인 PostgreSQL에 대해 배워봅시다!

![스크린샷 2024-11-07 오전 11.30.23.png](https://github.com/user-attachments/assets/08d20467-d1c4-4914-bb26-3e9d438b4dcb)

### 공식 사이트

- https://www.postgresql.org/

### 데이터베이스

- cluster - database - schema - table 순으로 구조화 되어있습니다.

### pgAdmin4

- pgAdmin4 툴을 사용하여 간단하게 테이블을 만들 수 있습니다. (정말 매우 쉬움..!)

![스크린샷 2024-11-07 오전 11.47.22.png](https://github.com/user-attachments/assets/2148d72c-e7af-47bf-ac59-4499746dcf4a)

- 데이터 또한 매우 쉽게 Insert, Select 할 수 있습니다.

![스크린샷 2024-11-07 오전 11.49.58.png](https://github.com/user-attachments/assets/b41a4aa0-1710-4bdb-9cf9-65b6d1dcf371)

- Query 또한 작성하여 데이터를 조작할 수 있습니다.

![스크린샷 2024-11-07 오전 11.52.05.png](https://github.com/user-attachments/assets/4e62be51-487b-4161-9bd9-f9ee141587fd)

### Query

**조회**

- `SELECT id, title FROM topic WHERE id > 1 ORDER BY id;`

**생성**

- `INSERT INTO topic(title, body) VALUES(’Select’, ‘Select is … ‘);`

**수정**

- `UPDATE topic SET title = ‘Delete’, body = ‘Delete is …’ WHERE id = 4;`

**삭제**

- `DELTE FROM topic WHERE id=4;`

### Join

- 관계형 데이터의 핵심입니다.
- 분리된 테이블을 하나의 테이블로 합쳐서 가지고 올 수 있는 기능입니다.
