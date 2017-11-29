---
title: "Obtenir des attributs de texte à l'aide d'UI Automation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
caps.latest.revision: "13"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c95fbbe2917261e6b8a4a911a7ea5978da00d662
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="obtain-text-attributes-using-ui-automation"></a><span data-ttu-id="08492-102">Obtenir des attributs de texte à l'aide d'UI Automation</span><span class="sxs-lookup"><span data-stu-id="08492-102">Obtain Text Attributes Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="08492-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="08492-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="08492-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="08492-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="08492-105">Cette rubrique montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour obtenir des attributs de texte d’une plage de texte.</span><span class="sxs-lookup"><span data-stu-id="08492-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attributes from a text range.</span></span> <span data-ttu-id="08492-106">Une plage de texte peut correspondre à l’emplacement actuel du signe insertion (ou de la sélection dégénérée) dans un document, une sélection contiguë de texte, une collection de sélections disjointes de texte ou l’ensemble du contenu textuel d’un document.</span><span class="sxs-lookup"><span data-stu-id="08492-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08492-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="08492-107">Example</span></span>  
 <span data-ttu-id="08492-108">L’exemple de code suivant montre comment obtenir le <xref:System.Windows.Automation.TextPattern.FontNameAttribute> d’une plage de texte.</span><span class="sxs-lookup"><span data-stu-id="08492-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <span data-ttu-id="08492-109">Le modèle de contrôle <xref:System.Windows.Automation.TextPattern> , associé à la classe <xref:System.Windows.Automation.Text.TextPatternRange> , prend en charge les attributs de texte, les propriétés et les méthodes de base.</span><span class="sxs-lookup"><span data-stu-id="08492-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="08492-110">Pour les fonctionnalités spécifiques au contrôle qui ne sont pas prises en charge par <xref:System.Windows.Automation.TextPattern> ou <xref:System.Windows.Automation.Text.TextPatternRange> , la classe <xref:System.Windows.Automation.AutomationElement>fournit des méthodes permettant à un client UI Automation d’accéder au modèle objet natif correspondant.</span><span class="sxs-lookup"><span data-stu-id="08492-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange> the <xref:System.Windows.Automation.AutomationElement>, class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08492-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08492-111">See Also</span></span>  
 [<span data-ttu-id="08492-112">Vue d’ensemble de TextPattern UI Automation</span><span class="sxs-lookup"><span data-stu-id="08492-112">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="08492-113">Ajouter du contenu à une zone de texte à l’aide d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="08492-113">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="08492-114">Rechercher et mettre en surbrillance le texte à l’aide d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="08492-114">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [<span data-ttu-id="08492-115">Vue d’ensemble du modèles contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="08492-115">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="08492-116">Modèles de contrôle UI Automation pour les Clients</span><span class="sxs-lookup"><span data-stu-id="08492-116">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="08492-117">Obtenir des détails d’attribut de texte mixte à l’aide d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="08492-117">Obtain Mixed Text Attribute Details Using UI Automation</span></span>](../../../docs/framework/ui-automation/obtain-mixed-text-attribute-details-using-ui-automation.md)
