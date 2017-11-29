---
title: "Gestionnaire d'annulation sur une activité compensable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b39b5d9277767160225a34be9e0c71a36e7b6d78
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cancellation-handler-on-compensable-activity"></a>Gestionnaire d'annulation sur une activité compensable
Cet exemple montre l'utilisation d'un gestionnaire d'annulation sur un <xref:System.Activities.Statements.CompensableActivity>.  
  
 Cet exemple contient deux scénarios qui illustrent l'utilisation de l'annulation <xref:System.Activities.Statements.CompensableActivity>. Le premier scénario contient une activité compensable racine qui contient trois activités compensables enfants. Deux activités enfants terminent l'exécution de leurs corps d'activité avec succès. Lorsque le troisième corps d'activité enfant s'exécute, il rencontre une exception gérée en annulant le traitement de la troisième activité, après quoi l'annulation de l'activité racine est déclenchée. La logique dans l'activité racine de cet exemple consiste à compenser les deux autres activités enfants terminées précédemment.  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
```  
  
 Le deuxième scénario illustre l'exécution d'un <xref:System.Activities.Statements.TryCatch> en parallèle avec un <xref:System.Activities.Statements.Delay>, qui finit avant la branche <xref:System.Activities.Statements.TryCatch>. La condition d'achèvement a la valeur `true` une fois que la première branche est terminée, ce qui provoque l'annulation de l'autre branche.  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez CompensationCancellation.sln.  
  
2.  Générez l'exemple en appuyant sur Ctrl+Maj+B ou sélectionnez Générer la solution dans le menu Générer.  
  
3.  Exécutez l'exemple en appuyant sur F5 ou sélectionnez Démarrer le débogage dans le menu Déboguer. Vous pouvez également appuyer sur Ctrl+F5 ou sélectionner Exécuter sans débogage dans le menu Déboguer.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`  
  
## <a name="see-also"></a>Voir aussi
