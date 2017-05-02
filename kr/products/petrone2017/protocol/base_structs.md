***PETRONE2017 / Protocol / BaseStructs***<br>
Modified : 2017.05.02

---

#### 데이터 전송 시 그대로 전달되지는 않으나 다른 구조체의 일부분으로 포함되는 구조체들을 소개합니다.

---

<br>

## <a name="Control::Double8">Control::Double8</a>
PETRONE 자동차 조종 시에 사용합니다. 드론 모드일 때 이 명령을 전송하면 무시합니다.
```cpp
namespace Control
{
    struct Double8
    {
		s8		wheel;		// wheel
		s8		accel;		// accel
    };
}
```

Control::Double8 입력 값의 범위는 다음과 같습니다


|이름      | 형식 | 범위        | 방향      | 음수 값(-) | 양수 값(+)    |
|:--------:|:----:|:-----------:|:---------:|:----------:|:-------------:|
| wheel     | s8   | -100 ~ 100  | 좌우 회전 | 좌회전       | 우회전          |
| accel | s8   | -100 ~ 100  | 전후진 속도    | 후진       | 전진          |

<br>
<br>

## <a name="Control::Quad8">Control::Quad8</a>
PETRONE 드론 및 자동차 조종 시에 사용합니다.
```cpp
namespace Control
{
    struct Quad8
    {
		s8		roll;		// roll
		s8		pitch;		// pitch
		s8		yaw;		// yaw
		s8		throttle;	// throttle
    };
}
```

Control 입력 값의 범위는 다음과 같습니다. Drive 모드에서는 **throttle**(전후)과 **roll**(좌우)만 사용합니다.


|이름      | 형식 | 범위        | 방향      | 음수 값(-) | 양수 값(+)    |
|:--------:|:----:|:-----------:|:---------:|:----------:|:-------------:|
| roll     | s8   | -100 ~ 100  | 좌우 이동 | 좌측       | 우측          |
| pitch    | s8   | -100 ~ 100  | 전후 이동 | 후방       | 전방          |
| yaw      | s8   | -100 ~ 100  | 좌우 회전 | 반시계     | 시계 방향     |
| throttle | s8   | -100 ~ 100  | 승하강    | 하강       | 상승          |

<br>
<br>

## <a name="CommandBase">Protocol::CommandBase</a>
PETRONE의 설정을 변경하거나 데이터를 요청할 때 사용합니다.
```cpp
namespace Protocol
{
    struct CommandBase
    {
        u8 commandType;   // 명령 타입
        u8 option;        // 명령에 대한 옵션
    };
}
```
- commandType : [Protocol::CommandType::Type](definitions.md#CommandType)
- option : [System::ModeVehicle::Type](definitions.md#ModeVehicle), [System::Coordinate::Type](definitions.md#Coordinate), [System::Trim::Type](definitions.md#Trim),  [System::FlightEvent::Type](definitions.md#FlightEvent), [Protocol::DataType::Type](datatype.md#DataType)

<br>
<br>

## <a name="LightModeBase">Protocol::LightModeBase</a>
LED 모드를 변경할 때 사용하는 구조체입니다.
```cpp
namespace Protocol
{
    struct LightModeBase
    {
        u8 mode;         // LED 모드
        u8 color;        // RGB 색상(팔레트 인덱스)
        u8 interval;     // 내부 연산 함수 호출 주기
    };
}
```
- mode : [Light::Mode::Type](definitions.md#LightMode)
- color : [Light::Colors::Type](definitions.md#LightColors)

<br>
<br>

## <a name="LightColor">Light::Color</a>
RGB LED의 색상을 직접 지정할 때 사용하는 구조체입니다.
```cpp
namespace Light
{
    struct Color
    {
        u8 r;           // Red
        u8 g;           // Green
        u8 b;           // Blue
    };
}
```

<br>
<br>

## <a name="LightModeColorBase">Protocol::LightModeColorBase</a>
LED 모드를 변경할 때 사용하는 구조체입니다. RGB 색상을 직접 지정할 수 있습니다.
```cpp
namespace Protocol
{
    struct LightModeColorBase
    {
        u8             mode;           // LED 모드
        Light::Color   color;          // RGB 색상
        u8             interval;       // 내부 연산 함수 호출 주기
    };
}
```
- mode : [Light::Mode::Type](definitions.md#LightMode)
- color : [Light::Color](#LightColor)

<br>
<br>

## <a name="LightEventBase">Protocol::LightEventBase</a>
LED 이벤트를 실행할 때 사용하는 구조체입니다. 지정한 횟수만큼 반복 실행 후 기존 실행하던 모드로 복귀합니다.
```cpp
namespace Protocol
{
    struct LightEventBase
    {
        u8 event;        // LED 모드
        u8 color;        // RGB 색상(팔레트 인덱스)
        u8 interval;     // 내부 연산 함수 호출 주기
        u8 repeat;       // 반복 횟수
    };
}
```
- event : [Light::Mode::Type](definitions.md#LightMode)
- color : [Light::Colors::Type](definitions.md#LightColors)

<br>
<br>

## <a name="LightEventColorBase">Protocol::LightEventColorBase</a>
LED 이벤트를 실행할 때 사용하는 구조체입니다. 지정한 횟수만큼 반복 실행 후 기존 실행하던 모드로 복귀합니다. RGB 색상을 직접 지정할 수 있습니다.
```cpp
namespace Protocol
{
    struct LightEventColorBase
    {
        u8             event;          // LED 모드
        Light::Color   color;          // RGB 색상
        u8             interval;       // 내부 연산 함수 호출 주기
        u8             repeat;         // 반복 횟수
    };
}
```
- event : [Light::Mode::Type](definitions.md#LightMode)
- color : [Light::Color](#LightColor)

<br>
<br>

## <a name="MotorBase">Protocol::MotorBase</a>
모터를 작동하거나 현재 모터에 적용된 입력값을 확인하는데 사용하는 구조체입니다.
```cpp
namespace Protocol
{
    struct MotorBase
    {
        s16 forward;        // 정방향
        s16 reverse;        // 역방향
    };
}
```


<br>

---

### PETRONE 2017

1. [Intro](intro.md)
2. [Typedef](typedef.md)
3. [DataType](datatype.md)
4. [Definitions](definitions.md)
5. ***Base Structs***
6. [Structs](structs.md)
7. [Structs - Light](structs_light.md)

<br>

[Index](index.md)
