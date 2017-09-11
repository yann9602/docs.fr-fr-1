---
title: "Atténuation : AuthorizationContext par défaut"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cfeee63-b148-429a-a7e6-6fe9b0cb7610
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 48363d0f8e515b703e49761a763379566e217844
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-default-authorizationcontext"></a><span data-ttu-id="74c1e-102">Atténuation : AuthorizationContext par défaut</span><span class="sxs-lookup"><span data-stu-id="74c1e-102">Mitigation: Default AuthorizationContext</span></span>
<span data-ttu-id="74c1e-103">L’implémentation du <xref:System.IdentityModel.Policy.AuthorizationContext> retourné par un appel à la méthode <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> avec un argument `null``authorizationPolicies` a changé dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].</span><span class="sxs-lookup"><span data-stu-id="74c1e-103">The implementation of the <xref:System.IdentityModel.Policy.AuthorizationContext> returned by a call to the <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> with a `null``authorizationPolicies` argument has changed its implementation in the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].</span></span>  
  
## <a name="impact"></a><span data-ttu-id="74c1e-104">Impact</span><span class="sxs-lookup"><span data-stu-id="74c1e-104">Impact</span></span>  
 <span data-ttu-id="74c1e-105">Dans de rares cas, les applications WCF qui utilisent l'authentification personnalisée peuvent voir les différences de comportement.</span><span class="sxs-lookup"><span data-stu-id="74c1e-105">In rare cases, WCF apps that use custom authentication may see behavioral differences.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="74c1e-106">Atténuation</span><span class="sxs-lookup"><span data-stu-id="74c1e-106">Mitigation</span></span>  
 <span data-ttu-id="74c1e-107">Vous pouvez restaurer le comportement précédent de deux manières :</span><span class="sxs-lookup"><span data-stu-id="74c1e-107">You can restore the previous behavior in either of two ways:</span></span>  
  
-   <span data-ttu-id="74c1e-108">Recompiler l'application pour cibler une version antérieure du .NET Framework autre que 4.6.</span><span class="sxs-lookup"><span data-stu-id="74c1e-108">Recompile your app to target an earlier version of the .NET Framework than 4.6.</span></span> <span data-ttu-id="74c1e-109">Pour les services hébergés dans IIS, utilisez l'élément `<httpRuntime targetFramework="x.x" />` pour cibler une version antérieure du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="74c1e-109">For IIS-hosted services, use the `<httpRuntime targetFramework="x.x" />` element to target an earlier version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="74c1e-110">Ajoutez la ligne suivante à la section `<appSettings>` de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="74c1e-110">Add the following line to the `<appSettings>` section of your app.config file:</span></span>  
  
    ```xml  
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="74c1e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74c1e-111">See Also</span></span>  
 [<span data-ttu-id="74c1e-112">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="74c1e-112">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

