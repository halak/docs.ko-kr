---
title: '방법: XDocument, XElement 또는 LINQ for XML 쿼리 결과에 바인딩'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: 7e4f9cc2f5e6815a35b4911f5b4a480161d66ef3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556694"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>방법: XDocument, XElement 또는 LINQ for XML 쿼리 결과에 바인딩
XML 데이터를 바인딩하는 방법을 보여 주는이 예제는 <xref:System.Windows.Controls.ItemsControl> 를 사용 하 여 <xref:System.Xml.Linq.XDocument>합니다.  
  
## <a name="example"></a>예제  
 다음 XAML 코드 정의 <xref:System.Windows.Controls.ItemsControl> 형식의 데이터에 대 한 데이터 템플릿을 포함 `Planet` 에 `http://planetsNS` XML 네임 스페이스입니다. 네임스페이스를 차지하는 XML 데이터 형식은 중괄호에서 네임스페이스를 포함해야 하고 XAML 태그 확장이 표시되는 위치에 표시되는 경우 중괄호 이스케이프 시퀀스를 가진 네임스페이스 앞에 표시되어야 합니다. 이 코드에 해당 하는 동적 속성에 바인딩하는 <xref:System.Xml.Linq.XContainer.Element%2A> 및 <xref:System.Xml.Linq.XElement.Attribute%2A> 의 메서드는 <xref:System.Xml.Linq.XElement> 클래스입니다. 동적 속성을 사용하면 XAML을 메서드의 이름을 공유하는 동적 속성에 바인딩할 수 있습니다. 자세한 내용은 [LINQ to XML 동적 속성](/visualstudio/designers/linq-to-xml-dynamic-properties)을 참조하세요. XML의 기본 네임스페이스 선언이 특성 이름에 적용되지 않는지를 확인합니다.  
  
 [!code-xaml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 다음 C# 코드에서는 <xref:System.Xml.Linq.XDocument.Load%2A> 라는 요소의 모든 하위 요소를 스택 패널 데이터 컨텍스트를 설정 하 고 `SolarSystemPlanets` 에 `http://planetsNS` XML 네임 스페이스입니다.  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 XML 데이터를 사용 하 여 XAML 리소스도 저장할 수 <xref:System.Windows.Data.ObjectDataProvider>합니다. 전체 예제는 [L2DBForm.xaml 소스 코드](http://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e)를 참조하세요. 다음 샘플에서는 코드가 데이터 컨텍스트를 개체 리소스로 설정하는 방법을 보여 줍니다.  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 동적 속성에 매핑되는 <xref:System.Xml.Linq.XContainer.Element%2A> 및 <xref:System.Xml.Linq.XElement.Attribute%2A> XAML 내에서 유연성을 제공 합니다. 코드는 LINQ for XML 쿼리의 결과에 바인딩될 수도 있습니다. 이 예제는 요소 값으로 정렬된 쿼리 결과에 바인딩됩니다.  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a>참고 항목  
 [바인딩 소스 개요](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [LINQ to XML로 WPF 데이터 바인딩 개요](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)  
 [LINQ to XML 예제를 사용한 WPF 데이터 바인딩](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)  
 [LINQ to XML 동적 속성](/visualstudio/designers/linq-to-xml-dynamic-properties)
