# 117p - 서브쿼리를 활용한 필터링

## 문제

제목에 `PET`이라는 문자열이 포함된 영화가 가족용으로 안전하다고 할 경우,
`film` 테이블에서 서브쿼리를 실행하여 해당 영화와 관련된 모든 등급을 검색한 다음,
해당 등급 중 하나가 포함된 `영화`를 모둘 검색하는 쿼리를 작성하세요.

## 정답

```sql
SELECT title, rating
  FROM film
  WHERE rating IN (SELECT rating FROM film WHERE title LIKE '%PET%');
```

## 서브 쿼리를 사용하지 않고 풀기

```sql
SELECT rating
	from film as f
	where title like '%pet%';
```

위의 쿼리를 실행했을때의 결과가 G, PG, PG과 같이 나왔을때 아래의 쿼리처럼 작성할 수 있다.

```sql
SELECT title, rating
	from film as f
	where rating in('G','PG');
```

## 추가로 알게된 점

서브쿼리 사용해 필터링 했을때 조건을 직접 지정하지 않아, 다른 조건에 따라 데이터를 필터링할 수 있는 유연성을 제공합니다.
