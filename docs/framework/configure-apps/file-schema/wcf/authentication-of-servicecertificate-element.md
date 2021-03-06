---
title: "&lt;authentication&gt; элемента &lt; serviceCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e8c9530097593f1694af67396773fc32d5534d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ltauthenticationgt-of-ltservicecertificategt-element"></a>&lt;authentication&gt; элемента &lt; serviceCertificate&gt;
Задает параметры, которые использует прокси клиента для проверки подлинности сертификатов службы, полученных при помощи согласования SSL/TLS.  
  
 \<система. ServiceModel >  
\<поведения >  
раздел endpointBehaviors  
\<поведение >  
\<clientCredentials >  
\<serviceCertificate >  
\<Проверка подлинности >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<authentication customCertificateValidatorType="String" certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"   
trustedStoreLocation="LocalMachine/CurrentUser" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описываются атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|customCertificateValidatorType|Строка. Тип и сборка, используемые для проверки пользовательского типа.|  
|certificateValidationMode|Задает один из трех режимов для проверки учетных данных. Если задано значение `Custom`, также необходимо предоставить customCertificateValidator. Значение по умолчанию — `ChainTrust`.|  
|revocationMode|Один из режимов, используемых для проверки списков отозванных сертификатов (CRL). Значение по умолчанию — `Online`.|  
|trustedStoreLocation|Одно из двух местоположений системного хранилища: `LocalMachine` или `CurrentUser`. Данное значение используется при согласовании сертификата службы для клиента. Проверка выполняется для **доверенные лица** хранения в указанном местоположении хранилища. Значение по умолчанию — `CurrentUser`.|  
  
## <a name="customcertificatevalidator-attribute"></a>Атрибут customCertificateValidator  
  
|Значение|Описание|  
|-----------|-----------------|  
|Строковое|Задает имя типа и сборку, а также другие данные, используемые для поиска типа.|  
  
## <a name="certificatevalidationmode-attribute"></a>Атрибут certificateValidationMode  
  
|Значение|Описание|  
|-----------|-----------------|  
|Перечисление|Одно из следующих значений: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.<br /><br /> Дополнительные сведения см. в разделе [работа с сертификатами](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>Атрибут revocationMode  
  
|Значение|Описание|  
|-----------|-----------------|  
|Перечисление|Одно из следующих значений: NoCheck, Online, Offline.<br /><br /> Дополнительные сведения см. в разделе [работа с сертификатами](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>Атрибут trustedStoreLocation  
  
|Значение|Описание|  
|-----------|-----------------|  
|Перечисление|Одно из следующих значений: LocalMachine или CurrentUser. Значение по умолчанию - CurrentUser. Если клиентское приложение выполняется в контексте системной учетной записи, сертификат обычно находится в LocalMachine. Если клиентское приложение выполняется в контексте учетной записи пользователя, то сертификат обычно находится в CurrentUser.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Задает сертификат для использования при проверке подлинности службы для клиента.|  
  
## <a name="remarks"></a>Примечания  
 Атрибут `certificateValidationMode` данного элемента конфигурации указывает уровень доверия, который используется при проверке подлинности сертификатов. По умолчанию для уровня устанавливается значение `ChainTrust`, которое указывает, что каждый сертификат должен находиться в иерархии сертификатов, которая на самом верху цепи завершается доверенным центром сертификации. Это наиболее безопасный режим. Также можно установить значение `PeerOrChainTrust`, в этом случае будут приниматься как самостоятельно выдаваемые сертификаты (доверие одноранговой группы), так и сертификаты, которые находятся в цепи доверия. Данное значение используется при разработке и отладке клиентов и служб, так как самостоятельно выданные сертификаты не нужно приобретать у доверенного центра сертификации. При развертывании клиента вместо этого значения следует использовать значение `ChainTrust`. Также можно задать значение `Custom` или `None`. Чтобы использовать значение `Custom`, необходимо также установить атрибут `customCertificateValidator` для сборки и типа, которые используются при проверке сертификата. Для создания собственного пользовательского проверяющего элемента управления необходимо унаследовать его от абстрактного класса X509CertificateValidator. Дополнительные сведения см. в разделе [как: создание службы, использующей пользовательское средство проверки сертификатов](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 Атрибут `revocationMode` указывает способ проверки отозванных сертификатов. По умолчанию используется значение `online`, которое указывает, что проверка, является ли сертификат отозванным, будет выполняться автоматически. Дополнительные сведения см. в разделе [работа с сертификатами](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется две задачи. Во-первых, указывается сертификат службы для клиента, который должен использоваться при связи по протоколу HTTP с конечными точками, именем домена которых является www.contoso.com. Во-вторых, в этом примере указывается режим отзыва и место хранения, которые используются при проверке подлинности.  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a>См. также  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>  
 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>  
 [Поведения безопасности](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Работа с сертификатами](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Практическое руководство. Создание службы, использующей пользовательский проверяющий элемент управления для сертификатов](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [\<Проверка подлинности >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [Защита клиентов](../../../../../docs/framework/wcf/securing-clients.md)  
 [Защита служб и клиентов](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
