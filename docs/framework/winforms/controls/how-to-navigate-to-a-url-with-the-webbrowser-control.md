---
title: "Comment&#160;: naviguer vers une URL avec un contr&#244;le WebBrowser | Microsoft Docs"
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
  - "WebBrowser.Navigate"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "exemples (Windows Forms), WebBrowser (contrôle)"
  - "URL, naviguer vers"
  - "WebBrowser (contrôle Windows Forms), exemples"
  - "WebBrowser (contrôle Windows Forms), naviguer vers les URL"
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: naviguer vers une URL avec un contr&#244;le WebBrowser
L'exemple de code suivant montre comment naviguer dans le contrôle <xref:System.Windows.Forms.WebBrowser> jusqu'à une URL spécifique.  
  
 Pour déterminer le moment où le nouveau document est totalement chargé, gérez l'événement <xref:System.Windows.Forms.WebBrowser.DocumentCompleted>.  Pour une démonstration de cet événement, consultez [Comment : imprimer avec un contrôle WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md).  
  
## Exemple  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.WebBrowser> nommé `webBrowser1` ;  
  
-   Références aux assemblys `System` et `System.Windows.Forms`.  
  
## Voir aussi  
 <xref:System.Windows.Forms.WebBrowser>   
 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=fullName>   
 <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=fullName>   
 <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=fullName>   
 [WebBrowser, contrôle](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)   
 [Comment : imprimer avec un contrôle WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)