---
title: "&lt;etwEnable&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d94d49fcb2c395de5172a730923dbe42f67cf35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltetwenablegt-element"></a><span data-ttu-id="f4fd7-102">&lt;etwEnable&gt; élément</span><span class="sxs-lookup"><span data-stu-id="f4fd7-102">&lt;etwEnable&gt; Element</span></span>
<span data-ttu-id="f4fd7-103">Indique s’il faut activer le Suivi d’événements pour Windows (ETW) pour les événements du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="f4fd7-104">\<configuration > élément</span><span class="sxs-lookup"><span data-stu-id="f4fd7-104">\<configuration> Element</span></span>  
<span data-ttu-id="f4fd7-105">\<runtime > élément</span><span class="sxs-lookup"><span data-stu-id="f4fd7-105">\<runtime> Element</span></span>  
<span data-ttu-id="f4fd7-106">\<etwEnabled ></span><span class="sxs-lookup"><span data-stu-id="f4fd7-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4fd7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4fd7-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4fd7-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f4fd7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f4fd7-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4fd7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="f4fd7-110">Attributes</span></span>  
  
|<span data-ttu-id="f4fd7-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="f4fd7-111">Attribute</span></span>|<span data-ttu-id="f4fd7-112">Description</span><span class="sxs-lookup"><span data-stu-id="f4fd7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f4fd7-113">enabled</span><span class="sxs-lookup"><span data-stu-id="f4fd7-113">enabled</span></span>|<span data-ttu-id="f4fd7-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="f4fd7-115">Spécifie si ETW doit être activé.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f4fd7-116">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="f4fd7-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="f4fd7-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="f4fd7-117">Value</span></span>|<span data-ttu-id="f4fd7-118">Description</span><span class="sxs-lookup"><span data-stu-id="f4fd7-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f4fd7-119">true</span><span class="sxs-lookup"><span data-stu-id="f4fd7-119">true</span></span>|<span data-ttu-id="f4fd7-120">Activer ETW.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-120">Enable ETW.</span></span> <span data-ttu-id="f4fd7-121">Il s’agit de la valeur par défaut pour les versions de Windows qui commence avec les systèmes d’exploitation Windows Vista et Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="f4fd7-122">False</span><span class="sxs-lookup"><span data-stu-id="f4fd7-122">false</span></span>|<span data-ttu-id="f4fd7-123">Désactiver ETW.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-123">Disable ETW.</span></span> <span data-ttu-id="f4fd7-124">Il s’agit de la valeur par défaut pour les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4fd7-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f4fd7-125">Child Elements</span></span>  
 <span data-ttu-id="f4fd7-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4fd7-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f4fd7-127">Parent Elements</span></span>  
  
|<span data-ttu-id="f4fd7-128">Élément</span><span class="sxs-lookup"><span data-stu-id="f4fd7-128">Element</span></span>|<span data-ttu-id="f4fd7-129">Description</span><span class="sxs-lookup"><span data-stu-id="f4fd7-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f4fd7-130">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f4fd7-131">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4fd7-132">Notes</span><span class="sxs-lookup"><span data-stu-id="f4fd7-132">Remarks</span></span>  
 <span data-ttu-id="f4fd7-133">À compter de Windows Vista, ETW est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="f4fd7-134">Utilisez cet élément pour désactiver ETW pour une application.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="f4fd7-135">Dans les versions antérieures de Windows, utilisez cet élément pour activer ETW pour une application.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4fd7-136">ETW peut être activé ou désactivé globalement sur un serveur à l’aide d’un paramètre du Registre.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="f4fd7-137">Consultez [contrôle de l’enregistrement .NET Framework](../../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="f4fd7-137">See [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4fd7-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="f4fd7-138">Example</span></span>  
 <span data-ttu-id="f4fd7-139">L’exemple suivant montre comment activer le suivi ETW pour une application.</span><span class="sxs-lookup"><span data-stu-id="f4fd7-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4fd7-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4fd7-140">See Also</span></span>  
 [<span data-ttu-id="f4fd7-141">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="f4fd7-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="f4fd7-142">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="f4fd7-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="f4fd7-143">Contrôle de l’enregistrement .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f4fd7-143">Controlling .NET Framework Logging</span></span>](../../../../../docs/framework/performance/controlling-logging.md)
