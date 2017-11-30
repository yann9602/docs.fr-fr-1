---
title: GetCustomUI
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f3c101ad13df9b99a2d872bac8783baed8b4b9a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="getcustomui"></a><span data-ttu-id="2133f-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="2133f-102">GetCustomUI</span></span>
<span data-ttu-id="2133f-103">Appelée par PresentationHost.exe pour obtenir des messages d’erreur et d’avancement personnalisés à partir de l’ordinateur hôte, si implémenté.</span><span class="sxs-lookup"><span data-stu-id="2133f-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2133f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2133f-104">Syntax</span></span>  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2133f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2133f-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="2133f-106">[out] Pointeur vers l’assembly qui contient l’interface utilisateur fournie par l’hôte de progression.</span><span class="sxs-lookup"><span data-stu-id="2133f-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="2133f-107">[out] Le nom de la classe qui est l’interface utilisateur d’avancement fournie par l’hôte, de préférence un [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] de fichiers avec <xref:System.Windows.Controls.Page> comme élément de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="2133f-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="2133f-108">Cette classe se trouve dans l’assembly spécifié par `pwzProgressAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="2133f-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="2133f-109">[out] Pointeur vers l’assembly qui contient l’interface utilisateur d’erreur fourni par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="2133f-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="2133f-110">[out] Le nom de la classe qui est l’utilisateur d’erreur fourni par l’hôte de l’interface, de préférence un fichier XAML avec <xref:System.Windows.Controls.Page> comme élément de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="2133f-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="2133f-111">Cette classe se trouve dans l’assembly spécifié par `pwzErrorAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="2133f-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="2133f-112">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2133f-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="2133f-113">HRESULT : ignoré.</span><span class="sxs-lookup"><span data-stu-id="2133f-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2133f-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="2133f-114">Remarks</span></span>  
 <span data-ttu-id="2133f-115">Une application hôte peut avoir un thème spécifique ne soit pas conforme à des interfaces utilisateur de PresentationHost.exe par défaut.</span><span class="sxs-lookup"><span data-stu-id="2133f-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="2133f-116">Si c’est le cas, l’application hôte peut implémenter [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) pour retourner la progression et erreur des interfaces utilisateur à PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="2133f-116">If this is the case, the host application can implement [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="2133f-117">PresentationHost.exe appelle toujours [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) avant d’utiliser ses interfaces d’utilisateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2133f-117">PresentationHost.exe will always call [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="2133f-118">Cette fonction est appelée une fois au cours de l’initialisation de PresentationHost.</span><span class="sxs-lookup"><span data-stu-id="2133f-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2133f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2133f-119">See Also</span></span>  
 [<span data-ttu-id="2133f-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="2133f-120">IWpfHostSupport</span></span>](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)
