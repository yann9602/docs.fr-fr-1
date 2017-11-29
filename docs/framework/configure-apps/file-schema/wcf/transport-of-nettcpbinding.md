---
title: '&lt;transport&gt; de &lt;netTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: adec2ce082f063f5d3f2cff2c1c428a770aeb76d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a>&lt;transport&gt; de &lt;netTcpBinding&gt;
Définit le type d’exigences de sécurité au niveau du message pour un point de terminaison configuré avec la [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<système. ServiceModel >  
\<liaisons >  
\<netTcpBinding >  
\<liaison >  
\<sécurité >  
\<transport >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netTcpBinding>  
    <binding>  
        <security  
         mode="None|Transport|Message|TransportWithMessageCredential">  
            <transport clientCredentialType="None|Windows|Certificate"  
             protectionLevel="None|Sign|EncryptAndSign"             sslProtocols="Tls|Tls11|Tls12">  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|clientCredentialType|Facultatif. Spécifie le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité de transport.<br /><br /> -La valeur par défaut est `Windows`.<br />-Cet attribut est de type <xref:System.ServiceModel.TcpClientCredentialType>.|  
|protectionLevel|Facultatif. Définit la sécurité au niveau du transport TCP. La signature des messages atténue le risque de modification par un tiers pendant le transfert. Le chiffrement garantit la confidentialité des données pendant le transport.<br /><br /> La valeur par défaut est `EncryptAndSign`.|  
|sslProtocols|Valeur d'indicateur d'énumération SslProtocols qui spécifie les protocoles SSL pris en charge. La valeur par défaut est Tls &#124; Tls11 &#124; Tls12.|  
|policyEnforcement|Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.<br /><br /> 1.  Never : la stratégie n'est jamais appliquée (la protection étendue est désactivée).<br />2.  WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.<br />3.  Always : la stratégie est toujours appliquée. Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.|  
  
## <a name="clientcredentialtype-attribute"></a>Attribut clientCredentialType  
  
|Valeur|Description|  
|-----------|-----------------|  
|None|Le client est anonyme. Cela requiert un certificat pour le service.|  
|Windows|Spécifie l'authentification Windows du client à l'aide de la négociation SP (négociation Kerberos).|  
|Certificat|Le client est authentifié à l'aide d'un certificat. Cette valeur utilise la négociation SSL et requiert un certificat pour le service.|  
  
## <a name="protectionlevel-attribute"></a>protectionLevel, attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|None|Aucune protection.|  
|Sign|Les messages sont signés.|  
|EncryptAndSign|-Les messages sont chiffrés et signés.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Spécifie les fonctions de sécurité de le [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Remarques  
 Utilisez la sécurité de transport pour l'intégrité et la confidentialité du message SOAP et l'authentification mutuelle. Si ce mode de sécurité est sélectionné sur une liaison, la pile de canaux est configurée à l’aide d’un transport sécurisé et les messages SOAP sont sécurisés à l’aide d’une sécurité de transport, telle que Windows (Negotiate) ou SSL sur TCP.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Sécurisation des Services et Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)  
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<liaison >](../../../../../docs/framework/misc/binding.md)
