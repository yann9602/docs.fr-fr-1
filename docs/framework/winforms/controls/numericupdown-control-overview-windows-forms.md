---
title: "Vue d'ensemble du contrôle NumericUpDown (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 067a8862ee991213e584819e1cf99eddde06e2bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="numericupdown-control-overview-windows-forms"></a>Vue d'ensemble du contrôle NumericUpDown (Windows Forms)
Le <xref:System.Windows.Forms.NumericUpDown> contrôle se présente comme une combinaison d’une zone de texte et une paire de flèches sur lesquelles l’utilisateur peut cliquer pour ajuster une valeur. Le contrôle affiche et définit une valeur numérique unique à partir d’une liste de choix de valeurs numériques fixes. L’utilisateur peut augmenter et diminuer le nombre par le haut et vers le bas flèches, en appuyant sur les touches de direction haut et bas ou en tapant un nombre dans la zone de texte du contrôle. En cliquant sur la flèche haut déplace le numéro de la valeur maximale ; en cliquant sur la touche de direction bas déplace le nombre vers la valeur minimale.  
  
 En raison de ses fonctionnalités polyvalentes, ce contrôle est, par exemple, un choix évident, si vous souhaitez créer un contrôle de volume pour une application de lecteur de musique. Le <xref:System.Windows.Forms.NumericUpDown> contrôle est utilisé dans de nombreuses applications du Panneau de configuration Windows.  
  
## <a name="key-properties-and-methods"></a>Méthodes et propriétés de clé  
 Les nombres affichés dans la zone de texte du contrôle peuvent être dans divers formats, y compris hexadécimales. Pour plus d’informations, consultez [Comment : mettre en forme le contrôle NumericUpDown Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). Les principales propriétés du contrôle sont <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (valeur par défaut 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (valeur par défaut 0), et <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (valeur par défaut 1). Le <xref:System.Windows.Forms.NumericUpDown.Value%2A> propriété définit le nombre actuellement sélectionné dans le contrôle. Le <xref:System.Windows.Forms.NumericUpDown.Increment%2A> propriété définit le montant que le nombre est ajusté par lorsque l’utilisateur clique sur un haut ou flèche vers le bas. Lorsque le focus quitte le contrôle, toute valeur entrée est validée sur les valeurs numériques minimales et maximales. Vous pouvez augmenter la vitesse à laquelle le contrôle se déplace à travers les nombres, lorsque l’utilisateur appuie continuellement sur le haut ou flèche bas, avec la <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> propriété. Les principales méthodes du contrôle sont <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> et <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.NumericUpDown>  
 [NumericUpDown, contrôle](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [Guide pratique pour définir le format du contrôle NumericUpDown Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)  
 [TextBox, contrôle](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
