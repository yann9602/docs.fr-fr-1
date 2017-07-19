---
title: "Gestion de l&#39;alimentation dans Windows&#160;Forms | Microsoft Docs"
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
  - "états de la batterie"
  - "états de l'alimentation"
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Gestion de l&#39;alimentation dans Windows&#160;Forms
Vos applications Windows Forms peuvent bénéficier des fonctionnalités de gestion de l'alimentation du système d'exploitation Windows.  Vos applications peuvent surveiller l'état de l'alimentation d'un ordinateur et agir lorsqu'une modification de l'état se produit.  Par exemple, si votre application s'exécute sur un ordinateur portable, certaines fonctionnalités dans votre application devront peut\-être être désactivées lorsque la charge de la batterie de l'ordinateur descend en\-dessous d'un certain niveau.  
  
 Le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fournit un événement <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> qui se produit chaque fois que l'état de l'alimentation change, par exemple, lorsqu'un utilisateur interrompt ou redémarre le système d'exploitation ou lorsque l'état de l'alimentation secteur ou de la batterie change.  La propriété <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> de la classe <xref:System.Windows.Forms.SystemInformation> peut être utilisée pour demander l'état actuel, comme indiqué dans l'exemple de code suivant.  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 En plus des énumérations <xref:System.Windows.Forms.BatteryChargeStatus>, la propriété <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> contient également des énumérations permettant de déterminer la capacité de la batterie \(<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>\) ainsi que le pourcentage de charge de la batterie \(<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>\).  
  
 Vous pouvez utiliser la méthode <xref:System.Windows.Forms.Application.SetSuspendState%2A> du <xref:System.Windows.Forms.Application> pour mettre un ordinateur en veille prolongée ou en mode veille.  Si l'argument `force` a la valeur `false`, le système d'exploitation diffuse un événement à toutes les applications demandant l'autorisation de mettre en veille.  Si l'argument `disableWakeEvent` a la valeur `true`, le système d'exploitation désactive tous les événements de mise en éveil.  
  
 L'exemple de code suivant montre comment mettre un ordinateur en veille prolongée.  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## Voir aussi  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>   
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>   
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>   
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>