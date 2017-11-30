---
title: OverloadGroups
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c866d337b6e02fa18241b6fafd9d4e5a397ef69
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="overloadgroups"></a>OverloadGroups
Cet exemple se compose d'une activité (`CreateLocation`) qui a deux caractéristiques intéressantes :  
  
1.  Elle comprend quelques arguments obligatoires et quelques arguments facultatifs.  
  
2.  Elle permet à l'utilisateur de fournir un jeu d'arguments sélectionné parmi deux jeux d'arguments différents.  
  
 Ces comportements sont obtenus à l'aide des deux fonctionnalités suivantes :  
  
-   `[isRequired]` valide qu'une propriété d'une activité spécifique est affectée et, dans le cas contraire, lève une exception.  
  
-   `[OverloadGroup]` réunit un jeu d'arguments afin que l'utilisateur de l'activité puisse choisir d'utiliser l'un des deux jeux. L'utilisateur ne peut pas utiliser d'arguments de différents groupes surchargés dans la même instance.  
  
 Après avoir configuré des workflows différents, appelez <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> qui retourne une collection <xref:System.Activities.Validation.ValidationResults> de <xref:System.Activities.Validation.Constraint>. Imprimez les objets <xref:System.Activities.Validation.Constraint> sur la console.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez le **OverloadGroups.sln** exemple de solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez et exécutez la solution.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
