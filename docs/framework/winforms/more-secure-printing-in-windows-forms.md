---
title: "Impression plus sécurisée dans les Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b89a94fd0223d817b0dee37f7a3ed84dcbacbbec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="more-secure-printing-in-windows-forms"></a>Impression plus sécurisée dans les Windows Forms
Les applications Windows Forms incluent souvent des fonctionnalités d’impression. Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] utilise le <xref:System.Drawing.Printing.PrintingPermission> classe pour contrôler l’accès aux fonctionnalités d’impression et associé <xref:System.Drawing.Printing.PrintingPermissionLevel> valeur d’énumération pour indiquer le niveau d’accès. Par défaut, l’impression est activée par défaut dans les zones Intranet Local et Internet ; Toutefois, le niveau d’accès est limité dans les deux zones. Si votre application peut imprimer, nécessite une interaction utilisateur, ou ne peut pas imprimer dépend de la valeur de l’autorisation accordée à l’application. Par défaut, la zone Intranet Local reçoit <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> accès et la zone Intranet reçoit <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> accès.  
  
 Le tableau suivant présente les fonctionnalités disponibles à chaque niveau d’autorisation d’impression.  
  
|PrintingPermissionLevel|Description|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|Fournit un accès complet à toutes les imprimantes installées.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|Permet l’impression par programmation à l’imprimante par défaut et l’impression plus sécurisée via une boîte de dialogue d’impression restrictive. <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> est un sous-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|Fournit une impression uniquement à partir d’une boîte de dialogue plus restrictive. <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> est un sous-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|Empêche l’accès à des imprimantes. <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> est un sous-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [Considérations supplémentaires sur la sécurité des Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [Vue d’ensemble de la sécurité dans les Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Sécurité de Windows Forms](../../../docs/framework/winforms/windows-forms-security.md)
