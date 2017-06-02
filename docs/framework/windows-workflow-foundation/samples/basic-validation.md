---
title: "Validation de base | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Validation de base
Cet exemple se compose d'une activité, `CreateProduct`, qui valide que son argument `Cost` est plus petit ou égal à son argument `Price`.  
  
## Détails de l'exemple  
 Deux auteurs utilisent la validation, l'auteur d'activité \(qui crée la logique de validation pour l'activité\) et l'auteur de workflow qui appelle des services de validation sur un workflow spécifique.Dans ce scénario, l'auteur d'activité souhaite faire en sorte que chaque instance de son activité ait un coût inférieur ou égal au prix.  
  
 L'auteur d'activité \(à l'intérieur de l'activité\) doit effectuer les opérations suivantes :  
  
-   Créer une contrainte \(`PriceGreaterThanCost`\).Il s'agit de l'emplacement de toute la logique de validation.  
  
-   Substituer <xref:System.Activities.CodeActivity%601.OnGetConstraints%2A> et ajouter la contrainte \(`PriceGreaterThanCost`\) aux contraintes <xref:System.Collections.IList>.  
  
 L'auteur de workflow \(programme principal\) doit effectuer les opérations suivantes :  
  
-   Créer un workflow avec une instance de l'activité à valider \(`CreateProduct`\).  
  
-   Appeler <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, qui retourne une collection <xref:System.Activities.Validation.ValidationResults> de <xref:System.Activities.Validation.ConstraintViolation>.  
  
-   \(Facultatif\) Imprimer les objets <xref:System.Activities.Validation.ConstraintViolation>.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez l'exemple de solution BasicValidation.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez et exécutez la solution.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`  
  
## Voir aussi