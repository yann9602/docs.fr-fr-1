---
title: "Utilisation de l'activité InvokeMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ba0c2333c14eaebdb6409323bb6b92aa2b29d2ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-invokemethod-activity"></a>Utilisation de l'activité InvokeMethod
Cet exemple montre comment utiliser le <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) activité qui permet d’appeler des méthodes publiques dans des classes publiques. Le <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) activité permet à un workflow à appeler des méthodes sur des objets, passer des paramètres, obtenir la valeur de retour, spécifier des types pour les méthodes génériques et indiquer si la méthode est synchrone ou asynchrone. 
  
Il existe une version non générique de la <xref:System.Activities.Statements.InvokeMethod> activité où la valeur de retour est définie pour le <xref:System.Activities.Statements.InvokeMethod.Result%2A> propriété et une version générique de la <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) activité où la valeur de retour est retournée via le <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx) propriété de type `TResult`. 
  
 Cet exemple montre comment appeler différents types de méthode. La liste suivante détaille les types de méthode illustrés dans cet exemple :  
  
-   Appeler une méthode d'instance sans paramètres.  
  
-   Appeler une méthode d'instance avec deux paramètres (System.String et System.Int32).  
  
-   Appeler une méthode d'instance avec deux paramètres (System.String et System.Int32) et un tableau de paramètres de type System.String[].  
  
-   Appeler une méthode d'instance avec deux paramètres (deux nombres System.Int32) et un résultat de type System.Int32.  
  
     La valeur de retour est liée à une variable et imprimée sur la console à l'aide de l'activité <xref:System.Activities.Statements.WriteLine>.  
  
-   Appeler une méthode statique avec deux paramètres (System.String et System.Int32).  
  
-   Appeler une méthode d'instance avec un paramètre générique (System.String).  
  
-   Appeler une méthode statique avec deux paramètres génériques (System.String et System.Int32).  
  
-   Appeler une méthode d'instance qui a un paramètre passée par référence (System.String).  
  
     Le paramètre référencé est lié à une variable et imprimé sur la console à l'aide de l'activité <xref:System.Activities.Statements.WriteLine>.  
  
-   Appeler une méthode d'instance asynchrone.  
  
## <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution InvokeMethodUsage.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`