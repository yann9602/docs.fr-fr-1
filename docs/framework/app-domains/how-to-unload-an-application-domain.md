---
title: "Comment : décharger un domaine d'application"
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
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eefaf670202e6b4977d75fffa906f1b07053eb3e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="ea613-102">Comment : décharger un domaine d'application</span><span class="sxs-lookup"><span data-stu-id="ea613-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="ea613-103">Quand vous avez fini d’utiliser un domaine d’application, déchargez-le à l’aide de la méthode <xref:System.AppDomain.Unload%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ea613-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="ea613-104">La méthode **Unload** arrête de façon correcte le domaine d’application spécifié.</span><span class="sxs-lookup"><span data-stu-id="ea613-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="ea613-105">Au cours du processus de déchargement, aucun nouveau thread ne peut accéder au domaine d’application, et toutes les structures de données spécifiques au domaine d’application sont libérées.</span><span class="sxs-lookup"><span data-stu-id="ea613-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="ea613-106">Les assemblys chargés dans le domaine d’application sont supprimés et ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="ea613-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="ea613-107">Si un assembly dans le domaine d’application est indépendant du domaine, les données de l’assembly restent en mémoire jusqu’à ce que l’ensemble du processus soit arrêté.</span><span class="sxs-lookup"><span data-stu-id="ea613-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="ea613-108">Pour décharger un assembly indépendant du domaine, il n’existe pas d’autre mécanisme que l’arrêt de l’ensemble du processus.</span><span class="sxs-lookup"><span data-stu-id="ea613-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="ea613-109">Il existe des cas où la demande de déchargement d’un domaine d’application ne fonctionne pas et provoque une exception <xref:System.CannotUnloadAppDomainException>.</span><span class="sxs-lookup"><span data-stu-id="ea613-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="ea613-110">L’exemple suivant crée un nouveau domaine d’application appelé `MyDomain`, imprime certaines informations dans la console, puis décharge le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="ea613-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="ea613-111">Remarquez que le code tente ensuite d’imprimer le nom convivial du domaine d’application déchargé dans la console.</span><span class="sxs-lookup"><span data-stu-id="ea613-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="ea613-112">Cette action génère une exception qui est gérée par les instructions try/catch à la fin du programme.</span><span class="sxs-lookup"><span data-stu-id="ea613-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea613-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="ea613-113">Example</span></span>  
 <span data-ttu-id="ea613-114">[!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)] [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)] [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="ea613-114">[!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)] [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)] [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea613-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea613-115">See Also</span></span>  
 <span data-ttu-id="ea613-116">[Programmation avec des domaines d’application](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span><span class="sxs-lookup"><span data-stu-id="ea613-116">[Programming with Application Domains](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span></span>  
 <span data-ttu-id="ea613-117">[Guide pratique pour créer un domaine d’application](../../../docs/framework/app-domains/how-to-create-an-application-domain.md) </span><span class="sxs-lookup"><span data-stu-id="ea613-117">[How to: Create an Application Domain](../../../docs/framework/app-domains/how-to-create-an-application-domain.md) </span></span>  
 [<span data-ttu-id="ea613-118">Utilisation des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="ea613-118">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

