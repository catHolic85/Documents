***PETRONE2017 / Protocol / Structs / Light***<br>
Modified : 2017.07.04

---

#### LED 제어와 관련된 정의 및 구조체들을 소개합니다.

---

<br>
<br>

# Definitions

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
                None        = 0x00,
                
                EyeRed      = 0x80,
                EyeGreen    = 0x40,
                EyeBlue     = 0x20,

                ArmRed      = 0x10,
                ArmGreen    = 0x08,
                ArmBlue     = 0x04
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
                
                // Team
                TeamNone = 0x10,
                TeamManual,             // 수동 조작
                TeamHold,
                TeamFlicker,
                TeamFlickerDouble,
                TeamDimming,
                
                EndOfType
            };
        }
    }
}
```

<br>
<br>

## <a name="Light_Controller_Flags">Light::Controller::Flags::Type</a>
드론 LED를 직접 지정하여 제어할 때 사용합니다.

```cpp
namespace Light
{
    namespace Controller
    {
        namespace Flags
        {
            enum Type
            {
                None        = 0x00,
                
                Red         = 0x08,
                Green       = 0x04,
                Blue        = 0x02
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
            AliceBlue,              // 0x00
            AntiqueWhite,           // 0x01 
            Aqua,                   // 0x02
            Aquamarine,             // 0x03
            Azure,                  // 0x04
            Beige,                  // 0x05
            Bisque,                 // 0x06 
            Black,                  // 0x07 
            BlanchedAlmond,         // 0x08 
            Blue,                   // 0x09 
            BlueViolet,             // 0x0A
            Brown,                  // 0x0B 
            BurlyWood,              // 0x0C 
            CadetBlue,              // 0x0D 
            Chartreuse,             // 0x0E 
            Chocolate,              // 0x0F
            Coral,                  // 0x10
            CornflowerBlue,         // 0x11
            Cornsilk,               // 0x12
            Crimson,                // 0x13
            Cyan,                   // 0x14
            DarkBlue,               // 0x15
            DarkCyan,               // 0x16
            DarkGoldenRod,          // 0x17
            DarkGray,               // 0x18
            DarkGreen,              // 0x19
            DarkKhaki,              // 0x1A
            DarkMagenta,            // 0x1B
            DarkOliveGreen,         // 0x1C
            DarkOrange,             // 0x1D
            DarkOrchid,             // 0x1E
            DarkRed,                // 0x1F
            DarkSalmon,             // 0x20
            DarkSeaGreen,           // 0x21
            DarkSlateBlue,          // 0x22
            DarkSlateGray,          // 0x23
            DarkTurquoise,          // 0x24
            DarkViolet,             // 0x25
            DeepPink,               // 0x26
            DeepSkyBlue,            // 0x27
            DimGray,                // 0x28
            DodgerBlue,             // 0x29
            FireBrick,              // 0x2A
            FloralWhite,            // 0x2B
            ForestGreen,            // 0x2C
            Fuchsia,                // 0x2D
            Gainsboro,              // 0x2E
            GhostWhite,             // 0x2F
            Gold,                   // 0x30
            GoldenRod,              // 0x31
            Gray,                   // 0x32
            Green,                  // 0x33
            GreenYellow,            // 0x34
            HoneyDew,               // 0x35
            HotPink,                // 0x36
            IndianRed,              // 0x37
            Indigo,                 // 0x38
            Ivory,                  // 0x39
            Khaki,                  // 0x3A
            Lavender,               // 0x3B
            LavenderBlush,          // 0x3C
            LawnGreen,              // 0x3D
            LemonChiffon,           // 0x3E
            LightBlue,              // 0x3F
            LightCoral,             // 0x40
            LightCyan,              // 0x41
            LightGoldenRodYellow,   // 0x42
            LightGray,              // 0x43
            LightGreen,             // 0x44
            LightPink,              // 0x45
            LightSalmon,            // 0x46
            LightSeaGreen,          // 0x47
            LightSkyBlue,           // 0x48
            LightSlateGray,         // 0x49
            LightSteelBlue,         // 0x4A
            LightYellow,            // 0x4B
            Lime,                   // 0x4C
            LimeGreen,              // 0x4D
            Linen,                  // 0x4E
            Magenta,                // 0x4F
            Maroon,                 // 0x50
            MediumAquaMarine,       // 0x51
            MediumBlue,             // 0x52
            MediumOrchid,           // 0x53
            MediumPurple,           // 0x54
            MediumSeaGreen,         // 0x55
            MediumSlateBlue,        // 0x56
            MediumSpringGreen,      // 0x57
            MediumTurquoise,        // 0x58
            MediumVioletRed,        // 0x59
            MidnightBlue,           // 0x5A
            MintCream,              // 0x5B
            MistyRose,              // 0x5C
            Moccasin,               // 0x5D
            NavajoWhite,            // 0x5E
            Navy,                   // 0x5F
            OldLace,                // 0x60
            Olive,                  // 0x61
            OliveDrab,              // 0x62
            Orange,                 // 0x63
            OrangeRed,              // 0x64
            Orchid,                 // 0x65
            PaleGoldenRod,          // 0x66
            PaleGreen,              // 0x67
            PaleTurquoise,          // 0x68
            PaleVioletRed,          // 0x69
            PapayaWhip,             // 0x6A
            PeachPuff,              // 0x6B
            Peru,                   // 0x6C
            Pink,                   // 0x6D
            Plum,                   // 0x6E
            PowderBlue,             // 0x6F
            Purple,                 // 0x70
            RebeccaPurple,          // 0x71
            Red,                    // 0x72
            RosyBrown,              // 0x73
            RoyalBlue,              // 0x74
            SaddleBrown,            // 0x75
            Salmon,                 // 0x76
            SandyBrown,             // 0x77
            SeaGreen,               // 0x78
            SeaShell,               // 0x79
            Sienna,                 // 0x7A
            Silver,                 // 0x7B
            SkyBlue,                // 0x7C
            SlateBlue,              // 0x7D
            SlateGray,              // 0x7E
            Snow,                   // 0x7F
            SpringGreen,            // 0x80
            SteelBlue,              // 0x81
            Tan,                    // 0x82
            Teal,                   // 0x83
            Thistle,                // 0x84
            Tomato,                 // 0x85
            Turquoise,              // 0x86
            Violet,                 // 0x87
            Wheat,                  // 0x88
            White,                  // 0x89
            WhiteSmoke,             // 0x8A
            Yellow,                 // 0x8B
            YellowGreen,            // 0x8C
            
            EndOfColor
        };
    }
}
```

<br>
<br>

# Structs

<br>
<br>


## <a name="Light_Color">Light::Color</a>
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
- r : 0 ~ 255 사이의 값. 값이 클수록 밝음
- g : 0 ~ 255 사이의 값. 값이 클수록 밝음
- b : 0 ~ 255 사이의 값. 값이 클수록 밝음


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
            u16 flags;         // Flags 열거형을 조합한 값
            u8  brightness;    // 밝기     
        };
    }
}
```
- flags : [Light::Drone::Flags](#Light_Drone_Flags), [Light::Controller::Flags](#Light_Controller_Flags)
- brightness : 0 ~ 255 사이의 값. 값이 클수록 밝음


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
            u8      mode;       // LED 모드
            u16     interval;   // LED 모드의 갱신 주기
        };
    }
}
```
- mode : [Light::Drone::Mode::Type](#Light_Drone_Mode), [Light::Controller::Mode::Type](#Light_Controller_Mode)
- interval : 0 ~ 65535


<br>
<br>


## <a name="Protocol_Light_ModeCommand">Protocol::Light::ModeCommand</a>
LED 모드 변경과 명령을 전달합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeCommand
        {
            Protocol::Light::Mode   mode;
            Protocol::Command       command;
        };
    }
}
```
- mode : [Protocol::Light::Mode](#Protocol_Light_Mode)
- command : [Protocol::Command](structs.md#Protocol_Command)


<br>
<br>


## <a name="Protocol_Light_ModeCommandIr">Protocol::Light::ModeCommandIr</a>
LED 모드 변경과 명령, IR 데이터 전송.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeCommandIr
        {
            Protocol::Light::Mode   mode;
            Protocol::Command       command;
            u32                     irData;
        };
    }
}
```
- mode : [Protocol::Light::Mode](#Protocol_Light_Mode)
- command : [Protocol::Command](structs.md#Protocol_Command)


<br>
<br>


## <a name="Protocol_Light_ModeColor">Protocol::Light::ModeColor</a>
LED 모드 변경. RGB 값을 직접 지정합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeColor
        {
            Protocol::Light::Mode   mode;
            Light::Color            color;
        };
    }
}
```
- mode : [Protocol::Light::Mode](#Protocol_Light_Mode)
- color : [Light::Color](#Light_Color)


<br>
<br>


## <a name="Protocol_Light_ModeColorCommand">Protocol::Light::ModeColorCommand</a>
LED 모드 변경 및 명령. RGB 값을 직접 지정합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeColorCommand
        {
            Protocol::Light::Mode   mode;
            Light::Color            color;
            Protocol::Command       command;
        };
    }
}
```
- mode : [Protocol::Light::Mode](#Protocol_Light_Mode)
- color : [Light::Color](#Light_Color)
- command : [Protocol::Command](structs.md#Protocol_Command)


<br>
<br>


## <a name="Protocol_Light_ModeColorCommandIr">Protocol::Light::ModeColorCommandIr</a>
LED 모드 변경 및 명령, IR 데이터 전송. RGB 값을 직접 지정합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeColorCommandIr
        {
            Protocol::Light::Mode   mode;
            Light::Color            color;
            Protocol::Command       command;
            u32                     irData;
        };
    }
}
```
- mode : [Protocol::Light::Mode](#Protocol_Light_Mode)
- color : [Light::Color](#Light_Color)
- command : [Protocol::Command](structs.md#Protocol_Command)

<br>
<br>


## <a name="Protocol_Light_ModeColors">Protocol::Light::ModeColors</a>
LED 모드 변경. 팔레트의 인덱스를 사용합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeColors
        {
            Protocol::Light::Mode   mode;
            u8                      colors;
        };
    }
}
```
- mode : [Protocol::Light::Mode](#Protocol_Light_Mode)
- colors : [Light::Colors::Type](#Light_Colors)


<br>
<br>


## <a name="Protocol_Light_ModeColorsCommand">Protocol::Light::ModeColorsCommand</a>
LED 모드 변경 및 명령. 팔레트의 인덱스를 사용합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeColorsCommand
        {
            Protocol::Light::Mode   mode;
            u8                      colors;
            Protocol::Command       command;
        };
    }
}
```
- mode : [Protocol::Light::Mode](#Protocol_Light_Mode)
- colors : [Light::Colors::Type](#Light_Colors)
- command : [Protocol::Command](structs.md#Protocol_Command)


<br>
<br>


## <a name="Protocol_Light_ModeColorsCommandIr">Protocol::Light::ModeColorsCommandIr</a>
LED 모드 변경 및 명령, IR 데이터 전송. 팔레트의 인덱스를 사용합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeColorsCommandIr
        {
            Protocol::Light::Mode   mode;
            u8                      colors;
            Protocol::Command       command;
            u32                     irData;
        };
    }
}
```
- mode : [Protocol::Light::Mode](#Protocol_Light_Mode)
- colors : [Light::Colors::Type](#Light_Colors)
- command : [Protocol::Command](structs.md#Protocol_Command)


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
            u8      event;      // LED 이벤트
            u16     interval;   // LED 이벤트 갱신 주기
            u8      repeat;     // LED 이벤트 반복 횟수
        };
    }
}
```
- event : [Light::Drone::Mode::Type](#Light_Drone_Mode), [Light::Controller::Mode::Type](#Light_Controller_Mode)
- interval : 0 ~ 65535
- repeat : 0 ~ 255


<br>
<br>


## <a name="Protocol_Light_EventCommand">Protocol::Light::EventCommand</a>
LED 이벤트 실행, 명령.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventCommand
        {
            Protocol::Light::Event  event;
            Protocol::Command       command;
        };
    }
}
```
- event : [Protocol::Light::Event](#Protocol_Light_Event)
- command : [Protocol::Command](structs.md#Protocol_Command)


<br>
<br>


## <a name="Protocol_Light_EventCommandIr">Protocol::Light::EventCommandIr</a>
LED 이벤트 실행, 명령, IR 데이터 전송.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventCommandIr
        {
            Protocol::Light::Event  event;
            Protocol::Command       command;
            u32                     irData;
        };
    }
}
```
- event : [Protocol::Light::Event](#Protocol_Light_Event)
- command : [Protocol::Command](structs.md#Protocol_Command)


<br>
<br>


## <a name="Protocol_Light_EventColor">Protocol::Light::EventColor</a>
LED 이벤트 실행. RGB 값을 직접 지정합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventColor
        {
            Protocol::Light::Event  event;
            Light::Color            color;
        };
    }
}
```
- event : [Protocol::Light::Event](#Protocol_Light_Event)
- color : [Light::Color](#Light_Color)


<br>
<br>


## <a name="Protocol_Light_EventColorCommand">Protocol::Light::EventColorCommand</a>
LED 이벤트 실행, 명령. RGB 값을 직접 지정합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventColorCommand
        {
            Protocol::Light::Event  event;
            Light::Color            color;
            Protocol::Command       command;
        };
    }
}
```
- event : [Protocol::Light::Event](#Protocol_Light_Event)
- color : [Light::Color](#Light_Color)
- command : [Protocol::Command](structs.md#Protocol_Command)


<br>
<br>


## <a name="Protocol_Light_EventColorCommandIr">Protocol::Light::EventColorCommandIr</a>
LED 이벤트 실행, 명령, IR 데이터 전송. RGB 값을 직접 지정합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventColorCommandIr
        {
            Protocol::Light::Event  event;
            Light::Color            color;
            Protocol::Command       command;
            u32                     irData;
        };
    }
}
```
- event : [Protocol::Light::Event](#Protocol_Light_Event)
- color : [Light::Color](#Light_Color)
- command : [Protocol::Command](structs.md#Protocol_Command)


<br>
<br>


## <a name="Protocol_Light_EventColors">Protocol::Light::EventColors</a>
LED 이벤트 실행. 팔레트의 인덱스를 사용합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventColors
        {
            Protocol::Light::Event  event;
            u8                      colors;
        };
    }
}
```
- event : [Protocol::Light::Event](#Protocol_Light_Event)
- colors : [Light::Colors::Type](#Light_Colors)


<br>
<br>


## <a name="Protocol_Light_EventColorsCommand">Protocol::Light::EventColorsCommand</a>
LED 이벤트 실행, 명령. 팔레트의 인덱스를 사용합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventColorsCommand
        {
            Protocol::Light::Event  event;
            u8                      colors;
            Protocol::Command       command;
        };
    }
}
```
- event : [Protocol::Light::Event](#Protocol_Light_Event)
- colors : [Light::Colors::Type](#Light_Colors)
- command : [Protocol::Command](structs.md#Protocol_Command)


<br>
<br>


## <a name="Protocol_Light_EventColorsCommandIr">Protocol::Light::EventColorsCommandIr</a>
LED 이벤트 실행, 명령, IR 데이터 전송. 팔레트의 인덱스를 사용합니다.
```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventColorsCommandIr
        {
            Protocol::Light::Event  event;
            u8                      colors;
            Protocol::Command       command;
            u32                     irData;
        };
    }
}
```
- event : [Protocol::Light::Event](#Protocol_Light_Event)
- colors : [Light::Colors::Type](#Light_Colors)
- command : [Protocol::Command](structs.md#Protocol_Command)


<br>
<br>


---

### PETRONE 2017

1. [Intro](intro.md)
2. [Typedef](typedef.md)
3. [DataType](datatype.md)
4. [Definitions](definitions.md)
5. [Structs](structs.md)
6. ***Structs - Light***

<br>

[Index](index.md)
