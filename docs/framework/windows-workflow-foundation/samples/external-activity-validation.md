---
title: "Validation d&#39;activit&#233; externe | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Validation d&#39;activit&#233; externe
Cet exemple montre comment ajouter une logique de validation à une activité intégrée dont vous n'êtes pas l'auteur.La logique de validation consiste à garantir que soit la propriété <xref:System.Activities.Statements.If.Then%2A>, soit la propriété <xref:System.Activities.Statements.If.Else%2A> de toutes les activités <xref:System.Activities.Statements.If> présentes dans le workflow soit définie.De plus, la logique de validation vérifie que toutes les activités <xref:System.Activities.Statements.Pick> présentes dans le workflow ont plusieurs branches, et si ce n'est pas le cas, un avertissement est généré.  
  
## Détails de l'exemple  
 Cet exemple crée un workflow avec une instance de chaque activité à valider : l'activité <xref:System.Activities.Statements.If> et l'activité <xref:System.Activities.Statements.Pick>.Un <xref:System.Activities.Validation.Constraint> est créé pour chaque comportement de validation.Les contraintes créées dans cet exemple sont `ConstraintError_IfShouldHaveThenOrElse` et `ConstraintWarning_PickHasOneBranch`.Ces contraintes sont ensuite ajoutées à la collection `AdditionalConstraints` d'une instance <xref:System.Activities.Validation.ValidationSettings>.Enfin, la méthode `static`<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> de <xref:System.Activities.Validation.ActivityValidationServices> est appelée pour valider les activités dans le workflow et les résultats de la validation sont imprimés sur la console.  
  
> [!NOTE]
>  Vous pouvez ajouter des contraintes de stratégie à toute activité.Par exemple, vous pouvez ajouter une contrainte de stratégie à une activité <xref:System.Activities.Statements.Sequence> ou <xref:System.Activities.Statements.Parallel>.  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier ExternalActivityValidation.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`  
  
## Voir aussi