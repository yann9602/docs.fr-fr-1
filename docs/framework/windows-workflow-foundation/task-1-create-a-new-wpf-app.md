---
title: "Tâche 1 : créer une nouvelle application Windows Presentation Foundation."
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a207b09ff7124bb161678627f365a6fa4021a38d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Tâche 1 : créer une nouvelle application Windows Presentation Foundation.
Dans cette tâche, vous allez créer une application [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] vide à l'aide du modèle Visual Studio d'application WPF, et ajouter des références aux assemblys de workflow [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] appropriés.  
  
### <a name="to-create-the-wpf-application-project"></a>Pour créer le projet d'application WPF  
  
1.  Ouvrez [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] et sur le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, sélectionnez soit **Visual C#** ou **Visual Basic** à partir de la **modèles installés** volet situé à gauche de la zone. Si la langue de votre choix n’apparaît pas, regardez sous **autres langages**.  
  
3.  Sélectionnez **Windows** dans les **modèles installés** volet.  
  
4.  Dans le volet supérieur, vérifiez que (la valeur par défaut) **.NET Framework 4** a été sélectionné dans la zone de liste déroulante, puis sélectionnez **Application WPF**.  
  
5.  Définissez le nom du projet pour **HostingApplication** au bas de la fenêtre.  
  
6.  Définissez le nom de la solution sur **RehostingTheDesigner**.  
  
7.  Cliquez sur **OK** pour créer le projet d’application. [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] crée une interface utilisateur WPF de base de votre application et inclut le code XAML et les fichiers code-behind appropriés.  
  
8.  Ajoutez des références aux **WorkflowModel** assemblys. Pour ce faire, dans **l’Explorateur de solutions**, avec le bouton droit le **HostingApplication** de projet et sélectionnez **ajouter une référence**.  
  
9. Dans le **ajouter une référence** boîte de dialogue, cliquez sur le **.NET** onglet, maintenez la touche CTRL enfoncée, sélectionnez les assemblys suivants, puis cliquez sur **OK**:  
  
    -   System.Activities  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. Cliquez sur **OK**.  
  
11. Consultez [tâche 2 : héberger le Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) pour en savoir plus sur l’hôte de la zone de conception du Concepteur de workflow.  
  
## <a name="see-also"></a>Voir aussi  
 [Réhébergement du concepteur de flux de travail](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Tâche 2 : Héberger le concepteur de flux de travail](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
