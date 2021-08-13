## Utility Types (유틸리티 타입)
> TypeScript는 공통 타입 변환을 용이하게 하기 위해 몇 가지 유틸리티 타입을 제공한다.

### Partial
> Partial 타입은 특정 타입의 **부분 집합을 만족**하는 타입을 정의할 수 있다.

```ts
interface Address {
  email: string;
  address: string;
}

type MyEmail = Partial<Address>;
const me: MyEmail = {}; // 가능
const you: MyEmail = { email: "noh5524@gmail.com" }; // 가능
const all: MyEmail = { email: "noh5524@gmail.com", address: "secho" }; // 가능
```
