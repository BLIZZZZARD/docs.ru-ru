---
title: "Пользовательский кодировщик сообщений: кодировщик сжатия | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
caps.latest.revision: 37
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 37
---
# Пользовательский кодировщик сообщений: кодировщик сжатия
Этот образец демонстрирует, как реализовать пользовательский кодировщик с помощью платформы [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере.Перед продолжением проверьте следующий каталог \(по умолчанию\).  
>   
>  `<диск_установки>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите на страницу [Образцы Windows Communication Foundation \(WCF\) и Windows Workflow Foundation \(WF\) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780), чтобы загрузить все образцы [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] и [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Этот образец расположен в следующем каталоге.  
>   
>  `<диск_установки>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## Подробные сведения об образце  
 Образец содержит консольную программу клиента \(EXE\), консольную программу резидентной службы \(EXE\) и библиотеку кодировщика сжатия сообщений \(DLL\).Служба реализует контракт, определяющий шаблон взаимодействия "запрос\-ответ".Контракт определяется интерфейсом `ISampleServer`, предоставляющим базовые операции отображения строк \(`Echo` и `BigEcho`\).Клиент осуществляет синхронные вызовы заданной операции, а служба отвечает, снова отправляя это сообщение назад клиенту.Действия клиента и службы отображаются в окнах консолей.Этот образец предназначен для того, чтобы показать, как написать пользовательский кодировщик, и продемонстрировать влияние сжатия сообщения на передачу по сети.К кодировщику сжатия сообщений можно добавить инструментарий для вычисления размера сообщения, времени обработки или обоих этих параметров.  
  
> [!NOTE]
>  В .NET Framework 4 автоматическая распаковка была включена на клиенте [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] при отправке сервером сжатого ответа \(созданного с помощью такого алгоритма, как GZip или Deflate\).Если служба размещена на веб\-сервере в службах IIS, то для службы IIS необходимо настроить отправку сжатого ответа.Можно использовать этот образец, если служба является резидентной и сжатие и распаковка должны быть выполнены и на клиенте, и в службе.  
  
 Образец демонстрирует, как построить и интегрировать пользовательский кодировщик сообщений в приложение [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Библиотека GZipEncoder.dll развертывается как с клиентом, так и со службой.Этот образец также демонстрирует влияние сжатия сообщений.Код в библиотеке GZipEncoder.dll демонстрирует следующие операции.  
  
-   Построение пользовательского кодировщика и фабрики кодировщика.  
  
-   Разработка элемента привязки для пользовательского кодировщика.  
  
-   Использование конфигурации пользовательской привязки для интеграции элементов пользовательской привязки.  
  
-   Разработка обработчика пользовательской конфигурации для обеспечения настройки элемента пользовательской привязки в файле.  
  
 Как указывалось ранее, существуют несколько уровней, реализованных в пользовательском кодировщике.Чтобы лучше показать взаимоотношения между различными уровнями, ниже приведен упрощенный список событий для запуска службы.  
  
1.  Запускается служба.  
  
2.  Считывается информация о конфигурации.  
  
    1.  Конфигурация службы регистрирует пользовательских обработчик конфигурации.  
  
    2.  Создается и открывается основное приложение для данной службы.  
  
    3.  Пользовательский элемент конфигурации создает и возвращает пользовательский элемент привязки.  
  
    4.  Пользовательский элемент привязки создает и возвращает фабрику кодировщиков сообщений.  
  
3.  Принимается сообщение.  
  
4.  Фабрика кодировщиков сообщений возвращает кодировщик сообщения для чтения сообщения и записи ответа.  
  
5.  Уровень кодировщика реализован как фабрика класса.Для пользовательского кодировщика должна быть общедоступна только фабрика класса кодировщика.Объект фабрики возвращается элементом привязки при создании объекта <xref:System.ServiceModel.ServiceHost> или <xref:System.ServiceModel.ChannelFactory%601>.Кодировщики сообщений могут работать в режиме буферизации или в режиме потоковой передачи.В этом образце демонстрируется как режим буферизации, так и режим потоковой передачи.  
  
 Для каждого режима имеются соответствующие методы `ReadMessage` и `WriteMessage` абстрактного класса `MessageEncoder`.Большая часть работы по кодированию выполняется в этих методах.Данный образец выступает в роли оболочки существующих кодировщиков текстовых и двоичных сообщений.Это позволяет образецу делегировать внутреннему кодировщику чтение и запись сообщений в форме, передаваемой по сети, а кодировщику сжатия сжимать и распаковывать результаты.Ввиду отсутствия конвейера для кодирования сообщений это только модель использования нескольких кодировщиков в [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].После того как сообщение распаковано, оно передается вверх стека для обработки стеком канала.Во время сжатия получающееся сжатое сообщение записывается непосредственно в указанный поток.  
  
 В этом образце используются вспомогательные методы \(`CompressBuffer` и `DecompressBuffer`\) для преобразования из буферов в потоки, чтобы использовать класс `GZipStream`.  
  
 Буферизованные классы `ReadMessage` и `WriteMessage` используют класс `BufferManager`.Кодировщик доступен только через фабрику кодировщиков.Абстрактный класс `MessageEncoderFactory` предоставляет свойство с именем `Encoder` для доступа к текущему кодировщику и метод с именем `CreateSessionEncoder` для создания кодировщика, поддерживающего сеансы.Такой кодировщик может использоваться в сценарии, в котором канал поддерживает сеансы и является упорядоченным и надежным.Этот сценарий допускает в каждом сеансе оптимизацию данных, записанных в сеть.Если это не требуется, не следует перегружать базовый метод.Свойство `Encoder` обеспечивает механизм для доступа к кодировщику, не поддерживающему сеансы, и реализация по умолчанию метода `CreateSessionEncoder` возвращает значение этого свойства.Так как для обеспечения сжатия образец выступает в роли оболочки для существующих кодировщиков, реализация `MessageEncoderFactory` принимает фабрику `MessageEncoderFactory`, которая представляет фабрику внутреннего кодировщика.  
  
 После того как кодировщик и фабрика кодировщиков определены, их можно использовать с клиентом и службой [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Однако необходимо добавить эти кодировщики в стек канала.Чтобы добавить эту фабрику кодировщиков вручную, можно создать производные классы от классов <xref:System.ServiceModel.ServiceHost> и <xref:System.ServiceModel.ChannelFactory%601> и переопределить методы `OnInitialize`.Доступ к фабрике кодировщиков можно также предоставить через пользовательский элемент привязки.  
  
 Чтобы создать новый пользовательский элемент привязки, создайте класс, производный от класса <xref:System.ServiceModel.Channels.BindingElement>.Однако существует несколько типов элементов привязки.Чтобы обеспечить распознавание пользовательского элемента привязки в качестве элемента привязки кодирования сообщений, необходимо также реализовать класс <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.Класс <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> предоставляет метод для создания новой фабрики кодировщиков сообщений \(`CreateMessageEncoderFactory`\), реализованный для возврата экземпляра соответствующей фабрики кодировщиков сообщений.Кроме того, класс <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> имеет свойство, указывающее версию адресации.Так как этот образец выступает в роли оболочки для существующих кодировщиков, реализация образца также создает оболочку для существующих элементов привязки кодировщиков, принимает элемент привязки внутреннего кодировщика в качестве параметра конструктора и предоставляет его через свойство.В следующем образце кода показана реализация класса `GZipMessageEncodingBindingElement`.  
  
```  
public sealed class GZipMessageEncodingBindingElement   
                        : MessageEncodingBindingElement //BindingElement  
                        , IPolicyExportExtension  
{  
  
    //We use an inner binding element to store information   
    //required for the inner encoder.  
    MessageEncodingBindingElement innerBindingElement;  
  
        //By default, use the default text encoder as the inner encoder.  
        public GZipMessageEncodingBindingElement()  
            : this(new TextMessageEncodingBindingElement()) { }  
  
    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)  
    {  
        this.innerBindingElement = messageEncoderBindingElement;  
    }  
  
    public MessageEncodingBindingElement InnerMessageEncodingBindingElement  
    {  
        get { return innerBindingElement; }  
        set { innerBindingElement = value; }  
    }  
  
    //Main entry point into the encoder binding element.   
    // Called by WCF to get the factory that creates the  
    //message encoder.  
    public override MessageEncoderFactory CreateMessageEncoderFactory()  
    {  
        return new   
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get { return innerBindingElement.MessageVersion; }  
        set { innerBindingElement.MessageVersion = value; }  
    }  
  
    public override BindingElement Clone()  
    {  
        return new   
        GZipMessageEncodingBindingElement(this.innerBindingElement);  
    }  
  
    public override T GetProperty<T>(BindingContext context)  
    {  
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))  
        {  
            return innerBindingElement.GetProperty<T>(context);  
        }  
        else   
        {  
            return base.GetProperty<T>(context);  
        }  
    }  
  
    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelFactory<TChannel>();  
    }  
  
    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelListener<TChannel>();  
    }  
  
    public override bool CanBuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.CanBuildInnerChannelListener<TChannel>();  
    }  
  
    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)  
    {  
        if (policyContext == null)  
        {  
            throw new ArgumentNullException("policyContext");  
        }  
       XmlDocument document = new XmlDocument();  
       policyContext.GetBindingAssertions().Add(document.CreateElement(  
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,  
            GZipMessageEncodingPolicyConstants.GZipEncodingName,  
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));  
    }  
}  
```  
  
 Обратите внимание, что класс `GZipMessageEncodingBindingElement` реализует интерфейс `IPolicyExportExtension`, чтобы этот элемент привязки можно было экспортировать в виде политики в метаданных, как показано в следующем примере.  
  
```  
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">  
    <wsp:ExactlyOne>  
      <wsp:All>  
        <gzip:text xmlns:gzip=  
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />   
       <wsaw:UsingAddressing />   
     </wsp:All>  
   </wsp:ExactlyOne>  
</wsp:Policy>  
  
```  
  
 Класс `GZipMessageEncodingBindingElementImporter` реализует интерфейс `IPolicyImportExtension`, этот класс импортирует политику для класса `GZipMessageEncodingBindingElement`.Для импорта политик в файл конфигурации может использоваться средство Svcutil.exe; для обработки `GZipMessageEncodingBindingElement` в файл Svcutil.exe.config необходимо добавить следующие строки.  
  
```  
  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="gzipMessageEncoding"   
          type=  
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </bindingElementExtensions>  
    </extensions>  
    <client>  
      <metadata>  
        <policyImporters>  
          <remove type=  
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
          <extension type=  
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
  
```  
  
 Обратите внимание, что имеется соответствующий элемент привязки для кодировщика сжатия, он может быть программно подключен к службе или клиенту путем создания нового пользовательского объекта привязки и добавления в него пользовательского элемента привязки, как показано в следующем образце кода.  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();  
bindingElements.Add(compBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
binding.Name = "SampleBinding";  
binding.Namespace = "http://tempuri.org/bindings";  
  
```  
  
 Хотя этого может быть достаточно для большинства пользовательских сценариев, поддержка конфигурации с помощью файлов критически важно, если служба будет размещена в Интернете.Для поддержки сценариев с размещением в Интернете необходимо разработать пользовательский обработчик конфигурации, позволяющий настраивать пользовательский элемент привязки в файле.  
  
 Пользовательский обработчик для элемента привязки можно построить на основе системы конфигурации, предоставляемой [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].Обработчик конфигурации для элемента привязки должен наследовать от класса <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.Свойство `BindingElementType` используется для информирования системы конфигурации о типе элемента конфигурации, который следует создать для этого раздела.Все аспекты элемента `BindingElement`, допускающие установку, должны быть представлены как свойства класса, производного от <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.Класс <xref:System.Configuration.ConfigurationPropertyAttribute> помогает при сопоставлении атрибутов элемента конфигурации со свойствами и задании значений по умолчанию в случае отсутствия атрибута.После того как значения из конфигурации загружены и применены к свойствам, вызывается метод <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A>, который преобразует свойства в конкретный экземпляр элемента привязки.Метод <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> используется для преобразования свойств производного класса <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>, в значения, задаваемые во вновь созданном элементе привязки.  
  
 В следующем образце кода показана реализация класса `GZipMessageEncodingElement`.  
  
```  
public class GZipMessageEncodingElement : BindingElementExtensionElement  
{  
    public GZipMessageEncodingElement()  
    {  
    }  
  
//Called by the WCF to discover the type of binding element this   
//config section enables  
    public override Type BindingElementType  
    {  
        get { return typeof(GZipMessageEncodingBindingElement); }  
    }  
  
    //The only property we need to configure for our binding element is   
    //the type of inner encoder to use. Here, we support text and  
    //binary.  
    [ConfigurationProperty("innerMessageEncoding",   
                         DefaultValue = "textMessageEncoding")]  
    public string InnerMessageEncoding  
    {  
        get { return (string)base["innerMessageEncoding"]; }  
        set { base["innerMessageEncoding"] = value; }  
    }  
  
    //Called by the WCF to apply the configuration settings (the   
    //property above) to the binding element  
    public override void ApplyConfiguration(BindingElement bindingElement)  
    {  
        GZipMessageEncodingBindingElement binding =   
                (GZipMessageEncodingBindingElement)bindingElement;  
        PropertyInformationCollection propertyInfo =   
                    this.ElementInformation.Properties;  
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=   
                                     PropertyValueOrigin.Default)  
        {  
            switch (this.InnerMessageEncoding)  
            {  
                case "textMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                      new TextMessageEncodingBindingElement();  
                    break;  
                case "binaryMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                         new BinaryMessageEncodingBindingElement();  
                    break;  
            }  
        }  
    }  
  
    //Called by the WCF to create the binding element  
    protected override BindingElement CreateBindingElement()  
    {  
        GZipMessageEncodingBindingElement bindingElement =   
                new GZipMessageEncodingBindingElement();  
        this.ApplyConfiguration(bindingElement);  
        return bindingElement;  
    }  
}   
```  
  
 Этот обработчик конфигурации сопоставляет следующее представление в файле App.config или Web.config для службы или клиента.  
  
```  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
  
```  
  
 Для использования этого обработчика конфигурации его необходимо зарегистрировать в элементе [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md), как показано в следующем образце конфигурации.  
  
```  
<extensions>  
    <bindingElementExtensions>  
       <add   
           name="gzipMessageEncoding"   
           type=  
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,  
           GZipEncoder, Version=1.0.0.0, Culture=neutral,   
           PublicKeyToken=null" />  
      </bindingElementExtensions>  
</extensions>  
  
```  
  
 При работе службы запросы и ответы операции отображаются в окне консоли.Чтобы закрыть службу, нажмите клавишу ВВОД в этом окне.  
  
```  
  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
  
```  
  
 При выполнении клиента запросы и ответы операции отображаются в окне консоли.Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.  
  
```  
  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
  
```  
  
#### Настройка, построение и выполнение образца  
  
1.  Установите [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, выполнив следующую команду.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
  
    ```  
  
2.  Убедитесь, что выполнены процедуры, описанные в разделе [Процедура однократной настройки образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Чтобы построить решение, следуйте инструкциям в разделе [Построение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Чтобы выполнить образец на одном или нескольких компьютерах, следуйте инструкциям в разделе [Выполнение примеров Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере.Перед продолжением проверьте следующий каталог \(по умолчанию\).  
>   
>  `<диск_установки>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите на страницу [Образцы Windows Communication Foundation \(WCF\) и Windows Workflow Foundation \(WF\) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780), чтобы загрузить все образцы [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] и [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Этот образец расположен в следующем каталоге.  
>   
>  `<диск_установки>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## См. также