***PETRONE2017 / Protocol / Structs / Light***<br>
Modified : 2017.05.02

---

#### LED 제어와 관련된 정의 및 구조체들을 소개합니다.

---

<br>
<br>

## <a name="Light_Drone_Mode">Light::Drone::Mode::Type</a>
드론 LED 모드 또는 이벤트 명령 시 동작 모드를 지정할 때 사용합니다.

```cpp
namespace Light
{
    namespace Drone
    {
        namespace Mode
        {
            enum Type
            {
                None,
                
                EyeNone = 0x10,
                EyeManual,              // 수동 제어
                EyeHold,                // 지정한 색상을 계속 켬
                EyeFlicker,             // 깜빡임         
                EyeFlickerDouble,       // 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)            
                EyeDimming,             // 밝기 제어하여 천천히 깜빡임
                
                ArmNone = 0x40,         
                ArmManual,              // 수동 제어
                ArmHold,                // 지정한 색상을 계속 켬
                ArmFlicker,             // 깜빡임         
                ArmFlickerDouble,       // 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)            
                ArmDimming,             // 밝기 제어하여 천천히 깜빡임
                
                EndOfType
            };
        }
    }
}
```

<br>
<br>

## <a name="Light_Drone_Flags">Light::Drone::Flags::Type</a>
드론 LED를 직접 지정하여 제어할 때 사용합니다.

```cpp
namespace Light
{
    namespace Drone
    {
        namespace Flags
        {
            enum Type
            {
				None		= 0x00,
				
				EyeRed		= 0x80,
				EyeGreen	= 0x40,
				EyeBlue		= 0x20,

				ArmRed		= 0x10,
				ArmGreen	= 0x08,
				ArmBlue		= 0x04
            };
        }
    }
}
```

<br>
<br>

## <a name="Light_Controller_Mode">Light::Controller::Mode::Type</a>
조종기 LED 모드 또는 이벤트 명령 시 동작 모드를 지정할 때 사용합니다.

```cpp
namespace Light
{
    namespace Controller
    {
        namespace Mode
        {
            enum Type
            {
                None,
                
                Manual,                         ///< 수동 조작
                
                // Team
                TeamNone = 0x10,
                
                TeamHoldRed,
                TeamHoldBlue,
                TeamHoldAll,
                
                TeamFlickerRed,
                TeamFlickerBlue,
                TeamFlickerAll,
                TeamFlickerSeesaw,
                
                TeamFlickerDoubleRed,
                TeamFlickerDoubleBlue,
                TeamFlickerDoubleAll,
                
                TeamDimmingRed,
                TeamDimmingBlue,
                TeamDimmingAll,
                TeamDimmingSeesaw,
                
                Team,                           ///< 팀 표시
                
                
                EndOfType
            };
        }
    }
}
```

<br>
<br>

## <a name="Light_Colors">Light::Colors::Type</a>
LED 색상을 지정할 때 사용합니다.

```cpp
namespace Light
{
    namespace Colors
    {
        enum Type
        {
            AliceBlue,
            AntiqueWhite,
            Aqua,
            Aquamarine,
            Azure,
            Beige,
            Bisque,
            Black,
            BlanchedAlmond,
            Blue,
            BlueViolet,
            Brown,
            BurlyWood,
            CadetBlue,
            Chartreuse,
            Chocolate,
            Coral,
            CornflowerBlue,
            Cornsilk,
            Crimson,
            Cyan,
            DarkBlue,
            DarkCyan,
            DarkGoldenRod,
            DarkGray,
            DarkGreen,
            DarkKhaki,
            DarkMagenta,
            DarkOliveGreen,
            DarkOrange,
            DarkOrchid,
            DarkRed,
            DarkSalmon,
            DarkSeaGreen,
            DarkSlateBlue,
            DarkSlateGray,
            DarkTurquoise,
            DarkViolet,
            DeepPink,
            DeepSkyBlue,
            DimGray,
            DodgerBlue,
            FireBrick,
            FloralWhite,
            ForestGreen,
            Fuchsia,
            Gainsboro,
            GhostWhite,
            Gold,
            GoldenRod,
            Gray,
            Green,
            GreenYellow,
            HoneyDew,
            HotPink,
            IndianRed,
            Indigo,
            Ivory,
            Khaki,
            Lavender,
            LavenderBlush,
            LawnGreen,
            LemonChiffon,
            LightBlue,
            LightCoral,
            LightCyan,
            LightGoldenRodYellow,
            LightGray,
            LightGreen,
            LightPink,
            LightSalmon,
            LightSeaGreen,
            LightSkyBlue,
            LightSlateGray,
            LightSteelBlue,
            LightYellow,
            Lime,
            LimeGreen,
            Linen,
            Magenta,
            Maroon,
            MediumAquaMarine,
            MediumBlue,
            MediumOrchid,
            MediumPurple,
            MediumSeaGreen,
            MediumSlateBlue,
            MediumSpringGreen,
            MediumTurquoise,
            MediumVioletRed,
            MidnightBlue,
            MintCream,
            MistyRose,
            Moccasin,
            NavajoWhite,
            Navy,
            OldLace,
            Olive,
            OliveDrab,
            Orange,
            OrangeRed,
            Orchid,
            PaleGoldenRod,
            PaleGreen,
            PaleTurquoise,
            PaleVioletRed,
            PapayaWhip,
            PeachPuff,
            Peru,
            Pink,
            Plum,
            PowderBlue,
            Purple,
            RebeccaPurple,
            Red,
            RosyBrown,
            RoyalBlue,
            SaddleBrown,
            Salmon,
            SandyBrown,
            SeaGreen,
            SeaShell,
            Sienna,
            Silver,
            SkyBlue,
            SlateBlue,
            SlateGray,
            Snow,
            SpringGreen,
            SteelBlue,
            Tan,
            Teal,
            Thistle,
            Tomato,
            Turquoise,
            Violet,
            Wheat,
            White,
            WhiteSmoke,
            Yellow,
            YellowGreen,
            
            EndOfColor
        };
    }
}
```

<br>
<br>

## <a name="Protocol_Light_Manual">Protocol::Light::Manual</a>
선택한 LED의 밝기를 직접 조정합니다.
```cpp
namespace Protocol
{
	namespace Light
	{
		struct Manual
		{
			u8	flags;         // Flags 열거형을 조합한 값
			u8	brightness;    // 밝기     
		};
	}
}
```
- flags : [Light::Drone::Flags](#Light_Drone_Flags)


<br>
<br>


## <a name="Protocol_Light_Mode">Protocol::Light::Mode</a>
LED 모드 변경
```cpp
namespace Protocol
{
	namespace Light
	{
		struct Mode
		{
			u8		mode;		// LED 모드
			u16		interval;	// LED 모드의 갱신 주기
		};
	}
}
```
- mode : [Protocol::LightModeBase](definitions.md#Light_Drone_Mode)

<br>
<br>


## <a name="Protocol_Light_Event">Protocol::Light::Event</a>
LED 이벤트 실행
```cpp
namespace Protocol
{
	namespace Light
	{
		struct Event
		{
			u8		event;		// LED 이벤트
			u16		interval;	// LED 이벤트 갱신 주기
			u8		repeat;		// LED 이벤트 반복 횟수
		};
	}
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
