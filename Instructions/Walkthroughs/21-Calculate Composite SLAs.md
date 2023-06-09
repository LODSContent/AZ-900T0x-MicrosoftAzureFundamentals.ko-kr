---
wts:
  title: 21 - 복합 SLA 계산(5분)
  module: 'Module 06: Describe Azure cost management and service level agreements'
---
# <a name="21---calculate-composite-slas-5-min"></a>21 - 복합 SLA 계산(5분)

이 연습에서는 Azure 서비스의 가용성 SLA를 결정한 다음 애플리케이션 복합 SLA 기반 예상 가용성을 계산합니다.

예제 애플리케이션은 다음과 같은 Azure 서비스로 구성됩니다. 이 연습의 목표는 개괄적인 예제를 제공하는 것이므로 아키텍처 구성 및 고려 사항에 대해 깊게 살펴보지는 않을 예정입니다.

+ **App service**: 애플리케이션을 호스트합니다.
+ **Azure AD B2C**: 사용자 로그인을 인증하고 프로필을 관리합니다.
+ **Application Gateway**: 애플리케이션 액세스, 스케일링을 관리합니다. 
+ **Azure SQL Database**: 애플리케이션 데이터를 저장합니다. 

# <a name="task-1-determine-the-sla-uptime-percentage-values-for-our-application"></a>작업 1: 애플리케이션의 SLA 가동 시간 백분율 값 결정

1. 브라우저에서 [Azure 서비스에 대한 SLA 요약](https://azure.microsoft.com/en-us/support/legal/sla/summary/) 페이지로 이동합니다.

2. **App Service** SLA 가동 시간 값을 찾습니다. **99.95%** 입니다. **전체 세부 정보 보기**를 클릭하고 **SLA 세부 정보**를 확장합니다. **월별 가동 시간 비율** 및 **서비스 크레딧**을 확인합니다.

3. SLA 웹 페이지로 돌아가서 **Azure Active Directory B2C** 서비스를 찾고 SLA 가동 시간 값을 확인합니다. **99.9%** 입니다. 

4. **Application Gateway** SLA 가동 시간 값을 찾습니다. **99.95%** 입니다. 

5. Azure SQL Database는 프리미엄 계층을 사용하지만 영역 중복 배포에는 구성되어 있지 않습니다. **Azure SQL Database** SLA 가동 시간 값을 찾습니다. **99.99%** 입니다. 

    **참고**: Azure SQL Database의 구성 및 배포에 따라 가동 시간 값이 다릅니다. 배포 및 구성을 계획하고 비용을 청구할 때는 필요한 가동 시간 값을 명확히 하는 것이 중요합니다. 가동 시간이 조금만 달라져도 서비스 비용이 영향을 받을 수 있으며 구성이 더 복잡할 수 있습니다. Azure SLA 요약 웹 페이지에서 관심을 끌 만한 다른 서비스로는 **가상 머신**, **스토리지 계정** 및 **Cosmos DB**가 있습니다.

# <a name="task-2-calculate-the-application-composite-sla-percentage-uptime"></a>작업 2: 애플리케이션의 복합 SLA 백분율 가동 시간 계산

1. 애플리케이션을 구성하는 서비스를 사용할 수 없게 되면 사용자가 애플리케이션에 로그인하고 사용할 수 없게 됩니다. 따라서 애플리케이션의 총 가동 시간은 다음과 같이 구성됩니다.

    **App Service % 가동 시간** X **Azure AD B2C % 가동 시간** X  **Azure Application Gateway % 가동 시간** X **Azure SQL Database % 가동 시간** = **총 % 가동 시간**

    백분율로 보면 다음과 같습니다.

    **99.95%** X **99.9%** X **99.95%** X **99.99%**  = **99.79%**

    이는 현재 서비스 및 아키텍처를 사용하는 애플리케이션의 SLA 기반 예상 가용성입니다.

축하합니다! 샘플 애플리케이션의 각 서비스에 대한 SLA 기반 가동 시간을 결정한 후 애플리케이션의 SLA 기반 예상 가용성을 계산하셨습니다.
