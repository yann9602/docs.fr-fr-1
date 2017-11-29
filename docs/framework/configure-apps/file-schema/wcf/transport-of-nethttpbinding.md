---
title: '&lt;transport&gt; of &lt;netHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 67bacedb9a2e46903b97ea0747880bbb1af24a68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnethttpbindinggt"></a>&lt;transport&gt; of &lt;netHttpBinding&gt;
Définit les propriétés qui déterminent les paramètres d'authentification pour le transport HTTP.  
  
\<system.serviceModel >  
\<liaisons >  
\<netHttpBinding >  
\<liaison >  
\<sécurité >  
\<transport >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<netHttpBinding>  
  <binding>  
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string">  
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"  
                                  protectionScenario="TransportSelected|TrustedProxy">  
          <customServiceNames></customServiceNames>  
        </extendedProtectionPolicy>  
      </transport>  
    </security>  
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|clientCredentialType|-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à l’aide de l’authentification HTTP.  La valeur par défaut est `None`. Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à partir d’un domaine à l’aide d’un proxy sur HTTP. Cet attribut est applicable uniquement lorsque l'attribut `mode` de l'élément `security` parent est `Transport` ou `TransportCredentialsOnly`. Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|realm|Chaîne qui spécifie le domaine utilisé par la méthode d'authentification HTTP pour l'authentification Digest ou de base. La valeur par défaut est une chaîne vide.|  
|policyEnforcement|Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.<br /><br /> 1.  Never : la stratégie n'est jamais appliquée (la protection étendue est désactivée).<br />2.  WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.<br />3.  Always : la stratégie est toujours appliquée. Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.|  
|protectionScenario|Cette énumération spécifie le scénario de protection appliqué par la stratégie.|  
  
## <a name="clientcredentialtype-attribute"></a>Attribut clientCredentialType  
  
|Valeur|Description|  
|-----------|-----------------|  
|None|Les messages ne sont pas sécurisés pendant le transfert.|  
|Basic|Spécifie l'authentification de base.|  
|Digest|Spécifie l'authentification Digest.|  
|Ntlm|Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.|  
|Windows|Spécifie l'authentification intégrée Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>Attribut proxyCredentialType  
  
|Valeur|Description|  
|-----------|-----------------|  
|Aucune|-Les messages ne sont pas sécurisés pendant le transfert.|  
|Basic|Spécifie l'authentification de base telle que définie par RFC 2617 – Authentification HTTP : Authentification de base et Digest.|  
|Digest|Spécifie l'authentification Digest telle que définie par RFC 2617 – Authentification HTTP : Authentification de base et Digest.|  
|Ntlm|Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.|  
|Windows|Spécifie l'authentification intégrée Windows.|  
|Certificat|Effectue l'authentification du client à l'aide d'un certificat. Cette option fonctionne uniquement si l'attribut `Mode` de l'élément `security` parent est configuré pour le transport et ne fonctionnera pas s'il a la valeur TransportCredentialOnly.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|Définit les fonctionnalités de sécurité pour le [ \<netHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre l’utilisation de la sécurité de transport SSL avec la liaison de base. Par défaut, la liaison de base prend en charge la communication HTTP.  
  
```xml
<system.serviceModel>  
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="netHttpBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
    <netHttpBinding>  
      <!-- Configure basicHttpBinding with Transport security -- >  
      <!-- mode and clientCredentialType set to None.-->  
      <binding name="Binding1">  
        <security mode="Transport">  
          <transport clientCredentialType="None"  
                     proxyCredentialType="None">  
            <extendedProtectionPolicy policyEnforcement="WhenSupported"  
                                      protectionScenario="TransportSelected">  
              <customServiceNames></customServiceNames>  
            </extendedProtectionPolicy>
          </transport> 
        </security>  
      </binding>  
    </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [Sécurisation des Services et Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)  
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<liaison >](../../../../../docs/framework/misc/binding.md)
