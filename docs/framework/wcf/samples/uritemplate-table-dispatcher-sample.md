---
title: UriTemplate Table Dispatcher, exemple
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8fe3440c6c770052b40bbade7483e1c31e1671a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="uritemplate-table-dispatcher-sample"></a>UriTemplate Table Dispatcher, exemple
La classe <xref:System.UriTemplateTable> fournit une structure de table associative de type dictionnaire permettant d'utiliser un ensemble d'instances d'<xref:System.UriTemplate>. Cet exemple illustre un moteur de distribution de base construit à l'aide d'`UriTemplateTable`, un scénario d'utilisation commun pour la classe `UriTemplateTable`.  
  
 Cet exemple illustre les concepts clés suivants pour la classe `UriTemplateTable` :  
  
-   Association de délégués à des `UriTemplates` dans une `UriTemplateTable`.  
  
-   Utilisation de <xref:System.UriTemplateTable.MatchSingle%2A> pour obtenir le délégué de gestionnaire correct pour un URI particulier.  
  
-   Appel du délégué de gestionnaire pour traiter la requête.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>Voir aussi  
 [Table UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
