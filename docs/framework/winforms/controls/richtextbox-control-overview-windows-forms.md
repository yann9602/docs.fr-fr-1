---
title: "Vue d'ensemble du contrôle RichTextBox (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4278f569a789ca6e8466e0b8e71557446b63955e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="richtextbox-control-overview-windows-forms"></a>Vue d'ensemble du contrôle RichTextBox (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RichTextBox> contrôle est utilisé pour l’affichage, la saisie et la manipulation de texte avec mise en forme. Le <xref:System.Windows.Forms.RichTextBox> contrôle effectue tout le <xref:System.Windows.Forms.TextBox> effectue, mais il peut également afficher des polices, couleurs et des liens ; charger du texte et des images incorporées à partir d’un fichier ; et rechercher les caractères spécifiés. Le <xref:System.Windows.Forms.RichTextBox> contrôle est généralement utilisé pour fournir la manipulation du texte et afficher les fonctionnalités similaires aux applications de traitement de texte tel que Microsoft Word. Comme le <xref:System.Windows.Forms.TextBox> (contrôle), le <xref:System.Windows.Forms.RichTextBox> contrôle peut afficher les barres de défilement ; mais contrairement à la <xref:System.Windows.Forms.TextBox> contrôle, sa valeur par défaut est pour afficher les barres de défilement horizontale et verticale en fonction des besoins, et il comporte des paramètres de barre de défilement supplémentaires.  
  
## <a name="working-with-the-richtextbox-control"></a>Utilisation du contrôle RichTextBox  
 Comme avec la <xref:System.Windows.Forms.TextBox> (contrôle), le texte affiché est défini le <xref:System.Windows.Forms.RichTextBox.Text%2A> propriété. Le <xref:System.Windows.Forms.RichTextBox> contrôle possède de nombreuses propriétés en forme du texte. Pour plus d’informations sur ces propriétés, consultez [Guide pratique pour définir les attributs de police du contrôle RichTextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) et [Guide pratique pour définir les retraits, les retraits négatifs de première ligne et les listes à puces avec le contrôle RichTextBox Windows Forms](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md). Pour manipuler les fichiers, les <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> et <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> méthodes peuvent afficher et écrire plusieurs formats de fichier, y compris le texte brut, texte brut Unicode et RTF (RICH Text Format). Formats de fichier sont répertoriés dans <xref:System.Windows.Forms.RichTextBoxStreamType>. Vous pouvez utiliser la <xref:System.Windows.Forms.RichTextBox.Find%2A> méthode pour rechercher des chaînes de texte ou des caractères spécifiques.  
  
 Vous pouvez également utiliser un <xref:System.Windows.Forms.RichTextBox> contrôle pour les liens de style Web en définissant le <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> propriété `true` et l’écriture de code pour gérer les <xref:System.Windows.Forms.RichTextBox.LinkClicked> événement. Pour plus d’informations, consultez [Guide pratique pour afficher des liens de style web avec le contrôle RichTextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md). Vous pouvez empêcher l’utilisateur à partir de la manipulation de tout ou partie du texte dans le contrôle en définissant le <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> propriété `true`.  
  
 Vous pouvez annuler et rétablir la plupart des opérations d’édition dans un <xref:System.Windows.Forms.RichTextBox> contrôle en appelant le <xref:System.Windows.Forms.TextBoxBase.Undo%2A> et <xref:System.Windows.Forms.RichTextBox.Redo%2A> méthodes. Le <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> méthode vous permet de déterminer si la dernière opération annulée par l’utilisateur peut être réappliquée au contrôle.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox, contrôle](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Vue d’ensemble du contrôle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
