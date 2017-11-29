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
# <a name="more-secure-printing-in-windows-forms"></a><span data-ttu-id="66a27-102">Impression plus sécurisée dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66a27-102">More Secure Printing in Windows Forms</span></span>
<span data-ttu-id="66a27-103">Les applications Windows Forms incluent souvent des fonctionnalités d’impression.</span><span class="sxs-lookup"><span data-stu-id="66a27-103">Windows Forms applications frequently include printing abilities.</span></span> <span data-ttu-id="66a27-104">Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] utilise le <xref:System.Drawing.Printing.PrintingPermission> classe pour contrôler l’accès aux fonctionnalités d’impression et associé <xref:System.Drawing.Printing.PrintingPermissionLevel> valeur d’énumération pour indiquer le niveau d’accès.</span><span class="sxs-lookup"><span data-stu-id="66a27-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uses the <xref:System.Drawing.Printing.PrintingPermission> class to control access to printing capabilities and the associated <xref:System.Drawing.Printing.PrintingPermissionLevel> enumeration value to indicate the level of access.</span></span> <span data-ttu-id="66a27-105">Par défaut, l’impression est activée par défaut dans les zones Intranet Local et Internet ; Toutefois, le niveau d’accès est limité dans les deux zones.</span><span class="sxs-lookup"><span data-stu-id="66a27-105">By default, printing is enabled by default in the Local Intranet and Internet zones; however, the level of access is restricted in both zones.</span></span> <span data-ttu-id="66a27-106">Si votre application peut imprimer, nécessite une interaction utilisateur, ou ne peut pas imprimer dépend de la valeur de l’autorisation accordée à l’application.</span><span class="sxs-lookup"><span data-stu-id="66a27-106">Whether your application can print, requires user interaction, or cannot print depends upon the permission value granted to the application.</span></span> <span data-ttu-id="66a27-107">Par défaut, la zone Intranet Local reçoit <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> accès et la zone Intranet reçoit <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> accès.</span><span class="sxs-lookup"><span data-stu-id="66a27-107">By default, the Local Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> access and the Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> access.</span></span>  
  
 <span data-ttu-id="66a27-108">Le tableau suivant présente les fonctionnalités disponibles à chaque niveau d’autorisation d’impression.</span><span class="sxs-lookup"><span data-stu-id="66a27-108">The following table shows the functionality available at each printing permission level.</span></span>  
  
|<span data-ttu-id="66a27-109">PrintingPermissionLevel</span><span class="sxs-lookup"><span data-stu-id="66a27-109">PrintingPermissionLevel</span></span>|<span data-ttu-id="66a27-110">Description</span><span class="sxs-lookup"><span data-stu-id="66a27-110">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|<span data-ttu-id="66a27-111">Fournit un accès complet à toutes les imprimantes installées.</span><span class="sxs-lookup"><span data-stu-id="66a27-111">Provides full access to all installed printers.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|<span data-ttu-id="66a27-112">Permet l’impression par programmation à l’imprimante par défaut et l’impression plus sécurisée via une boîte de dialogue d’impression restrictive.</span><span class="sxs-lookup"><span data-stu-id="66a27-112">Enables programmatic printing to the default printer and safer printing through a restrictive printing dialog box.</span></span> <span data-ttu-id="66a27-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> est un sous-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span><span class="sxs-lookup"><span data-stu-id="66a27-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|<span data-ttu-id="66a27-114">Fournit une impression uniquement à partir d’une boîte de dialogue plus restrictive.</span><span class="sxs-lookup"><span data-stu-id="66a27-114">Provides printing only from a more-restricted dialog box.</span></span> <span data-ttu-id="66a27-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> est un sous-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span><span class="sxs-lookup"><span data-stu-id="66a27-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|<span data-ttu-id="66a27-116">Empêche l’accès à des imprimantes.</span><span class="sxs-lookup"><span data-stu-id="66a27-116">Prevents access to printers.</span></span> <span data-ttu-id="66a27-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> est un sous-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span><span class="sxs-lookup"><span data-stu-id="66a27-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66a27-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66a27-118">See Also</span></span>  
 [<span data-ttu-id="66a27-119">Accès plus sécurisé aux fichiers et aux données dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66a27-119">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [<span data-ttu-id="66a27-120">Considérations supplémentaires sur la sécurité des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66a27-120">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [<span data-ttu-id="66a27-121">Vue d’ensemble de la sécurité dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66a27-121">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [<span data-ttu-id="66a27-122">Sécurité de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66a27-122">Windows Forms Security</span></span>](../../../docs/framework/winforms/windows-forms-security.md)
