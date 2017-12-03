---
title: "Attribution d'un nouveau nom à un service WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c2ecd78a7d72b86460f4d1972c42c8550010f02
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="renaming-a-wcf-service"></a>Attribution d'un nouveau nom à un service WCF
Cette rubrique décrit comment renommer un service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
## <a name="renaming-a-wcf-service"></a>Attribution d'un nouveau nom à un service WCF  
 Effectuez les étapes suivantes pour renommer un service dans un modèle [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]  
  
-   Modifiez le nom de la classe qui implémente le service.  
  
-   Dans le fichier de configuration du service, remplacez le nom du service par celui que vous avez choisi, comme indiqué dans l'exemple suivant. Selon votre modèle d'hébergement, le fichier de configuration sera app.config ou web.config.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   Si votre service est hébergé sur le Web, il utilise un fichier *.svc. Ouvrez le fichier svc et modifiez le nom de votre service comme indiqué dans l'exemple suivant. Cette étape n'est pas nécessaire pour les applications auto-hébergées, puisqu'il n'y a pas de fichier svc.  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>Attribution d'un nouveau nom à un contrat de service WCF  
  
-   Effectuez les étapes suivantes pour renommer le contrat de service  
  
-   Modifiez le nom du contrat de service.  
  
-   Dans le fichier de configuration du service, remplacez le nom du contrat de service par le celui que vous avez choisi, comme indiqué dans l'exemple suivant. Selon votre modèle d'hébergement, le fichier de configuration sera app.config ou web.config.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
