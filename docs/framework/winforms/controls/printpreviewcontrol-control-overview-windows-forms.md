---
title: "Vue d'ensemble du contrôle PrintPreviewControl (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47bef441b01d8bdcf9a365c341005cff28c64f27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a><span data-ttu-id="7a6e3-102">Vue d'ensemble du contrôle PrintPreviewControl (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7a6e3-102">PrintPreviewControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="7a6e3-103">Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> est utilisé pour afficher un [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) tel qu’il apparaîtra une fois imprimé.</span><span class="sxs-lookup"><span data-stu-id="7a6e3-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> is used to display a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) as it will appear when printed.</span></span> <span data-ttu-id="7a6e3-104">Ce contrôle n'ayant aucun bouton ni élément d'interface utilisateur, vous utilisez généralement <xref:System.Windows.Forms.PrintPreviewControl> uniquement si vous souhaitez écrire votre propre interface utilisateur d'aperçu avant impression.</span><span class="sxs-lookup"><span data-stu-id="7a6e3-104">This control has no buttons or other user interface elements, so typically you use the <xref:System.Windows.Forms.PrintPreviewControl> only if you wish to write your own print-preview user interface.</span></span> <span data-ttu-id="7a6e3-105">Si vous souhaitez que l’interface utilisateur standard, utilisez un <xref:System.Windows.Forms.PrintPreviewDialog> contrôle ; consultez [vue d’ensemble du contrôle PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) pour une vue d’ensemble.</span><span class="sxs-lookup"><span data-stu-id="7a6e3-105">If you want the standard user interface, use a <xref:System.Windows.Forms.PrintPreviewDialog> control; see [PrintPreviewDialog Control Overview](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) for an overview.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="7a6e3-106">Propriétés de clé</span><span class="sxs-lookup"><span data-stu-id="7a6e3-106">Key Properties</span></span>  
 <span data-ttu-id="7a6e3-107">Propriété de clé du contrôle <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, qui définit le document à afficher.</span><span class="sxs-lookup"><span data-stu-id="7a6e3-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="7a6e3-108">Le document doit être un <xref:System.Drawing.Printing.PrintDocument> objet.</span><span class="sxs-lookup"><span data-stu-id="7a6e3-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="7a6e3-109">Pour une vue d’ensemble de la création de documents pour l’impression, consultez [vue d’ensemble du composant PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) et [prise en charge de Windows Forms impression](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md).</span><span class="sxs-lookup"><span data-stu-id="7a6e3-109">For an overview of creating documents for printing, see [PrintDocument Component Overview](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) and [Windows Forms Print Support](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md).</span></span> <span data-ttu-id="7a6e3-110">Le <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> et <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> propriétés déterminent le nombre de pages affichées horizontalement et verticalement sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="7a6e3-110">The <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="7a6e3-111">L’anticrénelage peut lisser le texte, mais il peut également apporter de ralentir l’affichage ; pour l’utiliser, définissez la <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="7a6e3-111">Antialiasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a6e3-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a6e3-112">See Also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [<span data-ttu-id="7a6e3-113">Vue d’ensemble du contrôle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="7a6e3-113">PrintPreviewDialog Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [<span data-ttu-id="7a6e3-114">PrintPreviewControl, contrôle</span><span class="sxs-lookup"><span data-stu-id="7a6e3-114">PrintPreviewControl Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [<span data-ttu-id="7a6e3-115">Contrôles et composants de boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="7a6e3-115">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
