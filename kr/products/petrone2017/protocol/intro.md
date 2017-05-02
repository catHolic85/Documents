***PETRONE2017 / Protocol / Intro***<br>
Modified : 2017.03.28

---

<br>

# 1. PETRONE 2017 소개

**PETRONE 2017**은 Petrone의 통신 모듈을 변경하고, 조종기를 붙인 버젼입니다.


<br>
<br>


# 2. 전송 데이터 구조

Petrone2017은 주로 조종기를 PC에 연결한 상태에서 통신을 하게 됩니다. 이 때 송수신 데이터의 구조는 아래와 같습니다.

<table>
    <tr>
        <td><div align="center">0</div></td>
        <td><div align="center">1</div></td>
        <td><div align="center">2</div></td>
        <td><div align="center">3</div></td>
        <td><div align="center">4</div></td>
        <td><div align="center">5</div></td>
        <td><div align="center">...</div></td>
        <td><div align="center">N-1</div></td>
        <td><div align="center">N</div></td>
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="4"><div align="center">Header</div></td>
        <td rowspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
        <td><div align="center">From</div></td>
        <td><div align="center">To</div></td>
    </tr>
    <tr>
        <td><div align="center">0x0A</div></td>
        <td><div align="center">0x55</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
    </tr>
</table>
각 항목에 대한 설명은 다음과 같습니다.


|영역 | 설명 |
|:---|:---|
| Start code | 데이터 전송 시작을 알림 |
| Header | 헤더 뒤에 이어지는 데이터의 형식과 길이, 데이터를 전송하는 장치, 수신 받는 장치의 DeviceType |
| Data | 전송할 데이터 |
| CRC16 | Header와 Data가 정상적으로 전달되었는지 판별<br><a href="http://www.menie.org/georges/embedded/crc16.html">http://www.menie.org/georges/embedded/crc16.html</a>    |


Data 영역과 CRC16 영역 모두 Little Endian을 사용하고 있습니다. Little Endian일 때 2바이트 이상의 변수는 하위 바이트가 배열의 앞 부분에 위치합니다. C#에서는 Bitconverter를 사용하시면 편리하게 변경할 수 있습니다.


| | 0x1234 | 0x12345678 |
|:---:|:---:|:---:|
| Big Endian | [ 12 34 ] | [ 12 34 56 78 ] |
| Little Endian | [ 34 12 ] | [ 78 56 34 12 ] |


<br>
<br>


# 3. 사용 시 주의사항

- 모든 장치는 데이터를 요청했을 경우에만 관련된 데이터를 응답으로 전송합니다.

- 특정 장치를 명시한 경우, 해당 장치는 데이터를 요청받은 경우가 아니라면 Ack를 응답으로 보냅니다.

- Broadcasting으로 데이터를 전송한 경우, 데이터 요청이 아닌 일반적인 명령이었다면 해당 명령을 처리할 수 있는 장치는 해당 명령을 처리합니다.

- Broadcasting으로 데이터를 전송한 경우, 데이터 요청을 전달하였다면 해당 데이터에 대해 응답을 할 수 있는 장치가 응답을 합니다. 이 과정에서 두 개 이상의 장치가 동일한 데이터에 대해 응답이 가능하다면 데이터 송수신 간에 충돌이 발생할 수 있습니다. 사용시 주의하셔야 합니다.

- Broadcasting에 대해서는 Ack를 응답으로 보내지 않습니다.


<br>
<br>


# 4. 시리얼 통신 설정


|영역 | 설정값 |
|:---:|:---:|
| Baud Rate | 115200 |
| Parity | None      |
| Data Bits | 8 |
| Stop Bits | 1 |


<br>
<br>


# 5. 드라이버 설치

Petrone2017 조종기는 윈도우10인 경우 자동으로 인식합니다. 그 외에 장치를 인식하지 못하는 경우 별도의 드라이버를 설치하셔야 합니다.

<br>

---

### PETRONE

1. [Intro](intro.md)
2. [Typedef](typedef.md)
3. [DataType](datatype.md)
4. [Definitions](definitions.md)
5. [Base Structs](base_structs.md)
6. [Structs](structs.md)
7. [Structs - Light](structs_light.md)


<br>

[Home](../../README.md)

