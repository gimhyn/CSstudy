### SQL(structured Query Language)

- 관계 데이터베이스를 위한 표준 질의어
    1. DDL 데이터 정의어
        
        : 테이블 생성, 변경, 제거
        
        - CREATE (테이블 생성)
            
            ```sql
             CREATE TABLE tablename
            ```
            
        
        	 1. 각 속성 이름, 데이터 타입, 기본 제약 사항
        	 2. 기본 키 정의
        	 3. 대체 키 정의
        	 4. 외래키 정의
        	 5. 데이터 무결성을 위한 제약 조건 정의
        
        - ALTER (테이블 변경)
            
            ```sql
            ALTER TABLE tablename
            	ADD 속성이름 data_type [NOT NULL] [DEFAULT 기본값];
            ```
            
            - DROP (테이블 기존 속성 제거)
            
            ```sql
            ALTER TABLE tablename DROP 속성이름 CASCADE | RESTRICT;
            ```
            
            - CASCADE : 삭제할 속성과 관련된 제약 조건이나 참조하는 다른 속성을 함께 삭제
            - RESTRICT : 삭제할 속성과 관련된 제약 조건이나 참조하는 다른 속성이 존재하면 삭제 거부
        - DROP (테이블 제거)
            
            ```sql
            DROP TABLE tablename CASCADE | RESTRICT;
            ```
            
    2. DML 데이터 조작어
        
        : 테이블에 세 데이터 삽입, 저장된 데이터 수정 삭제 검색 기능
        
        - SELECT(데이터 검색)
            
            ```sql
            SELECT [ ALL | DISTINCT ] 속성_리스트
            FROM 테이블리스트;
            ```
            
            : 테이블 형태로 결과 반환
            
            - ALL : 결과 테이블이 투플의 중복을 허용하도록 지정, 생략 가능
            - DISTINCT : 결과 테이블이 투플의 중복을 허용하도록 지정
            - **산술식을 이용한 검색**
                
                ```sql
                SELECT 제품명, 단가+500 AS 조정단가 
                FROM 제품테이플;
                ```
                
            - **조건 검색**
                
                ```sql
                SELECT [ALL | DISTINCT] 속성_리스트
                FROM 테이블_리스트
                WHERE 조건;
                ```
                
            - **LIKE를 이용한 검색**
                
                
                | LIKE ‘data*’ | data로 시작하는 문자열 |
                | --- | --- |
                | LIKE ‘*data’ | data로 끝나는 문자열 |
                | LIKE ‘*data*’ | data 포함하는 문자열 |
                | LIKE ‘감자???’ | 감자로 시작하는 길이 5인 문자열(?=글자 개수) |
                | LIKE ‘??한*’ | 세 번째 글자가 ‘한’인 문자열 |
            - NULL을 이용한 검색
                
                : IS NULL/ IS NOT NULL 키워드를 통해 특정 속성에서 값이 NULL인지 확인
                
            - ORDER BY ASC/ DESC
                
                : 오름차순, 내림차순 정렬
                
            - 집계 함수를 이용한 검색
                - COUNT 속성 값 개수
                - MAX 속성 값의 최댓값
                - MIN 속성 값의 최솟값
                - SUM 속성 값의 합
                - AVG 속성 값의 평균
            - 그룹별 검색
                - GROUP BY
                - 집계 함수는 WHERE과 함께 사용 불가 HAVING 사용
            - JOIN을 이용한 검색
                
                : 여러 개의 테이블을 연결하여 데이터 검색
                
        - INSERT(데이터 삽입)
        - UPDATE(데이터 변경)
        - DELETE(데이터 삭제)
    3. DCL 데이터 제어어
        
        : 보안을 위해 데이터에 대한 접근 및 사용 권한을 사용자별로 부여하거나 취소