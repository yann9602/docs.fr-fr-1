---
title: "Comment&#160;: afficher une page Web &#224; partir d&#39;un contr&#244;le LinkLabel Windows Forms (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LinkLabel1_LinkClicked"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "exemples (Windows Forms), LinkLabel (contrôle)"
  - "lier, vers des pages Web à partir de formulaires"
  - "LinkLabel (contrôle Windows Forms), exemples"
  - "pages Web, afficher"
  - "Windows Forms, lier à des pages Web"
ms.assetid: 477a7398-5971-4de3-b24c-f49f32bdb28a
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: afficher une page Web &#224; partir d&#39;un contr&#244;le LinkLabel Windows Forms (Visual Basic)
Cet exemple affiche une page Web dans le navigateur par défaut lorsque l'utilisateur clique sur un contrôle <xref:System.Windows.Forms.LinkLabel> Windows Forms.  
  
## Exemple  
  
```vb  
Private Sub Form1_Load(ByVal sender As System.Object, ByVal e _  
As System.EventArgs) Handles MyBase.Load  
    LinkLabel1.Text = "Click here to get more info."  
    LinkLabel1.Links.Add(6, 4, "www.microsoft.com")  
End Sub  
Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, ByVal _  
e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) Handles _  
LinkLabel1.LinkClicked  
    System.Diagnostics.Process.Start(e.Link.LinkData.ToString())  
End Sub  
```  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Un Windows Form nommé `Form1`.  
  
-   un contrôle <xref:System.Windows.Forms.LinkLabel> nommé `LinkLabel1` ;  
  
-   une connexion Internet active.  
  
## Sécurité .NET Framework  
 L'appel à la méthode <xref:System.Diagnostics.Process.Start%2A> requiert une confiance totale.  Pour plus d'informations, consultez <xref:System.Security.SecurityException>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.LinkLabel>   
 [LinkLabel, contrôle](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)