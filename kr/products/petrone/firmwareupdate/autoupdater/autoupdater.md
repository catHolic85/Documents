
# Auto Updater

<br>

## 1. Petrone과 PetroneLink를 유선으로 연결할 때 사용하는 커넥터

![Image of PetroneLink](connector.jpg)

<br>
<br>

## 2. Petrone과 PetroneLink를 연결한 상태

![Image of PetroneLink](petronelink.jpg)

<br>
<br>

## 3. Auto Updater 프로그램을 실행한 화면

![Image of AutoUpdater_1](petrone_auto_updater_1.png)

<br>

#### 3.1. 버튼에 대한 설명

|이름      |  설명                                |
|:-------:|:-----------------------------------|
| SCAN | PC에 연결된 시리얼 통신 장치 검색 |
| FORCE MAIN | 메인 펌웨어 강제 업데이트 |
| FORCE SUB | 통신 펌웨어 강제 업데이트 |
| AUTO UPDATE | 펌웨어 업데이트 시작 |
| DISCONNECT | 펌웨어 업데이트 중단. PetroneLink와의 연결 해제 |

<br>

#### 3.2. 펌웨어 업데이트 진행 방법

> 1. PetroneLink를 PC에 연결
> 2. PetroneLink의 LED가 노란색으로 Dimming 되도록 버튼을 눌러 모드를 변경.
> 3. AUTO UPDATER에서 'SCAN' 버튼을 눌러 시리얼 통신 장치 검색
> 4. AUTO UPDATER에서'SCAN' 버튼 아래의 콤보 박스에서 PetroneLink의 포트 선택
> 5. AUTO UPDATER에서'AUTO UPDATE' 버튼을 눌러 펌웨어 업데이트 진행
> 6. PetroneLink에 Petrone을 연결하면 자동으로 업데이트가 진행됨. 펌웨어 업데이트가 완료되면 다음 Petrone을 연결하여 연속으로 업데이트 진행 가능
> 7. 모든 업데이트가 완료된 경우 'DISCONNECT' 버튼을 눌러 PetroneLink와의 연결을 해제

<br>

#### 3.3. 주의 사항

- 펌웨어 업데이트 시 업데이트가 필요한 경우에만 펌웨어 업데이트를 실행함.
- 업데이트를 완료한 장치는 업데이트 전의 펌웨어 버젼과 장치 주소가 '>> Devices'에 등록되며 이 리스트에서 삭제하기 전까지는 업데이트가 안됨.
- 버젼과 상관없이 강제로 펌웨어를 업데이트하려면 'FORCE MAIN'(메인 펌웨어) 또는 'FORCE SUB'(통신 펌웨어) 버튼을 눌러 활성화해야 함.
- 펌웨어 업데이트는 '통신 펌웨어' -> '메인 펌웨어' 순서로 진행됨.
- 업데이트 프로그램을 실행할 때에는 [.Net Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=17851)이 필요.
- PetroneLink를 PC와 연결할 때에는 [CP2104 드라이버](https://www.silabs.com/products/mcu/Pages/USBtoUARTBridgeVCPDrivers.aspx)가 필요. 

<br>
<br>

## 4. 펌웨어 업데이트를 진행하고 있는 화면.

![Image of AutoUpdater_2](petrone_auto_updater_2.png)

<br>
<br>

## 5. 펌웨어 업데이트가 완료된 화면.

![Image of AutoUpdater_3](petrone_auto_updater_3.png)

<br>

---

Modified : 2017.05.10
