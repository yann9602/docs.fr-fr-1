---
title: Vue d'ensemble du composant PrintDialog (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20bbfd02c7fe8f5ca89d67e045b0edd4f2db996c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="printdialog-component-overview-windows-forms"></a>Vue d'ensemble du composant PrintDialog (Windows Forms)
Windows Forms [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) composant est une boîte de dialogue préconfigurée utilisée pour sélectionner une imprimante, de choisir les pages à imprimer et de déterminer d’autres paramètres liés à l’impression dans les applications Windows. Utilisez-le comme un moyen simple de sélectionner une imprimante ou des paramètres d'impression au lieu de configurer votre propre boîte de dialogue. Vous pouvez activer les utilisateurs à imprimer de nombreuses parties de leurs documents : imprimer toutes les, imprimer une plage de pages sélectionnées ou imprimer une sélection. En vous appuyant sur des boîtes de dialogue Windows standard, vous pouvez créer des applications dont la fonction de base est immédiatement familière aux utilisateurs. Le <xref:System.Windows.Forms.PrintDialog> composant hérite de la <xref:System.Windows.Forms.CommonDialog> classe.  
  
## <a name="working-with-the-component"></a>Utilisation du composant  
 Utilisez la <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> méthode pour afficher la boîte de dialogue au moment de l’exécution. Ce composant possède des propriétés relatives à un travail d’impression unique (<xref:System.Drawing.Printing.PrintDocument> classe) ou les paramètres d’une imprimante spécifique (<xref:System.Drawing.Printing.PrinterSettings> classe). Une de ces, peut à son tour, être partagée par plusieurs imprimantes.  
  
 Lorsqu’il est ajouté à un formulaire, le <xref:System.Windows.Forms.PrintDialog> composant apparaît dans la barre d’état en bas du Concepteur Windows Forms.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.PrintDialog>  
 [PrintDialog, composant](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
