---
title: "Activité NoPersistScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfc651403988fa7558f79a4c99e42fb776efec4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="nopersistscope-activity"></a>Activité NoPersistScope
Cet exemple montre comment manipuler un état non sérialisable et supprimable dans un workflow. Il est important que les workflows n'essaient pas de rendre l'état non sérialisable persistant et il est également important de nettoyer les objets supprimables après qu'ils ont été utilisés dans le workflow.  
  
## <a name="demonstrates"></a>Démonstrations  
 Concepteur et activité personnalisée `NoPersistScope`.  
  
## <a name="using-the-nopersistzone-activity"></a>Utilisation de l'activité NoPersistZone  
 Lors de l'exécution de l'exemple de workflow, une activité personnalisée appelée `CreateTextWriter` crée un objet de type <xref:System.IO.TextWriter> et l'enregistre dans une variable de workflow. <xref:System.IO.TextWriter> est un objet <xref:System.IDisposable>. Ce <xref:System.IO.TextWriter>, configuré pour écrire dans un fichier nommé « out.txt » dans le répertoire dans lequel l'exemple s'exécute, est utilisé par une activité <xref:System.Activities.Statements.WriteLine> lors de l'écho de tout texte que vous entrez au niveau de la console.  
  
 La logique d'écho est exécutée dans une activité `NoPersistScope` (le code associé fait également partie de cet exemple), qui empêche de rendre le workflow persistant. Si vous tapez dans `unload` à la console, l’hôte tente de conserver l’instance de workflow, mais cette opération arrive à expiration, car le flux de travail reste dans un `NoPersistScope`. Le workflow utilise également une activité personnalisée appelée `Dispose` pour supprimer l'objet <xref:System.IO.TextWriter> lorsque le workflow a fini de l'utiliser. L'activité `Dispose` est placée dans le bloc <xref:System.Activities.Statements.TryCatch.Finally%2A> de l'activité <xref:System.Activities.Statements.TryCatch> où la variable <xref:System.IO.TextWriter> est déclarée pour garantir son exécution même si une exception devait se produire pendant l'exécution du bloc Try.  
  
 Vous pouvez taper dans `exit` pour terminer l’instance de workflow et de quitter le programme.  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez la solution NoPersistZone.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Pour générer la solution, appuyez sur CTRL + MAJ + B ou sélectionnez **générer la Solution** à partir de la **générer** menu.  
  
3.  Une fois la génération a réussi, appuyez sur F5 ou sélectionnez **démarrer le débogage** à partir de la **déboguer** menu ou bien, vous pouvez appuyer sur CTRL + F5 ou sélectionnez **démarrer sans débogage** à partir de la **Déboguer** menu pour exécuter sans débogage.  
  
#### <a name="to-cleanup-optional"></a>Pour effectuer un nettoyage (facultatif)  
  
1.  Pour supprimer le magasin d'instances SQL, exécutez Cleanup.cmd.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`