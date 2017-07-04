***PETRONE2017 / Protocol / Structs***<br>
Modified : 2017.07.04

---

#### 데이터 송수신 시에 사용하는 구조체들을 소개합니다.

---


<br>


## <a name="Protocol_Header">Protocol::Header</a>
데이터 송수신 시에 사용하는 헤더입니다.
```cpp
namespace Protocol
{
    struct Header
    {
        u8      dataType;       // 데이터의 형식
        u8      length;         // 데이터의 길이
        u8      from;           // 데이터를 전송하는 장치의 DeviceType
        u8      to;             // 데이터를 수신 받는 장치의 DeviceType
    };
}
```
- dataType : [Protocol::DataType::Type](datatype.md#Protocol_DataType)
- from, to : [Protocol::DeviceType::Type](definitions.md#Protocol_DeviceType)


<br>
<br>


## <a name="Protocol_Ping">Protocol::Ping</a>
특정 장치가 존재하는지를 확인할 때 사용합니다. 응답은 Ack를 받습니다.
```cpp
namespace Protocol
{
    struct Ping
    {
        u64     systemTime;   // Ping을 전송하는 장치의 시각
    };
}
```


<br>
<br>


## <a name="Protocol_Ack">Protocol::Ack</a>
특정한 데이터를 요청하지 않은 경우에 Ack를 응답으로 전송합니다. 수신 받은 데이터의 crc16을 포함하여 돌려보내기 때문에 데이터를 전송한 측에서 정상적으로 데이터를 전송했는지 판별하는데 사용합니다.
```cpp
namespace Protocol
{
    struct Ack
    {
        u64     systemTime;     // 수신 받은 시간
        u8      dataType;       // 수신 받은 데이터 타입
        u16     crc16;          // 수신 받은 데이터의 crc16
    };
}
```
- dataType : [Protocol::DataType::Type](datatype.md#Protocol_DataType)


<br>
<br>


## <a name="Protocol_Request">Protocol::Request</a>
PETRONE에 데이터를 요청할 때 사용합니다.
```cpp
namespace Protocol
{
    struct Request
    {
        u8   dataType;          // 요청할 데이터 타입
    };
}
```
- dataType : [Protocol::DataType::Type](datatype.md#Protocol_DataType)


<br>
<br>


## <a name="Protocol_Information">Protocol::Information</a>
드론 또는 조종기의 펌웨어 정보를 전달할 때 사용합니다.
```cpp
namespace Protocol
{
    struct Information
    {
        u8      modeUpdate;     // 현재 업데이트 모드

        u32     deviceType;     // 장치 타입
        u32     imageVersion;   // 현재 펌웨어의 버젼

        u16     year;           // 빌드 년
        u8      month;          // 빌드 월
        u8      day;            // 빌드 일
    };
}
```
- modeUpdate : [Mode::Update::Type](definitions.md#Mode_Update)
- deviceType : [Protocol::DeviceType::Type](definitions.md#Protocol_DeviceType)
- imageVersion : [Protocol::Version](#Protocol_Version)


<br>
<br>


## <a name="Protocol_Version">Protocol::Version</a>
드론 또는 조종기의 펌웨어 버젼을 의미합니다.
```cpp
namespace Protocol
{
    union Version
    {
        struct
        {
            u8                      major;      // Major Number
            u8                      minor;      // Minor Number
            DevelopmentStage::Type  stage:2;    // Development stage(0~3)
            u16                     build:14;   // Build Number(0~16383)
        };

        u32 v;
    };
}
```
- stage : [Protocol::DevelopmentStage::Type](#Protocol_DevelopmentStage)


<br>
<br>


## <a name="Protocol_DevelopmentStage">Protocol::DevelopmentStage::Type</a>
펌웨어 개발 단계를 나타냅니다.
```cpp
namespace Protocol
{
    namespace DevelopmentStage
    {
        enum Type
        {
            Alpha,
            Beta,
            ReleaseCandidate,
            Release
        };
    }
}
```


<br>
<br>


## <a name="Control_Double8">Control::Double8</a>
PETRONE 자동차 조종 시에 사용합니다. 드론 모드일 때 이 명령을 전송하면 무시합니다.
```cpp
namespace Control
{
    struct Double8
    {
        s8      wheel;      // wheel
        s8      accel;      // accel
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


## <a name="Control_Quad8">Control::Quad8</a>
PETRONE 드론 및 자동차 조종 시에 사용합니다.
```cpp
namespace Control
{
    struct Quad8
    {
        s8      roll;       // roll
        s8      pitch;      // pitch
        s8      yaw;        // yaw
        s8      throttle;   // throttle
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


## <a name="Protocol_Command">Protocol::Command</a>
PETRONE의 설정을 변경하거나 데이터를 요청할 때 사용합니다.
```cpp
namespace Protocol
{
    struct Command
    {
        u8 commandType;   // 명령 타입
        u8 option;        // 명령에 대한 옵션
    };
}
```
- commandType : [Protocol::CommandType::Type](definitions.md#Protocol_CommandType)
- option : [Mode::Vehicle::Type](definitions.md#Mode_Vehicle), [Coordinate::Type](definitions.md#Coordinate), [System::Trim::Type](definitions.md#Trim),  [System::FlightEvent::Type](definitions.md#FlightEvent), [Protocol::DataType::Type](datatype.md#Protocol_DataType), [UserInterface::Preset::Type](definitions.md#UserInterface_Preset)


<br>
<br>


## <a name="Protocol_Address">Protocol::Address</a>
장치 주소를 반환합니다.
```cpp
namespace Protocol
{
    struct Address
    {
        u8   address[8];
    };
}
```

<br>
<br>


## <a name="Protocol_State">Protocol::State</a>
PETRONE의 현재 상태값을 반환합니다.
```cpp
namespace Protocol
{
    struct State
    {
        u8          modeVehicle;        // 동작 모드
        
        u8          modeSystem;         // 시스템 모드
        u8          modeFlight;         // 비행 모드
        u8          modeDrive;          // 주행 모드
        
        u8          sensorOrientation;  // 센서 방향
        u8          coordinate;         // 방위
        u8          battery;            // 배터리량(0 ~ 100%)
    };
}
```
- modeVehicle : [Mode::Vehicle::Type](definitions.md#Mode_Vehicle)
- modeSystem : [Mode::System::Type](definitions.md#Mode_System)
- modeFlight : [Mode::Flight::Type](definitions.md#Mode_Flight)
- modeDrive : [Mode::Drive::Type](definitions.md#Mode_Drive)
- sensorOrientation : [SensorOrientation::Type](definitions.md#SensorOrientation)
- coordinate : [Coordinate::Type](definitions.md#Coordinate)


<br>
<br>


## <a name="Protocol_Attitude">Protocol::Attitude</a>
자세값을 반환합니다.
```cpp
namespace Protocol
{
    struct Attitude
    {
        s16          roll;         // Roll
        s16          pitch;        // Pitch
        s16          yaw;          // Yaw
    };
}
```

드론의 자세를 확인할 때의 사용 범위는 다음과 같습니다.

|이름      | 형식 | 범위        | 설명                                |
|:--------:|:----:|:-----------:|:-----------------------------------:|
| roll     | s16  | -180 ~ 180  | 좌우 기울기 각도                    |
| pitch    | s16  | -180 ~ 180  | 전후 기울기 각도                    |
| yaw      | s16  |    0 ~ 360  | 중력 방향을 축으로 회전할 때의 각도 |


자이로 센서 데이터를 확인할 때의 사용 범위는 다음과 같습니다.

|이름      | 형식 | 범위            |
|:--------:|:----:|:---------------:|
| roll     | s16  | -32768 ~ 32767  |
| pitch    | s16  | -32768 ~ 32767  |
| yaw      | s16  | -32768 ~ 32767  |


<br>
<br>


## <a name="Protocol_AccelBias">Protocol::AccelBias</a>
자이로 바이어스 값을 반환합니다.
```cpp
namespace Protocol
{
    struct AccelBias
    {
        s16          x;         // X
        s16          y;         // Y
        s16          z;         // Z
    };
}
```

<br>
<br>


## <a name="Protocol_GyroBias">Protocol::GyroBias</a>
자이로 바이어스 값을 반환합니다.
```cpp
namespace Protocol
{
    struct GyroBias
    {
        s16          roll;         // Roll
        s16          pitch;        // Pitch
        s16          yaw;          // Yaw
    };
}
```

<br>
<br>


## <a name="Protocol_TrimFlight">Protocol::TrimFlight</a>
비행 Trim을 조정할 때 사용합니다.
```cpp
namespace Protocol
{
    struct TrimFlight
    {
        s16          roll;         // Roll
        s16          pitch;        // Pitch
        s16          yaw;          // Yaw
        s16          throttle;     // Throttle
    };
}
```

<br>
<br>


## <a name="Protocol_TrimDrive">Protocol::TrimDrive</a>
자동차 Trim을 조정할 때 사용합니다.
```cpp
namespace Protocol
{
    struct TrimDrive
    {
        s16          wheel;         // Wheel
        s16          accel;         // Accel
    };
}
```

<br>
<br>


## <a name="Protocol_TrimAll">Protocol::TrimAll</a>
비행 및 자동차 Trim을 한 번에 조정할 때 사용합니다.
```cpp
namespace Protocol
{
    struct TrimAll
    {
        TrimFlight   flight;
        TrimDrive    drive;
    };
}
```
- flight : [Protocol::TrimFlight](#Protocol_TrimFlight)
- drive : [Protocol::TrimDrive](#Protocol_TrimDrive)


<br>
<br>


## <a name="Protocol_CountFlight">Protocol::CountFlight</a>
비행과 관련된 저장값을 읽을 때 사용합니다.
```cpp
namespace Protocol
{
    struct CountFlight
    {
        u64     timeFlight;             // 비행 시간
        
        u16     countTakeOff;           // 이륙 횟수
        u16     countLanding;           // 착륙 횟수
        u16     countAccident;          // 충돌 횟수
    };
}
```

<br>
<br>


## <a name="Protocol_CountDrive">Protocol::CountDrive</a>
주행과 관련된 저장값을 읽을 때 사용합니다.
```cpp
namespace Protocol
{
    struct CountDrive
    {
        u64     timeDrive;              // 주행 시간
        
        u16     countAccident;          // 충돌 횟수
    };
}
```
countAccident 변수는 주행 중 충돌을 카운트 하기 위해 만든 변수이나 실제 주행 시 노면이 고르지 못할 때의 충격에 의해서도 카운트가 증가하는 문제가 있습니다. 현재로는 크게 의미가 없는 값으로 생각하시면 됩니다.


<br>
<br>


## <a name="Protocol_IrMessage">Protocol::IrMessage</a>
IR 데이터를 전송하는데 사용하거나, PETRONE이 IR 데이터를 수신 받았을 때 외부 장치로 전송하는 데이터입니다.
```cpp
namespace Protocol
{
    struct IrMessage
    {
        u8      direction;               // 수신 받은 방향
        u32     irData;                  // IR 메세지
    };
}
```
- direction : [System::Direction::Type](definitions.md#Direction)


<br>
<br>


## <a name="Protocol_Imu">Protocol::Imu</a>
자이로 센서에서 출력한 값과 내부에서 계산한 드론의 자세 값을 반환합니다.
```cpp
namespace Protocol
{
    struct Imu
    {
        s16     accX;
        s16     accY;
        s16     accZ;
        s16     gyroRoll;
        s16     gyroPitch;
        s16     gyroYaw;
        s16     angleRoll;
        s16     anglePitch;
        s16     angleYaw;
    };
}
```


<br>
<br>


## <a name="Protocol_Battery">Protocol::Battery</a>
배터리 설정 값을 반환합니다.
```cpp
namespace Protocol
{
    struct Battery
    {
        f32     gradient;
        f32     yIntercept;
        f32     adjustGradient;
        f32     adjustYIntercept;
        u8      flagBatteryCalibration;

        s16     batteryRaw;
        f32     batteryPercent;

        f32     voltage;
    };
}
```


<br>
<br>


## <a name="Protocol_Pressure">Protocol::Pressure</a>
압력 센서의 출력값을 반환합니다.
```cpp
namespace Protocol
{
    struct Pressure
    {
        f32     temperature;
        f32     pressure;
    };
}
```
- temperature 출력 값의 단위는 Celsius(°C)입니다.
- pressure 출력 값의 단위는 미터(m)입니다.

<br>
<br>


## <a name="Protocol_ImageFlow">Protocol::ImageFlow</a>
자세 제어에 사용하는 영상 데이터 처리 값입니다.
```cpp
namespace Protocol
{
    struct ImageFlow
    {
        s32     positionX;
        s32     positionY;
    };
}
```
- positionX, positionY 출력 값의 단위는 미터(m)입니다.


<br>
<br>


## <a name="Protocol_Button">Protocol::Button</a>
버튼 입력 값입니다.
```cpp
namespace Protocol
{
    struct Button
    {
        u16     button;
        u8      event;
    };
}
```

<br>
<br>


## <a name="Protocol_Motor">Protocol::Motor</a>
모터를 동작시키거나, 현재 모터에 입력된 값을 확인할 때 사용합니다.
주로 모터 4개를 동시에 작동하거나 동작을 확인하는 데 사용합니다. 이 때에는 아래의 구조체를 배열로 사용합니다.
```cpp
namespace Protocol
{
    struct Motor
    {
        u8      rotation;
        s16     value;
    };
}
```
- rotation : [Rotation::Type](definitions.md#Rotation)
- value : 0 ~ 4096


<br>
<br>

## <a name="Protocol_MotorSingle">Protocol::MotorSingle</a>
하나의 모터를 동작시키거나, 현재 모터에 입력된 값을 확인할 때 사용합니다.
```cpp
namespace Protocol
{
    struct MotorSingle
    {
        u8      target;
        u8      rotation;
        s16     value;
    };
}
```
- target : [Motor::Part::Type](definitions.md#Motor_Part)
- rotation : [Rotation::Type](definitions.md#Rotation)
- value : 0 ~ 4096


<br>
<br>


## <a name="Protocol_Range">Protocol::Range</a>
거리 센서에서 입력받은 거리 값을 반환합니다. 앞으로 거리센서 모듈이 추가될 예정이어서 6방향에 대한 값을 모두 담는 구조체를 사용합니다.
```cpp
namespace Protocol
{
    struct Range
    {
        f32     left;
        f32     front;
        f32     right;
        f32     rear;
        f32     top;
        f32     bottom;
    };
}
```
- 모든 출력 값의 단위는 미터(m)입니다.


<br>
<br>


## <a name="Protocol_JoystickBlock">Protocol::JoystickBlock</a>
조종기 조이스틱 한 축의 입력 값입니다.
```cpp
namespace Protocol
{
    struct JoystickBlock
    {
        s8      x;
        s8      y;
        u8      direction;
        u8      event;
    };
}
```
- x : 조이스틱 가로축, -100 ~ 100
- y : 조이스틱 세로축, -100 ~ 100
- direction : [Joystick::Direction::Type](definitions.md#Joystick_Direction)
- event : [Joystick::Event::Type](definitions.md#Joystick_Event)


<br>
<br>


## <a name="Protocol_Joystick">Protocol::Joystick</a>
조종기 좌우 조이스틱의 입력 값입니다.
```cpp
namespace Protocol
{
    struct Joystick
    {
        Protocol::JoystickBlock     left;
        Protocol::JoystickBlock     right;
    };
}
```
- left : [Protocol::JoystickBlock](#Protocol_JoystickBlock)
- right : [Protocol::JoystickBlock](#Protocol_JoystickBlock)


<br>
<br>


## <a name="Protocol_Buzzer">Protocol::Buzzer</a>
조이스틱 버저 소리를 낼 때 사용합니다.
```cpp
namespace Protocol
{
    struct Buzzer
    {
        u8      mode;   // 버저 작동 모드
        u16     value;  // 옥타브 또는 주파수
        u16     time;   // 연주 시간(ms)
    };
}
```
- mode : [Buzzer::Mode::Type](definitions.md#Buzzer_Mode)
- value : mode에서 ScaleInstantally 또는 ScaleContinually를 선택한 경우 [Buzzer::Scale::Type](definitions.md#Buzzer_Scale), HzInstantally 또는 HzContinually를 선택한 경우 0 ~ 8000(Hz)
- time : 0 ~ 65535(ms)


<br>
<br>


## <a name="Protocol_Vibrator">Protocol::Vibrator</a>
조이스틱 진동 모터를 제어할 때 사용합니다.
```cpp
namespace Protocol
{
    struct Vibrator
    {
        u8      mode;   // 모드(0은 set, 1은 reserve)
        u16     on;     // 진동을 켠 시간(ms)
        u16     off;    // 진동을 끈 시간(ms)
        u16     total;  // 전체 진행 시간(ms)
    };
}
```
- mode : [Vibrator::Mode::Type](definitions.md#Vibrator_Mode)
- on : 0 ~ 65535(ms)
- off : 0 ~ 65535(ms)
- total : 0 ~ 65535(ms)


<br>
<br>


## <a name="Protocol_Pairing">Protocol::Pairing</a>
장치 페어링 시 사용합니다.
```cpp
namespace Protocol
{
    struct Pairing
    {
        u16     addressLocal;
        u16     addressRemote;
        u8      channel;
    };
}
```
- addressLocal : 0x0001 ~ 0xFFFE, 0x0000은 사용하지 않음, 0xFFFF는 Broadcasting에 사용
- addressRemote : 0x0001 ~ 0xFFFE, 0x0000은 사용하지 않음, 0xFFFF는 Broadcasting에 사용
- channel : 0 ~ 255(미확정)

<br>

---

### PETRONE 2017

1. [Intro](intro.md)
2. [Typedef](typedef.md)
3. [DataType](datatype.md)
4. [Definitions](definitions.md)
5. ***Structs***
6. [Structs - Light](structs_light.md)

<br>

[Index](index.md)
