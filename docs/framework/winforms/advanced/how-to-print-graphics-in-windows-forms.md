---
title: "Comment&#160;: imprimer des graphiques dans Windows&#160;Forms | Microsoft Docs"
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
  - "graphiques, imprimer"
  - "imprimer (Windows Forms), graphiques"
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Comment&#160;: imprimer des graphiques dans Windows&#160;Forms
Il arrive souvent de devoir imprimer des graphismes dans une application Windows.  La classe <xref:System.Drawing.Graphics> propose des méthodes pour dessiner des objets sur un périphérique, comme un écran ou une imprimante.  
  
### Pour imprimer des graphismes  
  
1.  Ajoutez le composant <xref:System.Drawing.Printing.PrintDocument> au formulaire.  
  
2.  Dans le gestionnaire d'événements <xref:System.Drawing.Printing.PrintDocument.PrintPage>, utilisez la propriété <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> de la classe <xref:System.Drawing.Printing.PrintPageEventArgs> pour indiquer à l'imprimante le type de graphisme dont il s'agit.  
  
     L'exemple de code suivant affiche un gestionnaire d'événements qui est utilisé pour créer une ellipse bleue dans un rectangle englobant.  Le rectangle possède l'emplacement et les dimensions suivants : il commence à 100, 150 avec une largeur de 250 et une hauteur de 250.  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillEllipse(Brushes.Blue, New Rectangle(100, 150, 250, 250))  
    End Sub  
  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Blue,   
         new Rectangle(100, 150, 250, 250));  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Blue,  
             Rectangle(100, 150, 250, 250));  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
## Voir aussi  
 <xref:System.Drawing.Graphics>   
 <xref:System.Drawing.Brush>   
 [Prise en charge de l'impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)