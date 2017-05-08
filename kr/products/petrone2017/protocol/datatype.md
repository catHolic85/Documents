<style type="text/css">
/*<![CDATA[*/
table.ex1 {width:98%; margin:0 auto; text-align:right; border-collapse:collapse}
.ex1 th, .ex1 td {padding:5px 10px}
.ex1 caption {font-weight:700; font-size:20px; padding:5px; color:#1BA6B2; text-align:left; margin-bottom:5px}
.ex1 thead th {background:#ABC668; color:#fff; text-align:center; border-right:1px solid #fff}
.ex1 tbody th {text-align:left; width:12%}
.ex1 tbody td.date1 {text-align:center; width:8%}
.ex1 tbody td.desc {text-align:left; width:35%}
.ex1 tbody tr.header {background:#a9c9f9}
.ex1 tbody tr.odd {background:#c9e9e9}
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

<table class="ex1">
    <tr class="header">
        <td>이름</td>
        <td>값</td>
        <td>설명</td>
        <td>구조체</td>
    </tr>
    <tr class="odd">
        <td>None</td>
        <td>0x00</td>
        <td class="desc">없음</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Ping</td>
        <td>0x01</td>
        <td class="desc">통신 확인</td>
        <td><a href="structs.md#Ping">Protocol::Ping</a></td>
    </tr>
    <tr class="odd">
        <td>Ack</td>
        <td>0x02</td>
        <td class="desc">데이터 수신에 대한 응답</td>
        <td><a href="structs.md#Ack">Protocol::Ack</a></td>
    </tr>
    <tr>
        <td>Error</td>
        <td>0x03</td>
        <td class="desc">오류(reserve, 비트 플래그는 추후에 지정)</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Request</td>
        <td>0x04</td>
        <td class="desc">지정한 타입의 데이터 요청</td>
        <td><a href="structs.md#Request">Protocol::Request</a></td>
    </tr>
    <tr>
        <td>Message</td>
        <td>0x05</td>
        <td class="desc">문자열 데이터</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Reserved_1</td>
        <td>0x06</td>
        <td class="desc">예약</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Reserved_2</td>
        <td>0x07</td>
        <td class="desc">예약</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Monitor</td>
        <td>0x08</td>
        <td>디버깅용 값 배열 전송</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>SystemCounter</td>
        <td>0x09</td>
        <td>시스템 카운터</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Information</td>
        <td>0x0A</td>
        <td>펌웨어 및 장치 정보</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>UpdateLocation</td>
        <td>0x0B</td>
        <td>펌웨어 업데이트 위치 정정</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Update</td>
        <td>0x0C</td>
        <td>펌웨어 업데이트</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Encrypt</td>
        <td>0x0D</td>
        <td>펌웨어 암호화</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Address</td>
        <td>0x0E</td>
        <td>장치 주소</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Administrator</td>
        <td>0x0F</td>
        <td>관리자 권한</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Control</td>
        <td>0x10</td>
        <td>조종 명령</td>
        <td><a href="structs.md#Control_Double8">Control::Double8</a>, <a href="structs.md#Control_Quad8">Control::Quad8</a></td>
    </tr>
    <tr>
        <td>Command</td>
        <td>0x11</td>
        <td>명령</td>
        <td><a href="structs.md#Command">Protocol::Command</a></td>
    </tr>
    <tr class="odd">
        <td>LightManual</td>
        <td>0x20</td>
        <td>LED 수동 제어</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>LightMode</td>
        <td>0x21</td>
        <td>LED 모드 지정</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>LightModeCommand</td>
        <td>0x22</td>
        <td>LED 모드, 커맨드</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>LightModeCommandIr</td>
        <td>0x23</td>
        <td>LED 모드, 커맨드, IR 데이터 송신</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>LightModeColor</td>
        <td>0x24</td>
        <td>LED 모드 3색 직접 지정</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>LightModeColorCommand</td>
        <td>0x25</td>
        <td>LED 모드 3색 직접 지정, 커맨드</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>LightModeColorCommandIr</td>
        <td>0x26</td>
        <td>LED 모드 3색 직접 지정, 커맨드, IR 데이터 송신</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>LightModeColors</td>
        <td>0x27</td>
        <td>LED 모드 팔레트의 색상으로 지정</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>LightModeColorsCommand</td>
        <td>0x28</td>
        <td>LED 모드 팔레트의 색상으로 지정, 커맨드</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>LightModeColorsCommandIr</td>
        <td>0x29</td>
        <td>LED 모드 팔레트의 색상으로 지정, 커맨드, IR 데이터 송신</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>LightEvent</td>
        <td>0x2A</td>
        <td>LED 이벤트</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>LightEventCommand</td>
        <td>0x2B</td>
        <td>LED 이벤트, 커맨드</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>LightEventCommandIr</td>
        <td>0x2C</td>
        <td>LED 이벤트, 커맨드, IR 데이터 송신</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>LightEventColor</td>
        <td>0x2D</td>
        <td>LED 이벤트 3색 직접 지정</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>LightEventColorCommand</td>
        <td>0x2E</td>
        <td>LED 이벤트 3색 직접 지정, 커맨드</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>LightEventColorCommandIr</td>
        <td>0x2F</td>
        <td>LED 이벤트 3색 직접 지정, 커맨드, IR 데이터 송신</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>LightEventColors</td>
        <td>0x30</td>
        <td>LED 이벤트 팔레트의 색상으로 지정</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>LightEventColorsCommand</td>
        <td>0x31</td>
        <td>LED 이벤트 팔레트의 색상으로 지정, 커맨드</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>LightEventColorsCommandIr</td>
        <td>0x32</td>
        <td>LED 이벤트 팔레트의 색상으로 지정, 커맨드, IR 데이터 송신</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>LightModeDefaultColor</td>
        <td>0x33</td>
        <td>LED 초기 모드 3색 직접 지정</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>State</td>
        <td>0x40</td>
        <td>드론의 상태(비행 모드, 방위기준, 배터리량)</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Attitude</td>
        <td>0x41</td>
        <td>드론의 자세(Angle)(Vector)</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>GyroBias</td>
        <td>0x42</td>
        <td>자이로 바이어스 값(Vector)</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>TrimAll</td>
        <td>0x43</td>
        <td>전체 트림</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>TrimFlight</td>
        <td>0x44</td>
        <td>비행 트림</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>TrimDrive</td>
        <td>0x45</td>
        <td>주행 트림</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>UserInterface</td>
        <td>0x46</td>
        <td>사용자 인터페이스 설정</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Imu</td>
        <td>0x50</td>
        <td>IMU Raw and Angle(Accel, Gyro, Angle)</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Pressure</td>
        <td>0x51</td>
        <td>압력 센서 데이터</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Battery</td>
        <td>0x52</td>
        <td>배터리</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Range</td>
        <td>0x53</td>
        <td>거리 센서</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>ImageFlow</td>
        <td>0x54</td>
        <td>ImageFlow</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>CameraImage</td>
        <td>0x55</td>
        <td>CameraImage</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Button</td>
        <td>0x70</td>
        <td>버튼 입력</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Joystick</td>
        <td>0x71</td>
        <td>조이스틱 입력</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Motor</td>
        <td>0x80</td>
        <td>모터 제어 및 현재 제어값 확인</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>MotorSingle</td>
        <td>0x81</td>
        <td>한 개의 모터 제어</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>IrMessage</td>
        <td>0x82</td>
        <td>IR 데이터 송수신</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Buzzer</td>
        <td>0x83</td>
        <td>부저 제어</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Vibrator</td>
        <td>0x84</td>
        <td>진동 제어</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>CountFlight</td>
        <td>0x90</td>
        <td>비행 관련 카운트</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>CountDrive</td>
        <td>0x91</td>
        <td>주행 관련 카운트</td>
        <td>&nbsp;</td>
    </tr>
    <tr class="odd">
        <td>Pairing</td>
        <td>0xA0</td>
        <td>페어링</td>
        <td>&nbsp;</td>
    </tr>
    <tr>
        <td>Rssi</td>
        <td>0xA1</td>
        <td>RSSI</td>
        <td>&nbsp;</td>
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
