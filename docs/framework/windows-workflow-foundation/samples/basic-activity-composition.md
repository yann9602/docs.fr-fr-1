---
title: "Composition de l&#39;activit&#233; de base | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Composition de l&#39;activit&#233; de base
Cet exemple montre comment composer des activités personnalisées et des activités fournies par le système pour générer d'autres activités personnalisées.  
  
 Le workflow, à l'aide de l'activité Survey, planifie l'enquête avec une liste de questions, puis fournit en sortie les réponses reçues.  
  
## Détails de l'exemple  
 Cet exemple utilise trois activités personnalisées.`ReadLine` est un <xref:System.Activities.NativeActivity>\<string\> simple qui crée un <xref:System.Activities.Bookmark> lorsqu'il est planifié, puis affecte à `Return`<xref:System.Activities.OutArgument%601> la valeur avec laquelle le <xref:System.Activities.Bookmark> est repris.`Prompt` est un <xref:System.Activities.Activity%601>\<string\> qui prend un <xref:System.Activities.InArgument%601>\<string\> nommé `Text` et retourne la réponse des utilisateurs dans `Result`<xref:System.Activities.OutArgument%601>\<string\>.L'activité `Prompt` utilise les activités <xref:System.Activities.Statements.Sequence> et <xref:System.Activities.Statements.WriteLine> fournies dans le cadre du .NET Framework, et incorpore également l'activité `ReadLine` personnalisée pour l'obtention de l'entrée d'utilisateur.La dernière activité personnalisée est l'activité `Survey`.Il s'agit d'une <xref:System.Activities.Activity>\<ICollection\<chaîne\>\>.Cette activité prend une <xref:System.Activities.InArgument%601>\<IEnumerable\<chaîne\>\> nommée `Questions` et remplit l'argument `Result` out avec les réponses.L'activité `Survey` utilise <xref:System.Activities.Statements.ForEach>, <xref:System.Activities.Statements.Sequence> et <xref:System.Activities.Statements.AddToCollection%601> du .NET Framework et emploie l'activité `Prompt` pour poser les questions de l'enquête et obtenir des réponses.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez l'exemple de solution **BasicActivityComposition.sln** dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez et exécutez la solution.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`  
  
## Voir aussi