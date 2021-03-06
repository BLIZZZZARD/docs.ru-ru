---
title: "Изменение узлов, содержимого и значений в XML-документе"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 00b923edb95852d9434db1b393df68fd9d0c8a1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>Изменение узлов, содержимого и значений в XML-документе
Существует множество способов изменения узлов и содержимого в документе. Можно выполнить следующие действия.  
  
-   изменять значение узлов с помощью свойства <xref:System.Xml.XmlNode.Value%2A>;  
  
-   изменять набор узлов в целом, заменяя узлы новыми. Это делается с помощью свойства <xref:System.Xml.XmlNode.InnerXml%2A>;  
  
-   заменять существующие узлы новыми с помощью метода <xref:System.Xml.XmlNode.RemoveChild%2A>;  
  
-   добавлять в узлы дополнительные символы, наследующие от класса <xref:System.Xml.XmlCharacterData>, используя методы <xref:System.Xml.XmlCharacterData.AppendData%2A>, <xref:System.Xml.XmlCharacterData.InsertData%2A> или <xref:System.Xml.XmlCharacterData.ReplaceData%2A>;  
  
-   изменять содержимое путем удаления диапазона символов с помощью метода <xref:System.Xml.XmlCharacterData.DeleteData%2A> для типов узлов, наследующих от <xref:System.Xml.XmlCharacterData>.  
  
 Изменить значение узла можно с помощью простого приема `node.Value = "new value";`. В следующей таблице перечислены типы узлов, в которых работает эта строка кода, и указано, какие данные изменяются для этого типа узла.  
  
|Тип узла|Изменяемые данные|  
|---------------|------------------|  
|Атрибут|Значение атрибута.|  
|CDATASection.|Содержимое CDATASection.|  
|Комментарий|Содержимое комментария.|  
|ProcessingInstruction;|Содержимое, за исключением цели.|  
|Text|Содержимое текстового узла.|  
|XmlDeclaration|Содержимое декларации, за исключением разметки `<?xml` и `?>`.|  
|Whitespace|Значение символа пробела. В качестве значения можно задать один из четырех различаемых в XML пробельных символов: пробел, табуляция, CR или LF.|  
|SignificantWhitespace|Значение значащих пробелов. В качестве значения можно задать один из четырех различаемых в XML пробельных символов: пробел, табуляция, CR или LF.|  
  
 Типы узлов, не представленные в таблице, являются недопустимыми для установки значений. При установке значения в узле такого типа вызывается исключение <xref:System.InvalidOperationException>.  
  
 Свойство <xref:System.Xml.XmlNode.InnerXml%2A> изменяет разметку дочерних узлов текущего узла. Задание этого свойства замещает дочерние узлы значением заданной строки, содержимое которой прошло синтаксический анализ. Синтаксический анализ выполняется в контексте текущего пространства имен. Кроме того, свойство <xref:System.Xml.XmlNode.InnerXml%2A> удаляет избыточные декларации пространств имен. В результате после многочисленных операций вырезания и вставки размер документа не будет увеличиваться за счет избыточных деклараций пространств имен. Пример кода, демонстрирующий влияние пространств имен на работу <xref:System.Xml.XmlNode.InnerXml%2A>, см. в свойстве <xref:System.Xml.XmlDocument.InnerXml%2A>.  
  
 Использование методов <xref:System.Xml.XmlCharacterData.ReplaceData%2A> и <xref:System.Xml.XmlNode.RemoveChild%2A> возвращает замещенный или удаленный узел. Затем этот узел можно повторно вставить в другом месте модели XML DOM. Метод <xref:System.Xml.XmlCharacterData.ReplaceData%2A> выполняет двойную проверку узла, вставляемого в документ. Первая проверка обеспечивает то, что узел становится дочерним для узла, который может иметь дочерние узлы такого типа. Вторая проверка обеспечивает то, что вставляемый узел не является предком узла, для которого он становится дочерним. Несоблюдение любого из этих условий вызывает исключение <xref:System.InvalidOperationException>.  
  
 Допустимо добавлять дочерний узел, доступный только для чтения, в узел, поддерживающий изменение, или удалять из него. Однако при попытке изменить сам узел, доступный только для чтения, вызывается исключение <xref:System.InvalidOperationException>. Примером может служить изменение потомков узла <xref:System.Xml.XmlEntityReference>. Потомки доступны только для чтения, и их нельзя изменить. Любая попытка изменить вызывает исключение <xref:System.InvalidOperationException>.  
  
## <a name="see-also"></a>См. также  
 [Модель объектов XML-документов (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
