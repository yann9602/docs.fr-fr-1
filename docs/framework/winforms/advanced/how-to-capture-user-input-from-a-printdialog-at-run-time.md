---
title: "Comment&#160;: capturer une entr&#233;e d&#39;utilisateur &#224; partir d&#39;un composant PrintDialog au moment de l&#39;ex&#233;cution | Microsoft Docs"
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
  - "options d'impression"
  - "options d'impression, modifier au moment de l'exécution"
  - "imprimer (Windows Forms), options"
  - "au moment de l'exécution, modifier les options d'impression"
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: capturer une entr&#233;e d&#39;utilisateur &#224; partir d&#39;un composant PrintDialog au moment de l&#39;ex&#233;cution
Alors que vous pouvez définir les options liées à l'impression au moment du design, vous souhaiterez quelquefois modifier ces options au moment de l'exécution, très probablement à cause des choix faits par l'utilisateur.  Vous pouvez capturer une entrée d'utilisateur pour imprimer un document à l'aide des composants <xref:System.Windows.Forms.PrintDialog> et <xref:System.Drawing.Printing.PrintDocument>.  
  
### Pour modifier les options d'impression par programme  
  
1.  Ajoutez les composants <xref:System.Windows.Forms.PrintDialog> et <xref:System.Drawing.Printing.PrintDocument> à votre formulaire.  
  
2.  Définissez la propriété <xref:System.Windows.Forms.PrintDialog.Document%2A> du contrôle <xref:System.Windows.Forms.PrintDialog> en fonction du composant <xref:System.Drawing.Printing.PrintDocument> ajouté au formulaire.  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  Affichez le composant <xref:System.Windows.Forms.PrintDialog> en utilisant la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  
  
    ```vb  
    PrintDialog1.ShowDialog()  
  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  Les choix d'impression de l'utilisateur qui figurent dans la boîte de dialogue seront copiés vers la propriété <xref:System.Drawing.Printing.PrinterSettings> du composant <xref:System.Drawing.Printing.PrintDocument>.  
  
## Voir aussi  
 [Comment : imprimer un fichier texte composé de plusieurs pages dans les Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)   
 [Prise en charge de l'impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)