---
title: "Guide pratique pour refuser la mise à niveau automatique de la boîte de dialogue Fichier"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01be9e29c00f39125c8ee645242e986fac178ba2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="f06b0-102">Guide pratique pour refuser la mise à niveau automatique de la boîte de dialogue Fichier</span><span class="sxs-lookup"><span data-stu-id="f06b0-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="f06b0-103">Lorsque le <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> classes sont utilisées dans une application, leur apparence et leur comportement dépendent de la version de Windows, l’application est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f06b0-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="f06b0-104">Lorsqu’une application qui a été créée sur le [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] ou antérieure est affichée sur [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> sont affichés automatiquement avec le [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] apparence et le comportement.</span><span class="sxs-lookup"><span data-stu-id="f06b0-104">When an application that was created on the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] or earlier is displayed on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] appearance and behavior.</span></span> <span data-ttu-id="f06b0-105">À compter de la [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], vous pouvez refuser la mise à niveau automatique pour afficher le <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> avec un [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-apparence et le comportement.</span><span class="sxs-lookup"><span data-stu-id="f06b0-105">Starting in the [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="f06b0-106">Pour refuser la mise à niveau automatique de la boîte de dialogue Fichier</span><span class="sxs-lookup"><span data-stu-id="f06b0-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1.  <span data-ttu-id="f06b0-107">Définir le <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriété du <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog> à `false` avant d’afficher la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f06b0-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f06b0-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f06b0-108">See Also</span></span>  
 <xref:System.Windows.Forms.FileDialog>
