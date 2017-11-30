---
title: "Guide pratique pour obtenir des informations relatives au type et aux membres à partir d'un assembly"
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
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9542fc8db84832437fb0d3b8e517ad4c7e01ca0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="02303-102">Guide pratique pour obtenir des informations relatives au type et aux membres à partir d'un assembly</span><span class="sxs-lookup"><span data-stu-id="02303-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="02303-103">L’espace de noms <xref:System.Reflection> contient de nombreuses méthodes pour obtenir des informations à partir d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="02303-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="02303-104">Cette section illustre l’une de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="02303-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="02303-105">Pour plus d’informations, consultez [Vue d’ensemble de la réflexion](../../../docs/framework/reflection-and-codedom/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="02303-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="02303-106">L’exemple suivant obtient des informations relatives au type et aux membres d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="02303-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02303-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="02303-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="02303-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02303-108">See Also</span></span>  
 [<span data-ttu-id="02303-109">Programmation avec des domaines d’Application</span><span class="sxs-lookup"><span data-stu-id="02303-109">Programming with Application Domains</span></span>](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="02303-110">Réflexion</span><span class="sxs-lookup"><span data-stu-id="02303-110">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [<span data-ttu-id="02303-111">Utilisation des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="02303-111">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
