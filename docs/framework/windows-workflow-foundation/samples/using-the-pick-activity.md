---
title: "Utilisation de l'activité Pick"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5a95567afd955848b81bc343109acfe3fd138c7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-pick-activity"></a>Utilisation de l'activité Pick
Cet exemple montre comment utiliser l'activité <xref:System.Activities.Statements.Pick>.  
  
 L'activité <xref:System.Activities.Statements.Pick> fournit une modélisation de contrôle basée sur les événements. Le comportement est semblable à celui de l'instruction `switch` de C#, qui exécute une seule des branches dans l'instruction `switch`. Contrairement à l'instruction `switch` dans laquelle une branche est exécutée en fonction d'une valeur, l'activité <xref:System.Activities.Statements.Pick> exécute une branche en fonction de l'exécution d'une activité.  
  
 Cet exemple invite un utilisateur à taper son nom sur la console dans une période de temps donné. L'activité <xref:System.Activities.Statements.Pick> dans l'exemple a deux branches qui sont exécutées selon si l'utilisateur tape son nom dans les 5 secondes ou non. Si l'utilisateur tape son nom dans les 5 secondes, la première branche, qui contient une activité `ReadLine` personnalisée est exécutée ; sinon, l'autre branche, qui contient une activité <xref:System.Activities.Statements.Delay> est exécutée. Une fois qu'un nom d'utilisateur est tapé sur la console, il est imprimé sur la console. Si rien n'est entré dans les 5 secondes, l'opération expire.  
  
## <a name="demonstrates"></a>Démonstrations  
 Activité <xref:System.Activities.Statements.Pick>  
  
## <a name="discussion"></a>Discussion  
 L'exemple inclut un workflow de concepteur et un workflow encodé.  
  
 Workflow de concepteur  
 La version concepteur de l'exemple montre comment créer un workflow dans le concepteur. Les fichiers suivants sont inclus :  
  
-   Program.cs : inclut la fonction `Main` qui exécute l'exemple de workflow.  
  
-   ReadString.cs : activité personnalisée qui lit une entrée de la console.  
  
-   Sequence1.xaml : workflow créé à l'aide du concepteur qui utilise Pick.  
  
 Workflow encodé  
 La version encodée de l'exemple montre comment créer un workflow dans le concepteur. Les fichiers suivants sont inclus :  
  
-   Program.cs : inclut la fonction `Main` qui exécute l'exemple de workflow.  
  
-   ReadString.cs : activité personnalisée qui lit une entrée de la console.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution Pick.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`  
  
## <a name="see-also"></a>Voir aussi
