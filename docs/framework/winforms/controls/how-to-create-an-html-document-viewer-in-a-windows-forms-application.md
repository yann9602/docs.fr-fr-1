---
title: "Comment&#160;: cr&#233;er une visionneuse de documents HTML dans une application Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "explorateurs de documents"
  - "WebBrowser (contrôle Windows Forms), créer un explorateur de document HTML"
  - "Windows Forms, créer des explorateurs de documents"
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: cr&#233;er une visionneuse de documents HTML dans une application Windows Forms
Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.WebBrowser> pour afficher et imprimer des documents HTML sans proposer les fonctionnalités complètes d'un navigateur Internet.  Cela est utile lorsque vous souhaitez tirer parti des fonctions de mise en forme du langage HTML, mais que vous ne souhaitez pas que vos utilisateurs chargent des pages Web arbitraires susceptibles de contenir des contrôles Web non fiables ou du code de script potentiellement nuisible.  Vous pouvez limiter les possibilités du contrôle <xref:System.Windows.Forms.WebBrowser> de cette manière, par exemple pour l'utiliser en tant que visionneuse de messagerie électronique HTML ou fournir une aide HTML dans votre application.  
  
### Pour créer une visionneuse de document HTML  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> la valeur `false` afin d'empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> d'ouvrir des fichiers qui sont déposés sur celui\-ci.  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.WebBrowser.Url%2A> l'emplacement du fichier initial à afficher.  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.WebBrowser> nommé `webBrowser1` ;  
  
-   Références aux assemblys `System` et `System.Windows.Forms`.  
  
## Voir aussi  
 <xref:System.Windows.Forms.WebBrowser>   
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>   
 <xref:System.Windows.Forms.WebBrowser.Url%2A>   
 [Vue d'ensemble du contrôle WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)   
 [Sécurité WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-security.md)   
 [Comment : naviguer vers une URL avec un contrôle WebBrowser](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)   
 [Comment : imprimer avec un contrôle WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)