---
title: "Utilisation de la classe WorkflowInvoker | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Utilisation de la classe WorkflowInvoker
Cet exemple montre comment utiliser la classe <xref:System.Activities.WorkflowInvoker> pour appeler une activité comme s'il s'agissait d'une méthode.  
  
## Détails de l'exemple  
 Utiliser la classe <xref:System.Activities.WorkflowInvoker> est la façon la plus simple d'exécuter une activité.Elle est conçue pour exécuter une activité directement comme s'il s'agissait d'un appel de méthode.C'est une API légère, hautement performante et simple d'utilisation, destinée à être utilisée dans des scénarios où l'exécution d'une activité ne requiert pas l'infrastructure de contrôle fournie par d'autres variations d'hébergement.  
  
 L'exemple utilise une activité personnalisée qui dérive de <xref:System.Activities.CodeActivity%601>\<Int32\> nommé `Add` qui ajoute deux <xref:System.Activities.InArgument%601>, `X` et `Y`, et retourne un `Result`<xref:System.Activities.OutArgument%601>.\(<xref:System.Activities.CodeActivity%601>\<T\> dérive de <xref:System.Activities.Activity%601>\<T\>, qui a un <xref:System.Activities.OutArgument%601>\<T\> nommé `Result`.\) Un `Dictionary`\<chaîne, objet\> est utilisé pour passer des arguments dans une activité appelée via <xref:System.Activities.WorkflowInvoker>.La clé du dictionnaire correspond au nom d'un argument sur l'activité appelée.La valeur associée à une clé particulière est liée à l'argument identifié par la clé.  
  
 L'exemple appelle <xref:System.Activities.WorkflowInvoker.Invoke%2A> et passe un dictionnaire qui contient des valeurs pour `X` et `Y`.La classe <xref:System.Activities.WorkflowInvoker> lie ces valeurs aux arguments de l'activité `Add`, exécute l'activité, puis retourne le résultat.  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution Invoker.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`  
  
## Voir aussi