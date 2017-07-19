---
title: "Utilisation de l&#39;activit&#233; InvokeMethod | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Utilisation de l&#39;activit&#233; InvokeMethod
Cet exemple montre comment utiliser l'activité <xref:System.Activities.Statements.InvokeMethod%601> pour appeler des méthodes publiques dans des classes publiques.L'activité <xref:System.Activities.Statements.InvokeMethod%601> permet à un workflow d'appeler des méthodes sur des objets, de passer des paramètres, d'obtenir la valeur de retour, de spécifier des types pour les méthodes génériques et d'indiquer si la méthode est synchrone ou asynchrone.  
  
 Il existe une version non générique de l'activité <xref:System.Activities.Statements.InvokeMethod> où la valeur de retour a pour valeur la propriété <xref:System.Activities.Statements.InvokeMethod.Result%2A> et une version générique de l'activité <xref:System.Activities.Statements.InvokeMethod%601> où la valeur de retour est retournée via la propriété <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> de type `TResult`.  
  
 Cet exemple montre comment appeler différents types de méthode.La liste suivante détaille les types de méthode illustrés dans cet exemple :  
  
-   Appeler une méthode d'instance sans paramètres.  
  
-   Appeler une méthode d'instance avec deux paramètres \(System.String et System.Int32\).  
  
-   Appeler une méthode d'instance avec deux paramètres \(System.String et System.Int32\) et un tableau de paramètres de type System.String\[\].  
  
-   Appeler une méthode d'instance avec deux paramètres \(deux nombres System.Int32\) et un résultat de type System.Int32.  
  
     La valeur de retour est liée à une variable et imprimée sur la console à l'aide de l'activité <xref:System.Activities.Statements.WriteLine>.  
  
-   Appeler une méthode statique avec deux paramètres \(System.String et System.Int32\).  
  
-   Appeler une méthode d'instance avec un paramètre générique \(System.String\).  
  
-   Appeler une méthode statique avec deux paramètres génériques \(System.String et System.Int32\).  
  
-   Appeler une méthode d'instance qui a un paramètre passée par référence \(System.String\).  
  
     Le paramètre référencé est lié à une variable et imprimé sur la console à l'aide de l'activité <xref:System.Activities.Statements.WriteLine>.  
  
-   Appeler une méthode d'instance asynchrone.  
  
## Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution InvokeMethodUsage.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`  
  
## Voir aussi