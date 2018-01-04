---
title: "Vue d'ensemble du contrôle RadioButton (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 67befd973dec38628f97a0d3153c399d48c18305
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="radiobutton-control-overview-windows-forms"></a>Vue d'ensemble du contrôle RadioButton (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RadioButton> contrôle présente un ensemble de deux ou plusieurs choix mutuellement exclusifs à l’utilisateur. Tandis que les cases à cocher et des cases d’option peut sembler fonctionner de la même façon, il existe une différence importante : lorsqu’un utilisateur sélectionne une case d’option, les autres cases d’option dans le même groupe ne peut pas être sélectionnée. En revanche, vous pouvez sélectionner autant de cases à cocher. Définition d’un groupe de cases d’option indique à l’utilisateur, « Voici un ensemble de choix à partir de laquelle vous pouvez choisir un seul et unique ».  
  
## <a name="using-the-control"></a>L’utilisation du contrôle  
 Lorsqu’un <xref:System.Windows.Forms.RadioButton> clic sur le contrôle, son <xref:System.Windows.Forms.RadioButton.Checked%2A> est définie sur `true` et le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements est appelé. Le <xref:System.Windows.Forms.RadioButton.CheckedChanged> événement est déclenché lorsque la valeur de la <xref:System.Windows.Forms.RadioButton.Checked%2A> de propriété est modifiée. Si le <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> est définie sur `true` (la valeur par défaut), lorsque la case d’option est sélectionnée, tous les autres dans le groupe sont automatiquement effacés. Cette propriété est généralement uniquement la valeur `false` lorsque le code de validation est utilisé s’assurer que la case d’option sélectionnée est une option autorisée. Le texte affiché dans le contrôle est défini avec la <xref:System.Windows.Forms.Control.Text%2A> propriété, qui peut contenir des raccourcis de touches d’accès. Une clé d’accès permet à un utilisateur « sur « le contrôle en appuyant sur la touche ALT et la clé d’accès. Pour plus d’informations, consultez [Comment : créer de touches d’accès rapide pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) et [Comment : définir le texte affiché par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 Le <xref:System.Windows.Forms.RadioButton> contrôle peut apparaître comme un bouton de commande, ce qui semble avoir été sélectionné, si le <xref:System.Windows.Forms.RadioButton.Appearance%2A> est définie sur <xref:System.Windows.Forms.Appearance.Button>. Cases d’option peuvent également afficher des images à l’aide de la <xref:System.Windows.Forms.ButtonBase.Image%2A> et <xref:System.Windows.Forms.ButtonBase.ImageList%2A> propriétés. Pour plus d’informations, consultez [Comment : définir l’Image affichée par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.RadioButton>  
 [Vue d’ensemble du contrôle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Vue d’ensemble du contrôle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [Vue d'ensemble du contrôle CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Guide pratique pour créer des touches d'accès rapide pour des contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [Guide pratique pour définir le texte affiché par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Guide pratique pour grouper des contrôles RadioButton Windows Forms en un ensemble fonctionnant indépendamment](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)  
 [RadioButton, contrôle](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
