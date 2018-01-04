---
title: "Comment : capturer une entrée d'utilisateur à partir d'un composant PrintDialog au moment de l'exécution"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fcc2ccc240752c8c54c28fe2358d3ef49cbf3b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a>Comment : capturer une entrée d'utilisateur à partir d'un composant PrintDialog au moment de l'exécution
Vous pouvez configurer les options relatives à l’impression au moment du design, vous devez parfois modifier ces options en cours d’exécution, probablement en raison des choix effectués par l’utilisateur. Vous pouvez capturer l’entrée d’utilisateur pour l’impression d’un document à l’aide de la <xref:System.Windows.Forms.PrintDialog> et <xref:System.Drawing.Printing.PrintDocument> composants.  
  
### <a name="to-change-print-options-programmatically"></a>Pour modifier les options d’impression par programmation  
  
1.  Ajouter un <xref:System.Windows.Forms.PrintDialog> et une <xref:System.Drawing.Printing.PrintDocument> à votre formulaire.  
  
2.  Définir le <xref:System.Windows.Forms.PrintDialog.Document%2A> propriété de la <xref:System.Windows.Forms.PrintDialog> à la <xref:System.Drawing.Printing.PrintDocument> ajouté au formulaire.  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  Afficher le <xref:System.Windows.Forms.PrintDialog> composant à l’aide de la <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> (méthode).  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  Choix de l’impression de l’utilisateur à partir de la boîte de dialogue seront copiés dans le <xref:System.Drawing.Printing.PrinterSettings> propriété de la <xref:System.Drawing.Printing.PrintDocument> composant.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : imprimer un fichier texte composé de plusieurs pages dans les Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [Prise en charge de l’impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
