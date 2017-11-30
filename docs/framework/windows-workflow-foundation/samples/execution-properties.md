---
title: "Propriétés d'exécution"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab7c81f051e6e65509d232479fd9f4ebe00ac99d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="execution-properties"></a>Propriétés d'exécution
Cet exemple montre comment définir et utiliser une propriété d'exécution dans une activité personnalisée. Dans cet exemple, la propriété d'exécution détermine la couleur de premier plan de la console. Un exemple de workflow montre comment différents chemins logiques d'exécution (branches d'une activité <xref:System.Activities.Statements.Parallel>) peuvent maintenir des couleurs de console différentes malgré l'exécution entrelacée d'activités (à travers les branches de l'activité <xref:System.Activities.Statements.Parallel>).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez l'exemple de solution ExecutionProperties.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    > [!NOTE]
    >  La consultation de ThreeColors.xaml avant la génération de la solution affiche une erreur, car les activités personnalisées utilisées doivent être générées en même temps que la solution.  
  
2.  Générez et exécutez la solution.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`