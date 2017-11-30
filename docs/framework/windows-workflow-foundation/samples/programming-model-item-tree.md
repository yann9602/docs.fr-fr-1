---
title: "Programmation de l’arborescence des éléments de modèle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 18de9d7f9cedc40a6c143a4dae5567c9acf2cf88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="programming-model-item-tree"></a>Programmation de l’arborescence des éléments de modèle
Cet exemple montre comment parcourir l'arborescence <xref:System.Activities.Presentation.Model.ModelItem> à l'aide de la liaison de données déclarative à partir de l'arborescence de [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)].  
  
## <a name="sample-details"></a>Détails de l'exemple  
 L'arborescence <xref:System.Activities.Presentation.Model.ModelItem> est l'abstraction utilisée par l'infrastructure du [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] pour exposer les données relatives à l'instance sous-jacente en cours de modification. L'illustration suivante est une description des différentes couches d'infrastructure dans le [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].  
  
 ![Architecture du Concepteur de flux de travail](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")  
  
 Un <xref:System.Activities.Presentation.Model.ModelItem> se compose d'un pointeur vers la valeur sous-jacente, ainsi que d'une collection d'objets <xref:System.Activities.Presentation.Model.ModelProperty>. Un objet <xref:System.Activities.Presentation.Model.ModelProperty>, quant à lui, se compose de données telles que le nom et le type de la propriété, puis d'un pointeur vers la valeur qui, à son tout, est un autre <xref:System.Activities.Presentation.Model.ModelItem>. Un convertisseur de valeurs est utilisé pour manipuler certains des <xref:System.Activities.Presentation.Model.ModelItem> retournés à partir d'un <xref:System.Activities.Presentation.Model.ModelProperty> pour les faire apparaître correctement dans l'arborescence. L'exemple montre ensuite comment effectuer une programmation de façon impérative sur l'arborescence <xref:System.Activities.Presentation.Model.ModelItem> à l'aide de la syntaxe impérative.  
  
```csharp  
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;  
ModelProperty mp = mi.Properties["Activities"];  
mp.Collection.Add(new Persist());  
ModelItem justAdded = mp.Collection.Last();  
justAdded.Properties["DisplayName"].SetValue("new name");  
```  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Ouvrez la solution ProgrammingModelItemTree.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez la solution en sélectionnant **générer la Solution** à partir de la **générer** menu.  
  
3.  Appuyez sur F5 pour exécuter l'application. Le formulaire [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] s'affiche alors.  
  
4.  Cliquez sur le **charger WF** bouton Charger le <xref:System.Activities.Presentation.Model.ModelItem> et la lier à l’arborescence.  
  
5.  En cliquant sur le **arborescence d’éléments de modèle de modification** bouton exécute le code précédent pour ajouter un élément dans l’arborescence et définir une propriété.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Data.IValueConverter>
