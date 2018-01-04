---
title: Prise en charge de l'impression dans les Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81f89ee41eb9f8b492ab12e30ae4580cdffbd8f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-print-support"></a>Prise en charge de l'impression dans les Windows Forms
L’impression dans les Windows Forms consiste principalement à l’aide de la [composant PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) composant pour permettre à l’utilisateur d’imprimer et le [contrôle PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) contrôle, [PrintDialog Composant](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) et [composant PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) composants afin de fournir une interface graphique familière aux utilisateurs habitués au système d’exploitation Windows.  
  
 En général, vous créez une nouvelle instance de la <xref:System.Drawing.Printing.PrintDocument> composant, définir les propriétés qui décrivent les éléments à imprimer à l’aide de la <xref:System.Drawing.Printing.PrinterSettings> et <xref:System.Drawing.Printing.PageSettings> classes, puis appelez le <xref:System.Drawing.Printing.PrintDocument.Print%2A> méthode pour imprimer le document.  
  
 Au cours de l’impression à partir d’une application Windows, le <xref:System.Drawing.Printing.PrintDocument> composant affiche une boîte de dialogue d’impression d’annulation afin d’alerter les utilisateurs de l’impression en cours et pour autoriser le travail d’impression doit être annulée.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour créer des travaux d’impression Windows Forms standard](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 Explique comment utiliser le <xref:System.Drawing.Printing.PrintDocument> composant pour imprimer à partir d’un Windows Form.  
  
 [Guide pratique pour capturer une entrée d’utilisateur à partir d’un composant PrintDialog au moment de l’exécution](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Explique comment modifier les options d’impression sélectionnées par programme en utilisant le <xref:System.Windows.Forms.PrintDialog> composant.  
  
 [Guide pratique pour choisir les imprimantes connectées à l'ordinateur d'un utilisateur dans les Windows Forms](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 Décrit la modification de l’imprimante à utiliser à l’aide de la <xref:System.Windows.Forms.PrintDialog> composant au moment de l’exécution.  
  
 [Comment : imprimer des graphiques dans Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 Décrit l’envoi de graphismes à l’imprimante.  
  
 [Comment : imprimer un fichier texte composé de plusieurs pages dans les Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Décrit l’envoi de texte à l’imprimante.  
  
 [Guide pratique pour terminer des travaux d'impression Windows Forms](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 Explique comment avertir les utilisateurs de l’achèvement d’un travail d’impression.  
  
 [Guide pratique pour imprimer un Windows Form](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 Montre comment imprimer une copie de l’écran actuel.  
  
 [Guide pratique pour imprimer dans les Windows Forms en utilisant l'aperçu avant impression](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 Montre comment utiliser un <xref:System.Windows.Forms.PrintPreviewDialog> pour imprimer un document.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Composant PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 Explique comment utiliser le <xref:System.Drawing.Printing.PrintDocument> composant.  
  
 [PrintDialog, composant](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 Explique comment utiliser le <xref:System.Windows.Forms.PrintDialog> composant.  
  
 [PrintPreviewDialog, contrôle](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 Explique comment utiliser le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle.  
  
 [PageSetupDialog, composant](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 Explique comment utiliser le <xref:System.Windows.Forms.PageSetupDialog> composant.  
  
 <xref:System.Drawing.Printing>  
 Décrit les classes dans le <xref:System.Drawing.Printing> espace de noms.
