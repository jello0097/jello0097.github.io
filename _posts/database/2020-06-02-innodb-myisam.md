---
title: InnoDB 와 MyISAM
categories:
- database
- mysql
tags:
- database
- mysql
toc_sticky: true
toc: true
---

### 시작하기 
InnoDB와 MyISAM은 mysql에서 사용하는 스토리지 엔진이다. <br>
이러한 스토리지 엔진은 어플리케이션의 요구사항에 따라 장단점을 살펴본 뒤 선택해야 한다.  <br>
전반적인 내용은 mysql 공식 사이트의 stroage-engines 부분을 참고하여 작성하였다. <br>
(MySQL 8.0 Supported Storage Engines)<br>

[참고, mysql 공식사이트](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)

mysql 8.0의 기본 저장 엔진은 innoDB
### InnoDB와 MyISAM 차이점

| InnoDB | MyISAM |
| -------- | -------- |
| 트랜잭션 지원 o  | 트랜잭션 지원 x  |
| Low-level locking 가능<br/>insert, update시 MyISAM보다 속도가 빠름 | Low-level locking 불가능<br/>Table-level locking만 가능 |
| Fulltext 인덱스 지원 x | Fulltext 인덱스 지원 o |
| 테이블 비교 시 속도가 상대적으로 느림 | 테이블 비교 시 속도가 상대적으로 빠름 |
| 트랜잭션을 지원하므로 큰 프로젝트에 적합 | 소규모 프로젝트에 적합 |
| ACID 지원 o | ACID 지원 x | 
| AUTO_INCREMENT 필드가 인덱스의 일부가 됨 | AUTO_INCREMENT필드가 인덱스의 일부가 되지 않음 |
| 테이블을 삭제한 경우 re-establish 불가능 | 테이블을 삭제한 경우 re-establish 가능 |
| 테이블 단위로 데이터를 저장하지 않음<br/>즉, select count(*) from table 인 경우 테이블을<br/> full scan 하여 row number를 계산함 | 테이블 단위로 데이터를 저장하므로<br/>저장되어 있는row number를 쉽게 읽을 수 있음 |
| Foreign Key 지원 o | Foreign Key 지원 x |

### ACID란?
* **원자성(Atomicity)**은 트랜잭션과 관련된 작업들이 부분적으로 실행되다가 중단되지 않는 것을 보장하는 능력이다. 예를 들어, 자금 이체는 성공할 수도 실패할 수도 있지만 보내는 쪽에서 돈을 빼 오는 작업만 성공하고 받는 쪽에 돈을 넣는 작업을 실패해서는 안된다. 원자성은 이와 같이 중간 단계까지 실행되고 실패하는 일이 없도록 하는 것이다.

* **일관성(Consistency)**은 트랜잭션이 실행을 성공적으로 완료하면 언제나 일관성 있는 데이터베이스 상태로 유지하는 것을 의미한다. 무결성 제약이 모든 계좌는 잔고가 있어야 한다면 이를 위반하는 트랜잭션은 중단된다.

* **독립성(Isolation)**은 트랜잭션을 수행 시 다른 트랜잭션의 연산 작업이 끼어들지 못하도록 보장하는 것을 의미한다. 이것은 트랜잭션 밖에 있는 어떤 연산도 중간 단계의 데이터를 볼 수 없음을 의미한다. 은행 관리자는 이체 작업을 하는 도중에 쿼리를 실행하더라도 특정 계좌간 이체하는 양 쪽을 볼 수 없다. 성능관련 이유로 인해 이 특성은 가장 유연성 있는 제약 조건이다.

* **지속성(Durability)**은 성공적으로 수행된 트랜잭션은 영원히 반영되어야 함을 의미한다. 시스템 문제, DB 일관성 체크 등을 하더라도 유지되어야 함을 의미한다. 전형적으로 모든 트랜잭션은 로그로 남고 시스템 장애 발생 전 상태로 되돌릴 수 있다. 트랜잭션은 로그에 모든 것이 저장된 후에만 commit 상태로 간주될 수 있다. 

[참고, wikipedia](https://ko.wikipedia.org/wiki/ACID)
