---
title: "S&#233;curit&#233; WebBrowser | Microsoft Docs"
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
  - "sécurité (Windows Forms), WebBrowser (contrôle)"
  - "WebBrowser (contrôle Windows Forms), sécurité"
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# S&#233;curit&#233; WebBrowser
Le contrôle <xref:System.Windows.Forms.WebBrowser> est conçu pour fonctionner uniquement avec un niveau de confiance totale.  Le contenu HTML affiché dans le contrôle peut provenir de serveurs Web externes et peut contenir du code non managé sous la forme de scripts ou de contrôles Web.  Si vous utilisez le contrôle <xref:System.Windows.Forms.WebBrowser> dans cette situation, il n'est pas moins sécurisé qu'Internet Explorer ; par contre, le contrôle <xref:System.Windows.Forms.WebBrowser> managé n'empêche pas l'exécution du code non managé.  
  
 Pour plus d'informations sur les problèmes de sécurité relatifs au contrôle `WebBrowser` ActiveX sous\-jacent, consultez [Contrôle WebBrowser \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=198812).  
  
## Voir aussi  
 <xref:System.Windows.Forms.WebBrowser>   
 [Vue d'ensemble du contrôle WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)   
 [Contrôle WebBrowser \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=198812)