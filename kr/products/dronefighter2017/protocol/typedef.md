***DRONEFIGHTER2017 / Protocol / Typedef***<br>
Modified : 2017.05.18

---

#### DRONE FIGHTER 2017 프로젝트 내부에서 사용하고 있는 변수 형식을 소개합니다.

---

<br>

**변수 형식**
-----------------
데이터 송수신 시에는 지정된 열거형이 있는 경우라도 데이터 길이를 명확하게 표시하고자 아래와 같은 변수형을 사용하고 있습니다.
```cpp
typedef int64_t   s64;
typedef int32_t   s32;
typedef int16_t   s16;
typedef int8_t    s8;

typedef uint64_t  u64;
typedef uint32_t  u32;
typedef uint16_t  u16;
typedef uint8_t   u8;

typedef float     f32;
typedef double    f64;
```




<br>

---

### DRONE FIGHTER 2017

1. [Intro](intro.md)
2. ***Typedef***
3. [DataType](datatype.md)
4. [Definitions](definitions.md)
5. [Structs](structs.md)
6. [Structs - Light](structs_light.md)

<br>

[Index](index.md)

