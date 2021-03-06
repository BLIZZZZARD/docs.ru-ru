---
title: "Расширение разметки ComponentResourceKey"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4bfaee35ba9f8cf60deb01c52a142433d08021c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="componentresourcekey-markup-extension"></a>Расширение разметки ComponentResourceKey
Определения и ключи для ресурсов, которые загружаются из внешних сборок ссылок. Это позволяет при поиске ресурса указать целевой тип в сборке, вместо явного словаря ресурса в сборке или в классе.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Использование атрибута XAML (Установка ключа, компактный)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Использование атрибута XAML (Установка ключа, подробный)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Использование атрибута XAML (запрос ресурса, компактный)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Использование атрибута XAML (запрос ресурса, подробный)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>Значения XAML  
  
|||  
|-|-|  
|`targetTypeName`|Имя открытого [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] типа, определенного в сборке ресурсов.|  
|`targetID`|Ключ ресурса. Если ресурсы ищутся, `targetID` будет аналогичен [директива x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) ресурса.|  
  
## <a name="remarks"></a>Примечания  
 Как показано в вариантах применения выше, {`ComponentResourceKey`} расширение разметки находится в двух местах:  
  
-   Определение ключ в словаре ресурсов тем, предоставляемые автором элемента управления.  
  
-   Если доступ к ресурсу темы из сборки, являются создания новых шаблонов элемента управления, но нужно использовать значения свойств из ресурсов, предоставленных темами элемента управления.  
  
 Для ссылки на компонент ресурсов, поступивших из темы, обычно рекомендуется использовать `{DynamicResource}` вместо `{StaticResource}`. Это показано в вариантах применения. `{DynamicResource}`рекомендуется, поскольку тема сама по себе может быть изменена пользователем. Если требуется ресурс компонента, который наиболее близко соответствует цели автора элемента управления для поддержки темы, следует включить компонент ресурсов справочной информации для также быть динамическими.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Определяет тип, который существует в целевой сборки, где фактически определенных ресурсов. Объект `ComponentResourceKey` определяется и используется независимо от точно знать, где <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> определен, но в конечном счете необходимо разрешить тип из сборок, на которую указывает ссылка.  
  
 Распространенным вариантом применения для <xref:System.Windows.ComponentResourceKey> необходимо определить ключи, которые затем отображаются как члены класса. Для такого использования, используйте <xref:System.Windows.ComponentResourceKey> конструктора класса, не расширения разметки. Дополнительные сведения см. в разделе <xref:System.Windows.ComponentResourceKey>, либо в разделе «Определение и создание ссылок на ключи для темы ресурсов» раздела [элементах](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Для установки ключей и ссылки на различаемых ресурсы, синтаксис атрибутов обычно используется для `ComponentResourceKey` расширения разметки.  
  
 Компактный синтаксис, показанный зависит <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> сигнатуры конструктора и использование позиционного параметра расширения разметки. Порядок, в котором `targetTypeName` и `targetID` получают важен. Подробный синтаксис зависит от <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> конструктор по умолчанию, а затем устанавливает <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> и <xref:System.Windows.ComponentResourceKey.ResourceId%2A> в результате которого аналогичен синтаксису true атрибутов элемента объекта. В подробном синтаксисе порядок, в котором задаются свойства не имеет значения. Связь и механизмы из этих двух вариантов (компактный и подробный синтаксис) является более подробно в разделе [расширения разметки и WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 С технической точки зрения значение `targetID` может быть любым объектом, не имеет в виде строки. Наиболее распространенное использование в WPF то, чтобы выровнять `targetID` значение с формами, которые представляют собой строки, а когда такие строки являются допустимыми в [Грамматика XamlName](../../../../docs/framework/xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey`может использоваться в синтаксисе элемента объекта. В этом случае укажите значение параметра оба <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> и <xref:System.Windows.ComponentResourceKey.ResourceId%2A> свойства, необходимые для правильной инициализации расширения.  
  
 В [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] реализацию средства чтения, обработка для данного расширения разметки определяется <xref:System.Windows.ComponentResourceKey> класса.  
  
 `ComponentResourceKey` является расширением разметки. Расширения разметки обычно реализуются, если требуется заменить значения атрибутов на нелитеральные значения или имена обработчиков и если требуется больше, чем простая настройка преобразователей типов на работу с определенными типами или свойствами. Все расширения разметки в [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] используют символы "{" и "}" в синтаксисе их атрибутов, который является соглашением, по которому обработчик [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] распознает, что расширение разметки должно обработать атрибут. Дополнительные сведения см. в разделе [Расширения разметки и XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.ComponentResourceKey>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Общие сведения о разработке элементов управления](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Общие сведения о языке XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Расширения разметки и XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
