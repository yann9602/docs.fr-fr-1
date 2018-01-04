---
title: "Comment : créer des travaux d'impression Windows Forms standard"
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
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69499cdee7803de504e960b08754df33602cfcf6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Comment : créer des travaux d'impression Windows Forms standard
La base de l’impression dans les Windows Forms est la <xref:System.Drawing.Printing.PrintDocument> composant, plus spécifiquement, le <xref:System.Drawing.Printing.PrintDocument.PrintPage> événement. En écrivant du code pour gérer les <xref:System.Drawing.Printing.PrintDocument.PrintPage> événement, vous pouvez spécifier les éléments à imprimer et l’imprimer.  
  
### <a name="to-create-a-print-job"></a>Pour créer un travail d’impression  
  
1.  Ajouter un <xref:System.Drawing.Printing.PrintDocument> à votre formulaire.  
  
2.  Écrivez du code pour gérer l’événement <xref:System.Drawing.Printing.PrintDocument.PrintPage>.  
  
     Vous devez coder votre propre logique d’impression. En outre, vous devez spécifier l’élément à imprimer.  
  
     Dans l’exemple de code suivant, un exemple de graphisme sous la forme d’un rectangle rouge est créé dans le <xref:System.Drawing.Printing.PrintDocument.PrintPage> Gestionnaire d’événements à l’élément à imprimer.  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     Vous pouvez également écrire du code pour le <xref:System.Drawing.Printing.PrintDocument.BeginPrint> et <xref:System.Drawing.Printing.PrintDocument.EndPrint> événements, en incluant éventuellement un entier représentant le nombre total de pages à imprimer qui est décrémenté à mesure que chaque page est imprimée.  
  
    > [!NOTE]
    >  Vous pouvez ajouter un <xref:System.Windows.Forms.PrintDialog> à votre formulaire pour fournir une interface propre et efficace de l’utilisateur (IU) à vos utilisateurs. Définition de la <xref:System.Windows.Forms.PrintDialog.Document%2A> propriété de la <xref:System.Windows.Forms.PrintDialog> permet de composant vous permet de définir les propriétés relatives à l’impression de documents vous travaillez sur votre formulaire. Pour plus d’informations sur la <xref:System.Windows.Forms.PrintDialog> composant, consultez [du composant PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md).  
  
     Pour plus d’informations sur les spécificités des Windows Forms, les travaux d’impression, y compris la création d’un travail d’impression par programmation, consultez <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Prise en charge de l’impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
