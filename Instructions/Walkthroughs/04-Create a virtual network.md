---
wts:
  title: 04 - 가상 네트워크 만들기(20분)
  module: Module 02 - Core Azure Services (Workloads)
---
# <a name="04---create-a-virtual-network-20-min"></a>04 - 가상 네트워크 만들기(20분)

이 연습에서는 가상 네트워크를 만들고 가상 머신 2개를 해당 가상 네트워크에 배포한 다음 해당 가상 네트워크 내에서 한 가상 머신이 다른 가상 머신을 ping하도록 구성합니다.

# <a name="task-1-create-a-virtual-network"></a>작업 1: 가상 네트워크 만들기 

이 작업에서는 가상 네트워크를 만듭니다. 

참고: 랩을 시작하기 전에 시작 메뉴 > 설정 > 네트워크 및 인터넷 > Windows 방화벽 찾기를 열어 가상 머신에서 공용 방화벽과 프라이빗 방화벽을 모두 사용하지 않도록 설정합니다.

1. <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>에서 Azure Portal에 로그인합니다.

2. **모든 서비스** 블레이드에서 **가상 네트워크**를 검색하여 선택한 다음 **+ 추가, + 만들기, + 새로 만들기**를 클릭합니다. 

3. **기본** 탭에서 다음 정보를 채웁니다(다른 항목은 기본값을 사용).

    | 설정 | 값 | 
    | --- | --- |
    | 구독 | **제공된 기본값 유지** |
    | 리소스 그룹 | **새 리소스 그룹 만들기** |
    | 이름 | **vnet1** |
    | 지역 | **(미국) 미국 동부** |
    
   
4. Click the <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept> button. Ensure the validation passes. Then hit create to deploy the resource.


# <a name="task-2-create-two-virtual-machines"></a>작업 2: 두 개의 가상 머신 만들기

이 작업에서는 가상 네트워크에서 2개의 가상 머신을 만듭니다. 

1. **모든 서비스** 블레이드에서 **가상 머신**을 검색한 다음 **+ 추가, +만들기, +새로 만들기**를 클릭하고 드롭다운에서 **가상 머신**을 선택합니다. 

2. **기본** 탭에서 다음 정보를 채웁니다(다른 항목은 기본값을 사용).

   | 설정 | 값 | 
   | --- | --- |
   | 구독 | **제공된 기본값 사용** |
   | Resource group |  **드롭다운에서 기본값 선택** |
   | 가상 머신 이름 | **vm1**|
   | 지역 | **(미국) 미국 동부** |
   | 이미지 | **Windows Server 2019 Datacenter - Gen2** |
   | 사용자 이름| **azureuser** |
   | 암호| **Pa$$w0rd1234** |
   | 공용 인바운드 포트| **선택한 포트 허용**을 선택합니다.  |
   | 선택한 인바운드 포트| **RDP(3389)** |
   

3. Select the <bpt id="p1">**</bpt>Networking<ept id="p1">**</ept> tab. Make sure the virtual machine is placed in the <bpt id="p2">**</bpt>vnet1<ept id="p2">**</ept> virtual network. Review the default settings, but do not make any other changes. 

4. Click <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept>. After the Validation passes, click <bpt id="p1">**</bpt>Create<ept id="p1">**</ept>. Deployment times can vary but it can generally take between three to six minutes to deploy.

5. 배포를 모니터링하면서 다음 단계로 계속합니다. 

6. Create a second virtual machine by repeating steps <bpt id="p1">**</bpt>2 to 4<ept id="p1">**</ept> above. Make sure you use a different virtual machine name, that the virtual machine is in the same virtual network, and is using a new public IP address:

    | 설정 | 값 |
    | --- | --- |
    | Resource group | **드롭다운에서 기본값 선택(Task1-3 & Task2-2와 동일)** |
    | 가상 머신 이름 |  **vm2** |
    | 가상 네트워크 | **vnet1** |
    | 공용 IP | **vm2-ip** |

7. 두 가상 머신이 배포되고 *실행 중* 상태가 될 때까지 기다립니다.

# <a name="task-3-test-the-connection"></a>작업 3: 연결 테스트 

In this task, we will try to test whether the virtual machines can communicate (ping) each other. If not we will install a rule to allow an ICMP connection. Usually ICMP connections are automatically blocked.

1. From the <bpt id="p1">**</bpt>All resources<ept id="p1">**</ept> blade, search for <bpt id="p2">**</bpt>vm1<ept id="p2">**</ept>, open its <bpt id="p3">**</bpt>Overview<ept id="p3">**</ept> blade, and make sure its <bpt id="p4">**</bpt>Status<ept id="p4">**</ept> is <bpt id="p5">**</bpt>Running<ept id="p5">**</ept>. You may need to <bpt id="p1">**</bpt>Refresh<ept id="p1">**</ept> the page.

2. **개요** 블레이드에서 **연결**을 선택하고 드롭다운에서 **RDP**를 선택합니다.

    **참고**: 다음 지침은 Windows 컴퓨터에서 VM에 연결하는 방법을 알려줍니다. 

3. **RDP와 연결** 블레이드에서 포트 3389를 통해 IP 주소로 연결하는 기본 옵션을 유지하고 **RDP 파일 다운로드**를 클릭합니다.

4. 다운로드된 RDP 파일(VM의 왼쪽 하단에 위치함)을 열고, 관련 메시지가 표시되면 **연결**을 클릭합니다. 

5. **Windows 보안** 창에서 사용자 이름 **azureuser** 및 암호 **Pa$$w0rd1234**를 입력한 다음 **확인**을 클릭합니다.

6. You may receive a certificate warning during the sign-in process. Click <bpt id="p1">**</bpt>Yes<ept id="p1">**</ept> to create the connection and connect to your deployed VM. You should connect successfully. Close the Windows Server and Dashboard windows that pop up. You should see a Blue Windows background. You are now in your virtual machine.

7. 새로 만든 가상 머신 **모두**에서 RDP를 통해 연결하고 시작 메뉴 > 설정 > 네트워크 및 인터넷 > Windows 방화벽 찾기를 열어 공용 방화벽과 프라이빗 방화벽을 모두 사용하지 않도록 설정합니다.

8. **시작** 단추를 클릭하고, 검색에 **PowerShell**을 입력하고, **Windows PowerShell**을 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**하여 가상 머신에서 PowerShell을 엽니다.

9. Powershell에서 다음을 입력하여 vm2를 ping해 봅니다.

   ```PowerShell
   ping vm2
   ```

 10. You should be successful. You have pinged VM2 from VM1.


<bpt id="p1">**</bpt>Congratulations!<ept id="p1">**</ept> You have configured and deployed two virtual machines in a virtual network, and then you were able to connect them.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
