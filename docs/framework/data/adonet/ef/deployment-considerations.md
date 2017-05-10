---
title: "배포 고려 사항(Entity Framework) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 배포 고려 사항(Entity Framework)
이 항목에서는 데이터 액세스를 위해 ADO.NET Entity Framework를 사용하는 응용 프로그램 배포에 대한 정보를 제공합니다.  Entity Framework에 대한 자세한 내용은 [시작](../../../../../docs/framework/data/adonet/ef/getting-started.md)를 참조하세요.  
  
 Entity Framework에서는 Visual Studio에서 개발을 용이하게 하는 통합된 도구 집합을 제공합니다.  자세한 내용은 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/ko-kr/91076853-0881-421b-837a-f582f36be527)을 참조하세요.  이 항목에서 Entity Framework 기반 응용 프로그램을 배포하기 위해 특정 기술을 사용하는 방법을 설명하지는 않습니다.  
  
 Visual Studio에서는 ClickOnce 배포와 같은 응용 프로그램 배포에 대한 기능을 제공합니다.  자세한 내용은 Visual Studio 설명서에서 [응용 프로그램 및 구성 요소 배포](../Topic/Deploying%20Applications,%20Services,%20and%20Components.md)를 참조하세요.  
  
 Entity Framework를 사용하는 응용 프로그램을 배포할 때 다음 사항을 고려해야 합니다.  
  
-   Entity Framework는 .NET Framework 3.5 서비스 팩 1\(SP1\)과 함께 시작하는 .NET Framework의 구성 요소입니다.  Entity Framework 기반 응용 프로그램을 배포할 때 .NET Framework 3.5 SP1 이상 버전이 설치되어 있어야 합니다.  
  
-   엔터티 데이터 모델 마법사를 통해 개념적 모델이 생성되면 응용 프로그램 구성 파일에서 연결 문자열이 만들어집니다.  모델 및 매핑 파일이 응용 프로그램 리소스로 포함되거나 출력 디렉터리에 복사될 수 있습니다.  기본적으로 모델 및 매핑 파일은 포함된 응용 프로그램 리소스로 배포됩니다.  Entity Designer 파일의 `Metadata Artifact Processing` 속성을 사용하여 이러한 옵션 중 하나를 선택합니다.  자세한 내용은 [How to: Copy Model and Mapping Files to the Output Directory](http://msdn.microsoft.com/ko-kr/e2c9820f-1705-457e-9fdb-8b289f3179b4)을 참조하세요.  
  
-   CSDL\(개념 스키마 정의 언어\), SSDL\(저장소 스키마 정의 언어\) 및 MSL\(매핑 사양 언어\)로 표현되는 모델 및 매핑 정보가 연결 문자열에 의해 지정된 위치에 응용 프로그램과 함께 배포됩니다.  자세한 내용은 [연결 문자열](../../../../../docs/framework/data/adonet/ef/connection-strings.md)을 참조하세요.  
  
-   모델 및 매핑 정보를 응용 프로그램 리소스로 포함하는 경우 개념적 모델이 업데이트될 때마다 응용 프로그램을 다시 컴파일하고 다시 배포해야 합니다.  
  
-   Entity Framework는 .NET Framework의 구성 요소이므로 .NET Framework 사용권 계약에 허용된 대로 응용 프로그램과 함께 재배포할 수 있습니다.  
  
## 참고 항목  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)   
 [개발 및 배포 고려 사항](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)