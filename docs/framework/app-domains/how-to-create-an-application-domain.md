---
title: "Comment : créer un domaine d'application"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 39d8db32f82827e76d9517d387e2fc001fc209aa
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="fc33c-102">Comment : créer un domaine d'application</span><span class="sxs-lookup"><span data-stu-id="fc33c-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="fc33c-103">Un hôte Common Language Runtime crée automatiquement des domaines d’application quand ils sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="fc33c-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="fc33c-104">Toutefois, vous pouvez créer vos propres domaines d’application et y charger les assemblys que vous souhaitez gérer personnellement.</span><span class="sxs-lookup"><span data-stu-id="fc33c-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="fc33c-105">Vous pouvez également créer des domaines d’application à partir desquels vous exécutez du code.</span><span class="sxs-lookup"><span data-stu-id="fc33c-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="fc33c-106">Vous pouvez créer un domaine d’application à l’aide de l’une des méthodes **CreateDomain** surchargées dans la classe <xref:System.AppDomain?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="fc33c-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=fullName> class.</span></span> <span data-ttu-id="fc33c-107">Vous pouvez nommer le domaine d’application et le référencer par ce nom.</span><span class="sxs-lookup"><span data-stu-id="fc33c-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="fc33c-108">L’exemple suivant crée un domaine d’application et lui attribue le nom `MyDomain`, puis imprime le nom du domaine hôte et du domaine d’application enfant créé dans la console.</span><span class="sxs-lookup"><span data-stu-id="fc33c-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc33c-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="fc33c-109">Example</span></span>  
 <span data-ttu-id="fc33c-110">[!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)] [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)] [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="fc33c-110">[!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)] [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)] [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc33c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc33c-111">See Also</span></span>  
 <span data-ttu-id="fc33c-112">[Programmation avec des domaines d’application](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span><span class="sxs-lookup"><span data-stu-id="fc33c-112">[Programming with Application Domains](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span></span>  
 [<span data-ttu-id="fc33c-113">Utilisation des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="fc33c-113">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

