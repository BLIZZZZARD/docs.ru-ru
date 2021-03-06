---
title: "Практическое руководство. Анимация свойства без раскадровки"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a1292dae3a6fc7e86387ecbe3bf2b1da6912cc0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>Практическое руководство. Анимация свойства без раскадровки
В этом примере показан один из способов применения анимации свойства без использования <xref:System.Windows.Media.Animation.Storyboard>.  
  
> [!NOTE]
>  Эта функциональность недоступна в [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Дополнительные сведения об анимации свойств в [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] см. в разделе [Анимация свойства с помощью раскадровки](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Чтобы применить локальную анимацию к свойству, используйте <xref:System.Windows.UIElement.BeginAnimation%2A> метод. Этот метод принимает два параметра: <xref:System.Windows.DependencyProperty> , указывающий анимируемое свойство и анимации, применяемую к этому свойству.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как анимация ширины и цвета фона <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Различные классы анимации в <xref:System.Windows.Media.Animation> существует пространство имен для анимации различных типов свойств. Дополнительные сведения об анимации свойств см. в разделе [Общие сведения об эффектах анимации](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Дополнительные сведения о свойствах зависимостей (тип свойств, приведенных в этих примерах) и их функциях см. в разделе [Общие сведения о свойствах зависимостей](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 Существуют другие способы анимации без использования <xref:System.Windows.Media.Animation.Storyboard> объектов; Дополнительные сведения см. в разделе [Общие сведения о методах анимации свойства](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [Общие сведения о методах анимации свойств](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Общие сведения об эффектах анимации](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
