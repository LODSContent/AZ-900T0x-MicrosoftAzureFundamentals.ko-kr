---
wts:
  title: 20 - Azure TCO 계산기 사용(10분)
  module: 'Module 06: Describe Azure cost management and service level agreements'
---
# <a name="20---use-the-azure-tco-calculator-10-min"></a>20 - Azure TCO 계산기 사용(10분)


이 연습에서는 TCO(총 소유 비용) 계산기를 사용하여 온-프레미스 환경의 비용 비교 보고서를 생성합니다.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: This walkthrough provides example definitions of on-premises infrastructure and workloads for a typical datacenter. To create a TCO Calculator report, use the example definitions or provide details of your <bpt id="p1">*</bpt>actual<ept id="p1">*</ept> on-premises infrastructure and workloads.

# <a name="task-1-configure-the-tco-calculator"></a>작업 1: TCO 계산기 구성

이 작업에서는 계산기에 인프라 정보를 추가합니다. 

1. 브라우저에서 [TCO(총 소유 비용) 계산기](https://azure.microsoft.com/en-us/pricing/tco/calculator/) 페이지로 이동합니다.

2. 온-프레미스 서버 인프라의 세부 정보를 추가하기 위해 **워크로드 정의** 창에서 **+ 서버 워크로드 추가**를 클릭합니다.

    | 설정 | 값 |
    | -- | -- |
    | Name | **서버: Windows VM** |
    | 작업 | **Windows/Linux server** |
    | 환경 | **Virtual Machines** |
    | 운영 체제 | **Windows** |  
    | VM | **50** |
    | 가상화 | **Hyper-V** |
    | 코어 | **8**|
    | RAM(GB) | **16** |
    | 최적화 기준 | **CPU** |
    | Windows Server 2008/2008 R2 | 해제 |

3. **+ 서버 워크로드 추가**를 선택하여 새 서버 워크로드정의에 대한 행을 만듭니다. 

    | 설정 | 값 |
    | -- | -- |
    | Name | **서버: Linux VM** |
    | 작업 | **Windows/Linux server** |
    | 환경 | **Virtual Machines** |
    | 운영 체제 | **Linux** |  
    | VM | **50** |
    | 가상화 | **VMware** |
    | 코어 | **8**|
    | RAM(GB) | **16** |
    | 최적화 기준 | **CPU** |
    | Windows Server 2008/2008 R2 | 해제 |

4. **스토리지** 창에서 **스토리지 추가**를 클릭합니다.

    | 설정 | 값 |
    | -- | -- |
    | Name | **서버 스토리지** |
    | 스토리지 유형 | **로컬 디스크/SAN** |
    | 디스크 유형 | **HDD** |
    | 용량 | **60TB** |  
    | Backup | **120TB** |
    | 보관 | **0TB** |

5. **네트워킹** 창에서 대역폭을 추가합니다. 

    | 설정 | 값 |
    | -- | -- |
    | 아웃바운드 대역폭 | 15TB|

6. **다음**을 클릭합니다.

7. 옵션을 탐색하고 필요한 사항을 조정합니다. 

    | 설정 | 값 |
    | -- | -- |
    | 통화 | **유로** |

8. **다음**을 클릭합니다.

# <a name="task-2-review-the-results-and-save-a-copy"></a>작업 2: 결과를 검토하고 복사본 저장

이 작업에서는 비용 절감 권장 사항을 검토하고 보고서를 다운로드합니다. 

1. Azure 비용 절감 권장 사항 및 시각화를 검토합니다.

    | 설정 | 값 |
    | -- | -- |
    | 시간 범위| **3년** |
    | 지역 | **북유럽** |

2. 제공한 정보를 수정하려면 페이지 아래쪽으로 이동하고 **뒤로**를 클릭합니다. 

3. 보고서의 PDF 사본을 저장하거나 인쇄하려면 **다운로드**를 클릭합니다.

    ![Screenshot of the report pane of the tco calculator in Azure. The highlighted and completed input fields indicates how set the tco calculator timeframe to three years and the region to north europe. A graph shows the cost of on-premises infrastructure and workloads off-set against the reduced cost of using Azure.](../images/2001.png)

Congratulations! You have used the TCO Calculator to generate a cost comparison report for an on-premises environment.
