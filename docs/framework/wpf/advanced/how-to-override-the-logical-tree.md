---
title: "Guide pratique pour remplacer l’arborescence logique"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e487220f8b06515f3d37f7d55ab7ff6214c85d92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-override-the-logical-tree"></a><span data-ttu-id="668aa-102">Guide pratique pour remplacer l’arborescence logique</span><span class="sxs-lookup"><span data-stu-id="668aa-102">How to: Override the Logical Tree</span></span>
<span data-ttu-id="668aa-103">Bien que cela ne soit pas nécessaire dans la plupart des cas, les auteurs de contrôles avancés ont la possibilité de remplacer l’arborescence logique.</span><span class="sxs-lookup"><span data-stu-id="668aa-103">Although it is not necessary in most cases, advanced control authors have the option to override the logical tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="668aa-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="668aa-104">Example</span></span>  
 <span data-ttu-id="668aa-105">Cet exemple décrit comment créer une sous-classe <xref:System.Windows.Controls.StackPanel> pour remplacer l’arborescence logique, dans ce cas pour appliquer un comportement que le panneau de configuration peut avoir uniquement et effectue le rendu uniquement un seul élément enfant.</span><span class="sxs-lookup"><span data-stu-id="668aa-105">This example describes how to subclass <xref:System.Windows.Controls.StackPanel> to override the logical tree, in this case to enforce a behavior that the panel may only have and will only render a single child element.</span></span> <span data-ttu-id="668aa-106">Ce n’est pas nécessairement un comportement souhaitable, mais il est indiqué ici afin d’illustrer le scénario permettant de remplacer l’arborescence logique normale d’un élément.</span><span class="sxs-lookup"><span data-stu-id="668aa-106">This isn't necessarily a practically desirable behavior, but is shown here as a means of illustrating the scenario for overriding an element's normal logical tree.</span></span>  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 <span data-ttu-id="668aa-107">Pour plus d’informations sur l’arborescence logique, consultez [Arborescences dans WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="668aa-107">For more information on the logical tree, see [Trees in WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span></span>
