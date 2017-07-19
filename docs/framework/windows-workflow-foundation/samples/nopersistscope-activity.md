---
title: "Activit&#233; NoPersistScope | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Activit&#233; NoPersistScope
Cet exemple montre comment manipuler un état non sérialisable et supprimable dans un workflow.Il est important que les workflows n'essaient pas de rendre l'état non sérialisable persistant et il est également important de nettoyer les objets supprimables après qu'ils ont été utilisés dans le workflow.  
  
## Démonstrations  
 Concepteur et activité personnalisée `NoPersistScope`.  
  
## Utilisation de l'activité NoPersistZone  
 Lors de l'exécution de l'exemple de workflow, une activité personnalisée appelée `CreateTextWriter` crée un objet de type <xref:System.IO.TextWriter> et l'enregistre dans une variable de workflow.<xref:System.IO.TextWriter> est un objet <xref:System.IDisposable>.Ce <xref:System.IO.TextWriter>, configuré pour écrire dans un fichier nommé « out.txt » dans le répertoire dans lequel l'exemple s'exécute, est utilisé par une activité <xref:System.Activities.Statements.WriteLine> lors de l'écho de tout texte que vous entrez au niveau de la console.  
  
 La logique d'écho est exécutée dans une activité `NoPersistScope` \(le code associé fait également partie de cet exemple\), qui empêche de rendre le workflow persistant.Si vous entrez `décharger` au niveau de la console, l'hôte essaie de rendre l'instance de workflow persistante, mais cette opération expire car le workflow reste dans un `NoPersistScope`.Le workflow utilise également une activité personnalisée appelée `Dispose` pour supprimer l'objet <xref:System.IO.TextWriter> lorsque le workflow a fini de l'utiliser.L'activité `Dispose` est placée dans le bloc <xref:System.Activities.Statements.TryCatch.Finally%2A> de l'activité <xref:System.Activities.Statements.TryCatch> où la variable <xref:System.IO.TextWriter> est déclarée pour garantir son exécution même si une exception devait se produire pendant l'exécution du bloc Try.  
  
 Vous pouvez entrer `quitter` pour terminer l'instance de workflow et quitter le programme.  
  
#### Pour exécuter l'exemple  
  
1.  Ouvrez la solution NoPersistZone.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B ou sélectionnez **Générer la solution** dans le menu **Générer**.  
  
3.  Une fois que la génération a réussi, appuyez sur F5 ou sélectionnez **Démarrer le débogage** dans le menu **Déboguer**. Vous pouvez également appuyer sur CTRL\+F5 ou sélectionner **Exécuter sans débogage** dans le menu **Déboguer** pour une exécution sans débogage.  
  
#### Pour effectuer un nettoyage \(facultatif\)  
  
1.  Pour supprimer le magasin d'instances SQL, exécutez Cleanup.cmd.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`  
  
## Voir aussi