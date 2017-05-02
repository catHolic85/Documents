***PETRONE / BLE / Protocol / DataType***<br>
Modified : 2017.04.05

---

#### 데이터 타입을 소개합니다.

---

<br>

## <a name="DataType">Protocol::DataType::Type</a>
데이터 타입

```cpp
namespace Protocol
{
    namespace DataType
    {
        enum Type
        {
            None                        = 0x00,     ///< 없음
            Ping                        = 0x01,     ///< 통신 확인
            Ack                         = 0x02,     ///< 데이터 수신에 대한 응답
            Error                       = 0x03,     ///< 오류(reserve, 비트 플래그는 추후에 지정)
            Request                     = 0x04,     ///< 지정한 타입의 데이터 요청
            Message                     = 0x05,     ///< 문자열 데이터
            Reserved_1                  = 0x06,     ///< 예약
            Reserved_2                  = 0x07,     ///< 예약
            Monitor                     = 0x08,     ///< 디버깅용 값 배열 전송. 첫번째 바이트에 타입, 두 번째 바이트에 페이지 지정(수신 받는 데이터의 저장 경로 구분)
            SystemCounter               = 0x09,     ///< 시스템 카운터
            Information                 = 0x0A,     ///< 펌웨어 및 장치 정보
            UpdateLocation              = 0x0B,     ///< 펌웨어 업데이트 위치 정정
            Update                      = 0x0C,     ///< 펌웨어 업데이트
            Encrypt                     = 0x0D,     ///< 펌웨어 암호화
            Address                     = 0x0E,     ///< 장치 주소
            Administrator               = 0x0F,     ///< 관리자 권한 획득
            Control                     = 0x10,     ///< 조종 명령
    
            Command                     = 0x11,     ///< 명령

            // Light
            LightManual                 = 0x20,     ///< LED 수동 제어

            LightMode                   = 0x21,     ///< LED 모드 지정
            LightModeCommand            = 0x22,     ///< LED 모드, 커맨드
            LightModeCommandIr          = 0x23,     ///< LED 모드, 커맨드, IR 데이터 송신
            LightModeColor              = 0x24,     ///< LED 모드 3색 직접 지정
            LightModeColorCommand       = 0x25,     ///< LED 모드 3색 직접 지정, 커맨드
            LightModeColorCommandIr     = 0x26,     ///< LED 모드 3색 직접 지정, 커맨드, IR 데이터 송신
            LightModeColors             = 0x27,     ///< LED 모드 팔레트의 색상으로 지정
            LightModeColorsCommand      = 0x28,     ///< LED 모드 팔레트의 색상으로 지정, 커맨드
            LightModeColorsCommandIr    = 0x29,     ///< LED 모드 팔레트의 색상으로 지정, 커맨드, IR 데이터 송신

            LightEvent                  = 0x2A,     ///< LED 이벤트
            LightEventCommand           = 0x2B,     ///< LED 이벤트, 커맨드
            LightEventCommandIr         = 0x2C,     ///< LED 이벤트, 커맨드, IR 데이터 송신
            LightEventColor             = 0x2D,     ///< LED 이벤트 3색 직접 지정
            LightEventColorCommand      = 0x2E,     ///< LED 이벤트 3색 직접 지정, 커맨드
            LightEventColorCommandIr    = 0x2F,     ///< LED 이벤트 3색 직접 지정, 커맨드, IR 데이터 송신
            LightEventColors            = 0x30,     ///< LED 이벤트 팔레트의 색상으로 지정
            LightEventColorsCommand     = 0x31,     ///< LED 이벤트 팔레트의 색상으로 지정, 커맨드
            LightEventColorsCommandIr   = 0x32,     ///< LED 이벤트 팔레트의 색상으로 지정, 커맨드, IR 데이터 송신

            LightModeDefaultColor       = 0x33,     ///< LED 초기 모드 3색 직접 지정
            
            // 상태, 설정
            State                       = 0x40,     ///< 드론의 상태(비행 모드, 방위기준, 배터리량)
            Attitude,                               ///< 드론의 자세(Angle)(Vector)
            GyroBias,                               ///< 자이로 바이어스 값(Vector)
            TrimAll,                                ///< 전체 트림
            TrimFlight,                             ///< 비행 트림
            TrimDrive,                              ///< 주행 트림
            UserInterface,                          ///< 사용자 인터페이스 설정
    
            // Sensor raw data      
            Imu                         = 0x50,     ///< IMU Raw
            Pressure,                               ///< 압력 센서 데이터
            Battery,                                ///< 배터리
            Range,                                  ///< 거리 센서
            ImageFlow,                              ///< ImageFlow
            CameraImage,                            ///< CameraImage
                    
            // Input        
            Button                      = 0x70,     ///< 버튼 입력
            Joystick,                               ///< 조이스틱 입력
                    
            // Devices      
            Motor                       = 0x80,     ///< 모터 제어 및 현재 제어값 확인
            MotorSingle,                            ///< 한 개의 모터 제어
            IrMessage,                              ///< IR 데이터 송수신
            Buzzer,                                 ///< 부저 제어
            Vibrator,                               ///< 진동 제어
    
            // 카운트       
            CountFlight                 = 0x90,     ///< 비행 관련 카운트
            CountDrive,                             ///< 주행 관련 카운트
                    
            // RF       
            Pairing                     = 0xA0,     ///< 페어링
            Rssi,                                   ///< RSSI

            EndOfType
        };
    }
}
```


<br>

---

### PETRONE

1. [Intro](intro.md)
2. [Typedef](typedef.md)
3. ***DataType***
4. [Definitions](definitions.md)
5. [Base Structs](base_structs.md)
6. [Structs](structs.md)
7. [Structs - Light](structs_light.md)


<br>

[Home](../../README.md)

