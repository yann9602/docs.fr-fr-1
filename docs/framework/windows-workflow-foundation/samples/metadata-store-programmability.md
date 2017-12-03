---
title: "Programmabilité du magasin des métadonnées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01d51c9727847f00bdcf3f62945207882e3f41d6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="metadata-store-programmability"></a>Programmabilité du magasin des métadonnées
Le magasin des métadonnées est une fonctionnalité du [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] qui permet d'associer des métadonnées arbitraires, sous la forme d'attributs CLR, à des types au moment de l'exécution. Cela permet un couplage faible entre les composants runtime et leurs équivalents au moment du design, ainsi que la modification des composants au moment du design sans affecter le runtime. L'exemple montre comment d'écrire des programmes par rapport au magasin des métadonnées en appliquant des attributs à un type au moment de l'exécution, la source sur laquelle nous n'avons aucun contrôle. La terminologie généralement utilisée est qu'une application d'hébergement enregistre les métadonnées pour un ensemble de types.  
  
 Dans la sortie, vous pouvez remarquer un attribut supplémentaire inattendu, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`. Il est ajouté lorsque l'API des métadonnées est utilisée, et n'a aucun impact sur l'exécution de l'exemple.  
  
 Cet exemple illustre les opérations suivantes :  
  
## <a name="demonstrates"></a>Démonstrations  
  
-   Injection d'attributs à l'aide de l'API du magasin des métadonnées.  
  
-   Utilisation d'un mécanisme de rappel pour différer l'inscription des métadonnées.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution ProgrammingMetadataStore.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`