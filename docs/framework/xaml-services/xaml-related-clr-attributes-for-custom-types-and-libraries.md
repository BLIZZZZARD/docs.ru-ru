---
title: "Относящиеся к XAML атрибуты среды CLR для пользовательских типов и библиотек"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25aac1d4478279561cbcdda6c1cf912c3c3b2cde
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Относящиеся к XAML атрибуты среды CLR для пользовательских типов и библиотек
В этом разделе описаны общие атрибуты языка среды CLR, определенные в службах XAML .NET Framework. Здесь также описываются другие атрибуты среды CLR, которые определены в .NET Framework, которые ситуации, связанные с XAML, для приложения для сборки или типы. Присвоение атрибутов сборки, типы или члены этих атрибутов CLR предоставляет о системе типов XAML, связанную с пользовательскими типами. Сведения предоставляются потребителю XAML, использующий служб XAML .NET Framework для обработки потока узлов XAML напрямую или через выделенные средства чтения и записи XAML.  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Атрибуты среды CLR, связанные с XAML для пользовательских типов и пользовательских элементов  
 Использование атрибутов CLR подразумевает CLR в целом используется для определения типов, в противном случае такие атрибуты не доступны. При использовании среды CLR для определения резервирования типов контекст схемы XAML по умолчанию, используемый средствами записи XAML служб XAML .NET Framework можно прочитать атрибуты среды CLR через отражение в резервных сборках.  
  
 В следующих разделах описаны атрибуты, связанные с XAML, которые можно применять к пользовательским типам и пользовательские элементы. Каждый атрибут CLR передает сведения, относящиеся к системе типов XAML. В пути загрузки информация атрибутов либо помогает средству чтения XAML сформировать допустимый поток узлов XAML, или он позволяет средству записи XAML создать допустимый граф объектов. Сохранить путь, информация атрибутов либо помогает средству чтения XAML сформировать допустимый поток узлов XAML, который восстанавливает информации о системе типов XAML; или он объявляет указания сериализации или требований к средству записи XAML или других потребителей XAML.  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **Применяется к:** класса, свойства, или `get` доступа членов, которые поддерживают присоединяемого свойства.  
  
 **Аргументы:** None  
  
 <xref:System.Windows.Markup.AmbientAttribute>Указывает, что свойство или все свойства, которые принимают тип с атрибутом, должны интерпретироваться в рамках концепции внешнего свойства в XAML. Концепция окружения относится к тому, как обработчики XAML определяют владельцев типов членов. Внешнее свойство является свойством, где значение должно быть доступным в контексте средства синтаксического анализа при создании графа объектов, но поиск типичного члена типа откладывается для немедленного создания набора узлов XAML.  
  
 Концепция окружения может применяться к присоединяемым членам, которые не представлены в виде свойств в том смысле, как присвоение атрибутов CLR определяет <xref:System.AttributeTargets>. Использование однозначного соответствия метода должны применяться только в случае использования `get` доступа, который поддерживает использование присоединяемого для XAML.  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **Применяется к:** класса  
  
 **Аргументы:** строка, указывающая имя свойства, которое соответствует аргументу один конструктор.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute>Указывает, что объект можно инициализировать с помощью синтаксиса конструктора не по умолчанию, и что свойство с указанным именем предоставляет информацию о конструкции. Эта информация предназначена главным образом для сериализации XAML. Дополнительные сведения см. в разделе <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### <a name="contentpropertyattribute"></a>Атрибут ContentPropertyAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **Применяется к:** класса  
  
 **Аргументы:** строка, указывающая имя члена типа с атрибутом.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute>Указывает, что свойства как названный аргумент должен использоваться в качестве свойством содержимого XAML для этого типа. Определение свойства содержимого XAML наследует все производные типы, которые можно назначить типу. Отдельный производный тип можно переопределить, применяя <xref:System.Windows.Markup.ContentPropertyAttribute> к отдельному производный тип.  
  
 Для свойства, которое служит в качестве свойства содержимого XAML можно опустить элемент свойства, добавление тегов для свойства при использовании XAML. Как правило можно назначить свойства содержимого XAML, обеспечивающих упрощенной разметки XAML для модели содержимое и вложения. Так как свойство содержимого XAML можно назначить только один член, иногда имеют разработки вариантов, какое из нескольких контейнеров свойств типа должны быть обозначены как свойством содержимого XAML. Остальные свойства контейнера должны использоваться с явными элементами свойства.  
  
 В потоке узлов XAML свойства содержимого XAML по-прежнему выдавать `StartMember` и `EndMember` узлов, используя имя свойства для <xref:System.Xaml.XamlMember>. Чтобы определить, является ли член свойством содержимого XAML, проверьте <xref:System.Xaml.XamlType> значение из `StartObject` размещения и получения значений <xref:System.Xaml.XamlType.ContentProperty%2A>.  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **Применяется к:** класса, в частности типы коллекций.  
  
 **Аргументы:** A <xref:System.Type> , указывающий тип в качестве типа содержимого оболочки для внешнего содержимого.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute>Указывает один или несколько типов для типа связанной коллекции, которая будет использоваться как оболочка для внешнего содержимого. Внешнее содержимое относится к случаям, когда ограничения системы для типа свойства содержимого не охватывают все возможные варианты содержимого, поддерживающих использование XAML для типа-владельца. Например, поддержка XAML для содержимого, определенного типа может включать строки в строго типизированной универсальной коллекции <xref:System.Collections.ObjectModel.Collection%601>. Оболочки содержимого удобны при перенос существующих соглашения разметки в XAML в понятие присваиваемых значений для коллекций, например перенос содержимого модели, связанных с текстом.  
  
 Чтобы указать несколько типов содержимого программы-оболочки, примените атрибут несколько раз.  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **Применяется к:** свойство  
  
 **Аргументы:** строка, указывающая имя элемента другого типа с атрибутом.  
  
 <xref:System.Windows.Markup.DependsOnAttribute>Указывает, что свойство с атрибутом зависит от значения другого свойства. Применение этого атрибута к определению свойства обеспечивает сначала обработать зависимые свойства записи объектов XAML. Использование <xref:System.Windows.Markup.DependsOnAttribute> указывает на исключительные случаи свойств типов, где для создания допустимых объектов должен соблюдаться определенный порядок анализа.  
  
 Можно применить несколько <xref:System.Windows.Markup.DependsOnAttribute> вариантов для определения свойства.  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **Применяется к:** класс, который должен быть <xref:System.Windows.Markup.MarkupExtension> производный тип.  
  
 **Аргументы:** A <xref:System.Type> , указывающее наиболее точный тип ожидать как `ProvideValue` результат атрибутом <xref:System.Windows.Markup.MarkupExtension>.  
  
 Дополнительные сведения см. в разделе [расширения разметки для XAML Обзор](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **Применяется к:** класса  
  
 **Аргументы:** поддерживает две формы однозначного соответствия:  
  
-   Строка, указывающая имя свойства типа с атрибутом.  
  
-   Строка, указывающая имя свойства, а также <xref:System.Type> для типа, который определяет именованное свойство. Эта форма предназначена для указания присоединяемого члена как свойство видимости имен XAML.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute>Задает свойство, которое предоставляет значение области имен XAML для класса с атрибутом. Свойства видимости имен XAML должен ссылаться на объект, реализующий интерфейс <xref:System.Windows.Markup.INameScope> и содержит фактическую область видимости имен XAML, ее хранилище и ее поведение.  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **Применяется к:** класса  
  
 **Аргументы:** строка, указывающая имя свойства времени выполнения имя типа с атрибутом.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>сообщает о свойстве типа атрибута, который сопоставляется с XAML [директива x: Name](../../../docs/framework/xaml-services/x-name-directive.md). Свойство должно быть типа <xref:System.String> и должен быть чтения и записи.  
  
 Определение наследует все производные типы, которые можно назначить типу. Отдельный производный тип можно переопределить, применяя <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> к отдельному производный тип.  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **Применяется к:** типы  
  
 **Аргументы:** None.  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>применяется к определенным типам, которые могут отображаться как дочерние элементы внутри существенного содержимого пустого пространства (содержимое, хранящихся в коллекции, которая содержит <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>основном относится к сохранения пути, но доступен в системе типов XAML в пути загрузки путем проверки <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>. Дополнительные сведения см. в разделе [Обработка пробелов в XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **Справочная документация:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **Применяется к:** класса, свойства или метода (единственным допустимым XAML случай метод `get` доступа, который поддерживает присоединяемого члена).  
  
 **Аргументы:** <xref:System.Type> из <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>в XAML контексте ссылается на пользовательское <xref:System.ComponentModel.TypeConverter>. Это <xref:System.ComponentModel.TypeConverter> предоставляет поведение преобразования типов для пользовательских типов и членов данного типа.  
  
 Можно применить <xref:System.ComponentModel.TypeConverterAttribute> атрибута к пользовательскому типу с указанием реализации преобразователя пользовательского типа. Можно определить преобразователи типов для XAML в классах, структурах или интерфейсы. Необходимо предоставить преобразование для перечислений, встроенными средствами преобразования.  
  
 Преобразователь типов должен иметь возможность преобразовать из строки, которая используется для атрибутов или инициализации текста в разметке в требуемый конечный тип. Дополнительные сведения см. в разделе [преобразователя](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
 Вместо того чтобы применять ко всем значениям типа, поведение преобразователя типов для XAML могут быть установлены на определенное свойство. В этом случае можно применить <xref:System.ComponentModel.TypeConverterAttribute> к определению свойства (внешнему определению, а не к конкретным `get` и `set` определения).  
  
 Поведение преобразователя типов для использования пользовательского присоединяемого члена XAML можно задать, применив атрибут <xref:System.ComponentModel.TypeConverterAttribute> для `get` метод доступа, который поддерживает использование XAML.  
  
 Аналогично <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> существовали в .NET Framework до появления XAML и модель преобразователя типов выполняла другие функции. Для указания и использования <xref:System.ComponentModel.TypeConverterAttribute>, необходимо полностью уточнить его или предоставить `using` инструкции для <xref:System.ComponentModel>. Система сборки также необходимо включить в своем проекте.  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **Применяется к:** класса  
  
 **Аргументы:** строка, указывающая свойство по имени.  
  
 Указывает свойство CLR класса, который является псевдонимом [x: Uid Directive](../../../docs/framework/xaml-services/x-uid-directive.md).  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **Применяется к:** класса  
  
 **Аргументы:** логическое значение. Если используемое предназначению атрибута, это должно всегда указываться как `true`.  
  
 Указывает, строится ли этот тип сверху вниз в ходе создания графа объекта XAML. Это сложное понятие, которое может быть тесно связано определение модель программирования. Дополнительные сведения см. в разделе <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **Применяется к:** класса, свойства или метода (единственным допустимым XAML случай метод `get` доступа, который поддерживает присоединяемого члена).  
  
 **Аргументы:** A <xref:System.Type> , указывающий класс поддержки значение сериализатор для сериализации все свойства типа с атрибутом или конкретные атрибуты свойства.  
  
 <xref:System.Windows.Markup.ValueSerializer>Указывает класс сериализации значений, требующий больше состояний и контекстов, чем <xref:System.ComponentModel.TypeConverter> does. <xref:System.Windows.Markup.ValueSerializer>можно связать с присоединяемого члена, применяя <xref:System.Windows.Markup.ValueSerializerAttribute> атрибута к статическому `get` метод доступа для присоединяемого члена. Сериализация значений также может применяться для перечисления, интерфейсы и структуры, но не для делегатов.  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **Применяется к:** класса, в частности типы коллекций, которые должны размещаться смешанное содержимое, где пустое пространство вокруг элементов объекта может оказаться довольно существенной представление пользовательского интерфейса.  
  
 **Аргументы:** None.  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>Указывает, что тип коллекции должен обрабатываться как значимый пробел, обработчик XAML, что влияет на создание узлов значений потока узлов XAML в пределах коллекции. Дополнительные сведения см. в разделе [Обработка пробелов в XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **Применяется к:** класса, свойства.  
  
 **Аргументы:** однозначного соответствия поддерживает две формы типов в виде строк или типов как <xref:System.Type>. См. раздел <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Указывает, что классу или свойству имеет использование отложенной загрузки для XAML (например, поведение шаблона) и сообщает класс, который позволяет задержку и его тип назначения и содержимого.  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **Применяется к:** класса  
  
 **Аргументы:** имена обратного вызова.  
  
 Указывает, что класс может использовать расширение разметки для предоставления значения для одного или нескольких из его свойств и ссылается на обработчик, который должно вызвать средство записи XAML перед выполнением операции установки расширения разметки для любого свойства класса.  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **Применяется к:** класса  
  
 **Аргументы:** имена обратного вызова.  
  
 Указывает, что класс может использовать преобразователь типов для предоставления значения для одного или нескольких из его свойств и ссылается на обработчик, который должно вызвать средство записи XAML перед выполнением операции установки преобразователя типа для любого свойства класса.  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **Применяется к:** класса  
  
 **Аргументы:** строка, указывающая имя свойства для псевдонима `xml:lang` типа с атрибутом.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute>сообщает о свойстве типа атрибута, который сопоставляет XML `lang` директивы. Свойство не обязательно типа <xref:System.String>, но должно быть присваиваемым из строки (этого можно добиться путем сопоставления преобразователя типов с типом свойства, либо к отдельному свойству). Свойство должно быть чтения и записи.  
  
 Сценарий сопоставления `xml:lang` так, что модель объекта среды выполнения имеет доступ к сведения о языке XML указано без отдельной обработки при помощи XMLDOM.  
  
 Определение наследует все производные типы, которые можно назначить типу. Отдельный производный тип можно переопределить, применяя <xref:System.Windows.Markup.XmlLangPropertyAttribute> к отдельному производному типу, хотя это и редко.  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Атрибуты среды CLR, связанные с XAML на уровне сборки  
 В следующих разделах описаны атрибуты, связанные с XAML, которые не применяются к типам и определениям членов, но вместо применяется к сборкам. Эти атрибуты имеют отношение к общей цели определения библиотеки, которая содержит пользовательские типы для использования в языке XAML. Некоторые атрибуты могут не оказывать влияние поток узлов XAML напрямую, но передаются в потоке узлов для других потребителей для использования. Потребители сведения относятся среды разработки и процессы сериализации, которым требуются сведения о пространстве имен XAML и соответствующие сведения о префиксах. Контекст схемы XAML (включая значение по умолчанию служб XAML .NET Framework) также использует эту информацию.  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Аргументы:**  
  
-   Строка, задающая идентификатор пространства имен XAML для разделения.  
  
-   Строка, задающая идентификатор пространства имен XAML, можно включить пространство имен XAML из предыдущего аргумента.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>Указывает, что пространство имен XAML может быть включено в другое пространство имен XAML. Как правило, поглощающее пространство имен XAML указывается в определенном ранее <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Этот метод можно использовать для управления версиями словарю XAML в библиотеке, а также для обеспечения совместимости с ранее определенной разметки к более старому словарю.  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Аргументы:**  
  
-   Строка, задающая идентификатор пространства имен XAML для определения.  
  
-   Строка, пространство имен CLR. Пространство имен CLR следует определять открытые типы в сборке, и по крайней мере один из типов имен среды CLR должен предназначен для использования XAML.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Указывает сопоставление для каждой сборки между пространством имен XAML и пространством имен CLR, которое затем используется для разрешения типов модулем записи объектов XAML или контекстом схемы XAML.  
  
 Существует несколько <xref:System.Windows.Markup.XmlnsDefinitionAttribute> может применяться к сборке. Это можно сделать для любой комбинации из следующих причин:  
  
-   Конструкция библиотеки содержит несколько пространств имен CLR для логической организации доступа к API среды выполнения; Тем не менее необходимо все типы в этих пространствах имен для использования XAML, ссылаясь на том же пространстве имен XAML. В этом случае необходимо применить несколько <xref:System.Windows.Markup.XmlnsDefinitionAttribute> атрибутов, используя те же <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> значение, но разные <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> значения. Это особенно полезно при определении сопоставления для пространства имен XAML, который framework или приложений должен находиться в общее использование пространства имен XAML по умолчанию.  
  
-   Конструкция библиотеки содержит несколько пространств имен CLR, и хотите преднамеренное разделение пространства имен XAML между использования типов в этих пространствах имен CLR.  
  
-   Пространство имен CLR определяется в сборке, и они были доступны через несколько пространств имен XAML. Это происходит при поддержке нескольких словарей с одной и той же базой кода.  
  
-   Поддержка языка XAML определяется в один или несколько пространств имен CLR. В этом случае <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> значение должно быть `http://schemas.microsoft.com/winfx/2006/xaml`.  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **Справочная документация:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Аргументы:**  
  
-   Строка, задающая идентификатор пространства имен XAML.  
  
-   Строка, определяющая рекомендуемый префикс.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Определяет рекомендуемый префикс для пространства имен XAML. Префикс удобен при записи элементов и атрибутов в файл XAML, который сериализуется в службах XAML .NET Framework <xref:System.Xaml.XamlXmlWriter>, или когда реализующая XAML библиотека взаимодействует со средой разработки, поддерживающей XAML возможности редактирования.  
  
 Существует несколько <xref:System.Windows.Markup.XmlnsPrefixAttribute> может применяться к сборке. Это можно сделать для любой комбинации из следующих причин:  
  
-   Сборка определяет типы для нескольких пространств имен XAML. В этом случае следует определить различные значения префиксов для каждого пространства имен XAML.  
  
-   Вы несколько словарей и использовать разные префиксы для каждого словаря и пространства имен XAML.  
  
-   Поддержка языка XAML определяется в сборке и иметь <xref:System.Windows.Markup.XmlnsDefinitionAttribute> для `http://schemas.microsoft.com/winfx/2006/xaml`. В этом случае обычно необходимо повысить уровень префикса `x`.  
  
> [!NOTE]
>  Службы XAML .NET framework также определяет атрибут, связанные с XAML <xref:System.Windows.Markup.RootNamespaceAttribute>. Этот атрибут является атрибут уровня сборки для поддержки системы проектов, и не относится к пользовательским типам XAML.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Attribute>  
 [Определение пользовательских типов для использования со службами XAML .NET Framework](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
