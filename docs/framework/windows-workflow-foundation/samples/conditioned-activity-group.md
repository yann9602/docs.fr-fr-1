---
title: "Groupe de l'activité conditionnée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0df4ddc6f2cc5404c8153b30df66cda41487691
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="conditioned-activity-group"></a>Groupe de l'activité conditionnée
L'exemple illustre une application de réservation de voyages. Le <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) comporte deux activités de code : une activité de type voiture et une autre de type compagnie aérienne. Dans le constructeur `SimpleCAGWorkflow`, un objet ArrayList "travelNeedType" est défini avec les types de réservations de voyage requises. En supprimant l'une ou les deux instructions `travelNeeds.Add`, vous modifiez le comportement du CAG en conséquence. À la fois, les activités voiture et compagnie aérienne ont leur condition <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> définie avec <xref:System.Workflow.Activities.CodeCondition>. L'activité Car s'exécute uniquement si la collection `travelNeeds` comporte une entrée `TravelNeeds.Car`, l'activité Airline s'exécute uniquement si la collection `travelNeeds` comporte une entrée `TravelNeeds.Airline`.  
  
 L'exécution de chaque activité supprime l'entrée correspondante de la collection. La condition <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> par défaut spécifie que le CAG doit se terminer lorsque aucun enfant ne s'exécute ou n'est prêt pour l'exécution (selon leurs conditions <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>). Dans cet exemple, cela signifie que le CAG se termine lorsque la collection `travelNeeds` est vide.  
  
### <a name="to-build-the-sample"></a>Pour générer l'exemple  
  
1.  Ouvrez la solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez la solution en appuyant sur Ctrl+Maj+B.  
  
3.  Exécutez la solution sans débogage en appuyant sur Ctrl+F5.  
  
### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
-   Dans la fenêtre Invite de commandes du Kit de développement logiciel (SDK), exécutez le fichier .exe dans le dossier SimpleCAG\bin\debug (ou le dossier SimpleCAG\bin pour la version Visual Basic de l'exemple), situé sous le dossier principal de l'exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer :  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant :  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
