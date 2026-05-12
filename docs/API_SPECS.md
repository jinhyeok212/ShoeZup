# API_SPEC.md

# API 명세서

---

# 공통 응답 형식

## 성공 응답

```json
{
  "success": true,
  "message": "요청 성공",
  "data": {}
}
```

---

## 실패 응답

```json
{
  "success": false,
  "message": "에러 메시지",
  "data": null
}
```

---

# 1. 상품 검색 API

## 설명

상품명을 기반으로 상품 목록 조회

---

## Request

```http
GET /api/products?keyword=jordan
```

---

## Query Parameters

| 이름 | 타입 | 설명 |
| --- | --- | --- |
| keyword | string | 상품 검색 키워드 |

---

## Response

```json
{
  "success": true,
  "message": "조회 성공",
  "data": [
    {
      "product_id": 1,
      "product_name": "Jordan 1 Retro High",
      "brand": "Nike",
      "recent_price": 320000
    }
  ]
}
```

---

# 2. 상품 상세 조회 API

## Request

```http
GET /api/products/{product_id}
```

---

## Path Parameters

| 이름 | 타입 | 설명 |
| --- | --- | --- |
| product_id | integer | 상품 ID |

---

## Response

```json
{
  "success": true,
  "message": "조회 성공",
  "data": {
    "product_id": 1,
    "product_name": "",
    "brand": "",
    "retail_price": 0,
    "recent_price": 0,
    "average_price": 0
  }
}
```

---

# 3. 가격 추이 조회 API

## Request

```http
GET /api/products/{product_id}/price-history
```

---

## Response

```json
{
  "success": true,
  "message": "조회 성공",
  "data": [
    {
      "date": "2026-05-12",
      "price": 320000
    }
  ]
}
```

---

# 4. 사이즈별 프리미엄 API

## Request

```http
GET /api/products/{product_id}/size-premium
```

---

## Response

```json
{
  "success": true,
  "message": "조회 성공",
  "data": [
    {
      "size": 270,
      "average_price": 355000
    }
  ]
}
```

---

# 상태 코드 규칙

| 코드 | 설명 |
| --- | --- |
| 200 | 요청 성공 |
| 400 | 잘못된 요청 |
| 404 | 데이터 없음 |
| 500 | 서버 오류 |

---

# API 개발 규칙

- 모든 응답은 JSON 형식 사용
- snake_case 사용
- 예외 처리 필수
- 성공 여부(success) 포함
- message 필드 포함
