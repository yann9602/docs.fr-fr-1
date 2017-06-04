---
title: "Attribution d&#39;un nouveau nom &#224; un service WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Attribution d&#39;un nouveau nom &#224; un service WCF
Cette rubrique décrit comment renommer un service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
## Attribution d'un nouveau nom à un service WCF  
 Effectuez les étapes suivantes pour renommer un service dans un modèle [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]  
  
-   Modifiez le nom de la classe qui implémente le service.  
  
-   Dans le fichier de configuration du service, remplacez le nom du service par celui que vous avez choisi, comme indiqué dans l'exemple suivant.Selon votre modèle d'hébergement, le fichier de configuration sera app.config ou web.config.  
  
```  
<system.servicemodel>  
   <services>  
      <service name=”WcfService.NewName”>  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   Si votre service est hébergé sur le Web, il utilise un fichier \*.svc.Ouvrez le fichier svc et modifiez le nom de votre service comme indiqué dans l'exemple suivant.Cette étape n'est pas nécessaire pour les applications auto\-hébergées, puisqu'il n'y a pas de fichier svc.  
  
```  
<%@ ServiceHost Service=”WcfService.NewName”>  
```  
  
## Attribution d'un nouveau nom à un contrat de service WCF  
  
-   Effectuez les étapes suivantes pour renommer le contrat de service  
  
-   Modifiez le nom du contrat de service.  
  
-   Dans le fichier de configuration du service, remplacez le nom du contrat de service par le celui que vous avez choisi, comme indiqué dans l'exemple suivant.Selon votre modèle d'hébergement, le fichier de configuration sera app.config ou web.config.  
  
```  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract=”WcfService.NewContractName” />  
      </service>  
   </services>  
</system.servicemodel>  
```