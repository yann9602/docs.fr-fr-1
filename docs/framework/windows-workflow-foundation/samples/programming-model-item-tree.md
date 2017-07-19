---
title: "Programmation de l&#39;arborescence des &#233;l&#233;ments de mod&#232;le | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Programmation de l&#39;arborescence des &#233;l&#233;ments de mod&#232;le
Cet exemple montre comment parcourir l'arborescence <xref:System.Activities.Presentation.Model.ModelItem> à l'aide de la liaison de données déclarative à partir de l'arborescence de [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)].  
  
## Détails de l'exemple  
 L'arborescence <xref:System.Activities.Presentation.Model.ModelItem> est l'abstraction utilisée par l'infrastructure du [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] pour exposer les données relatives à l'instance sous\-jacente en cours de modification.L'illustration suivante est une description des différentes couches d'infrastructure dans le [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].  
  
 ![Architecture du concepteur de flux de travail](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")  
  
 Un <xref:System.Activities.Presentation.Model.ModelItem> se compose d'un pointeur vers la valeur sous\-jacente, ainsi que d'une collection d'objets <xref:System.Activities.Presentation.Model.ModelProperty>.Un objet <xref:System.Activities.Presentation.Model.ModelProperty>, quant à lui, se compose de données telles que le nom et le type de la propriété, puis d'un pointeur vers la valeur qui, à son tout, est un autre <xref:System.Activities.Presentation.Model.ModelItem>.Un convertisseur de valeurs est utilisé pour manipuler certains des <xref:System.Activities.Presentation.Model.ModelItem> retournés à partir d'un <xref:System.Activities.Presentation.Model.ModelProperty> pour les faire apparaître correctement dans l'arborescence.L'exemple montre ensuite comment effectuer une programmation de façon impérative sur l'arborescence <xref:System.Activities.Presentation.Model.ModelItem> à l'aide de la syntaxe impérative.  
  
```csharp  
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;  
ModelProperty mp = mi.Properties["Activities"];  
mp.Collection.Add(new Persist());  
ModelItem justAdded = mp.Collection.Last();  
justAdded.Properties["DisplayName"].SetValue("new name");  
  
```  
  
#### Pour utiliser cet exemple  
  
1.  Ouvrez la solution ProgrammingModelItemTree.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez la solution en sélectionnant **Générer la solution** dans le menu **Générer**.  
  
3.  Appuyez sur F5 pour exécuter l'application.Le formulaire [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] s'affiche alors.  
  
4.  Cliquez sur le bouton **Charger WF** pour charger <xref:System.Activities.Presentation.Model.ModelItem> et le lier à l'arborescence.  
  
5.  Un clic sur le bouton **Modifier l'arborescence des éléments de modèle** exécute le code précédent pour ajouter un élément à l'arborescence et définir une propriété.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## Voir aussi  
 <xref:System.Windows.Data.IValueConverter>