---
title: "Service de bo&#238;te &#224; outils | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Service de bo&#238;te &#224; outils
Cet exemple montre comment mettre à jour les activités de la boîte à outils [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] en fonction du contexte du workflow.L'exemple contient un workflow qui modifie le contenu de la boîte à outils suivant qu'une activité personnalisée est sélectionnée ou non.  
  
## Discussion  
 Pendant la création de workflows, les clients veulent généralement que leur boîte à outils soit contextuelle.Par exemple, l'utilisateur peut vouloir s'assurer que la boîte à outils affiche des activités supplémentaires lorsqu'une activité spécifique est ajoutée au workflow.Si les activités sont supprimées du workflow, la boîte à outils doit réagir de façon appropriée en fonction des spécifications du domaine.  
  
 Dans un concepteur de workflow réhébergé, vous contrôlez le contrôle Toolbox et pouvez vous assurer que, suivant les modifications de modèle dans le workflow, l'hôte déclenche les modifications appropriées dans le contrôle Toolbox.Toutefois, dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], la boîte à outils n'est pas contrôlée par l'utilisateur. Par conséquent, une interface est requise pour modifier son contenu.`IActivityToolboxService` est cette interface.  
  
 L'API fournit les quatre méthodes suivantes :  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution WorkflowSimulator.sln.  
  
2.  Générez la solution en appuyant sur Ctrl\+Maj\+B.  
  
3.  Ouvrez le fichier Workflow.xaml.  
  
4.  Ajoutez un **CustomActivity** par le faisant glisser à partir de la boîte à outils.Notez une catégorie de boîte à outils supplémentaire appelée **Nouvelle catégorie WF** avec une activité **Assign** supplémentaire.  
  
5.  À présent, désélectionnez le **CustomActivity** en faisant glisser une autre activité dans celui\-ci.  
  
6.  L'élément **Assign** de la catégorie **Nouvelle catégorie WF** sous la boîte à outils est à présent supprimé.De plus, étant donné qu'il ne reste aucun élément dans la catégorie, cette dernière est également supprimée.  
  
7.  Sélectionnez à nouveau **CustomActivity** et la catégorie : l'activité **Assign** est alors à nouveau ajoutée.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`