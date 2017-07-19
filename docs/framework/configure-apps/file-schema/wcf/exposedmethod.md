---
title: "&lt;exposedMethod&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;exposedMethod&gt;
Représente une méthode COM\+ exposée lorsque l'interface sur un composant COM\+ est exposée en tant que service Web.  
  
## Syntaxe  
  
```  
  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Chaîne qui contient la méthode COM\+ exposée lorsque l'interface sur un composant COM\+ est exposée comme un service Web.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<exposedMethods\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|Collection d'éléments [\<exposedMethod\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md).|  
  
## Notes  
 Il est possible d'utiliser l'outil de configuration d'intégration COM\+ \(ComSvcConfig.exe\) pour ajouter des méthodes spécifiques issues d'une interface COM afin qu'elles apparaissent sur le contrat de service généré.  
  
 Par exemple, vous pouvez utiliser la commande suivante pour ajouter les trois méthodes nommées issues de l'interface COM `IFinances` sur le composant financier `ItemOrders` au contrat de service généré.  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 Lorsque vous exécutez également ComSvcConfig.exe, il génère le contrat de service suivant, qui répertorie les méthodes mentionnées précédemment comme éléments [\<exposedMethod\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md).  
  
```  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 Au moment de l'initialisation du service, le runtime tente de générer un contrat de service en reflétant sur les méthodes figurant dans la liste d'éléments [\<exposedMethod\>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) et en ajoutant uniquement ces méthodes.  Une trace est produite pour chaque méthode d'interface qui n'est pas incluse sur le contrat de service.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>   
 <xref:System.ServiceModel.Configuration.ComMethodElement>   
 [\<comContracts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)   
 [Intégration à des applications COM\+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)   
 [Comment : configurer des paramètres de service COM\+](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)