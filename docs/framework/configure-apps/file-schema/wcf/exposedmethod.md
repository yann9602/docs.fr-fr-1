---
title: '&lt;exposedMethod&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c89acb38678879f882d8bb2a2b5277b555a1eb26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltexposedmethodgt"></a>&lt;exposedMethod&gt;
Représente une méthode COM+ exposée lorsque l'interface sur un composant COM+ est exposée en tant que service Web.  
  
 \<système. ServiceModel >  
\<comContracts >  
\<comContract >  
\<méthodes >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Chaîne qui contient la méthode COM+ exposée lorsque l'interface sur un composant COM+ est exposée comme un service Web.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<exposedMethods >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|Une collection de [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) éléments.|  
  
## <a name="remarks"></a>Remarques  
 Il est possible d'utiliser l'outil de configuration d'intégration COM+ (ComSvcConfig.exe) pour ajouter des méthodes spécifiques issues d'une interface COM afin qu'elles apparaissent sur le contrat de service généré.  
  
 Par exemple, vous pouvez utiliser la commande suivante pour ajouter les trois méthodes nommées issues de l'interface COM `IFinances` sur le composant financier `ItemOrders` au contrat de service généré.  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 Lorsque vous exécutez également la ComSvcConfig.exe, il génère le contrat de service suivant, qui répertorie les méthodes mentionnées précédemment comme [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) éléments.  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 Au moment de l’initialisation du service, le runtime tente de générer un contrat de service en reflétant sur et en ajoutant uniquement les méthodes incluses dans la liste des [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) éléments. Une trace est produite pour chaque méthode d'interface qui n'est pas incluse sur le contrat de service.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>  
 <xref:System.ServiceModel.Configuration.ComMethodElement>  
 [\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [Intégration à des Applications COM +](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Comment : configurer les paramètres de Service COM +](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
