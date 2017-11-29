---
title: "Configuration de la validation d’activité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d17a640db012730ae8f5329f4e625823a4f5bff2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-activity-validation"></a>Configuration de la validation d’activité
La validation d'activité permet aux auteurs et aux utilisateurs d'activités d'identifier et de signaler des erreurs dans la configuration de toute activité, avant son exécution. [!INCLUDE[wf](../../../includes/wf-md.md)] fournit les trois types suivants de validation des activités :  
  
-   attributs `RequiredArgument` et `OverloadGroup` ;  
  
-   validation basée sur le code impératif ;  
  
-   contraintes déclaratives.  
  
 Les attributs `RequiredArgument` et `OverloadGroup` indiquent que certains arguments d'une activité sont requis. La validation basée sur le code impératif permet à une activité de fournir facilement sa propre validation. Quant aux contraintes déclaratives, elle permettent la validation de l'activité et de sa relation avec le flux de travail conteneur. Si une activité n'est pas configurée selon les spécifications de validation, des erreurs et avertissements de validation sont retournés. Si le flux de travail conteneur est créé à l'aide du Workflow Designer, l'ensemble des erreurs et avertissements de validation s'affichent dans le concepteur. Si le flux de travail est créé en dehors du Workflow Designer, toutes les erreurs de validation sont retournées lors de l'appel du flux de travail. Quelle que soit sa méthode de création, un flux de travail contenant des erreurs de validation n'est jamais autorisé à s'exécuter. Cette section offre une vue d’ensemble de ces types de validation d’activité et de la façon dont la validation d’activité est appelée.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Arguments obligatoires et groupes surchargés](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)  
 Explique comment utiliser les attributs `RequiredArgument` et `OverloadGroup` pour fournir la validation.  
  
 [Validation basée sur le code impératif](../../../docs/framework/windows-workflow-foundation/imperative-code-based-validation.md)  
 Explique comment utiliser la validation basée sur code pour les activités basées sur les objets <xref:System.Activities.CodeActivity> et <xref:System.Activities.NativeActivity>.  
  
 [Contraintes déclaratives](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)  
 Explique comment utiliser les contraintes déclaratives pour fournir la validation des activités complexes.  
  
 [Appel de la validation d’activité](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)  
 Explique dans quels cas la validation d’activité est appelée automatiquement et comment appeler explicitement la validation.  
  
## <a name="reference"></a>Référence  
  
## <a name="related-sections"></a>Rubriques connexes
