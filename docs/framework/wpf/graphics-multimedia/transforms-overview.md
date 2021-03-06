---
title: "Общие сведения о классах Transform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2-D transform
- transform classes [WPF], 2-D
- 2-D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4992b5be4243d8d29b6075c0ad746494dc2eb168
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="transforms-overview"></a>Общие сведения о классах Transform
В этом разделе описывается использование [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> классы для поворота, масштабирования, сдвига и наклона <xref:System.Windows.FrameworkElement> объектов.  
  
  
<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>Что такое преобразование?  
 Объект <xref:System.Windows.Media.Transform> определяет способ сопоставления или преобразования точек из одной системы координат в другую системы координат. Это сопоставление описано преобразованием <xref:System.Windows.Media.Matrix>, которое является коллекцией из трех строк с тремя столбцами из <xref:System.Double> значения.  
  
> [!NOTE]
>  В [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] используются матрицы на основе строк. Векторы представляют собой массивы на основе строк, а не на основе столбцов.  
  
 В следующей таблице показана структура матрицы [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="a-2-d-transformation-matrix"></a>Матрица двумерного преобразования  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> По умолчанию: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> По умолчанию: 0.0|0,0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> По умолчанию: 0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> По умолчанию: 1.0|0,0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> По умолчанию: 0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> По умолчанию: 0.0|1.0|  
  
 Изменяя значения элементов матрицы, можно поворачивать, масштабировать, наклонять и перемещать объект. Например, если изменить значение в первом столбце третьей строки ( <xref:System.Windows.Media.Matrix.OffsetX%2A> значение) до 100, он используется переместить объект на 100 единиц вдоль оси x. Если изменить значение во втором столбце второй строки на 3, можно использовать его для растяжения объекта в три раза больше по сравнению с текущим размером. Если изменить оба значения, объект будет перемещен на 100 единиц по оси X, а его ширина будет увеличена в 3 раза. Так как [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] поддерживает только аффинные преобразования, в правом столбце всегда указаны значения 0, 0, 1.  
  
 Несмотря на то что [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] дает возможность непосредственно управлять значениями матрицы, она также предоставляет несколько <xref:System.Windows.Media.Transform> классы, которые позволяют преобразовывать объект, не зная структуры матрицы. Например <xref:System.Windows.Media.ScaleTransform> позволяет масштабировать объект, установив его <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> и <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> свойства, вместо изменения матрицы преобразования. Аналогичным образом <xref:System.Windows.Media.RotateTransform> позволяет повернуть объект, просто задав его <xref:System.Windows.Media.RotateTransform.Angle%2A> свойство.  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Классы преобразования  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]предоставляет следующие [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> классы для общих операций преобразования:  
  
|Класс|Описание:|Пример|Рисунки|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Поворачивает элемент по заданному <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Вращение объекта](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object.md)|![Иллюстрация вращения](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Масштабирует элемент с указанным <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> и <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> суммы.|[Масштабирование элемента](../../../../docs/framework/wpf/graphics-multimedia/how-to-scale-an-element.md)|![Иллюстрация масштабирования](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Наклон элемент на указанный <xref:System.Windows.Media.SkewTransform.AngleX%2A> и <xref:System.Windows.Media.SkewTransform.AngleY%2A> суммы.|[Наклон элемента](../../../../docs/framework/wpf/graphics-multimedia/how-to-skew-an-element.md)|![Иллюстрация наклона](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Перемещает (преобразует) элемент по заданному <xref:System.Windows.Media.TranslateTransform.X%2A> и <xref:System.Windows.Media.TranslateTransform.Y%2A> суммы.|[Перемещение элемента](../../../../docs/framework/wpf/graphics-multimedia/how-to-translate-an-element.md)|![Иллюстрация перемещения](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Для более сложных преобразований [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] предоставляет следующие два класса.  
  
|Класс|Описание:|Пример|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Группирует несколько <xref:System.Windows.Media.TransformGroup> объектов в один <xref:System.Windows.Media.Transform> , затем можно применить преобразования свойств.|[Применение нескольких преобразований к объекту](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Создает настраиваемые преобразования, не предоставляются другим <xref:System.Windows.Media.Transform> классы. При использовании <xref:System.Windows.Media.MatrixTransform>, матрица управления напрямую.|[Использование MatrixTransform для создания пользовательских преобразований](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] также предоставляет преобразования [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]. Дополнительные сведения см. в описании класса <xref:System.Windows.Media.Media3D.Transform3D>.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Общие свойства преобразования  
 Один из способов преобразования объекта является объявление соответствующего <xref:System.Windows.Media.Transform> введите и применить его к свойству преобразования объекта. У различных типов объектов есть различные типы свойств преобразования. В следующей таблице перечислены некоторые часто используемые типы [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] и их свойства преобразования.  
  
|Тип|Свойства преобразования|  
|----------|-------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## <a name="transformations-and-coordinate-systems"></a>Преобразования и системы координат  
 При преобразовании объекта преобразуется не только объект, но и пространство координат, в котором он существует. По умолчанию в качестве центральной точки для преобразования используется начало системы координат целевого объекта: (0, 0). Единственное исключение — <xref:System.Windows.Media.TranslateTransform>; <xref:System.Windows.Media.TranslateTransform> не имеет свойства центра для так, как перевод действует так же, независимо от того, где он находился по центру.  
  
 В следующем примере используется <xref:System.Windows.Media.RotateTransform> Поворачиваемый <xref:System.Windows.Shapes.Rectangle> элементу, тип <xref:System.Windows.FrameworkElement>, на 45 градусов относительно его центра по умолчанию (0, 0). На следующем рисунке показан результат поворота.  
  
 ![FrameworkElement, повернутая на 45 градусов относительно &#40; 0,0 &#41; ] (../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Элемент Rectangle, повернутый на 45 градусов относительно точки (0,0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 По умолчанию элемент поворачивается относительно левого верхнего угла: (0, 0). <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform>, И <xref:System.Windows.Media.SkewTransform> классы предоставляют свойства CenterX и CenterY, которые позволяют указать точку, с которой применяется преобразование.  
  
 В следующем примере также используется <xref:System.Windows.Media.RotateTransform> Поворачиваемый <xref:System.Windows.Shapes.Rectangle> элемент на 45 градусов; тем не менее, это время <xref:System.Windows.Media.RotateTransform.CenterX%2A> и <xref:System.Windows.Media.RotateTransform.CenterY%2A> свойств, чтобы <xref:System.Windows.Media.RotateTransform> имеет центр (25, 25). На следующем рисунке показан результат поворота.  
  
 ![Геометрическая фигура, повернутая на 45 градусов о &#40; 25, 25 &#41; ] (../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Элемент Rectangle, повернутый на 45 градусов относительно точки (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>Преобразование элемента FrameworkElement  
 Применение преобразований к <xref:System.Windows.FrameworkElement>, создайте <xref:System.Windows.Media.Transform> и применить его к одному из двух свойств, <xref:System.Windows.FrameworkElement> класс предоставляет:  
  
-   <xref:System.Windows.FrameworkElement.LayoutTransform%2A>— Преобразование, которое применяется до передачи макета. После применения преобразования система разметки обрабатывает преобразованные размер и положение элемента.  
  
-   <xref:System.Windows.UIElement.RenderTransform%2A>— Преобразование, которое изменяет внешний вид элемента, но применяется после завершения передачи макета. С помощью <xref:System.Windows.UIElement.RenderTransform%2A> вместо <xref:System.Windows.FrameworkElement.LayoutTransform%2A> можно получить выигрыш в производительности.  
  
 Какое свойство следует использовать? Из-за повышение производительности, которые он предоставляет, используйте <xref:System.Windows.UIElement.RenderTransform%2A> свойство всякий раз, когда возможно, особенно при использовании анимации <xref:System.Windows.Media.Transform> объектов. Используйте <xref:System.Windows.FrameworkElement.LayoutTransform%2A> свойство при масштабирования, поворота или наклона и вы должны преобразованный ширины элемента родительского элемента. Обратите внимание, что, если они используются с <xref:System.Windows.FrameworkElement.LayoutTransform%2A> свойства <xref:System.Windows.Media.TranslateTransform> объектов, по-видимому, не влияют на элементы. Это вызвано тем, что система разметки возвращает преобразуемый элемент в исходное положение в ходе обработки.  
  
 Дополнительные сведения о разметке в [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] см. в разделе [Общие сведения о разметке](../../../../docs/framework/wpf/advanced/layout.md).  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Пример: поворот элемента FrameworkElement на 45 градусов  
 В следующем примере используется <xref:System.Windows.Media.RotateTransform> для поворота по часовой стрелке кнопки на 45 градусов. Кнопка содержится в <xref:System.Windows.Controls.StackPanel> , имеет две другие кнопки.  
  
 По умолчанию <xref:System.Windows.Media.RotateTransform> поворачивается вокруг точки (0, 0). Так как в примере не задана центральная точка, то кнопка поворачивается вокруг точки (0, 0), т. е. левого верхнего угла. <xref:System.Windows.Media.RotateTransform> Применяется к <xref:System.Windows.UIElement.RenderTransform%2A> свойство. На рисунке ниже показан результат преобразования.  
  
 ![Преобразованная кнопка с использованием RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Поворот на 45 градусов по часовой стрелке вокруг левого верхнего угла  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 В следующем примере также используется <xref:System.Windows.Media.RotateTransform> для поворота кнопки на 45 градусов по часовой стрелке, но он также задает <xref:System.Windows.UIElement.RenderTransformOrigin%2A> кнопки (0,5, 0,5). Значение <xref:System.Windows.UIElement.RenderTransformOrigin%2A> определяется размер кнопки. В результате кнопка поворачивается вокруг центра, а не вокруг левого верхнего угла. На рисунке ниже показан результат преобразования.  
  
 ![Кнопка, преобразованная по центру](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Поворот на 45 градусов по часовой стрелке вокруг центра  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 В следующем примере используется <xref:System.Windows.FrameworkElement.LayoutTransform%2A> вместо <xref:System.Windows.UIElement.RenderTransform%2A> свойство для поворота кнопки.  При этом преобразование влияет на разметку кнопки, что приводит к запуску полного прохода системы разметки. Так как размер кнопки был изменен, то после поворота кнопки также изменяется ее положение. На рисунке ниже показан результат преобразования.  
  
 ![Преобразованная кнопка с использованием LayoutTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
Поворот кнопки с использованием LayoutTransform  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Анимация преобразований  
 Так как они наследуют от <xref:System.Windows.Media.Animation.Animatable> класса <xref:System.Windows.Media.Transform> классы могут быть анимированы. Для анимации <xref:System.Windows.Media.Transform>, применения анимации совместимого типа, свойства, для которого должна начаться анимация.  
  
 В следующем примере используется <xref:System.Windows.Media.Animation.Storyboard> и <xref:System.Windows.Media.Animation.DoubleAnimation> с <xref:System.Windows.Media.RotateTransform> вносить <xref:System.Windows.Controls.Button> вращаться при его выборе.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Полный пример см. в разделе [Примеры двумерных преобразований](http://go.microsoft.com/fwlink/?LinkID=158252). Дополнительные сведения об анимации см. в разделе [Общие сведения об эффектах анимации](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Возможности объектов Freezable  
 Так как он наследуется от <xref:System.Windows.Freezable> класса, <xref:System.Windows.Media.Transform> класса обладают рядом специальных возможностей: <xref:System.Windows.Media.Transform> объектов могут быть объявлены как [ресурсов](../../../../docs/framework/wpf/advanced/xaml-resources.md), общие для нескольких объектов, доступным только для чтения для повышения производительность, клонировать и делать потокобезопасными. Дополнительные сведения о различных возможностях, предоставляемых <xref:System.Windows.Freezable> объектов, в разделе [Freezable Общие сведения об объектах](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Matrix>  
 [Разделы практического руководства](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Пример двумерных преобразований](http://go.microsoft.com/fwlink/?LinkID=158252)
