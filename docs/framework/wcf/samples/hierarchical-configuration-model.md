---
title: 계층적 구성 모델
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: 233a8d4ba36835ab26e0c4a8cd044cf60d497a0b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806632"
---
# <a name="hierarchical-configuration-model"></a>계층적 구성 모델
이 샘플에서는 서비스의 구성 파일 계층 구조를 구현하는 방법을 보여 줍니다. 또한 계층 구조의 상위 수준에서 바인딩, 서비스 동작 및 끝점 동작이 상속되는 방식을 보여 줍니다.  
  
## <a name="sample-details"></a>샘플 세부 정보  
 WCF에 용으로 개발 된 기능 중 하나는 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 는 향상 된 계층적 구성 모델입니다. 계층적 구성 모델의 예로는 Machine.config -> Rootweb.config -> Web.config로 정의되는 구성 모델이 있습니다. [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]에서는 명시적으로 구성할 필요 없이 구성 계층 구조의 상위 수준에 정의된 바인딩 및 동작이 서비스에 추가됩니다. 이 샘플에서는 컴퓨터 또는 응용 프로그램 수준에 정의된 구성 요소를 사용하여 서비스 구성을 단순화하는 방법을 보여 줍니다.  
  
 이 샘플은 계층 구조의 세 수준에 정의된 9개의 서비스로 구성되어 있습니다. `Service1`은 루트에 있습니다. `Service2` 및 `Service3`는 `Service1`에서 기본 요소를 상속합니다. `Service4`, `Service5`, `Service6` 및 `Service7`은 계층 구조의 세 번째 수준에 정의되어 있으며 `Service3`에서 기본 요소를 상속합니다. 마지막으로 `Service10` 및 `Service11`은 계층 구조의 네 번째 수준에 있습니다.  
  
 모든 서비스는 `IDesc` 계약을 구현합니다. 다음은 이 인터페이스에 노출되는 메서드를 보여 주는 `IDesc` 인터페이스의 정의입니다. `IDesc` 인터페이스는 Service1.cs에 정의되어 있습니다.  
  
```  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
```  
  
 서비스에서 이러한 메서드를 구현하는 과정은 간단합니다. `ListEndpoints`는 모든 서비스 끝점을 반복하고 서비스에 있는 모든 끝점의 목록을 반환합니다. `ListServiceBehaviors`는 서비스에 추가된 모든 동작을 반복하고 서비스와 관련된 모든 서비스 동작의 목록을 반환합니다. `ListEndpointBehaviors`는 끝점 동작의 목록을 반환한다는 점을 제외하고는 `ListServiceBehaviors`와 유사한 방식으로 동작합니다.  
  
 이 구현을 통해 클라이언트는 서비스에서 노출하는 끝점 수와 서비스에 추가된 서비스 동작 및 끝점 동작을 알 수 있습니다. 샘플의 일부로 구현된 클라이언트에서는 솔루션의 모든 서비스에 대한 서비스 참조를 추가하고 각 서비스에 대한 이러한 요소를 보여 줍니다.  
  
## <a name="to-use-this-sample"></a>이 샘플을 사용하려면  
  
#### <a name="to-run-the-client"></a>클라이언트를 실행하려면  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]에서 ConfigHierarchicalModel.sln 파일을 엽니다.  
  
2.  클라이언트 프로젝트가 아직 시작 프로젝트로 설정되지 않은 경우 다음 단계를 따릅니다.  
  
    1.  **솔루션 탐색기**를 솔루션을 마우스 오른쪽 단추로 클릭 한 다음 선택 **속성**합니다.  
  
    2.  **공용 속성**선택, **시작 프로젝트**, 클릭 하 고 **개의 시작 프로젝트**합니다.  
  
    3.  **개의 시작 프로젝트** 드롭다운 목록에서 선택 **클라이언트**합니다.  
  
    4.  클릭 **확인** 는 대화 상자를 닫습니다.  
  
3.  Ctrl+Shift+B를 눌러 샘플을 빌드합니다.  
  
4.  Ctrl+F5를 눌러 클라이언트를 실행합니다.  
  
> [!NOTE]
>  이러한 단계가 제대로 수행되지 않으면 다음 단계를 따라 사용 환경이 올바르게 설정되었는지 확인하세요.  
>   
>  1.  수행 했는지 확인 하십시오.는 [Windows Communication Foundation 샘플의 일회 설치 절차](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)합니다.  
> 2.  지침에 따라 솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](../../../../docs/framework/wcf/samples/building-the-samples.md)합니다.  
> 3.  지침에 따라 단일 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](../../../../docs/framework/wcf/samples/running-the-samples.md)합니다.  
  
> [!IMPORTANT]
>  컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다. 계속하기 전에 다음(기본) 디렉터리를 확인하세요.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  이 디렉터리가로 이동 [Windows Communication Foundation (WCF) 및.NET Framework 4에 대 한 Windows WF (Workflow Foundation) 샘플](http://go.microsoft.com/fwlink/?LinkId=150780) 모든 Windows Communication Foundation (WCF)를 다운로드 하 고 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 샘플. 이 샘플은 다음 디렉터리에 있습니다.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a>참고 항목  
 [AppFabric 관리 샘플](http://go.microsoft.com/fwlink/?LinkId=193960)
