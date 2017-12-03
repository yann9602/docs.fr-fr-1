---
title: Conseils de migration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0089d08604f5d738e04461f4ed5f8efcb1140420
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="migration-guidance"></a>Conseils de migration
Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], Microsoft publie la deuxième version principale de [!INCLUDE[wf](../../../includes/wf-md.md)]. [!INCLUDE[wf1](../../../includes/wf1-md.md)] a été intégré dans [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (ce qui comprenait les types dans les espaces de noms System.Workflow.*, à présent désignés sous le nom de WF3) et amélioré dans [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. WF3 est également dans le cadre de la [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], mais il est présent en même temps que la nouvelle technologie de workflow (les types dans System.Activities.\* espaces de noms ; appelée WF4). Lorsque vous pensez au moment opportun d'adopter WF4, il est important de savoir tout d'abord que c'est vous qui décidez.  
  
-   WF3 est une partie complètement prise en charge de [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
-   Les applications WF3 sont exécutées sur [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] sans modification et continuent à être totalement prises en charge.  
  
-   Des applications WF3 peuvent être créées et vos applications existantes peuvent être modifiées dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] et sont totalement prises en charge.  
  
 Par conséquent, la décision d’adopter .NET Framework 4 est dissociée de votre décision de passer à WF4 (System.Activities) à partir de WF3 (System.Workflow.\*). Cette rubrique fournit des liens vers des conseils de migration WF qui fournissent des informations sur l'utilisation de WF3 et WF4.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>Livres blancs et livres de recettes sur la migration WF (en anglais)  
 Le [WF Migration Overview](http://go.microsoft.com/fwlink/?LinkId=153873) rubrique fournit une vue d’ensemble de la relation entre WF3 et WF4 et la migration des stratégies. Les rubriques d'accompagnement traitent de sujets spécifiques.  
  
 [Présentation de la Migration WF](http://go.microsoft.com/fwlink/?LinkId=153873)  
 Décrit la relation entre WF3 et WF4 ainsi que les choix dont vous disposez en tant qu'utilisateur ou qu'utilisateur potentiel de la technologie de workflow dans .NET 4.  
  
 [Migration de WF : Meilleures pratiques pour le développement de WF3](http://go.microsoft.com/fwlink/?LinkId=153852)  
 Explique comment concevoir des artefacts WF3 afin que leur migration vers WF4 soit plus facile.  
  
 [Guide de WF : règles](http://go.microsoft.com/fwlink/?LinkId=153854)  
 Explique comment reporter des investissements liés aux règles dans des solutions [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
 [WF Guide : Ordinateur d’état](http://go.microsoft.com/fwlink/?LinkId=153855)  
 Explique la modélisation des flux de contrôle WF4 en l'absence d'une activité Ordinateur-État.  
  
 Notez que ces conseils s'appliquent uniquement aux projets de workflow qui ciblent le .NET Framework 4. Les workflows de machine à états ont été ajoutés dans le .NET 4.0.1 avec la mise en production de la mise à jour 1 de la plateforme, et ont été inclus dans le .NET Framework 4.5. [!INCLUDE[crabout](../../../includes/crabout-md.md)]workflows de machine d’état dans le .NET 4.0.1 - 4.0.3 et .NET Framework 4.5, consultez [mise à jour 4.0.1 pour Microsoft.NET Framework 4 fonctionnalités](http://msdn.microsoft.com/en-us/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) et [Workflows d’ordinateur d’état](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).  
  
 [Guide de Migration WF : Les activités personnalisées](http://go.microsoft.com/fwlink/?LinkId=153856)  
 Fournit des exemples et des instructions pour une nouvelle conception des activités personnalisées WF3 sur WF4.  
  
 [Guide de Migration WF : Les activités personnalisées avancées](http://go.microsoft.com/fwlink/?LinkId=275560)  
 Explique comment reconcevoir des activités personnalisées WF3 avancées qui utilisent les files d'attente WF3 et planifier des activités enfants en tant qu'activités personnalisées WF4.  
  
 [Guide de Migration WF : flux de travail](http://go.microsoft.com/fwlink/?LinkId=153858)  
 Fournit des exemples et des instructions pour une nouvelle conception des workflows WF3 sur WF4.  
  
 [WF Guide de Migration : Hébergement de flux de travail](http://go.microsoft.com/fwlink/?LinkId=275561)  
 Explique comment reconcevoir code d'hébergement WF3 en tant que code d'hébergement WF4. L'objectif est de couvrir les principales différences de l'hébergement de workflow entre WF3 et WF4.  
  
 [Guide de Migration WF : Le suivi de Workflow](http://go.microsoft.com/fwlink/?LinkId=275562)  
 Explique comment reconcevoir le code et la configuration de suivi WF3 à l'aide du code et de la configuration de suivi équivalents WF4.  
  
 [WF Guide : Services de flux de travail](http://go.microsoft.com/fwlink/?LinkId=275564)  
 Fournit des instructions détaillées orientées exemple pour reconcevoir les workflows qui implémentent des services Web Windows Communication Foundation (WCF) (en général connus sous le nom de services de workflowl) créés dans WF3 de façon à utiliser WF4, pour les scénarios courants d'activités prédéfinies.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Activities.Statements.Interop>
