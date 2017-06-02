---
title: "Suivi et tra&#231;age de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "programmation [WF], traçage et suivi"
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# Suivi et tra&#231;age de workflow
Le suivi Windows Workflow est une fonctionnalité de [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] conçue pour offrir plus de visibilité lors de l'exécution de workflow.Il fournit une infrastructure de suivi pour suivre l'exécution d'une instance de workflow.L'infrastructure de suivi WF instrumente de façon transparente un workflow pour émettre des enregistrements qui reflètent des événements clés pendant l'exécution.Cette fonctionnalité est disponible par défaut pour tous les workflows [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].Il n'est pas nécessaire de modifier un workflow [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] pour activer son suivi.Il suffit seulement de déterminer quelles données vous souhaitez obtenir.Lorsqu'une instance de workflow démarre ou se termine, les enregistrements de suivi de son exécution sont émis.Le suivi peut également extraire des données métier pertinentes associées aux variables de workflow.Par exemple, si le workflow représente un système de traitement des commandes, l'ID de commande peut être extrait avec l'objet <xref:System.Activities.Tracking.TrackingRecord>.En règle générale, le suivi WF facilite l'accès aux diagnostics ou aux analyses d'entreprise depuis l'exécution du workflow.  
  
 Ces composants de suivi sont équivalents au service de suivi dans [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)].Dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], les performances ont été améliorées et le modèle de programmation simplifié pour la fonctionnalité de suivi WF.L'exécution du suivi instrumente une instance de workflow pour émettre des événements associés au cycle de vie de workflow, aux activités de workflow et aux événements personnalisés.  
  
 Windows Server AppFabric permet également de surveiller l'exécution de WCF et des services de workflow.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Analyse Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=201273) et [Analyse d'applications avec Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=201287)  
  
 Pour résoudre les problèmes d'exécution de workflow, vous pouvez activer le suivi de workflow diagnostique.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Suivi de workflow](../../../docs/framework/windows-workflow-foundation//workflow-tracing.md).  
  
 Pour vous aider à comprendre le modèle de programmation, les principaux composants de l'infrastructure de suivi sont traités dans cette rubrique :  
  
-   Des objets <xref:System.Activities.Tracking.TrackingRecord> sont émis par l'exécution du workflow.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Enregistrements de suivi](../../../docs/framework/windows-workflow-foundation//tracking-records.md).  
  
-   Les objets <xref:System.Activities.Tracking.TrackingParticipant> s'abonnent aux objets <xref:System.Activities.Tracking.TrackingRecord>.Les participants de suivi contiennent la logique nécessaire pour traiter la charge utile des objets <xref:System.Activities.Tracking.TrackingRecord> \(par exemple, ils peuvent choisir d'écrire dans un fichier\).[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Participants de suivi](../../../docs/framework/windows-workflow-foundation//tracking-participants.md).  
  
-   Les objets <xref:System.Activities.Tracking.TrackingProfile> filtrent les enregistrements de suivi émis par une instance de workflow.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Modèles de suivi](../../../docs/framework/windows-workflow-foundation//tracking-profiles.md).  
  
## Infrastructure de suivi de workflow  
 L'infrastructure de suivi de workflow fonctionne sur un modèle Publier\/Abonner.L'instance de workflow est le serveur de publication des enregistrements de suivi, alors que les abonnés des enregistrements de suivi sont inscrits en tant qu'extensions du workflow.Ces extensions qui s'abonnent aux objets <xref:System.Activities.Tracking.TrackingRecord> sont appelées des participants de suivi.Les participants de suivi sont des points d'extensibilité qui accèdent aux objets <xref:System.Activities.Tracking.TrackingRecord> afin de les traiter de la manière prévue.L'infrastructure de suivi permet l'application d'un filtre sur les enregistrements de suivi sortants pour permettre à un participant de s'abonner à un sous\-ensemble des enregistrements.Ce mécanisme de filtrage s'effectue à l'aide d'un fichier modèle de suivi.  
  
 L'illustration suivante présente une vue globale de l'infrastructure de suivi.  
  
 ![Infrastructure du suivi des flux de travail](../../../docs/framework/windows-workflow-foundation//media/wv.gif "WV")  
  
## Dans cette section  
 [Enregistrements de suivi](../../../docs/framework/windows-workflow-foundation//tracking-records.md)  
 Décrit les enregistrements de suivi émis par l'exécution du workflow.  
  
 [Modèles de suivi](../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)  
 Explique l'utilisation des modèles de suivi.  
  
 [Participants de suivi](../../../docs/framework/windows-workflow-foundation//tracking-participants.md)  
 Décrit comment utiliser le participant de suivi fourni par le système ou comment créer des participants de suivi personnalisés.  
  
 [Configuration du suivi d'un workflow](../../../docs/framework/windows-workflow-foundation//configuring-tracking-for-a-workflow.md)  
 Décrit comment configurer le suivi pour un workflow.  
  
 [Suivi de workflow](../../../docs/framework/windows-workflow-foundation//workflow-tracing.md)  
 Décrit les deux méthodes d'activation du suivi de débogage pour un workflow.  
  
 [Détermination de la durée d'exécution d'un workflow à l'aide du suivi](../../../docs/framework/windows-workflow-foundation//determining-workflow-execution-duration-using-tracing.md)  
 Décrit comment utiliser les messages de suivi pour déterminer la durée d'exécution du workflow.  
  
## Voir aussi  
 [Suivi SQL](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)