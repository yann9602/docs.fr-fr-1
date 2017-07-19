---
title: "D&#233;bogage de workflows | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# D&#233;bogage de workflows
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] offre plusieurs options permettant de déboguer des workflows en cours d'exécution à partir de l'environnement de développement.  Les workflows peuvent être débogués dans le concepteur, dans XAML et dans le code.  
  
## Débogage dans le concepteur de workflow  
 Des points d'arrêt peuvent être définis sur des activités dans le concepteur de workflow soit en mettant en surbrillance l'activité voulue et en appuyant sur **F9**, soit en utilisant le menu contextuel de l'activité en question.  Ainsi, l'exécution du workflow s'arrête lorsque l'hôte de workflow est exécuté en mode débogage.  Dans la capture d'écran suivante, l'exécution du workflow est suspendue à un point d'arrêt.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Débogage de workflows avec Workflow Designer](../Topic/Debugging%20Workflows%20with%20the%20Workflow%20Designer.md).  
  
## Débogage dans XAML  
 Si un workflow a suspendu son exécution à un point d'arrêt dans le concepteur, le workflow peut également être débogué dans XAML.  Pour afficher le point d'exécution dans XAML, sélectionnez **Affichage XAML** dans le concepteur de workflow lorsque l'exécution du workflow est suspendue.  Il est possible de revenir au mode de débogage dans le concepteur de workflow en rouvrant le workflow dans le concepteur à partir de l'Explorateur de solutions.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Procédure : déboguer du code XAML avec Workflow Designer](../Topic/How%20to:%20Debug%20XAML%20with%20the%20Workflow%20Designer.md).  
  
## Débogage dans le code  
 Des points d'arrêt de code peuvent être utilisés dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] de la même façon que dans d'autres applications impératives.  Cliquez dans la marge de gauche du volet de code pour créer un point d'arrêt de code ou appuyez sur **F9** pour ajouter un point d'arrêt à l'emplacement du curseur.  
  
## Attachement à un processus de workflow  
 Le débogage de workflow permet également d'utiliser l'infrastructure de Visual Studio pour attacher un processus.  Cela permet à l'auteur de workflow de déboguer un workflow qui est exécuté dans un environnement hôte différent, tel qu'Internet Information Services 7.0 \(IIS\).  
  
## Débogage distant  
 Le débogage distant [!INCLUDE[wf](../../../includes/wf-md.md)] fonctionne sur le même principe que débogage distant d'autres composants [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)].  Pour plus d'informations sur l'utilisation du débogage à distance, consultez [Procédure : activation du débogage à distance](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
> [!NOTE]
>  Si l'application de workflow cible l'architecture x86 et est hébergée sur un ordinateur qui exécute un système d'exploitation 64 bits, le débogage à distance ne fonctionnera pas à moins que [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] ne soit installé sur l'ordinateur distant ou la cible de l'application de workflow soit remplacée par **Any CPU**.  
  
## Extension du service de débogage de workflow  
 Le service de débogage de workflow est maintenant public et peut être utilisé pour créer des applications personnalisées, notamment pour la surveillance, la simulation et le débogage dans un concepteur réhébergé.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)], la rubrique <xref:System.Activities.Presentation.Debug.DebuggerService>.