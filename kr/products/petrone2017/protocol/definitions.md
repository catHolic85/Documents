***PETRONE2017 / Protocol / Definitions***<br>
Modified : 2017.05.02

---

#### Petrone에서 사용하고 있는 기본 정의들을 소개합니다.

---

<br>

## <a name="CommandType">Protocol::CommandType::Type</a>
CommandBase 구조체에서 commandType 변수에 사용합니다.

```cpp
namespace Protocol
{
    namespace CommandType
    {
        enum Type
        {
            None = 0,                       // 이벤트 없음

            // 설정
            ModeVehicle = 0x10,             // Vehicle 동작 모드 전환

            // 제어
            Coordinate = 0x20,              // 방위 기준 변경
            Trim,                           // 트림 변경
            FlightEvent,                    // 비행 이벤트 실행
            DriveEvent,                     // 주행 이벤트 실행
            Stop,                           // 정지
            
            ClearTrim = 0x50,               // 트림 초기화
            GyroBiasAndTrimReset,           // 자이로 바이어스와 트림 리셋
            
            UserInterfacePreset = 0x80,     // 사용자 인터페이스 설정
            DataStorageWrite,               // 변경사항이 있는 경우 데이터 저장소에 기록

            // 관리자
            ClearCounter = 0xA0,            // 카운터 클리어(관리자 권한을 획득했을 경우에만 동작)

            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="Mode::Vehicle">Mode::Vehicle::Type</a>
페트론 동작 모드를 선택합니다.

```cpp
namespace Mode
{
    namespace Vehicle
    {
        enum Type
        {
            None = 0,           // 없음
            
            Flight = 0x10,      // 비행(가드 포함)
            FlightNoGuard,      // 비행(가드 없음)
            FlightFPV,          // 비행(FPV)
            
            Drive = 0x20,       // 주행
            DriveFPV,           // 주행(FPV)
            
            Test = 0x30,        // 테스트
            
            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="Mode::System">Mode::System::Type</a>
시스템 동작 상태를 나타냅니다.

```cpp
namespace Mode
{
    namespace System
    {
        enum Type
        {
            None = 0,           // 없음
            
            Boot,               // 부팅
            
            Start,              // 시작 코드 실행
            
            Running,            // 메인 코드 동작
                            
            ReadyToReset,       // 리셋 대기(1초 뒤 리셋)
                
            Error,              // 오류
                    
            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="Mode::Flight">Mode::Flight::Type</a>
비행 제어기 동작 상태를 나타냅니다.

```cpp
namespace Mode
{
    namespace Flight
    {
        enum Type
        {
            None = 0,           // 없음
            
            Ready = 0x10,       // 준비
            
            TakeOff,            // 이륙 (Flight로 자동전환)
            Flight,             // 비행
            Landing,            // 착륙
            Flip,               // 회전         
            Reverse,            // 뒤집기
            
            Stop = 0x20,        // 강제 정지
            
            Accident = 0x30,    // 사고 (Ready로 자동전환)
            Error,              // 오류
            
            Test = 0x40,        // 테스트 모드
                        
            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="Mode::Drive">Mode::Drive::Type</a>
자동차 제어기 동작 상태를 나타냅니다.

```cpp
namespace Mode
{
    namespace Drive
    {
        enum Type
        {
            None = 0,           // 없음
            
            Ready = 0x10,       // 준비
            
            Start,              // 출발
            Drive,              // 주행
            
            Stop = 0x20,        // 강제 정지
            
            Accident = 0x30,    // 사고 (Ready로 자동전환)
            Error,              // 오류
            
            Test = 0x40,        // 테스트 모드

            EndOfType
        };
    }
    
}
```

<br>
<br>

## <a name="SensorOrientation">SensorOrientation::Type</a>
센서 방향을 나타냅니다.
```cpp
namespace SensorOrientation
{
    enum Type
    {
        None = 0,           // 없음
        
        Normal,             // 정상
        ReverseStart,       // 뒤집히기 시작
        Reversed,           // 뒤집힘
        
        EndOfType
    };
}
```

<br>
<br>

## <a name="Direction">Direction::Type</a>
방향을 나타냅니다.
```cpp
namespace Direction
{
    enum Type
    {
        None = 0,

        Left,
        Front,
        Right,
        Rear,
        
        Top,
        Bottom,
        
        EndOfType
    };
}
```

<br>
<br>

## <a name="Coordinate">Coordinate::Type</a>
페트론 조종기 방향 기준을 선택합니다. World는 앱솔루트 모드입니다. 드론 외부 세계를 중심으로 좌표를 판단합니다. Local은 일반모드입니다. 드론을 중심으로 좌표를 판단합니다.

```cpp
namespace Coordinate
{
    enum Type
    {
        None = 0,           // 없음
        
        World,              // 고정 좌표계(Absolute)
        Local,              // 상대 좌표계(일반)
        
        EndOfType
    };
}
```

<br>
<br>

## <a name="Trim">Trim::Type</a>
페트론이 한쪽 방향으로 흐를 때 반대 방향을 입력하여 호버링을 할 수 있게 조정합니다. 한 번 전송할 때마다 일정하게 값이 변합니다.

```cpp
namespace Trim
{
    enum Type
    {
        None = 0,           // 없음

        RollIncrease,       // Roll 증가
        RollDecrease,       // Roll 감소                
        PitchIncrease,      // Pitch 증가
        PitchDecrease,      // Pitch 감소               
        YawIncrease,        // Yaw 증가
        YawDecrease,        // Yaw 감소             
        ThrottleIncrease,   // Throttle 증가
        ThrottleDecrease,   // Throttle 감소
        
        Reset,              // 전체 트림 리셋
        
        EndOfType
    };
}
```

<br>
<br>

## <a name="FlightEvent">FlightEvent::Type</a>
페트론 비행 이벤트를 실행합니다.

```cpp
namespace FlightEvent
{
    enum Type
    {
        None = 0,               // 없음
        
        Stop = 0x10,            // 정지
        TakeOff,                // 이륙
        Landing,                // 착륙
        
        Reverse,                // 뒤집기
        
        FlipFront,              // 회전
        FlipRear,               // 회전
        FlipLeft,               // 회전
        FlipRight,              // 회전
        
        Shot,                   // 미사일 쏠때 움직임
        UnderAttack,            // 미사일 맞을때 움직임
        
        ResetHeading = 0xA0,    // 헤딩 리셋(앱솔루트 모드 일 때 현재 heading을 0도로 변경)
        
        EndOfType   
    };
}
```

<br>
<br>

## <a name="Light::Drone::Mode">Light::Drone::Mode::Type</a>
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
                EyeManual,              ///< 수동 제어
                EyeHold,                ///< 지정한 색상을 계속 켬
                EyeFlicker,             ///< 깜빡임         
                EyeFlickerDouble,       ///< 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)            
                EyeDimming,             ///< 밝기 제어하여 천천히 깜빡임
                
                ArmNone = 0x40,         
                ArmManual,              ///< 수동 제어
                ArmHold,                ///< 지정한 색상을 계속 켬
                ArmFlicker,             ///< 깜빡임         
                ArmFlickerDouble,       ///< 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)            
                ArmDimming,             ///< 밝기 제어하여 천천히 깜빡임
                
                EndOfType
            };
        }
    }
}
```

<br>
<br>

## <a name="Light::Controller::Mode">Light::Controller::Mode::Type</a>
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

## <a name="LightColors">Light::Colors::Type</a>
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

---

### PETRONE

1. [Intro](intro.md)
2. [Typedef](typedef.md)
3. [DataType](datatype.md)
4. ***Definitions***
5. [Base Structs](base_structs.md)
6. [Structs](structs.md)
7. [Structs - Light](structs_light.md)

[Home](../../README.md)
