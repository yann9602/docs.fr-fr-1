---
title: "Activit&#233; personnalis&#233;e Hello World | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Activit&#233; personnalis&#233;e Hello World
Cet exemple illustre plusieurs fonctionnalités clés de [!INCLUDE[wf](../../../../includes/wf-md.md)], notamment la façon de créer une activité personnalisée simple.Certaines des fonctionnalités présentées dans cet exemple créent une activité personnalisée en C\# et utilisent les arguments `in` et `out` \(<xref:System.Activities.InArgument> et <xref:System.Activities.OutArgument>\).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## Création d'un workflow dans le code  
 Dans cet exemple, deux activités personnalisées sont créées à l'aide de code C\#.Les deux activités personnalisées héritent directement ou indirectement d'<xref:System.Activities.Activity%601> pour retourner une valeur unique.L'avantage de l'utilisation de la valeur de retour générique, plutôt que d'hériter de la classe <xref:System.Activities.Activity> non générique, est que certaines activités \(telles que <xref:System.Activities.Statements.Assign>\) peuvent accéder à la valeur de retour lorsqu'elles sont utilisées dans le cadre d'une activité composée.  
  
 AppendString  
 Cette activité hérite d'<xref:System.Activities.Activity%601>, et utilise une activité <xref:System.Activities.Statements.Assign> qui concatène deux chaînes.  
  
 PrependString  
 Cette activité hérite directement de <xref:System.Activities.CodeActivity%601>, et crée des fonctionnalités semblables à l'activité `AppendString`, laquelle utilise la logique implémentée au lieu d'être composée d'une activité préexistante.  
  
 Les fichiers suivants sont inclus dans ce projet :  
  
 AppendString.cs  
 Activité personnalisée qui ajoute des chaînes ensemble.Elle prend une chaîne et la combine avec une chaîne de texte littéral "says hello world" pour former un message complet comme sortie.  
  
 PrependString.cs  
 Cette activité fait précéder une chaîne d'entrée d'une chaîne prédéfinie.  
  
 Sequence1.xaml  
 Workflow qui utilise les activités personnalisées `AppendString` et `PrependString`.  
  
 Program.cs  
 Programme qui exécute le workflow.  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution HelloWorld.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur F5.  
  
## Voir aussi