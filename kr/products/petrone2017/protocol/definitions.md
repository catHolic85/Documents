***PETRONE2017 / Protocol / Definitions***<br>
Modified : 2017.07.04

---

#### Petrone에서 사용하고 있는 기본 정의들을 소개합니다.

---

<br>

## <a name="Protocol_CommandType">Protocol::CommandType::Type</a>
CommandBase 구조체에서 commandType 변수에 사용합니다.

```cpp
namespace Protocol
{
    namespace CommandType
    {
        enum Type
        {
            None = 0,

            // 설정
            ModeVehicle = 0x10,             // Vehicle 동작 모드 전환

            // 제어
            Coordinate = 0x20,              // 방위 기준 변경
            Trim,                           // 트림 변경
            FlightEvent,                    // 비행 이벤트 실행
            DriveEvent,                     // 주행 이벤트 실행
            Stop,                           // 정지
            
            ClearTrim = 0x50,               // 트림 초기화
            ClearGyroBias,                  // 자이로 바이어스 리셋
            
            DataStorageWrite = 0x80,        // 변경사항이 있는 경우 데이터 저장소에 기록

            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="Protocol_DeviceType">Protocol::DeviceType::Type</a>
CommandBase 구조체에서 DeviceType 변수에 사용합니다.

```cpp
namespace Protocol
{
    namespace DeviceType
    {
        enum Type
        {
            None = 0,

            Drone = 0x30,           // 드론
            Controller,             // 조종기
            Link,                   // 링크 모듈
            Tester,                 // 테스터
            Monitor,                // 모니터
            Updater,                // 펌웨어 업데이트 도구
            Encrypter,              // 암호화 도구
            Scratch,                // 스크래치
            Entry,                  // 네이버 엔트리
            ByScratch,              // 바이스크래치

            EndOfType,

            Broadcasting = 0xFF
        };
    }
}
```

<br>
<br>

## <a name="Mode_Vehicle">Mode::Vehicle::Type</a>
페트론 동작 모드를 선택합니다.

```cpp
namespace Mode
{
    namespace Vehicle
    {
        enum Type
        {
            None = 0,
            
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

## <a name="Mode_System">Mode::System::Type</a>
시스템 동작 상태를 나타냅니다.

```cpp
namespace Mode
{
    namespace System
    {
        enum Type
        {
            None = 0,
            
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

## <a name="Mode_Flight">Mode::Flight::Type</a>
비행 제어기 동작 상태를 나타냅니다.

```cpp
namespace Mode
{
    namespace Flight
    {
        enum Type
        {
            None = 0,
            
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

## <a name="Mode_Drive">Mode::Drive::Type</a>
자동차 제어기 동작 상태를 나타냅니다.

```cpp
namespace Mode
{
    namespace Drive
    {
        enum Type
        {
            None = 0,
            
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

## <a name="Mode_Update">Mode::Update::Type</a>
업데이트 상태를 나타냅니다.

```cpp
namespace Mode
{
    namespace Update
    {
        enum Type
        {
            None,           // 

            Ready,          // 업데이트 가능 상태
            Update,         // 업데이트 중
            Complete,       // 업데이트 완료
                
            Faild,          // 업데이트 실패(업데이트 완료까지 갔으나 body의 CRC16이 일치하지 않는 경우 등)

            NotAvailable,   // 업데이트 불가능 상태(Debug 모드 등)

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
        None = 0,
        
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
페트론 조종 시 방향 기준을 선택합니다. World는 드론 외부 세계를 중심으로 좌표를 판단합니다. Local은 드론을 중심으로 좌표를 판단합니다.
조종기 상에서는 World를 'Headless ON', Local을 'Headless Off'로 표현하고 있습니다. 기본 설정은 Local입니다.

```cpp
namespace Coordinate
{
    enum Type
    {
        None = 0,
        
        World,              // 고정 좌표계(Headless)
        Local,              // 상대 좌표계(Normal)
        
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
        None = 0,

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


## <a name="Rotation">Rotation::Type</a>
모터 회전 방향

```cpp
namespace Rotation
{
    enum Type
    {
        None = 0,
        
        Clockwise,				// 시계 방향
        Counterclockwise,		// 반시계 방향
        
        EndOfType
    };
}
```

<br>
<br>


## <a name="Motor_Part">Motor::Part::Type</a>
모터 번호

```cpp
namespace Rotation
{
    namespace Part
    {
        enum Type
        {
            M1,		// Front Left
            M2,		// Front Right
            M3,		// Rear Right
            M4,		// Rear Left
            
            EndOfPart,
            
            All
        };
    }
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


## <a name="Joystick_Direction">Joystick::Direction::Type</a>
조이스틱 방향

```cpp
namespace Joystick
{
    // 조이스틱 방향
    namespace Direction
    {
        enum Type
        {
            None    = 0,        // 정의하지 않은 영역(무시함)
            
            VT      = 0x10,     //   위(세로)
            VM      = 0x20,     // 중앙(세로)
            VB      = 0x40,     // 아래(세로)
            
            HL      = 0x01,     //   왼쪽(가로)
            HM      = 0x02,     //   중앙(가로)
            HR      = 0x04,     // 오른쪽(가로)
            
            TL = 0x11,  TM = 0x12,  TR = 0x14,
            ML = 0x21,  CN = 0x22,  MR = 0x24,
            BL = 0x41,  BM = 0x42,  BR = 0x44
        };
    }
}
```

<br>
<br>


## <a name="Joystick_Event">Joystick::Event::Type</a>
조이스틱 방향

```cpp
namespace Joystick
{
    // 조이스틱 방향
    namespace Event
    {
        enum Type
        {
            None    = 0,        // 이벤트 없음
            
            In,                 // 특정 영역에 진입
            Stay,               // 특정 영역에서 상태 유지
            Out,                // 특정 영역에서 벗어남
            
            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="Buzzer_Mode">Buzzer::Mode::Type</a>
버저 모드

```cpp
namespace Buzzer
{
    namespace Mode
    {
        enum Type
        {
            Stop                = 0,    // 정지(Mode에서의 Stop은 통신에서 받았을 때 Buzzer를 끄는 용도로 사용, set으로만 호출)

            MuteInstantally     = 1,    // 묵음 즉시 적용
            MuteContinually     = 2,    // 묵음 예약

            ScaleInstantally    = 3,    // 음계 즉시 적용
            ScaleContinually    = 4,    // 음계 예약

            HzInstantally       = 5,    // 주파수 즉시 적용
            HzContinually       = 6,    // 주파수 예약

            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="Buzzer_Scale">Buzzer::Scale::Type</a>
버저 음계

```cpp
namespace Buzzer
{
    namespace Scale
    {
        enum Type
        {
            C1, CS1, D1, DS1, E1, F1, FS1, G1, GS1, A1, AS1, B1,
            C2, CS2, D2, DS2, E2, F2, FS2, G2, GS2, A2, AS2, B2,
            C3, CS3, D3, DS3, E3, F3, FS3, G3, GS3, A3, AS3, B3,
            C4, CS4, D4, DS4, E4, F4, FS4, G4, GS4, A4, AS4, B4,
            
            C5, CS5, D5, DS5, E5, F5, FS5, G5, GS5, A5, AS5, B5,
            C6, CS6, D6, DS6, E6, F6, FS6, G6, GS6, A6, AS6, B6,
            C7, CS7, D7, DS7, E7, F7, FS7, G7, GS7, A7, AS7, B7,
            C8, CS8, D8, DS8, E8, F8, FS8, G8, GS8, A8, AS8, B8,
        
            EndOfType,
            
            Mute    = 0xEE,     // 묵음
            Fin     = 0xFF      // 악보의 끝
        };
    }
}
```

<br>
<br>


## <a name="Vibrator_Mode">Vibrator::Mode::Type</a>
진동 모드

```cpp
namespace Vibrator
{
    namespace Mode
    {
        enum Type
        {
            Stop            = 0,    // 정지
            
            Instantally     = 1,    // 즉시 적용
            Continually     = 2,    // 예약
            
            EndOfType
        };
    }
}
```

<br>
<br>


<br>


---

### PETRONE 2017

1. [Intro](intro.md)
2. [Typedef](typedef.md)
3. [DataType](datatype.md)
4. ***Definitions***
5. [Structs](structs.md)
6. [Structs - Light](structs_light.md)

<br>

[Index](index.md)
