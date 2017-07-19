---
title: "M&#233;thodes de s&#233;lection du contr&#244;le Button Windows Forms | Microsoft Docs"
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
  - "bouton (contrôle Windows Forms), sélectionner"
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# M&#233;thodes de s&#233;lection du contr&#244;le Button Windows Forms
Pour sélectionner le contrôle Button de Windows Forms, les méthodes suivantes sont à votre disposition :  
  
-   Cliquez sur le bouton à l'aide de la souris.  
  
-   Appelez l'événement <xref:System.Windows.Forms.Control.Click> du bouton dans le code.  
  
-   Déplacez le focus sur le bouton en appuyant sur la touche TAB, puis sélectionnez le bouton en appuyant sur la touche ESPACE ou ENTRÉE.  
  
-   Appuyez sur la touche d'accès rapide \(ALT \+ la lettre soulignée\) du bouton.  Pour plus d'informations sur les touches d'accès rapide, consultez [Comment : créer des touches d'accès rapide pour des contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).  
  
-   S'il s'agit du bouton « Accepter » du formulaire, il est sélectionné lorsque vous appuyez sur la touche ENTRÉE, et cela même si un autre contrôle a le focus, sauf si ce contrôle est un autre bouton, une zone de texte multiligne ou un contrôle personnalisé qui intercepte la touche ENTRÉE.  
  
-   S'il s'agit du bouton « annuler » du formulaire, vous pouvez le sélectionner en appuyant sur la touche ÉCHAP, et cela même si un autre contrôle a le focus.  
  
-   Appelez la méthode <xref:System.Windows.Forms.Button.PerformClick%2A> pour sélectionner le bouton par programme.  
  
## Voir aussi  
 [Vue d'ensemble du contrôle Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [Comment : répondre à un clic du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [Button, contrôle](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)