---
wts:
  title: 10 - PowerShell로 VM 만들기(10분)
  module: 'Module 03: Describe core solutions and management tools'
---
# <a name="10---create-a-vm-with-powershell-10-min"></a>10 - PowerShell로 VM 만들기(10분)

이 연습에서는 Cloud Shell을 구성하고, Azure PowerShell 모듈을 사용하여 리소스 그룹 및 가상 머신을 만들고, Azure Advisor 권장 사항을 검토합니다. 

# <a name="task-1-configure-the-cloud-shell"></a>작업 1: Cloud Shell 구성 

이 작업에서는 Cloud Shell을 구성합니다. 

1. [Azure Portal](https://portal.azure.com)에 로그인합니다.** 리소스 탭 내에서 로그인 자격 증명을 찾을 수 있습니다(이 지침 탭 바로 옆에 있음).
2. Azure Portal에서 오른쪽 상단의 아이콘을 클릭하여 **Azure Cloud Shell**을 엽니다.

    ![Azure Portal의 Azure Cloud Shell 아이콘 스크린샷.](../images/1002.png)

3. **Bash** 또는 **PowerShell**을 선택하라는 메시지가 표시되면 **PowerShell**을 선택합니다.

4. **장착된 스토리지가 없습니다** 화면에서 **고급 설정 보기**를 선택한 다음, 아래의 정보를 채웁니다.

    | 설정 | 값 |
    |  -- | -- |
    | 리소스 그룹 | **새 리소스 그룹 만들기** |
    | 스토리지 계정(전역적으로 고유한 이름을 사용하는 새 계정 만들기(예: cloudshellstoragemystorage)) | **cloudshellxxxxxxx** |
    | 파일 공유(새로 만들기) | **shellstorage** |

5. **스토리지 만들기**를 선택합니다.

# <a name="task-2-create-a-resource-group-and-virtual-machine"></a>작업 2: 리소스 그룹 및 가상 머신 만들기

이 작업에서는 PowerShell을 사용하여 리소스 그룹과 가상 머신을 만듭니다.  

1. Cloud Shell 창의 왼쪽 위 드롭다운 메뉴에서 **PowerShell**이 선택되어 있는지 확인합니다.

2. Verify your new resource group by running the following command in the Powershell window. Press <bpt id="p1">**</bpt>Enter<ept id="p1">**</ept> to run the command.

    ```PowerShell
    Get-AzResourceGroup | Format-Table
    ```

3. 터미널 창에 다음 명령을 붙여넣어 가상 머신을 만듭니다. 

    ```PowerShell
    New-AzVm `
    -ResourceGroupName "myRGPS" `
    -Name "myVMPS" `
    -Location "East US" `
    -VirtualNetworkName "myVnetPS" `
    -SubnetName "mySubnetPS" `
    -SecurityGroupName "myNSGPS" `
    -PublicIpAddressName "myPublicIpPS"
    ```
    
4. 메시지가 표시되면 해당 가상 머신에서 로컬 관리자 계정으로 구성될 사용자 이름(**azureuser**) 및 암호(**Pa$$w0rd1234**)를 입력합니다.

5. VM이 만들어지면 PowerShell 세션 Cloud Shell 창을 닫습니다.

6. In the Azure portal, search for <bpt id="p1">**</bpt>Virtual machines<ept id="p1">**</ept> and verify the <bpt id="p2">**</bpt>myVMPS<ept id="p2">**</ept> is running. This may take a few minutes.

    ![myVMPS가 실행 중인 가상 머신 페이지의 스크린샷.](../images/1001.png)

7. 새 가상 머신에 액세스하고 개요 및 네트워킹 설정을 검토하여 정보가 올바르게 배포되었는지 확인합니다. 

# <a name="task-3-execute-commands-in-the-cloud-shell"></a>작업 3: Cloud Shell에서 명령 실행

이 작업에서는 Cloud Shell에서 PowerShell 명령을 실행하는 연습을 합니다. 

1. Azure Portal에서 오른쪽 상단의 아이콘을 클릭하여 **Azure Cloud Shell**을 엽니다.

2. Cloud Shell 창의 왼쪽 위 드롭다운 메뉴에서 **PowerShell**이 선택되어 있는지 확인합니다.

3. Retrieve information about your virtual machine including name, resource group, location, and status. Notice the PowerState is <bpt id="p1">**</bpt>running<ept id="p1">**</ept>.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

4. 다음 명령을 사용하여 가상 머신을 중지합니다. 

    ```PowerShell
    Stop-AzVM -ResourceGroupName myRGPS -Name myVMPS
    ```
5. When prompted confirm (Yes) to the action. Wait for <bpt id="p1">**</bpt>Succeeded<ept id="p1">**</ept> status.

6. Verify your virtual machine state. The PowerState should now be <bpt id="p1">**</bpt>deallocated<ept id="p1">**</ept>. You can also verify the virtual machine status in the portal. Close Cloudshell.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

# <a name="task-4-review-azure-advisor-recommendations"></a>작업 4: Azure Advisor 권장 사항 검토

**참고:** 이 작업은 Azure CLI 랩을 사용하여 VM 만들기 작업과 동일합니다. 

이 작업에서는 가상 머신에 대한 Azure Advisor 권장 사항을 검토합니다. 

1. **모든 서비스** 블레이드에서 **Advisor**를 검색하고 선택합니다. 

2. On the <bpt id="p1">**</bpt>Advisor<ept id="p1">**</ept> blade, select <bpt id="p2">**</bpt>Overview<ept id="p2">**</ept>. Notice recommendations are grouped by Reliability, Security, Performance, and Cost. 

    ![Advisor 개요 페이지의 스크린샷. ](../images/1003.png)

3. **모든 권장 사항**을 선택하고 각 권장 사항 및 제안되는 작업을 검토합니다. 

    **참고:** 권장 사항은 리소스에 따라 다를 수 있습니다. 

    ![Advisor 모든 권장 사항 페이지의 스크린샷. ](../images/1004.png)

4. 권장 사항을 CSV 또는 PDF 파일로 다운로드할 수 있습니다. 

5. 경고를 만들 수도 있습니다. 

6. 시간이 있으면 Azure PowerShell을 사용하여 실험을 계속하세요. 

Congratulations! You have configured Cloud Shell, created a virtual machine using PowerShell, practiced with PowerShell commands, and viewed Advisor recommendations.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
