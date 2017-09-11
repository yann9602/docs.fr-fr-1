---
title: "Atténuation : Prise en charge des chemins d’accès longs"
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
ms.assetid: 3cbe2d77-6e2c-4665-a6c5-7000b9ad6890
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 138e96c3d45b79ccf30f6a3d39f0af26a48c0117
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-long-path-support"></a><span data-ttu-id="17df0-102">Atténuation : Prise en charge des chemins d’accès longs</span><span class="sxs-lookup"><span data-stu-id="17df0-102">Mitigation: Long Path Support</span></span>
<span data-ttu-id="17df0-103">À partir des applications qui ciblent le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], les méthodes d’E/S du système de fichiers ne lèvent plus automatiquement une <xref:System.IO.PathTooLongException> si un chemin ou nom de fichier complet dépasse 260 (ou `MAX_PATH`) caractères.</span><span class="sxs-lookup"><span data-stu-id="17df0-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)],  file system I/O methods not longer automatically throw a <xref:System.IO.PathTooLongException> if a path or fully qualified file name exceeds 260 (or `MAX_PATH`) characters.</span></span> <span data-ttu-id="17df0-104">Au lieu de cela, les chemins d’accès longs de sont pris en charge jusqu'à 32 000 caractères.</span><span class="sxs-lookup"><span data-stu-id="17df0-104">Instead, long paths of up to 32K characters are supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="17df0-105">Impact</span><span class="sxs-lookup"><span data-stu-id="17df0-105">Impact</span></span>  
 <span data-ttu-id="17df0-106">Les applications recompilées pour cibler [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] et qui levaient précédemment une <xref:System.IO.PathTooLongException> automatiquement car un chemin dépassait 260 caractères lèvent maintenant une <xref:System.IO.PathTooLongException> uniquement dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="17df0-106">Apps recompiled to target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] and that previously threw a <xref:System.IO.PathTooLongException> automatically because a path exceeded 260 characters will now throw a <xref:System.IO.PathTooLongException> only under the following conditions:</span></span>  
  
-   <span data-ttu-id="17df0-107">La longueur du chemin est supérieure à <xref:System.Int16.MaxValue?displayProperty=fullName> (32 767) caractères.</span><span class="sxs-lookup"><span data-stu-id="17df0-107">The length of the path is greater than  <xref:System.Int16.MaxValue?displayProperty=fullName> (32,767) characters.</span></span>  
  
-   <span data-ttu-id="17df0-108">Le système d’exploitation renvoie `COR_E_PATHTOOLONG` ou son équivalent.</span><span class="sxs-lookup"><span data-stu-id="17df0-108">The operating system returns `COR_E_PATHTOOLONG` or its equivalent.</span></span>  
  
 <span data-ttu-id="17df0-109">L’ancien comportement pour les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions antérieures faisait que le runtime levait automatiquement une <xref:System.IO.PathTooLongException> chaque fois qu’un chemin comportait plus de 260 caractères.</span><span class="sxs-lookup"><span data-stu-id="17df0-109">The legacy behavior for apps that target the[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier is that the runtime automatically throws a <xref:System.IO.PathTooLongException> whenever a path exceeds 260 characters.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="17df0-110">Atténuation</span><span class="sxs-lookup"><span data-stu-id="17df0-110">Mitigation</span></span>  
 <span data-ttu-id="17df0-111">Pour les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], vous pouvez annuler la prise en charge des longs chemins d’accès en ajoutant le code suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="17df0-111">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], you can opt out of long path support if it is not desirable by adding the following to    to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />   
</runtime>  
```  
  
 <span data-ttu-id="17df0-112">Pour les applications qui ciblent des versions antérieures de .NET Framework mais s’exécutent sur [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou version ultérieure, vous pouvez accepter la prise en charge des longs chemins d’accès en ajoutant le code suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="17df0-112">For apps that target earlier versions of the .NET Framework but run on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later., you can opt in to long path support by adding the following to    to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="17df0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17df0-113">See Also</span></span>  
 [<span data-ttu-id="17df0-114">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="17df0-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)

