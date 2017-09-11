---
title: "Atténuation : Vérifications des signes deux-points dans les chemins d’accès"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8eb6864213aa4420f7a4373b9abbf173880f035f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="5536b-102">Atténuation : Vérifications des signes deux-points dans les chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="5536b-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="5536b-103">Plusieurs modifications ont été apportées pour prendre en charge les chemins d’accès non pris en charge précédemment (à la fois en termes de longueur et le format), à commencer par les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5536b-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="5536b-104">En particulier, les vérifications de bonne syntaxe de séparateur de lecteur (le signe deux-points) ont été rendues plus correctes.</span><span class="sxs-lookup"><span data-stu-id="5536b-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="5536b-105">Impact</span><span class="sxs-lookup"><span data-stu-id="5536b-105">Impact</span></span>  
 <span data-ttu-id="5536b-106">Ces modifications bloquent certains chemins d’URI que les méthodes <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName> prenaient précédemment en charge.</span><span class="sxs-lookup"><span data-stu-id="5536b-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="5536b-107">Atténuation</span><span class="sxs-lookup"><span data-stu-id="5536b-107">Mitigation</span></span>  
 <span data-ttu-id="5536b-108">Pour contourner le problème d’un chemin précédemment acceptable qui n’est plus pris en charge par les méthodes <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName>, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5536b-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName> methods, you can do the following:</span></span>  
  
-   <span data-ttu-id="5536b-109">Supprimez manuellement le schéma à partir d’une URL.</span><span class="sxs-lookup"><span data-stu-id="5536b-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="5536b-110">Par exemple, supprimez `file://` à partir d’une URL.</span><span class="sxs-lookup"><span data-stu-id="5536b-110">For example, remove `file://` from a URL.</span></span>  
  
-   <span data-ttu-id="5536b-111">Passez l’URI à un constructeur <xref:System.Uri> et récupérez la valeur de la propriété <xref:System.Uri.LocalPath%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="5536b-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=fullName> property.</span></span>  
  
-   <span data-ttu-id="5536b-112">Refusez la nouvelle normalisation de chemin d’accès en affectant à `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="5536b-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5536b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5536b-113">See Also</span></span>  
 [<span data-ttu-id="5536b-114">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="5536b-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)

