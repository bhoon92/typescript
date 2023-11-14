### 타입스크립트의 주요 종류

1. 기본 타입 (boolean, number, string, null, undefined)
2. 객체 타입 (object, array, tuple, enum)
3. 함수 타입 (function)
4. 클래스와 인터페이스 타입 (class, interface)
5. 제네릭 타입 (generic)
6. 유니언과 인터섹션 타입 (union, intersection)
7. 타입 별칭과 리터럴 타입 (type alias, literal)
8. Nullable 타입 (nullability)
9. 타입 가드와 타입 추론 (type guard, type inference)

### 변수 타입 지정

변수를 선언하면서 값을 선언하지 않고, 타입만 지정해서 사용이 가능하다.

(dto, entity에서 사용하는 선언 등)

```tsx
...

export class CouponCodeEntity extends BaseEntity {
  @PrimaryGeneratedColumn()
  id: number;

  @ManyToOne(() => CouponPolicyEntity)
  @JoinColumn([{ name: 'coupon_policy_id', referencedColumnName: 'id' }])
  couponPolicy: CouponPolicyEntity;
  @Column()
  couponPolicyId: number;

  @Column({ type: 'varchar', comment: '쿠폰의 난수 번호' })
  uniqueCode: string;

  @Column({ type: 'varchar', comment: '유저 아이디, 식별자로 사용', nullable: true })
  userId?: string;

  @Column({ type: 'varchar', comment: '디바이스 아이디, 식별자로 사용', nullable: true })
  deviceId?: string;

  @Column({ type: 'date', comment: '발헹(등록) 일시', nullable: true })
  publishedAt?: Date;
}
```

### 모듈

- 다른 파일에서 선언한 변수를 가져오도록 선언할 수 있다.

```tsx
...
export interface PoiInterface {
  id: number;
  name: string;
  applicationId: number;
  brand?: BrandInterface;
  category?: CategoryInterface;
  gps: GpsInterface;
  imageUrl?: string;
  address?: string;
  url?: string;
  phone?: string;
  isActive: boolean;
}
```

### 마무리

- 원시타입에 대한 이해도 높이기
- 타입 시스템이 코드를 이해하는 방식 알기
- any타입의 사용을 지양하기
- 타입형태의 객체 멤버 활용하기
