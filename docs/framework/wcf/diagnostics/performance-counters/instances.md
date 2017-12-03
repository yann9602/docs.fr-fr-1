---
title: Instances
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 87423c3de551cb9fbf8c5a7756e2f0f999129a3b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="instances"></a>Instances
Nom du compteur : Instances.  
  
## <a name="description"></a>Description  
 Nombre de contextes d'instance que le service contient actuellement.  
  
 La plupart du temps, le nombre de contextes d'instance est identique au nombre d'instances. Toutefois, les scénarios suivants constituent des exceptions à cette règle.  
  
-   Une méthode de service appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> de manière explicite.  
  
-   Un <xref:System.ServiceModel.ReleaseInstanceMode> est appliqué à une instance <xref:System.ServiceModel.OperationBehaviorAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
