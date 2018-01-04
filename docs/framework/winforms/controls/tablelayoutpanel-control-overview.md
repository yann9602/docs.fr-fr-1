---
title: "Vue d'ensemble du contrôle TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 614887524a49e1163b3049111895166995fdace4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="tablelayoutpanel-control-overview"></a>Vue d'ensemble du contrôle TableLayoutPanel
Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> réorganise son contenu dans une grille. La disposition étant effectuée au moment du design et au moment de l'exécution, elle peut changer dynamiquement quand l'environnement d'application change. Cela permet de redimensionner proportionnellement les contrôles du panneau, pour pouvoir répondre à des modifications telles que le redimensionnement du contrôle parent ou le changement de longueur de texte en raison de la localisation.  
  
 Tout contrôle Windows Forms peut être un enfant du contrôle <xref:System.Windows.Forms.TableLayoutPanel>, y compris d'autres instances de <xref:System.Windows.Forms.TableLayoutPanel>. Cela vous permet de construire des dispositions sophistiquées qui s'adaptent aux modifications au moment de l'exécution.  
  
 Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> peut s'étendre pour accepter de nouveaux contrôles quand ils sont ajoutés, en fonction de la valeur des propriétés <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, et <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A>. L'affectation de la valeur 0 à la propriété <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> ou <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> indique que le <xref:System.Windows.Forms.TableLayoutPanel> sera indépendant dans la direction correspondante.  
  
 Vous pouvez également contrôler la direction d'expansion (horizontale ou verticale) une fois que le contrôle <xref:System.Windows.Forms.TableLayoutPanel> est rempli de contrôles enfants. Par défaut, le contrôle <xref:System.Windows.Forms.TableLayoutPanel> s'étend vers le bas en ajoutant des lignes.  
  
 Si vous souhaitez que les lignes et les colonnes se comportent différemment du comportement par défaut, vous pouvez contrôler leurs propriétés à l'aide des propriétés <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> et <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>. Vous pouvez définir les propriétés des lignes ou des colonnes individuellement.  
  
 Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> ajoute les propriétés suivantes à ses contrôles enfants : `Cell`, `Column`, `Row`, `ColumnSpan`, et `RowSpan`.  
  
 Vous pouvez fusionner des cellules dans le contrôle <xref:System.Windows.Forms.TableLayoutPanel> en définissant les propriétés `ColumnSpan` ou `RowSpan` sur un contrôle enfant.  
  
1.  [Comment : aligner et étirer un contrôle dans un contrôle TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [Comment : étendre des lignes et des colonnes dans un contrôle TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
3.  [Comment : modifier des colonnes et des lignes dans un contrôle TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
4.  [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [Guide pratique pour créer une présentation Windows Forms qui répond bien à la localisation](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Guide pratique pour créer un Windows Form redimensionnable pour l'entrée de données](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [Meilleures pratiques pour le contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
