---
title: "Atténuation : Constructeur ClaimsIdentity"
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
ms.assetid: 946903f1-0fbf-4f67-805b-1eb48352024d
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a50cbd69aa1f2c72adc9fc4d10a070f5faa0cf54
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-claimsidentity-constructor"></a><span data-ttu-id="d3382-102">Atténuation : Constructeur ClaimsIdentity</span><span class="sxs-lookup"><span data-stu-id="d3382-102">Mitigation: ClaimsIdentity Constructor</span></span>
<span data-ttu-id="d3382-103">À compter du [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], la façon dont le constructeur <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> définit la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> est modifiée.</span><span class="sxs-lookup"><span data-stu-id="d3382-103">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], there is change in how the <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> constructor sets the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> property.</span></span> <span data-ttu-id="d3382-104">Si l’argument <xref:System.Security.Principal.IIdentity> est un objet <xref:System.Security.Claims.ClaimsIdentity> et que la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> de cet objet <xref:System.Security.Claims.ClaimsIdentity> n’est pas `null`, la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> est jointe à l’aide de la méthode <xref:System.Security.Claims.ClaimsIdentity.Clone%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d3382-104">If the <xref:System.Security.Principal.IIdentity> argument is a <xref:System.Security.Claims.ClaimsIdentity> object, and the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> property of that <xref:System.Security.Claims.ClaimsIdentity> object is not `null`, the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> property is attached by using the <xref:System.Security.Claims.ClaimsIdentity.Clone%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="d3382-105">Dans le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> est jointe en tant que référence existante.</span><span class="sxs-lookup"><span data-stu-id="d3382-105">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> property is attached as a  existing reference.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="d3382-106">Impact</span><span class="sxs-lookup"><span data-stu-id="d3382-106">Impact</span></span>  
 <span data-ttu-id="d3382-107">À compter du [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> du nouvel objet <xref:System.Security.Claims.ClaimsIdentity> n’est pas égale à la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> de l’argument <xref:System.Security.Principal.IIdentity> du constructeur.</span><span class="sxs-lookup"><span data-stu-id="d3382-107">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> property of the new <xref:System.Security.Claims.ClaimsIdentity> object is not equal to the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> property of the constructor's <xref:System.Security.Principal.IIdentity> argument.</span></span> <span data-ttu-id="d3382-108">Dans [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions antérieures, il n’y a pas de différence.</span><span class="sxs-lookup"><span data-stu-id="d3382-108">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, it is equal.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="d3382-109">Atténuation</span><span class="sxs-lookup"><span data-stu-id="d3382-109">Mitigation</span></span>  
 <span data-ttu-id="d3382-110">Si ce comportement n’est pas souhaitable, vous pouvez restaurer le comportement précédent en réglant `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` dans votre fichier de configuration d’application sur `true`.</span><span class="sxs-lookup"><span data-stu-id="d3382-110">If this behavior is undesirable, you can restore the previous behavior by setting the `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` switch in your application configuration file to `true`.</span></span> <span data-ttu-id="d3382-111">Pour cela, vous ajoutez le code suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier web.config :</span><span class="sxs-lookup"><span data-stu-id="d3382-111">This requires that you add the following to  the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your web.config file:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3382-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3382-112">See Also</span></span>  
 [<span data-ttu-id="d3382-113">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="d3382-113">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

