<style type="text/css">
/*<![CDATA[*/
table.ex1 {width:98%; margin:0 auto; text-align:center; border-collapse:collapse}
.ex1 th, .ex1 td {padding:5px 10px}
.ex1 caption {font-weight:700; font-size:12px; padding:5px; color:#1BA6B2; text-align:center; margin-bottom:5px}
.ex1 thead th {background:#ABC668; color:#fff; text-align:center; vertical-align:middle; border-right:1px solid #fff}
.ex1 tbody th {text-align:left; width:12%}
.ex1 tbody td.date1 {text-align:center; width:8%}
.ex1 tbody td.desc {text-align:left; width:35%}
.ex1 tbody tr.header {background:#d9f0ee; text-align:center;}
.ex1 tbody tr.odd {background:#e5f0f0}
.ex1 tbody tr.odd th {background:#f2f2f2}
.ex1 tbody tr:hover {background:#F3F5BB}
.ex1 tbody tr:hover th {background:#F2F684; color:#1BA6B2}
.ex1 tfoot tr {border-top:6px solid #E9F7F6; color:#1BA6B2}
.ex1 tfoot th {text-align:left; padding-left:10px}
/*]]>*/
</style>

***PETRONE2017 / Protocol / DataType***<br>
Modified : 2017.05.02

---

#### 데이터 타입을 소개합니다.

---

<br>

## <a name="Protocol_DataType">Protocol::DataType::Type</a>
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
            Error                       = 0x03,     // 오류
            Request                     = 0x04,     // 지정한 타입의 데이터 요청
            Message                     = 0x05,     // 문자열 데이터
            Reserved_1                  = 0x06,     // 예약
            Reserved_2                  = 0x07,     // 예약
            Monitor                     = 0x08,     // 디버깅용 값 배열 전송
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

            LightMode                   = 0x21,     // LED 모드
            LightModeCommand            = 0x22,     // LED 모드, 커맨드
            LightModeCommandIr          = 0x23,     // LED 모드, 커맨드, IR
            LightModeColor              = 0x24,     // LED 모드 3색
            LightModeColorCommand       = 0x25,     // LED 모드 3색, 커맨드
            LightModeColorCommandIr     = 0x26,     // LED 모드 3색, 커맨드, IR
            LightModeColors             = 0x27,     // LED 모드 팔레트
            LightModeColorsCommand      = 0x28,     // LED 모드 팔레트, 커맨드
            LightModeColorsCommandIr    = 0x29,     // LED 모드 팔레트, 커맨드, IR

            LightEvent                  = 0x2A,     // LED 이벤트
            LightEventCommand           = 0x2B,     // LED 이벤트, 커맨드
            LightEventCommandIr         = 0x2C,     // LED 이벤트, 커맨드, IR
            LightEventColor             = 0x2D,     // LED 이벤트 3색
            LightEventColorCommand      = 0x2E,     // LED 이벤트 3색, 커맨드
            LightEventColorCommandIr    = 0x2F,     // LED 이벤트 3색, 커맨드, IR
            LightEventColors            = 0x30,     // LED 이벤트 팔레트
            LightEventColorsCommand     = 0x31,     // LED 이벤트 팔레트, 커맨드
            LightEventColorsCommandIr   = 0x32,     // LED 이벤트 팔레트, 커맨드, IR

            LightModeDefaultColor       = 0x33,     // LED 초기 모드 3색
            
            // 상태, 설정
            State                       = 0x40,     // 드론의 상태
            Attitude,                               // 드론의 자세
            GyroBias,                               // 자이로 바이어스 값
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

<table class="ex1">
    <tr class="header">
        <td>이름</td>
        <td>값</td>
        <td>대상</td>
        <td>설명</td>
        <td>구조체</td>
    </tr>
    <tr class="odd">
        <td>None</td>
        <td>0x00</td>
        <td>-</td>
        <td class="desc">없음</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Ping</td>
        <td>0x01</td>
        <td>A</td>
        <td class="desc">통신 확인</td>
        <td><a href="structs.md#Ping">Protocol::Ping</a></td>
    </tr>
    <tr class="odd">
        <td>Ack</td>
        <td>0x02</td>
        <td>A</td>
        <td class="desc">데이터 수신에 대한 응답</td>
        <td><a href="structs.md#Ack">Protocol::Ack</a></td>
    </tr>
    <tr>
        <td>Error</td>
        <td>0x03</td>
        <td>A</td>
        <td class="desc">오류(reserve, 비트 플래그는 추후에 지정)</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Request</td>
        <td>0x04</td>
        <td>A</td>
        <td class="desc">지정한 타입의 데이터 요청</td>
        <td><a href="structs.md#Request">Protocol::Request</a></td>
    </tr>
    <tr>
        <td>Message</td>
        <td>0x05</td>
        <td>A</td>
        <td class="desc">문자열 데이터</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Reserved_1</td>
        <td>0x06</td>
        <td>-</td>
        <td class="desc">예약</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Reserved_2</td>
        <td>0x07</td>
        <td>-</td>
        <td class="desc">예약</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Monitor</td>
        <td>0x08</td>
        <td>D</td>
        <td class="desc">디버깅용 값 배열 전송</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>SystemCounter</td>
        <td>0x09</td>
        <td>A</td>
        <td class="desc">시스템 카운터</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Information</td>
        <td>0x0A</td>
        <td>A</td>
        <td class="desc">펌웨어 및 장치 정보</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>UpdateLocation</td>
        <td>0x0B</td>
        <td>A</td>
        <td class="desc">펌웨어 업데이트 위치 정정</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Update</td>
        <td>0x0C</td>
        <td>A</td>
        <td class="desc">펌웨어 업데이트</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Encrypt</td>
        <td>0x0D</td>
        <td>A</td>
        <td class="desc">펌웨어 암호화</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Address</td>
        <td>0x0E</td>
        <td>A</td>
        <td class="desc">장치 주소</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Administrator</td>
        <td>0x0F</td>
        <td>A</td>
        <td class="desc">관리자 권한</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Control</td>
        <td>0x10</td>
        <td>D</td>
        <td class="desc">조종 명령</td>
        <td><a href="structs.md#Control_Double8">Control::Double8</a>, <a href="structs.md#Control_Quad8">Control::Quad8</a></td>
    </tr>
    <tr>
        <td>Command</td>
        <td>0x11</td>
        <td>A</td>
        <td class="desc">명령</td>
        <td><a href="structs.md#Command">Protocol::Command</a></td>
    </tr>
    <tr class="odd">
        <td>LightManual</td>
        <td>0x20</td>
        <td>A</td>
        <td class="desc">LED 수동 제어</td>
        <td><a href="structs_light.md#Protocol_Light_Manual">Protocol::Light::Manual</a></td>
    </tr>
    <tr>
        <td>LightMode</td>
        <td>0x21</td>
        <td>A</td>
        <td class="desc">LED 모드 지정</td>
        <td><a href="structs_light.md#Protocol_Light_Mode">Protocol::Light::Mode</a></td>
    </tr>
    <tr class="odd">
        <td>LightModeCommand</td>
        <td>0x22</td>
        <td>A</td>
        <td class="desc">LED 모드, 커맨드</td>
        <td><a href="structs_light.md#Protocol_Light_ModeCommand">Protocol::Light::ModeCommand</a></td>
    </tr>
    <tr>
        <td>LightModeCommandIr</td>
        <td>0x23</td>
        <td>A</td>
        <td class="desc">LED 모드, 커맨드, IR</td>
        <td><a href="structs_light.md#Protocol_Light_ModeCommandIr">Protocol::Light::ModeCommandIr</a></td>
    </tr>
    <tr class="odd">
        <td>LightModeColor</td>
        <td>0x24</td>
        <td>A</td>
        <td class="desc">LED 모드 3색</td>
        <td><a href="structs_light.md#Protocol_Light_ModeColor">Protocol::Light::ModeColor</a></td>
    </tr>
    <tr>
        <td>LightModeColorCommand</td>
        <td>0x25</td>
        <td>A</td>
        <td class="desc">LED 모드 3색, 커맨드</td>
        <td><a href="structs_light.md#Protocol_Light_ModeColorCommand">Protocol::Light::ModeColorCommand</a></td>
    </tr>
    <tr class="odd">
        <td>LightModeColorCommandIr</td>
        <td>0x26</td>
        <td>A</td>
        <td class="desc">LED 모드 3색, 커맨드, IR</td>
        <td><a href="structs_light.md#Protocol_Light_ModeColorCommandIr">Protocol::Light::ModeColorCommandIr</a></td>
    </tr>
    <tr>
        <td>LightModeColors</td>
        <td>0x27</td>
        <td>A</td>
        <td class="desc">LED 모드 팔레트</td>
        <td><a href="structs_light.md#Protocol_Light_ModeColors">Protocol::Light::ModeColors</a></td>
    </tr>
    <tr class="odd">
        <td>LightModeColorsCommand</td>
        <td>0x28</td>
        <td>A</td>
        <td class="desc">LED 모드 팔레트, 커맨드</td>
        <td><a href="structs_light.md#Protocol_Light_ModeColorsCommand">Protocol::Light::ModeColorsCommand</a></td>
    </tr>
    <tr>
        <td>LightModeColorsCommandIr</td>
        <td>0x29</td>
        <td>A</td>
        <td class="desc">LED 모드 팔레트, 커맨드, IR</td>
        <td><a href="structs_light.md#Protocol_Light_ModeColorsCommandIr">Protocol::Light::ModeColorsCommandIr</a></td>
    </tr>
    <tr class="odd">
        <td>LightEvent</td>
        <td>0x2A</td>
        <td>A</td>
        <td class="desc">LED 이벤트</td>
        <td><a href="structs_light.md#Protocol_Light_Event">Protocol::Light::Event</a></td>
    </tr>
    <tr>
        <td>LightEventCommand</td>
        <td>0x2B</td>
        <td>A</td>
        <td class="desc">LED 이벤트, 커맨드</td>
        <td><a href="structs_light.md#Protocol_Light_EventCommand">Protocol::Light::EventCommand</a></td>
    </tr>
    <tr class="odd">
        <td>LightEventCommandIr</td>
        <td>0x2C</td>
        <td>A</td>
        <td class="desc">LED 이벤트, 커맨드, IR</td>
        <td><a href="structs_light.md#Protocol_Light_EventCommandIr">Protocol::Light::EventCommandIr</a></td>
    </tr>
    <tr>
        <td>LightEventColor</td>
        <td>0x2D</td>
        <td>A</td>
        <td class="desc">LED 이벤트 3색</td>
        <td><a href="structs_light.md#Protocol_Light_EventColor">Protocol::Light::EventColor</a></td>
    </tr>
    <tr class="odd">
        <td>LightEventColorCommand</td>
        <td>0x2E</td>
        <td>A</td>
        <td class="desc">LED 이벤트 3색, 커맨드</td>
        <td><a href="structs_light.md#Protocol_Light_EventColorCommand">Protocol::Light::EventColorCommand</a></td>
    </tr>
    <tr>
        <td>LightEventColorCommandIr</td>
        <td>0x2F</td>
        <td>A</td>
        <td class="desc">LED 이벤트 3색, 커맨드, IR</td>
        <td><a href="structs_light.md#Protocol_Light_EventColorCommandIr">Protocol::Light::EventColorCommandIr</a></td>
    </tr>
    <tr class="odd">
        <td>LightEventColors</td>
        <td>0x30</td>
        <td>A</td>
        <td class="desc">LED 이벤트 팔레트</td>
        <td><a href="structs_light.md#Protocol_Light_EventColors">Protocol::Light::EventColors</a></td>
    </tr>
    <tr>
        <td>LightEventColorsCommand</td>
        <td>0x31</td>
        <td>A</td>
        <td class="desc">LED 이벤트 팔레트, 커맨드</td>
        <td><a href="structs_light.md#Protocol_Light_EventColorsCommand">Protocol::Light::EventColorsCommand</a></td>
    </tr>
    <tr class="odd">
        <td>LightEventColorsCommandIr</td>
        <td>0x32</td>
        <td>A</td>
        <td class="desc">LED 이벤트 팔레트, 커맨드, IR</td>
        <td><a href="structs_light.md#Protocol_Light_EventColorsCommandIr">Protocol::Light::EventColorsCommandIr</a></td>
    </tr>
    <tr>
        <td>LightModeDefaultColor</td>
        <td>0x33</td>
        <td>D</td>
        <td class="desc">LED 초기 모드 3색</td>
        <td><a href="structs_light.md#Protocol_Light_ModeColor">Protocol::Light::ModeColor</a></td>
    </tr>
    <tr class="odd">
        <td>State</td>
        <td>0x40</td>
        <td>D</td>
        <td class="desc">드론의 상태</td>
        <td><a href="structs.md#State">Protocol::State</a></td>
    </tr>
    <tr>
        <td>Attitude</td>
        <td>0x41</td>
        <td>D</td>
        <td class="desc">드론의 자세(Angle)</td>
        <td><a href="structs.md#Attitude">Protocol::Attitude</a></td>
    </tr>
    <tr class="odd">
        <td>GyroBias</td>
        <td>0x42</td>
        <td>D</td>
        <td class="desc">자이로 바이어스 값</td>
        <td><a href="structs.md#GyroBias">Protocol::GyroBias</a></td>
    </tr>
    <tr>
        <td>TrimAll</td>
        <td>0x43</td>
        <td>D</td>
        <td class="desc">전체 트림</td>
        <td><a href="structs.md#TrimAll">Protocol::TrimAll</a></td>
    </tr>
    <tr class="odd">
        <td>TrimFlight</td>
        <td>0x44</td>
        <td>D</td>
        <td class="desc">비행 트림</td>
        <td><a href="structs.md#TrimFlight">Protocol::TrimFlight</a></td>
    </tr>
    <tr>
        <td>TrimDrive</td>
        <td>0x45</td>
        <td>D</td>
        <td class="desc">주행 트림</td>
        <td><a href="structs.md#TrimDrive">Protocol::TrimDrive</a></td>
    </tr>
    <tr class="odd">
        <td>UserInterface</td>
        <td>0x46</td>
        <td>C</td>
        <td class="desc">사용자 인터페이스 설정</td>
        <td>[System::SensorOrientation::Type](definitions.md#SensorOrientation)   <a href="structs.md#Protocol_UserInterface">Protocol::UserInterface</a></td>
    </tr>
    <tr>
        <td>Imu</td>
        <td>0x50</td>
        <td>D</td>
        <td class="desc">IMU(Accel, Gyro, Angle)</td>
        <td><a href="structs.md#ImuRawAndAngle">Protocol::ImuRawAndAngle</a></td>
    </tr>
    <tr class="odd">
        <td>Pressure</td>
        <td>0x51</td>
        <td>D</td>
        <td class="desc">압력 센서 데이터</td>
        <td><a href="structs.md#Pressure">Protocol::Pressure</a></td>
    </tr>
    <tr>
        <td>Battery</td>
        <td>0x52</td>
        <td>D</td>
        <td class="desc">배터리</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Range</td>
        <td>0x53</td>
        <td>D</td>
        <td class="desc">거리 센서</td>
        <td><a href="structs.md#Range">Protocol::Range</a></td>
    </tr>
    <tr>
        <td>ImageFlow</td>
        <td>0x54</td>
        <td>D</td>
        <td class="desc">ImageFlow</td>
        <td><a href="structs.md#ImageFlow">Protocol::ImageFlow</a></td>
    </tr>
    <tr class="odd">
        <td>CameraImage</td>
        <td>0x55</td>
        <td>D</td>
        <td class="desc">CameraImage</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Button</td>
        <td>0x70</td>
        <td>C</td>
        <td class="desc">버튼 입력</td>
        <td><a href="structs.md#Button">Protocol::Button</a></td>
    </tr>
    <tr class="odd">
        <td>Joystick</td>
        <td>0x71</td>
        <td>C</td>
        <td class="desc">조이스틱 입력</td>
        <td><a href="structs.md#Protocol_Joystick">Protocol::Joystick</a></td>
    </tr>
    <tr>
        <td>Motor</td>
        <td>0x80</td>
        <td>D</td>
        <td class="desc">모터 제어 및 현재 제어값 확인</td>
        <td><a href="structs.md#Motor">Protocol::Motor</a></td>
    </tr>
    <tr class="odd">
        <td>MotorSingle</td>
        <td>0x81</td>
        <td>D</td>
        <td class="desc">한 개의 모터 제어</td>
        <td><a href="structs.md#">Protocol::</a></td>
    </tr>
    <tr>
        <td>IrMessage</td>
        <td>0x82</td>
        <td>D</td>
        <td class="desc">IR 데이터 송수신</td>
        <td><a href="structs.md#IrMessage">Protocol::IrMessage</a></td>
    </tr>
    <tr class="odd">
        <td>Buzzer</td>
        <td>0x83</td>
        <td>C</td>
        <td class="desc">버저 제어</td>
        <td><a href="structs.md#">Protocol::</a></td>
    </tr>
    <tr>
        <td>Vibrator</td>
        <td>0x84</td>
        <td>C</td>
        <td class="desc">진동 제어</td>
        <td><a href="structs.md#Protocol_Vibrator">Protocol::Vibrator</a></td>
    </tr>
    <tr class="odd">
        <td>CountFlight</td>
        <td>0x90</td>
        <td>D</td>
        <td class="desc">비행 관련 카운트</td>
        <td><a href="structs.md#CountFlight">Protocol::CountFlight</a></td>
    </tr>
    <tr>
        <td>CountDrive</td>
        <td>0x91</td>
        <td>D</td>
        <td class="desc">주행 관련 카운트</td>
        <td><a href="structs.md#CountDrive">Protocol::CountDrive</a></td>
    </tr>
    <tr class="odd">
        <td>Pairing</td>
        <td>0xA0</td>
        <td>A</td>
        <td class="desc">페어링</td>
        <td><a href="structs.md#">Protocol::</a></td>
    </tr>
    <tr>
        <td>Rssi</td>
        <td>0xA1</td>
        <td>A</td>
        <td class="desc">RSSI</td>
        <td><a href="structs.md#">Protocol::</a></td>
    </tr>
</table>

<br>

- A: 모든 장치(All)
- C: 조종기(Controller)
- D: 드론(Drone)

<br>

---

### PETRONE 2017

1. [Intro](intro.md)
2. [Typedef](typedef.md)
3. ***DataType***
4. [Definitions](definitions.md)
5. [Structs](structs.md)
6. [Structs - Light](structs_light.md)

<br>

[Index](index.md)
