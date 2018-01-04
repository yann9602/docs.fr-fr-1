---
title: "Comment : substituer la méthode OnRender de Panel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 958595cdfa521b372270d6283c7134ef0ba0ef79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-override-the-panel-onrender-method"></a>Comment : substituer la méthode OnRender de Panel
Cet exemple montre comment remplacer la <xref:System.Windows.Controls.Panel.OnRender%2A> méthode <xref:System.Windows.Controls.Panel> afin d’ajouter des effets de graphiques personnalisées à un élément de disposition.  
  
## <a name="example"></a>Exemple  
 Utilisez la <xref:System.Windows.Controls.Panel.OnRender%2A> méthode afin d’ajouter des effets graphiques à un élément du Panneau de configuration de rendu. Par exemple, vous pouvez utiliser cette méthode pour ajouter une bordure personnalisée ou des effets d’arrière-plan. A <xref:System.Windows.Media.DrawingContext> objet est passé en tant qu’argument, qui fournit des méthodes pour dessiner des formes, texte, images ou vidéos. Par conséquent, cette méthode est utile pour la personnalisation d’un objet Panneau de configuration.  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.Panel>  
 [Vue d’ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Panneau Radial personnalisé, exemple](http://go.microsoft.com/fwlink/?LinkID=159982)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
