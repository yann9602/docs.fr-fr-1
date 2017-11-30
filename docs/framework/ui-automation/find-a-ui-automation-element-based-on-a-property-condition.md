---
title: "Rechercher un élément UI Automation basé sur une condition de propriété"
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
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cafd84ce3acea80905d686f33f23338e3581a9c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="ff953-102">Rechercher un élément UI Automation basé sur une condition de propriété</span><span class="sxs-lookup"><span data-stu-id="ff953-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
>  <span data-ttu-id="ff953-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="ff953-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ff953-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="ff953-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ff953-105">Cette rubrique contient des exemples de code qui montre comment rechercher un élément dans le [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] arborescence basée sur une ou plusieurs propriétés spécifiques.</span><span class="sxs-lookup"><span data-stu-id="ff953-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff953-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="ff953-106">Example</span></span>  
 <span data-ttu-id="ff953-107">Dans l’exemple suivant, un ensemble de conditions de propriété sont spécifiés qui identifient un élément particulier (ou des éléments) d’intérêt dans le <xref:System.Windows.Automation.AutomationElement> arborescence.</span><span class="sxs-lookup"><span data-stu-id="ff953-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="ff953-108">Une recherche de tous les éléments correspondants est ensuite exécutée avec la <xref:System.Windows.Automation.AutomationElement.FindAll%2A> méthode qui incorpore une série de <xref:System.Windows.Automation.AndCondition> opérations booléennes pour limiter le nombre d’éléments correspondants.</span><span class="sxs-lookup"><span data-stu-id="ff953-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff953-109">Lors de la recherche à partir de la <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, vous devez tenter d’obtenir uniquement les enfants directs.</span><span class="sxs-lookup"><span data-stu-id="ff953-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="ff953-110">Une recherche des descendants peut itérer au sein de centaines ou milliers d’éléments, ce qui peut provoquer un débordement de pile.</span><span class="sxs-lookup"><span data-stu-id="ff953-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="ff953-111">Si vous tentez d’obtenir un élément spécifique de niveau inférieur, vous devez commencer votre recherche à partir de la fenêtre d’application ou d’un conteneur de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="ff953-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="ff953-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff953-112">See Also</span></span>  
 [<span data-ttu-id="ff953-113">InvokePattern et ExpandCollapsePattern Menu exemple d’élément</span><span class="sxs-lookup"><span data-stu-id="ff953-113">InvokePattern and ExpandCollapsePattern Menu Item Sample</span></span>](http://msdn.microsoft.com/en-us/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [<span data-ttu-id="ff953-114">Obtention d’éléments UI Automation</span><span class="sxs-lookup"><span data-stu-id="ff953-114">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [<span data-ttu-id="ff953-115">Utilisez la propriété AutomationID</span><span class="sxs-lookup"><span data-stu-id="ff953-115">Use the AutomationID Property</span></span>](../../../docs/framework/ui-automation/use-the-automationid-property.md)
