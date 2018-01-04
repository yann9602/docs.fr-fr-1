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
ms.workload: dotnet
ms.openlocfilehash: 1f36ee150e4dcca74141b644a55451abd4a4fd21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="more-secure-printing-in-windows-forms"></a><span data-ttu-id="505ce-102">Impression plus sécurisée dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="505ce-102">More Secure Printing in Windows Forms</span></span>
<span data-ttu-id="505ce-103">Les applications Windows Forms incluent souvent des fonctionnalités d’impression.</span><span class="sxs-lookup"><span data-stu-id="505ce-103">Windows Forms applications frequently include printing abilities.</span></span> <span data-ttu-id="505ce-104">Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] utilise le <xref:System.Drawing.Printing.PrintingPermission> classe pour contrôler l’accès aux fonctionnalités d’impression et associé <xref:System.Drawing.Printing.PrintingPermissionLevel> valeur d’énumération pour indiquer le niveau d’accès.</span><span class="sxs-lookup"><span data-stu-id="505ce-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uses the <xref:System.Drawing.Printing.PrintingPermission> class to control access to printing capabilities and the associated <xref:System.Drawing.Printing.PrintingPermissionLevel> enumeration value to indicate the level of access.</span></span> <span data-ttu-id="505ce-105">Par défaut, l’impression est activée par défaut dans les zones Intranet Local et Internet ; Toutefois, le niveau d’accès est limité dans les deux zones.</span><span class="sxs-lookup"><span data-stu-id="505ce-105">By default, printing is enabled by default in the Local Intranet and Internet zones; however, the level of access is restricted in both zones.</span></span> <span data-ttu-id="505ce-106">Si votre application peut imprimer, nécessite une interaction utilisateur, ou ne peut pas imprimer dépend de la valeur de l’autorisation accordée à l’application.</span><span class="sxs-lookup"><span data-stu-id="505ce-106">Whether your application can print, requires user interaction, or cannot print depends upon the permission value granted to the application.</span></span> <span data-ttu-id="505ce-107">Par défaut, la zone Intranet Local reçoit <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> accès et la zone Intranet reçoit <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> accès.</span><span class="sxs-lookup"><span data-stu-id="505ce-107">By default, the Local Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> access and the Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> access.</span></span>  
  
 <span data-ttu-id="505ce-108">Le tableau suivant présente les fonctionnalités disponibles à chaque niveau d’autorisation d’impression.</span><span class="sxs-lookup"><span data-stu-id="505ce-108">The following table shows the functionality available at each printing permission level.</span></span>  
  
|<span data-ttu-id="505ce-109">PrintingPermissionLevel</span><span class="sxs-lookup"><span data-stu-id="505ce-109">PrintingPermissionLevel</span></span>|<span data-ttu-id="505ce-110">Description</span><span class="sxs-lookup"><span data-stu-id="505ce-110">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|<span data-ttu-id="505ce-111">Fournit un accès complet à toutes les imprimantes installées.</span><span class="sxs-lookup"><span data-stu-id="505ce-111">Provides full access to all installed printers.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|<span data-ttu-id="505ce-112">Permet l’impression par programmation à l’imprimante par défaut et l’impression plus sécurisée via une boîte de dialogue d’impression restrictive.</span><span class="sxs-lookup"><span data-stu-id="505ce-112">Enables programmatic printing to the default printer and safer printing through a restrictive printing dialog box.</span></span> <span data-ttu-id="505ce-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> est un sous-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span><span class="sxs-lookup"><span data-stu-id="505ce-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|<span data-ttu-id="505ce-114">Fournit une impression uniquement à partir d’une boîte de dialogue plus restrictive.</span><span class="sxs-lookup"><span data-stu-id="505ce-114">Provides printing only from a more-restricted dialog box.</span></span> <span data-ttu-id="505ce-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> est un sous-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span><span class="sxs-lookup"><span data-stu-id="505ce-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|<span data-ttu-id="505ce-116">Empêche l’accès à des imprimantes.</span><span class="sxs-lookup"><span data-stu-id="505ce-116">Prevents access to printers.</span></span> <span data-ttu-id="505ce-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> est un sous-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span><span class="sxs-lookup"><span data-stu-id="505ce-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="505ce-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="505ce-118">See Also</span></span>  
 [<span data-ttu-id="505ce-119">Accès plus sécurisé aux fichiers et aux données dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="505ce-119">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [<span data-ttu-id="505ce-120">Considérations supplémentaires sur la sécurité des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="505ce-120">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [<span data-ttu-id="505ce-121">Vue d’ensemble de la sécurité dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="505ce-121">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [<span data-ttu-id="505ce-122">Sécurité de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="505ce-122">Windows Forms Security</span></span>](../../../docs/framework/winforms/windows-forms-security.md)
