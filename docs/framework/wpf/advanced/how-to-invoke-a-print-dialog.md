---
title: "Comment : appeler une boîte de dialogue Imprimer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ba541b367e56a809fa444528dccd69860c4de46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="755c7-102">Comment : appeler une boîte de dialogue Imprimer</span><span class="sxs-lookup"><span data-stu-id="755c7-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="755c7-103">Pour fournir la possibilité d’imprimer depuis votre application, vous pouvez simplement créer et ouvrir un <xref:System.Windows.Controls.PrintDialog> objet.</span><span class="sxs-lookup"><span data-stu-id="755c7-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="755c7-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="755c7-104">Example</span></span>  
 <span data-ttu-id="755c7-105">Le contrôle <xref:System.Windows.Controls.PrintDialog> offre un point d'entrée unique pour l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], la configuration et la soumission de travaux [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)].</span><span class="sxs-lookup"><span data-stu-id="755c7-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] job submission.</span></span> <span data-ttu-id="755c7-106">Le contrôle est facile à utiliser et peut être instancié à l’aide de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] balisage ou code.</span><span class="sxs-lookup"><span data-stu-id="755c7-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="755c7-107">L’exemple suivant montre comment instancier et ouvrir le contrôle dans le code et l’impression à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="755c7-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="755c7-108">Il montre également comment s’assurer que la boîte de dialogue donner à l’utilisateur la possibilité de définir une plage de pages spécifique.</span><span class="sxs-lookup"><span data-stu-id="755c7-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="755c7-109">L’exemple de code suppose qu’il existe un fichier FixedDocumentSequence.xps à la racine du lecteur C:.</span><span class="sxs-lookup"><span data-stu-id="755c7-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="755c7-110">Une fois que la boîte de dialogue est ouverte, les utilisateurs pourront sélectionner dans les imprimantes installées sur leur ordinateur.</span><span class="sxs-lookup"><span data-stu-id="755c7-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="755c7-111">Ils aura également la possibilité de sélectionner le [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319) pour créer un [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] fichier au lieu de l’impression.</span><span class="sxs-lookup"><span data-stu-id="755c7-111">They will also have the option of selecting the [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319) to create an [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] file instead of printing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="755c7-112">Le <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> contrôle de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], qui est décrite dans cette rubrique, ne doit pas être confondu avec le <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> composant de [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="755c7-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].</span></span>  
  
 <span data-ttu-id="755c7-113">En principe, vous pouvez utiliser la <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> méthode sans jamais ouvrir la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="755c7-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="755c7-114">Dans ce sens, le contrôle peut être utilisé comme un composant d’impression inaperçu.</span><span class="sxs-lookup"><span data-stu-id="755c7-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="755c7-115">Mais pour des raisons de performances, il serait préférable d’utiliser le <xref:System.Printing.PrintQueue.AddJob%2A> méthode ou l’une des nombreuses <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> et <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> méthodes de la <xref:System.Windows.Xps.XpsDocumentWriter>.</span><span class="sxs-lookup"><span data-stu-id="755c7-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="755c7-116">Pour plus d’informations, consultez [par programme les fichiers impression XPS](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) et.</span><span class="sxs-lookup"><span data-stu-id="755c7-116">For more about this, see [Programmatically Print XPS Files](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="755c7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="755c7-117">See Also</span></span>  
 <xref:System.Windows.Controls.PrintDialog>  
 [<span data-ttu-id="755c7-118">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="755c7-118">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="755c7-119">Vue d’ensemble de l’impression</span><span class="sxs-lookup"><span data-stu-id="755c7-119">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="755c7-120">Microsoft XPS Document Writer</span><span class="sxs-lookup"><span data-stu-id="755c7-120">Microsoft XPS Document Writer</span></span>](http://go.microsoft.com/fwlink/?LinkId=147319)
