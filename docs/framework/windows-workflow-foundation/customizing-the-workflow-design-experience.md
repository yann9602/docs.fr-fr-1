---
title: "Personnalisation de l'expérience de conception de workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60e8d01ad32e10f06191f7e0b38dcb648780ba29
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="customizing-the-workflow-design-experience"></a>Personnalisation de l'expérience de conception de workflow
Les scénarios destinés à la conception d'activités personnalisées et au réhébergement du [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] ont été considérablement simplifiés dans [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. Le développement et le déploiement sont maintenant à la fois plus facile et plus souple. La principale modification apportée à l'infrastructure est que le nouveau modèle de programmation de concepteur d'activités est basé sur [!INCLUDE[avalon1](../../../includes/avalon1-md.md)]. Cela vous permet de définir des concepteurs d'activités de façon déclarative et de réhéberger le [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] dans d'autres applications en toute simplicité. Lors du réhébergement, un éditeur d'expressions personnalisé peut être développé pour prendre en charge IntelliSense ou un domaine d'expression simplifié. L'intégration à [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] est devenue plus transparente avec l'utilisation de services de workflow. Les concepteurs d’activités personnalisées et l’arborescence d’éléments de modèle peuvent être utilisés pour améliorer les expériences au moment du design dans les concepteurs de workflow réhébergés.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Utilisation de concepteurs d’activités et de modèles d’activité personnalisés](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)  
 Explique comment créer de nouveaux concepteurs d'activités et modèles d'activité personnalisés.  
  
 [Réhébergement du concepteur de flux de travail](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 Explique comment réhéberger le [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] en dehors de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] et comment afficher les erreurs de validation.  
  
 [Utilisation d’un éditeur d’expressions personnalisé](../../../docs/framework/windows-workflow-foundation/using-a-custom-expression-editor.md)  
 Explique comment implémenter un éditeur d'expressions personnalisé à utiliser avec les concepteurs de workflow réhébergés en dehors de [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
## <a name="reference"></a>Référence  
 <xref:System.Activities.Presentation.ActivityDesigner>  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/extend.md)  
 [Concepteur](../../../docs/framework/windows-workflow-foundation/samples/designer.md)  
 [Concepteurs d’activités personnalisées](../../../docs/framework/windows-workflow-foundation/samples/custom-activity-designers.md)  
 [Réhébergement du Concepteur](../../../docs/framework/windows-workflow-foundation/samples/designer-rehosting.md)
