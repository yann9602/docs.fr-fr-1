---
title: "Utilisation d&#39;activit&#233;s de collection | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Utilisation d&#39;activit&#233;s de collection
Cet exemple montre comment utiliser les activités de collection \(<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601> et <xref:System.Activities.Statements.RemoveFromCollection%601>\) avec une classe qui implémente l'interface <xref:System.Collections.ICollection> et comment créer une activité personnalisée qui itère au sein d'une collection pour imprimer le contenu de chaque élément de la collection.L'activité personnalisée nommée `PrintCollection`imprime sur la console les membres d'élément d'une collection nommée `Numbers`.  
  
 Le tableau suivant décrit les quatre activités qui fournissent la manipulation de collection pour les workflows.  
  
|Nom de l'activité|Description|  
|-----------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|Ajoute un élément à une collection.|  
|<xref:System.Activities.Statements.ClearCollection%601>|Efface tous les éléments d'une collection.|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|Retourne `true` si l'élément spécifié existe dans la collection.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|Supprime un élément d'une collection.|  
  
 L'exemple se compose de deux solutions, une sous le répertoire CodedWorkflow et l'autre sous le répertoire DesignerWorkflow.Elles illustrent deux façons différentes d'utiliser les activités dans le même but.  
  
||||  
|-|-|-|  
|Solution|Description|Fichiers principaux|  
|CodedWorkflow|Exemple d'application cliente qui montre comment appeler les activités de collection par programmation.|**PrintCollection.cs** : activité d'assistance pour imprimer sur la console chaque élément dans une collection.<br /><br /> **Program.cs** : crée par programmation une activité de séquence qui contient une série d'activités de collection et l'exécute.|  
|DesignerWorkflow|Exemple d'application cliente qui montre comment utiliser de façon déclarative les activités de collection dans le concepteur de workflow.|**CollectionWorkflow.xaml** : workflow créé de façon déclarative avec le concepteur qui utilise les activités de collection.<br /><br /> **PrintCollection.cs** : activité d'assistance pour imprimer sur la console chaque élément dans une collection.<br /><br /> **Program.cs** : appelle le workflow décrit dans CollectionWorkflow.xaml.|  
  
 Dans la démonstration, les membres d'élément de collection `Numbers` sont imprimés sur la console à l'aide d'une activité définie pour la personnalisation appelée `PrintCollection`.  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution Collection.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`  
  
## Voir aussi