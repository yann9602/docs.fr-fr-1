---
title: "OverloadGroups | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# OverloadGroups
Cet exemple se compose d'une activité \(`CreateLocation`\) qui a deux caractéristiques intéressantes :  
  
1.  Elle comprend quelques arguments obligatoires et quelques arguments facultatifs.  
  
2.  Elle permet à l'utilisateur de fournir un jeu d'arguments sélectionné parmi deux jeux d'arguments différents.  
  
 Ces comportements sont obtenus à l'aide des deux fonctionnalités suivantes :  
  
-   `[isRequired]` valide qu'une propriété d'une activité spécifique est affectée et, dans le cas contraire, lève une exception.  
  
-   `[OverloadGroup]` réunit un jeu d'arguments afin que l'utilisateur de l'activité puisse choisir d'utiliser l'un des deux jeux.L'utilisateur ne peut pas utiliser d'arguments de différents groupes surchargés dans la même instance.  
  
 Après avoir configuré des workflows différents, appelez <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> qui retourne une collection <xref:System.Activities.Validation.ValidationResults> de <xref:System.Activities.Validation.ConstraintViolation>.Imprimez les objets <xref:System.Activities.Validation.ConstraintViolation> sur la console.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez l'exemple de solution **OverloadGroups.sln** dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez et exécutez la solution.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`  
  
## Voir aussi