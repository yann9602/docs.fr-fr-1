---
title: "Guide pratique pour configurer un domaine d’application"
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
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1024d41d99b9752fbbf8ef9458a8396d91c68fd0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="db3f2-102">Guide pratique pour configurer un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="db3f2-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="db3f2-103">Vous pouvez fournir au Common Language Runtime des informations de configuration pour un nouveau domaine d’application à l’aide de la classe <xref:System.AppDomainSetup>.</span><span class="sxs-lookup"><span data-stu-id="db3f2-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="db3f2-104">Quand vous créez vos propres domaines d’application, la propriété la plus importante est <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="db3f2-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="db3f2-105">Les autres propriétés **AppDomainSetup** sont utilisées principalement par les hôtes du runtime pour configurer un domaine d’application particulier.</span><span class="sxs-lookup"><span data-stu-id="db3f2-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="db3f2-106">La propriété **ApplicationBase** définit le répertoire racine de l’application.</span><span class="sxs-lookup"><span data-stu-id="db3f2-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="db3f2-107">Quand le runtime a besoin de satisfaire une demande de type, il interroge l’assembly contenant le type dans le répertoire spécifié par la propriété **ApplicationBase**.</span><span class="sxs-lookup"><span data-stu-id="db3f2-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db3f2-108">Un nouveau domaine d’application hérite uniquement de la propriété **ApplicationBase** du créateur.</span><span class="sxs-lookup"><span data-stu-id="db3f2-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="db3f2-109">L’exemple suivant crée une instance de la classe **AppDomainSetup**, utilise cette classe pour créer un domaine d’application, écrit les informations dans la console, puis décharge le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="db3f2-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db3f2-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="db3f2-110">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="db3f2-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db3f2-111">See Also</span></span>  
 [<span data-ttu-id="db3f2-112">Programmation avec des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="db3f2-112">Programming with Application Domains</span></span>](http://msdn.microsoft.com/library/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="db3f2-113">Utilisation des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="db3f2-113">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
