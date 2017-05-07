***PETRONE2017 / Protocol / DataType***<br>
Modified : 2017.05.02

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
            None                        = 0x00,     // 없음
            Ping                        = 0x01,     // 통신 확인
            Ack                         = 0x02,     // 데이터 수신에 대한 응답
            Error                       = 0x03,     // 오류(reserve, 비트 플래그는 추후에 지정)
            Request                     = 0x04,     // 지정한 타입의 데이터 요청
            Message                     = 0x05,     // 문자열 데이터
            Reserved_1                  = 0x06,     // 예약
            Reserved_2                  = 0x07,     // 예약
            Monitor                     = 0x08,     // 디버깅용 값 배열 전송. 첫번째 바이트에 타입, 두 번째 바이트에 페이지 지정(수신 받는 데이터의 저장 경로 구분)
            SystemCounter               = 0x09,     // 시스템 카운터
            Information                 = 0x0A,     // 펌웨어 및 장치 정보
            UpdateLocation              = 0x0B,     // 펌웨어 업데이트 위치 정정
            Update                      = 0x0C,     // 펌웨어 업데이트
            Encrypt                     = 0x0D,     // 펌웨어 암호화
            Address                     = 0x0E,     // 장치 주소
            Administrator               = 0x0F,     // 관리자 권한 획득
            Control                     = 0x10,     // 조종 명령
    
            Command                     = 0x11,     // 명령

            // Light
            LightManual                 = 0x20,     // LED 수동 제어

            LightMode                   = 0x21,     // LED 모드 지정
            LightModeCommand            = 0x22,     // LED 모드, 커맨드
            LightModeCommandIr          = 0x23,     // LED 모드, 커맨드, IR 데이터 송신
            LightModeColor              = 0x24,     // LED 모드 3색 직접 지정
            LightModeColorCommand       = 0x25,     // LED 모드 3색 직접 지정, 커맨드
            LightModeColorCommandIr     = 0x26,     // LED 모드 3색 직접 지정, 커맨드, IR 데이터 송신
            LightModeColors             = 0x27,     // LED 모드 팔레트의 색상으로 지정
            LightModeColorsCommand      = 0x28,     // LED 모드 팔레트의 색상으로 지정, 커맨드
            LightModeColorsCommandIr    = 0x29,     // LED 모드 팔레트의 색상으로 지정, 커맨드, IR 데이터 송신

            LightEvent                  = 0x2A,     // LED 이벤트
            LightEventCommand           = 0x2B,     // LED 이벤트, 커맨드
            LightEventCommandIr         = 0x2C,     // LED 이벤트, 커맨드, IR 데이터 송신
            LightEventColor             = 0x2D,     // LED 이벤트 3색 직접 지정
            LightEventColorCommand      = 0x2E,     // LED 이벤트 3색 직접 지정, 커맨드
            LightEventColorCommandIr    = 0x2F,     // LED 이벤트 3색 직접 지정, 커맨드, IR 데이터 송신
            LightEventColors            = 0x30,     // LED 이벤트 팔레트의 색상으로 지정
            LightEventColorsCommand     = 0x31,     // LED 이벤트 팔레트의 색상으로 지정, 커맨드
            LightEventColorsCommandIr   = 0x32,     // LED 이벤트 팔레트의 색상으로 지정, 커맨드, IR 데이터 송신

            LightModeDefaultColor       = 0x33,     // LED 초기 모드 3색 직접 지정
            
            // 상태, 설정
            State                       = 0x40,     // 드론의 상태(비행 모드, 방위기준, 배터리량)
            Attitude,                               // 드론의 자세(Angle)(Vector)
            GyroBias,                               // 자이로 바이어스 값(Vector)
            TrimAll,                                // 전체 트림
            TrimFlight,                             // 비행 트림
            TrimDrive,                              // 주행 트림
            UserInterface,                          // 사용자 인터페이스 설정
    
            // Sensor raw data      
            Imu                         = 0x50,     // IMU Raw
            Pressure,                               // 압력 센서 데이터
            Battery,                                // 배터리
            Range,                                  // 거리 센서
            ImageFlow,                              // ImageFlow
            CameraImage,                            // CameraImage
                    
            // Input        
            Button                      = 0x70,     // 버튼 입력
            Joystick,                               // 조이스틱 입력
                    
            // Devices      
            Motor                       = 0x80,     // 모터 제어 및 현재 제어값 확인
            MotorSingle,                            // 한 개의 모터 제어
            IrMessage,                              // IR 데이터 송수신
            Buzzer,                                 // 부저 제어
            Vibrator,                               // 진동 제어
    
            // 카운트       
            CountFlight                 = 0x90,     // 비행 관련 카운트
            CountDrive,                             // 주행 관련 카운트
                    
            // RF       
            Pairing                     = 0xA0,     // 페어링
            Rssi,                                   // RSSI

            EndOfType
        };
    }
}
```


<br>
<br>

아래는 각 DataType와 연관된 구조체들을 링크로 연결해두었습니다.

<table>
    <tr>
        <td><div align="center">이름</div></td>
        <td><div align="center">값</div></td>
        <td><div align="center">설명</div></td>
        <td><div align="center">구조체</div></td>
    </tr>
    <tr>
        <td><div align="center">None</div></td>
        <td><div align="center">0x00</div></td>
        <td><div align="center">없음</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Ping</div></td>
        <td><div align="center">0x01</div></td>
        <td><div align="center">통신 확인</div></td>
        <td><div align="center"><a href="structs.md#Ping">Protocol::Ping</a></div></td>
    </tr>
    <tr>
        <td><div align="center">Ack</div></td>
        <td><div align="center">0x02</div></td>
        <td><div align="center">데이터 수신에 대한 응답</div></td>
        <td><div align="center"><a href="structs.md#Ack">Protocol::Ack</a></div></td>
    </tr>
    <tr>
        <td><div align="center">Error</div></td>
        <td><div align="center">0x03</div></td>
        <td><div align="center">오류(reserve, 비트 플래그는 추후에 지정)</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Request</div></td>
        <td><div align="center">0x04</div></td>
        <td><div align="center">지정한 타입의 데이터 요청</div></td>
        <td><div align="center"><a href="structs.md#Request">Protocol::Request</a></div></td>
    </tr>
    <tr>
        <td><div align="center">Message</div></td>
        <td><div align="center">0x05</div></td>
        <td><div align="center">문자열 데이터</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Reserved_1</div></td>
        <td><div align="center">0x06</div></td>
        <td><div align="center">예약</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Reserved_2</div></td>
        <td><div align="center">0x07</div></td>
        <td><div align="center">예약</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Monitor</div></td>
        <td><div align="center">0x08</div></td>
        <td><div align="center">디버깅용 값 배열 전송</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">SystemCounter</div></td>
        <td><div align="center">0x09</div></td>
        <td><div align="center">시스템 카운터</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Information</div></td>
        <td><div align="center">0x0A</div></td>
        <td><div align="center">펌웨어 및 장치 정보</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">UpdateLocation</div></td>
        <td><div align="center">0x0B</div></td>
        <td><div align="center">펌웨어 업데이트 위치 정정</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Update</div></td>
        <td><div align="center">0x0C</div></td>
        <td><div align="center">펌웨어 업데이트</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Encrypt</div></td>
        <td><div align="center">0x0D</div></td>
        <td><div align="center">펌웨어 암호화</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Address</div></td>
        <td><div align="center">0x0E</div></td>
        <td><div align="center">장치 주소</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Administrator</div></td>
        <td><div align="center">0x0F</div></td>
        <td><div align="center">관리자 권한</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Control</div></td>
        <td><div align="center">0x10</div></td>
        <td><div align="center">조종 명령</div></td>
        <td><div align="center"><a href="structs.md#Control_Double8">Control::Double8</a>, <a href="structs.md#Control_Quad8">Control::Quad8</a></div></td>
    </tr>
    <tr>
        <td><div align="center">Command</div></td>
        <td><div align="center">0x11</div></td>
        <td><div align="center">명령</div></td>
        <td><div align="center"><a href="structs.md#Command">Protocol::Command</a></div></td>
    </tr>
    <tr>
        <td><div align="center">LightManual</div></td>
        <td><div align="center">0x20</div></td>
        <td><div align="center">LED 수동 제어</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightMode</div></td>
        <td><div align="center">0x21</div></td>
        <td><div align="center">LED 모드 지정</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightModeCommand</div></td>
        <td><div align="center">0x22</div></td>
        <td><div align="center">LED 모드, 커맨드</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightModeCommandIr</div></td>
        <td><div align="center">0x23</div></td>
        <td><div align="center">LED 모드, 커맨드, IR 데이터 송신</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightModeColor</div></td>
        <td><div align="center">0x24</div></td>
        <td><div align="center">LED 모드 3색 직접 지정</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightModeColorCommand</div></td>
        <td><div align="center">0x25</div></td>
        <td><div align="center">LED 모드 3색 직접 지정, 커맨드</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightModeColorCommandIr</div></td>
        <td><div align="center">0x26</div></td>
        <td><div align="center">LED 모드 3색 직접 지정, 커맨드, IR 데이터 송신</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightModeColors</div></td>
        <td><div align="center">0x27</div></td>
        <td><div align="center">LED 모드 팔레트의 색상으로 지정</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightModeColorsCommand</div></td>
        <td><div align="center">0x28</div></td>
        <td><div align="center">LED 모드 팔레트의 색상으로 지정, 커맨드</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightModeColorsCommandIr</div></td>
        <td><div align="center">0x29</div></td>
        <td><div align="center">LED 모드 팔레트의 색상으로 지정, 커맨드, IR 데이터 송신</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightEvent</div></td>
        <td><div align="center">0x2A</div></td>
        <td><div align="center">LED 이벤트</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightEventCommand</div></td>
        <td><div align="center">0x2B</div></td>
        <td><div align="center">LED 이벤트, 커맨드</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightEventCommandIr</div></td>
        <td><div align="center">0x2C</div></td>
        <td><div align="center">LED 이벤트, 커맨드, IR 데이터 송신</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightEventColor</div></td>
        <td><div align="center">0x2D</div></td>
        <td><div align="center">LED 이벤트 3색 직접 지정</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightEventColorCommand</div></td>
        <td><div align="center">0x2E</div></td>
        <td><div align="center">LED 이벤트 3색 직접 지정, 커맨드</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightEventColorCommandIr</div></td>
        <td><div align="center">0x2F</div></td>
        <td><div align="center">LED 이벤트 3색 직접 지정, 커맨드, IR 데이터 송신</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightEventColors</div></td>
        <td><div align="center">0x30</div></td>
        <td><div align="center">LED 이벤트 팔레트의 색상으로 지정</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightEventColorsCommand</div></td>
        <td><div align="center">0x31</div></td>
        <td><div align="center">LED 이벤트 팔레트의 색상으로 지정, 커맨드</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightEventColorsCommandIr</div></td>
        <td><div align="center">0x32</div></td>
        <td><div align="center">LED 이벤트 팔레트의 색상으로 지정, 커맨드, IR 데이터 송신</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">LightModeDefaultColor</div></td>
        <td><div align="center">0x33</div></td>
        <td><div align="center">LED 초기 모드 3색 직접 지정</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">State</div></td>
        <td><div align="center">0x40</div></td>
        <td><div align="center">드론의 상태(비행 모드, 방위기준, 배터리량)</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Attitude</div></td>
        <td><div align="center">0x41</div></td>
        <td><div align="center">드론의 자세(Angle)(Vector)</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">GyroBias</div></td>
        <td><div align="center">0x42</div></td>
        <td><div align="center">자이로 바이어스 값(Vector)</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">TrimAll</div></td>
        <td><div align="center">0x43</div></td>
        <td><div align="center">전체 트림</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">TrimFlight</div></td>
        <td><div align="center">0x44</div></td>
        <td><div align="center">비행 트림</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">TrimDrive</div></td>
        <td><div align="center">0x45</div></td>
        <td><div align="center">주행 트림</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">UserInterface</div></td>
        <td><div align="center">0x46</div></td>
        <td><div align="center">사용자 인터페이스 설정</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Imu</div></td>
        <td><div align="center">0x50</div></td>
        <td><div align="center">IMU Raw and Angle(Accel, Gyro, Angle)</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Pressure</div></td>
        <td><div align="center">0x51</div></td>
        <td><div align="center">압력 센서 데이터</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Battery</div></td>
        <td><div align="center">0x52</div></td>
        <td><div align="center">배터리</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Range</div></td>
        <td><div align="center">0x53</div></td>
        <td><div align="center">거리 센서</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">ImageFlow</div></td>
        <td><div align="center">0x54</div></td>
        <td><div align="center">ImageFlow</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">CameraImage</div></td>
        <td><div align="center">0x55</div></td>
        <td><div align="center">CameraImage</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Button</div></td>
        <td><div align="center">0x70</div></td>
        <td><div align="center">버튼 입력</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Joystick</div></td>
        <td><div align="center">0x71</div></td>
        <td><div align="center">조이스틱 입력</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Motor</div></td>
        <td><div align="center">0x80</div></td>
        <td><div align="center">모터 제어 및 현재 제어값 확인</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">MotorSingle</div></td>
        <td><div align="center">0x81</div></td>
        <td><div align="center">한 개의 모터 제어</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">IrMessage</div></td>
        <td><div align="center">0x82</div></td>
        <td><div align="center">IR 데이터 송수신</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Buzzer</div></td>
        <td><div align="center">0x83</div></td>
        <td><div align="center">부저 제어</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Vibrator</div></td>
        <td><div align="center">0x84</div></td>
        <td><div align="center">진동 제어</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">CountFlight</div></td>
        <td><div align="center">0x90</div></td>
        <td><div align="center">비행 관련 카운트</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">CountDrive</div></td>
        <td><div align="center">0x91</div></td>
        <td><div align="center">주행 관련 카운트</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Pairing</div></td>
        <td><div align="center">0xA0</div></td>
        <td><div align="center">페어링</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
    <tr>
        <td><div align="center">Rssi</div></td>
        <td><div align="center">0xA1</div></td>
        <td><div align="center">RSSI</div></td>
        <td><div align="center">&nbsp;</div></td>
    </tr>
</table>

<br>

---

### PETRONE 2017

1. [Intro](intro.md)
2. [Typedef](typedef.md)
3. ***DataType***
4. [Definitions](definitions.md)
5. [Base Structs](base_structs.md)
6. [Structs](structs.md)
7. [Structs - Light](structs_light.md)

<br>

[Index](index.md)
