---
title: "Obtenir des modèles de contrôle UI Automation pris en charge"
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
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
caps.latest.revision: "10"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 8917890d86f059d85ad9b6a0bcf6d9a41d65585a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="e5fb7-102">Obtenir des modèles de contrôle UI Automation pris en charge</span><span class="sxs-lookup"><span data-stu-id="e5fb7-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
>  <span data-ttu-id="e5fb7-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="e5fb7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e5fb7-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="e5fb7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e5fb7-105">Cette rubrique montre comment récupérer des objets de modèle de contrôle à partir de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] éléments.</span><span class="sxs-lookup"><span data-stu-id="e5fb7-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="e5fb7-106">Obtenir tous les modèles de contrôle</span><span class="sxs-lookup"><span data-stu-id="e5fb7-106">Obtain All Control Patterns</span></span>  
  
1.  <span data-ttu-id="e5fb7-107">Obtenir le <xref:System.Windows.Automation.AutomationElement> les modèles dont le contrôle vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="e5fb7-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2.  <span data-ttu-id="e5fb7-108">Appelez <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> pour obtenir tous les modèles de contrôle de l’élément.</span><span class="sxs-lookup"><span data-stu-id="e5fb7-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e5fb7-109">Il est fortement recommandé qu’un client n’utilise pas <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5fb7-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="e5fb7-110">Performances peuvent être gravement affectées, car cette méthode appelle <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> en interne pour chaque modèle de contrôle existant.</span><span class="sxs-lookup"><span data-stu-id="e5fb7-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="e5fb7-111">Si possible, un client doit appeler <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> pour les modèles les plus intéressants.</span><span class="sxs-lookup"><span data-stu-id="e5fb7-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="e5fb7-112">Obtenir un modèle de contrôle spécifique</span><span class="sxs-lookup"><span data-stu-id="e5fb7-112">Obtain a Specific Control Pattern</span></span>  
  
1.  <span data-ttu-id="e5fb7-113">Obtenir le <xref:System.Windows.Automation.AutomationElement> les modèles dont le contrôle vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="e5fb7-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2.  <span data-ttu-id="e5fb7-114">Appelez <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> pour rechercher un modèle spécifique.</span><span class="sxs-lookup"><span data-stu-id="e5fb7-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="e5fb7-115">Ces méthodes sont similaires, mais si le modèle est introuvable, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lève une exception, et <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="e5fb7-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5fb7-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="e5fb7-116">Example</span></span>  
 <span data-ttu-id="e5fb7-117">L’exemple suivant récupère une <xref:System.Windows.Automation.AutomationElement> pour un élément de liste et obtient un <xref:System.Windows.Automation.SelectionItemPattern> à partir de cet élément.</span><span class="sxs-lookup"><span data-stu-id="e5fb7-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="e5fb7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5fb7-118">See Also</span></span>  
 [<span data-ttu-id="e5fb7-119">Modèles de contrôle UI Automation pour les Clients</span><span class="sxs-lookup"><span data-stu-id="e5fb7-119">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
