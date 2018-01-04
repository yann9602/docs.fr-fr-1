---
title: "Ajout d'une référence de service dans une solution de workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee974ee5a9f4564b0e44256bc4773f9898d89fc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>Ajout d'une référence de service dans une solution de workflow
L'ajout d'une référence de service dans une application de workflow fonctionne de façon légèrement différente que dans une application WCF normale. Lorsque vous sélectionnez Ajouter une référence de service et lorsque vous spécifiez l'URL du service, les métadonnées sont téléchargées et les activités personnalisées sont générées pour vous permettre d'appeler le service WCF ou le service de workflow WCF auquel vous avez ajouté une référence. Après l'ajout d'une référence de service, régénérez la solution pour que les activités générées soient construites. Celles-ci vont ensuite apparaître dans la boîte à outils du concepteur de workflow. Notez toutefois que cela ne fonctionne que si vous ajoutez une référence de service dans une solution de workflow. Le cast web suivant montre comment ajouter une référence de service dans d’autres types de projets : [appeler un Service WCF à partir d’un flux de travail dans un projet Web](http://go.microsoft.com/fwlink/?LinkId=207725).  
  
 L'ajout de deux ou plus références de service aux services qui contiennent le même nom d'opération entraîne un problème. Les activités générées vont appeler uniquement la première opération de service. Pour contourner ce problème, il faut renommer les opérations de service avec des noms différents ou modifier le nom de la configuration de point de terminaison dans chaque activité générée.  
  
## <a name="see-also"></a>Voir aussi  
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Guide pratique pour créer un service de workflow qui appelle un autre service de workflow](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 [Appeler un Service WCF à partir d’un flux de travail dans un projet Web](http://go.microsoft.com/fwlink/?LinkId=207725)
