***PETRONE2017 / Protocol / Structs / Light***<br>
Modified : 2017.05.02

---

#### LED 제어와 관련된 구조체들을 소개합니다.

---

<br>

## <a name="Light_Manual">Protocol::Light::Manual</a>
선택한 LED의 밝기를 직접 조정합니다.
```cpp
namespace Protocol
{
    struct LightMode
    {
        u8	flags;         // Flags 열거형을 조합한 값
        u8	brightness;    // 밝기     
    };
}
```
- lightMode : [Protocol::LightModeBase](base_structs.md#LightModeBase)


<br>
<br>


## <a name="LightMode">Protocol::Light::Mode</a>
LED 모드 변경 하나를 전달합니다.
```cpp
namespace Protocol
{
    struct LightMode
    {
        LightModeBase   lightMode;
    };
}
```
- lightMode : [Protocol::LightModeBase](base_structs.md#LightModeBase)

<br>
<br>

## <a name="LightModeCommand">Protocol::LightModeCommand</a>
LED 모드 변경 하나와 명령 하나를 전달합니다.
```cpp
namespace Protocol
{
    struct LightModeCommand
    {
        LightModeBase   lightMode;
        CommandBase     command;
    };
}
```
- lightMode : [Protocol::LightModeBase](base_structs.md#LightModeBase)
- command : [Protocol::CommandBase](base_structs.md#CommandBase)

<br>
<br>

## <a name="LightModeCommandIr">Protocol::LightModeCommandIr</a>
LED 모드 변경 하나와 명령 하나, 그리고 IR 메세지를 전달합니다.
```cpp
namespace Protocol
{
    struct LightModeCommandIr
    {
        LightModeBase   lightMode;
        CommandBase     command;
        u32             irData;
    };
}
```
- lightMode : [Protocol::LightModeBase](base_structs.md#LightModeBase)
- command : [Protocol::CommandBase](base_structs.md#CommandBase)

<br>
<br>

## <a name="LightModeColor">Protocol::LightModeColor</a>
LED 모드 변경 하나를 전달합니다. RGB 값을 직접 지정합니다.
```cpp
namespace Protocol
{
    struct LightModeColor
    {
        LightModeColorBase   lightModeColor;
    };
}
```
- lightModeColor : [Protocol::LightModeColorBase](base_structs.md#LightModeColorBase)

<br>
<br>

## <a name="LightEvent">Protocol::LightEvent</a>
LED 이벤트 실행 하나를 전달합니다.
```cpp
namespace Protocol
{
    struct LightEvent
    {
        LightEventBase   lightEvent;
    };
}
```
- lightEvent : [Protocol::LightEventBase](base_structs.md#LightEventBase)

<br>
<br>

## <a name="LightEventCommand">Protocol::LightEventCommand</a>
LED 이벤트 실행 하나와 명령 하나를 전달합니다.
```cpp
namespace Protocol
{
    struct LightEventCommand
    {
        LightEventBase   lightEvent;
        CommandBase      command;
    };
}
```
- lightEvent : [Protocol::LightEventBase](base_structs.md#LightEventBase)
- command : [Protocol::CommandBase](base_structs.md#CommandBase)

<br>
<br>

## <a name="LightEventCommandIr">Protocol::LightEventCommandIr</a>
LED 이벤트 실행 하나와 명령 하나, 그리고 IR 메세지를 전달합니다.
```cpp
namespace Protocol
{
    struct LightEventCommandIr
    {
        LightEventBase   lightEvent;
        CommandBase      command;
        u32              irData;
    };
}
```
- lightEvent : [Protocol::LightEventBase](base_structs.md#LightEventBase)
- command : [Protocol::CommandBase](base_structs.md#CommandBase)

<br>
<br>

## <a name="LightEventColor">Protocol::LightEventColor</a>
LED 이벤트 실행 하나를 전달합니다. RGB 값을 직접 지정합니다.
```cpp
namespace Protocol
{
    struct LightEventColor
    {
        LightEventColorBase   lightEventColor;
    };
}
```
- lightEventColor : [Protocol::LightEventColorBase](base_structs.md#LightEventColorBase)

<br>
<br>

## <a name="LightModeDefaultColor">Protocol::LightModeDefaultColor</a>
LED 시작 모드를 설정합니다. RGB 값을 직접 지정합니다. 여기서 지정한 값은 드론의 내부 메모리에 저장합니다.
```cpp
namespace Protocol
{
    struct LightModeDefaultColor
    {
        LightModeColorBase   lightModeDefaultColor;
    };
}
```
- lightModeDefaultColor : [Protocol::LightModeColorBase](base_structs.md#LightModeColorBase)

<br>
<br>


---

### PETRONE 2017

1. [Intro](intro.md)
2. [Typedef](typedef.md)
3. [DataType](datatype.md)
4. [Definitions](definitions.md)
5. [Base Structs](base_structs.md)
6. [Structs](structs.md)
7. ***Structs - Light***

<br>

[Index](index.md)
