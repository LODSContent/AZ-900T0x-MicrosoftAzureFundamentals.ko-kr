---
wts:
  title: 12 - Azure Key Vault 구현(5분)
  module: 'Module 04: Describe general security and network security features'
---
# <a name="12---implement-azure-key-vault-5-min"></a>12 - Azure Key Vault 구현(5분)

이 연습에서는 Azure Key Vault를 만든 다음 해당 Key Vault 내에서 암호를 만들어 안전하게 저장되고 중앙에서 관리되는 암호를 애플리케이션에서 사용할 수 있도록 합니다.

# <a name="task-1-create-an-azure-key-vault"></a>작업 1: Azure Key Vault 만들기 

1. [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. **모든 서비스** 블레이드에서 **Key Vault**를 검색하여 선택한 다음 **+추가+새로 만들기+만들기**를 선택합니다.

3. Configure the key vault (replace <bpt id="p1">**</bpt>xxxx<ept id="p1">**</ept> in the name of the key vault with letters and digits such that the name is globally unique). Leave the defaults for everything else.

    | 설정 | 값 | 
    | --- | --- |
    | 구독 | **제공된 기본값 사용** |
    | Resource group | **새 리소스 그룹 만들기** |
    | 키 자격 증명 모음 이름 | **keyvaulttestxxx** |
    | 위치 | **미국 동부** |
    | 가격 책정 계층 | **표준** |
    
    **참고** **xxxx**를 바꿔서 고유한 이름을 찾습니다.
4. **검토 + 만들기**를 클릭한 다음 **만들기**를 클릭합니다. 

5. Once the new key vault is provisioned, click <bpt id="p1">**</bpt>Go to resource<ept id="p1">**</ept>. Or you can locate your new key vault by searching for it. 

6. Click on the key vault <bpt id="p1">**</bpt>Overview<ept id="p1">**</ept> tab and take note of the <bpt id="p2">**</bpt>Vault URI<ept id="p2">**</ept>. Applications that use your vault through the REST APIs will need this URI.

7. Take a moment to browse through some of the other key vault options. Under <bpt id="p1">**</bpt>Settings<ept id="p1">**</ept> review <bpt id="p2">**</bpt>Keys<ept id="p2">**</ept>, <bpt id="p3">**</bpt>Secrets<ept id="p3">**</ept>, <bpt id="p4">**</bpt>Certificates<ept id="p4">**</ept>, <bpt id="p5">**</bpt>Access Policies<ept id="p5">**</ept>, <bpt id="p6">**</bpt>Firewalls and virtual networks<ept id="p6">**</ept>.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: Your Azure account is the only one authorized to perform operations on this new vault. You can modify this if you wish in the <bpt id="p1">**</bpt>Settings<ept id="p1">**</ept> and then the <bpt id="p2">**</bpt>Access policies<ept id="p2">**</ept> section.

# <a name="task-2-add-a-secret-to-the-key-vault"></a>작업 2: Key Vault에 암호 추가
        
이 작업에서는 키 자격 증명에 암호를 추가합니다. 

1. **설정**에서 **암호**를 클릭한 다음 **+ 생성/가져오기**를 클릭합니다.

2. Configure the secret. Leave the other values at their defaults. Notice you can set an activation and expiration date. Notice you can also disable the secret.

    | 설정 | 값 | 
    | --- | --- |
    | 업로드 옵션 | **수동** |
    | Name | **ExamplePassword** |
    | 값 | **hVFkk96** |

3. **만들기**를 클릭합니다.

4. 암호가 성공적으로 만들어지면 **ExamplePassword**를 클릭하고 상태가 **사용**인지 확인합니다.

5. Select the secret you just created, note the the <bpt id="p1">**</bpt>Secret Identifier<ept id="p1">**</ept>. This is the url value that you can now use with applications. It provides a centrally managed and securely stored password. 

6. **암호 값 표시** 단추를 클릭하여 이전에 지정한 암호를 표시합니다.


Key Vault를 구성합니다(Key Vault 이름에서 **xxxx**를 문자와 숫자로 대체하여 이름을 전역적으로 고유하게 지정).

다른 항목은 기본값을 사용합니다.
