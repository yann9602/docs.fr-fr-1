---
title: "Impression plus s&#233;curis&#233;e dans les Windows Forms | Microsoft Docs"
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
  - "imprimer (Windows Forms), sécurité"
  - "PrintingPermission (classe), sécurité Windows Forms"
  - "sécurité (Windows Forms), imprimer"
  - "Windows Forms, imprimer"
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Impression plus s&#233;curis&#233;e dans les Windows Forms
Les applications Windows Forms incluent souvent des fonctionnalités d'impression.  Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] utilise la classe <xref:System.Drawing.Printing.PrintingPermission> pour contrôler l'accès aux fonctions d'impression et à la valeur de l'énumération <xref:System.Drawing.Printing.PrintingPermissionLevel> associée pour indiquer le niveau d'accès.  L'impression est autorisée par défaut dans les zones Intranet local et Internet ; le niveau d'accès est toutefois restreint dans les deux zones.  Le fait que votre application puisse ou non imprimer, ou nécessite une interaction avec l'utilisateur, dépend de la valeur d'autorisation qui lui a été accordée.  Par défaut, un accès <xref:System.Drawing.Printing.PrintingPermissionLevel> est accordé à la zone Intranet local et un accès <xref:System.Drawing.Printing.PrintingPermissionLevel> est accordé à la zone Intranet.  
  
 Le tableau suivant répertorie les fonctionnalités disponibles à chaque niveau d'autorisation d'impression.  
  
|PrintingPermissionLevel|Description|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel>|Autorise un accès total à toutes les imprimantes installées.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel>|Permet l'impression par programmation sur l'imprimante par défaut et une impression plus sécurisée grâce à la boîte de dialogue d'impression restrictive.  <xref:System.Drawing.Printing.PrintingPermissionLevel> est un sous\-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel>|Fournit une impression uniquement à partir d'une boîte de dialogue à accès plus restreint.  <xref:System.Drawing.Printing.PrintingPermissionLevel> est un sous\-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel>|Interdit l'accès aux imprimantes.  <xref:System.Drawing.Printing.PrintingPermissionLevel> est un sous\-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel>.|  
  
## Voir aussi  
 [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)   
 [Considérations supplémentaires sur la sécurité des Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)   
 [Vue d'ensemble de la sécurité dans les Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)   
 [Sécurité des Windows Forms](../../../docs/framework/winforms/windows-forms-security.md)