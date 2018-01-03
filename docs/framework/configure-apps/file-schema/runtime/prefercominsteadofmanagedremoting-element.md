---
title: "&lt;PreferComInsteadOfManagedRemoting&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad60d73e30bf02fd52f9c8f3bd707b571959bdd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a><span data-ttu-id="6af24-102">&lt;PreferComInsteadOfManagedRemoting&gt; élément</span><span class="sxs-lookup"><span data-stu-id="6af24-102">&lt;PreferComInsteadOfManagedRemoting&gt; Element</span></span>
<span data-ttu-id="6af24-103">Spécifie si le runtime utilisera COM interop au lieu de la communication à distance pour tous les appels entre les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="6af24-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="6af24-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6af24-104">\<configuration></span></span>  
<span data-ttu-id="6af24-105">\<runtime ></span><span class="sxs-lookup"><span data-stu-id="6af24-105">\<runtime></span></span>  
<span data-ttu-id="6af24-106">\<PreferComInsteadOfManagedRemoting ></span><span class="sxs-lookup"><span data-stu-id="6af24-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af24-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6af24-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6af24-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6af24-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6af24-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6af24-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6af24-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="6af24-110">Attributes</span></span>  
  
|<span data-ttu-id="6af24-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="6af24-111">Attribute</span></span>|<span data-ttu-id="6af24-112">Description</span><span class="sxs-lookup"><span data-stu-id="6af24-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6af24-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="6af24-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="6af24-114">Indique si le runtime utilisera COM interop au lieu de la communication à distance entre les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="6af24-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6af24-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="6af24-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="6af24-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="6af24-116">Value</span></span>|<span data-ttu-id="6af24-117">Description</span><span class="sxs-lookup"><span data-stu-id="6af24-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6af24-118">Le runtime utilise la communication à distance entre les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="6af24-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="6af24-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="6af24-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="6af24-120">Le runtime utilisera COM interop au-delà des limites de domaine application.</span><span class="sxs-lookup"><span data-stu-id="6af24-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6af24-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6af24-121">Child Elements</span></span>  
 <span data-ttu-id="6af24-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6af24-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6af24-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6af24-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6af24-124">Élément</span><span class="sxs-lookup"><span data-stu-id="6af24-124">Element</span></span>|<span data-ttu-id="6af24-125">Description</span><span class="sxs-lookup"><span data-stu-id="6af24-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6af24-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6af24-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6af24-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6af24-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6af24-128">Notes</span><span class="sxs-lookup"><span data-stu-id="6af24-128">Remarks</span></span>  
 <span data-ttu-id="6af24-129">Lorsque vous définissez la `enabled` attribut `true`, le runtime se comporte comme suit :</span><span class="sxs-lookup"><span data-stu-id="6af24-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
-   <span data-ttu-id="6af24-130">Le runtime n’appelle pas [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) pour un [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface quand un [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) accède au domaine via une interface COM.</span><span class="sxs-lookup"><span data-stu-id="6af24-130">The runtime does not call [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="6af24-131">Au lieu de cela, il construit un [Wrapper RCW](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) autour de l’objet.</span><span class="sxs-lookup"><span data-stu-id="6af24-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
-   <span data-ttu-id="6af24-132">Le runtime retourne E_NOINTERFACE lorsqu’il reçoit un `QueryInterface` appeler pour une [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface pour toute [Wrapper CCW](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) qui a été créé dans ce domaine.</span><span class="sxs-lookup"><span data-stu-id="6af24-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="6af24-133">Ces deux comportements garantissent que tous les appels sur COM des interfaces entre les objets gérés sur l’utilisation des limites du domaine d’application COM et COM interop au lieu de la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="6af24-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6af24-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="6af24-134">Example</span></span>  
 <span data-ttu-id="6af24-135">L’exemple suivant montre comment spécifier que le runtime doit utiliser COM interop au-delà des limites d’isolation :</span><span class="sxs-lookup"><span data-stu-id="6af24-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6af24-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6af24-136">See Also</span></span>  
 [<span data-ttu-id="6af24-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="6af24-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="6af24-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="6af24-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
