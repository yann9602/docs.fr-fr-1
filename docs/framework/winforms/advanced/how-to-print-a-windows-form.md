---
title: "Comment&#160;: imprimer un Windows Form | Microsoft Docs"
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
  - "imprimer (Windows Forms), imprimer un formulaire"
  - "imprimer (Windows Forms)"
  - "imprimer un formulaire"
  - "Windows Forms, imprimer"
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: imprimer un Windows Form
Dans le cadre du processus de développement, vous souhaiterez généralement imprimer une copie du Windows Form.  L'exemple de code suivant indique comment imprimer une copie du formulaire actuel en utilisant la méthode <xref:System.Drawing.Graphics.CopyFromScreen%2A>.  
  
## Exemple  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## Compilation du code  
 Il s'agit d'un exemple de code complet qui contient une méthode `Main`.  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Vous n'avez pas l'autorisation d'accéder à l'imprimante.  
  
-   Aucune imprimante n'est installée.  
  
## Sécurité .NET Framework  
 Pour exécuter cet exemple de code, vous devez posséder une autorisation d'accès à l'imprimante que vous utilisez avec votre ordinateur.  
  
## Voir aussi  
 <xref:System.Drawing.Printing.PrintDocument>   
 [Comment : rendre des images avec GDI\+](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)   
 [Comment : imprimer des graphiques dans Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)