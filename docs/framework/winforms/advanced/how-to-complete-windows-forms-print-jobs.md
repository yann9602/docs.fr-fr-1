---
title: "Comment&#160;: terminer des travaux d&#39;impression Windows Forms | Microsoft Docs"
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
  - "travaux d'impression, exécuter dans les Windows Forms"
  - "imprimer (Windows Forms), travaux d'impression"
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# Comment&#160;: terminer des travaux d&#39;impression Windows Forms
Les traitements de texte et d'autres applications qui impliquent des travaux d'impression offrent la possibilité d'afficher un message destiné aux utilisateurs au terme d'un travail d'impression.  Vous pouvez fournir cette fonctionnalité dans vos Windows Forms en gérant l'événement <xref:System.Drawing.Printing.PrintDocument.EndPrint> du composant <xref:System.Drawing.Printing.PrintDocument>.  
  
 La procédure suivante requiert la création d'une application Windows comprenant un composant <xref:System.Drawing.Printing.PrintDocument>, ce qui est la façon standard d'activer l'impression à partir d'une application Windows.  Pour plus d'informations sur l'impression à partir de Windows Forms à l'aide du composant <xref:System.Drawing.Printing.PrintDocument>, consultez [Comment : créer des travaux d'impression Windows Forms standard](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md).  
  
### Pour terminer un travail d'impression  
  
1.  Définissez la propriété <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> du composant <xref:System.Drawing.Printing.PrintDocument>.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2.  Écrivez le code permettant de gérer l'événement <xref:System.Drawing.Printing.PrintDocument.EndPrint>.  
  
     Dans l'exemple de code ci\-dessous, un message est affiché, indiquant la fin de l'impression du document.  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,   
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +   
          " has finished printing.");  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## Voir aussi  
 <xref:System.Drawing.Printing.PrintDocument>   
 [Prise en charge de l'impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)