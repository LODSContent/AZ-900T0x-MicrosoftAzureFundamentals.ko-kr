---
wts:
  title: 21 - 복합 SLA 계산(5분)
  module: 'Module 06: Describe Azure cost management and service level agreements'
---
# <a name="21---calculate-composite-slas-5-min"></a>21 - 복합 SLA 계산(5분)

이 연습에서는 Azure 서비스의 가용성 SLA를 결정한 다음 애플리케이션 복합 SLA 기반 예상 가용성을 계산합니다.

Our example application consists of these Azure services. We will not go in to deep architectural configuration and considerations, the intention here is to give an high level example.

+ **App service**: 애플리케이션을 호스트합니다.
+ **Azure AD B2C**: 사용자 로그인을 인증하고 프로필을 관리합니다.
+ **Application Gateway**: 애플리케이션 액세스, 스케일링을 관리합니다. 
+ **Azure SQL Database**: 애플리케이션 데이터를 저장합니다. 

# <a name="task-1-determine-the-sla-uptime-percentage-values-for-our-application"></a>작업 1: 애플리케이션의 SLA 가동 시간 백분율 값 결정

1. 브라우저에서 [Azure 서비스에 대한 SLA 요약](https://azure.microsoft.com/en-us/support/legal/sla/summary/) 페이지로 이동합니다.

2. Locate the <bpt id="p1">**</bpt>App Service<ept id="p1">**</ept> SLA uptime value, <bpt id="p2">**</bpt>99.95%<ept id="p2">**</ept>. Click <bpt id="p1">**</bpt>View full details<ept id="p1">**</ept>, and then expand <bpt id="p2">**</bpt>SLA details<ept id="p2">**</ept>. Notice the <bpt id="p1">**</bpt>Monthly uptime percentages<ept id="p1">**</ept> and <bpt id="p2">**</bpt>Service Credits<ept id="p2">**</ept>.

3. SLA 웹 페이지로 돌아가서 **Azure Active Directory B2C** 서비스를 찾고 SLA 가동 시간 값을 확인합니다. **99.9%** 입니다. 

4. **Application Gateway** SLA 가동 시간 값을 찾습니다. **99.95%** 입니다. 

5. The Azure SQL database uses Premium tiers but is not configured for Zone Redundant Deployments. Locate the <bpt id="p1">**</bpt>Azure SQL Database<ept id="p1">**</ept> SLA uptime value, <bpt id="p2">**</bpt>99.99%<ept id="p2">**</ept>. 

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: There are different uptime values for different configurations and deployments of Azure SQL Database. It is important you are clear on your required uptime values, when planning and costing your deployment and configuration. Small changes in uptime can have impact on service costs as well as potentially increase complexity in configuration. Some other services that may be of interest on the Azure SLA summary web page would include <bpt id="p1">**</bpt>Virtual Machines<ept id="p1">**</ept>, <bpt id="p2">**</bpt>Storage Accounts<ept id="p2">**</ept> and <bpt id="p3">**</bpt>Cosmos DB<ept id="p3">**</ept>.

# <a name="task-2-calculate-the-application-composite-sla-percentage-uptime"></a>작업 2: 애플리케이션의 복합 SLA 백분율 가동 시간 계산

1. 예제 애플리케이션은 다음과 같은 Azure 서비스로 구성됩니다.

    **App Service % 가동 시간** X **Azure AD B2C % 가동 시간** X  **Azure Application Gateway % 가동 시간** X **Azure SQL Database % 가동 시간** = **총 % 가동 시간**

    백분율로 보면 다음과 같습니다.

    **99.95%** X **99.9%** X **99.95%** X **99.99%**  = **99.79%**

    이는 현재 서비스 및 아키텍처를 사용하는 애플리케이션의 SLA 기반 예상 가용성입니다.

이 연습의 목표는 개괄적인 예제를 제공하는 것이므로 아키텍처 구성 및 고려 사항에 대해 깊게 살펴보지는 않을 예정입니다.
