---
title: "Comment : grouper des contrôles RadioButton Windows Forms en un ensemble fonctionnant indépendamment"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c92048374941f735568bcd758ed475eba78b81e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Comment : grouper des contrôles RadioButton Windows Forms en un ensemble fonctionnant indépendamment
Windows Forms <xref:System.Windows.Forms.RadioButton> contrôles sont conçus pour donner aux utilisateurs un choix entre deux ou plusieurs paramètres, dont une seule peut être assignée à une procédure ou un objet. Par exemple, un groupe de <xref:System.Windows.Forms.RadioButton> contrôles peuvent afficher une liste des transporteurs de package pour une commande, mais un seul des transporteurs sera utilisé. Par conséquent, seul <xref:System.Windows.Forms.RadioButton> à la fois peut être sélectionné, même si elle fait partie d’un groupe fonctionnel.  
  
 Groupe de cases d’option en dessinant comme à l’intérieur d’un conteneur un <xref:System.Windows.Forms.Panel> (contrôle), un <xref:System.Windows.Forms.GroupBox> contrôle ou un formulaire. Toutes les cases d’option qui sont ajoutées directement à un groupe d’un formulaire deviennent. Pour ajouter des groupes distincts, vous devez les placer à l’intérieur des panneaux ou zones de groupe. Pour plus d’informations sur les panneaux ou zones de groupe, consultez [vue d’ensemble du contrôle de panneau](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) ou [vue d’ensemble du contrôle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>Pour regrouper des contrôles RadioButton comme un ensemble fonctionnant indépendamment des autres jeux  
  
1.  Faites glisser un <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel> contrôle depuis la **Windows Forms** onglet le **boîte à outils** vers le formulaire.  
  
2.  Dessiner <xref:System.Windows.Forms.RadioButton> contrôle sur le <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel> contrôle.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.RadioButton>  
 [Vue d’ensemble du contrôle RadioButton](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)  
 [Vue d’ensemble du contrôle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Vue d’ensemble du contrôle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [Vue d'ensemble du contrôle CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [RadioButton, contrôle](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
