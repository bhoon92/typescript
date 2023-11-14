union타입: 값에 허용된 타입을 두 개 이상의 가능한 타입으로 확장하는 것

narrowing 타입: 값에 허용된 타입이 하나 이상의 가능한 타입이 허용되지 않도록 하는 것

### 유니온 타입 선언

```tsx
# error message 예시
export interface RequestExceptionResponse {
  status: number;
  code: number;
  message: string | string[];
  desc: string | string[];
  error: { reqId: string; code: string; desc: string[] };
}
```

### 유니온 타입 속성

- 사용할 string | number 로 설정 했을 때, .toString()은 가능하나, .toUpperCase등 string타입에만 사용할 수 있는 methode에 대해서는 사용할 수 없다.

### 값 할당을 통한 내로잉

- 초기값이 주어지면, 따로 선언하지 않아도 타입이 지정 된다.
- 초기값을 const test = “string” 으로 선언하면 test변수는 자동으로 설정 된다.

### 조건 검사를 통한 내로잉

- 조건문을 사용하여 타입을 유추할 수 있다.

### typeof를 사용한 검사

- 그렇다.

### 리터럴 타입

- 좀 더 구체적인 버전의 원시타입이다.
- 원시 타입 값 중 어떤 것이 아닌 특정 우너식밧으로 알려진 타입이 리터럴이다

→ const ollie = ‘Ollie’ 해당값은 string이라고도 볼 수 있으나, ollie = Ollie라는 특정 원시값을 가진다는 의미이다.

- 즉 원시 타입은 해당 타입의 가능한 모든 리터럴 값의 집합이다.

### 리터럴 할당 가능성

- const는 그냥 픽스야!

### 엄격한 null 검사

- null체크를 유동적(Eric아님)으로 할 수 있다.

### 타입 별칭과 타입 별칭 결합

- 재사용하는 타입에 대해서 더 간편하게 사용 할 수 있도록 타입 별칭(type alias)을 선언할 수 있다.
- 해당 기능은 typescript에만 있어서, javascript에서는 컴파일 되지 않는다.

```tsx
export interface AdminInterface {
  id: number;
  name: string;
  email: string;
  password: string;
  salt: string;
}
export type RequestMakeAdminInterface = Omit<
  AdminInterface,
  "id" | "salt" | "email"
>;
```

### 마무리

- Union type은 결합이다.
- 타입을 strict하게 할수록 안정성이 높아진다.
- nullable은 양날의 검임을 잊지 말자.
- 여러개의 타입을 지정할 떄는 union alias를 사용하자.
