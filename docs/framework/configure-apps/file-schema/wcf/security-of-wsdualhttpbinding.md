---
title: '&lt;security&gt; de &lt;wsDualHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 72d1c451efe267d098ef4d529194905ee14d6ae3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a>&lt;security&gt; de &lt;wsDualHttpBinding&gt;
Définit les fonctionnalités de sécurité le [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 \<système. ServiceModel >  
\<liaisons >  
\<wsDualHttpBinding >  
\<liaison >  
\<sécurité >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|mode|-Facultatif. Spécifie le type de sécurité appliqué. La valeur par défaut est `Message`. Cet attribut est de type <xref:System.ServiceModel.WSDualHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>Mode, attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|None|La sécurité est désactivée.|  
|Message|La sécurité est fournie à l'aide de la sécurité des messages SOAP.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<message >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|Définit les paramètres de sécurité au niveau du message. Cet élément est de type <xref:System.ServiceModel.MessageSecurityOverHttp>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison >](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison de la [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).|  
  
## <a name="remarks"></a>Remarques  
 Une liaison double expose l’adresse IP du client au service. Ce client doit utiliser un mode de sécurité qui vérifiera qu'il se connecte uniquement à des services de confiance.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [Sécurisation des Services et Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)  
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<liaison >](../../../../../docs/framework/misc/binding.md)
