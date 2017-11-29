---
title: "Comment : naviguer vers une URL avec un contrôle WebBrowser"
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
f1_keywords: WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 28ceb5e465b8737d047c9c0e65bd9efc8cd3c8ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Comment : naviguer vers une URL avec un contrôle WebBrowser
L’exemple de code suivant montre comment parcourir le <xref:System.Windows.Forms.WebBrowser> contrôle vers une URL spécifique.  
  
 Pour déterminer quand le nouveau document est complètement chargé, gérez le <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> événement. Pour une démonstration de cet événement, consultez [Comment : imprimer avec un contrôle WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md).  
  
## <a name="example"></a>Exemple  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.WebBrowser> nommé `webBrowser1` ;  
  
-   des références aux assemblys `System` et `System.Windows.Forms`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>  
 [WebBrowser, contrôle](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
 [Guide pratique pour imprimer avec un contrôle WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
