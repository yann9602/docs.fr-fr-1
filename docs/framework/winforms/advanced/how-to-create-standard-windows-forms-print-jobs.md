---
title: "Comment&#160;: cr&#233;er des travaux d&#39;impression Windows Forms standard | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "imprimer (Visual Basic), dans les applications Windows"
  - "imprimer (Windows Forms)"
  - "imprimer (Windows Forms), créer des travaux d'impression"
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: cr&#233;er des travaux d&#39;impression Windows Forms standard
L'élément clé de l'impression dans les Windows Forms est le composant <xref:System.Drawing.Printing.PrintDocument>, et plus spécialement l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage>.  En écrivant du code pour gérer l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage>, vous pouvez spécifier les éléments à imprimer et les modalités d'impression.  
  
### Pour créer un travail d'impression  
  
1.  Ajoutez le composant <xref:System.Drawing.Printing.PrintDocument> au formulaire.  
  
2.  Écrivez du code pour gérer l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage>.  
  
     Vous devez coder votre propre logique d'impression.  En outre, vous devez spécifier le type d'élément à imprimer.  
  
     Dans l'exemple de code ci\-dessous, un exemple de graphisme sous la forme d'un rectangle rouge est créé dans le gestionnaire d'événements <xref:System.Drawing.Printing.PrintDocument.PrintPage> pour représenter l'élément à imprimer.  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
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
  
     Il est possible que vous souhaitiez également écrire du code pour les événements <xref:System.Drawing.Printing.PrintDocument.BeginPrint> et <xref:System.Drawing.Printing.PrintDocument.EndPrint>, en incluant éventuellement un nombre entier représentant le nombre total de pages à imprimer, nombre qui est décrémenté à mesure que les pages s'impriment.  
  
    > [!NOTE]
    >  Vous pouvez ajouter un composant <xref:System.Windows.Forms.PrintDialog> au formulaire pour offrir aux utilisateurs une interface utilisateur claire et efficace.  La définition de la propriété <xref:System.Windows.Forms.PrintDialog.Document%2A> du composant <xref:System.Windows.Forms.PrintDialog> vous permet de définir des propriétés relatives au document d'impression utilisé dans votre formulaire.  Pour plus d'informations sur le composant <xref:System.Windows.Forms.PrintDialog>, consultez [PrintDialog, composant](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md).  
  
     Pour plus d'informations sur les spécificités des travaux d'impression Windows Forms, et notamment la création d'un travail d'impression par programme, consultez <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## Voir aussi  
 <xref:System.Drawing.Printing.PrintDocument>   
 [Prise en charge de l'impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)