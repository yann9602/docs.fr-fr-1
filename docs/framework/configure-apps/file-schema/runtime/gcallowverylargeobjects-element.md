---
title: "&lt;gcAllowVeryLargeObjects&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49046c343ef749e597402f7e19a08fe1f2c98ca0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltgcallowverylargeobjectsgt-element"></a><span data-ttu-id="58247-102">&lt;gcAllowVeryLargeObjects&gt; élément</span><span class="sxs-lookup"><span data-stu-id="58247-102">&lt;gcAllowVeryLargeObjects&gt; Element</span></span>
<span data-ttu-id="58247-103">Sur les plateformes 64 bits, autorise les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).</span><span class="sxs-lookup"><span data-stu-id="58247-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
 <span data-ttu-id="58247-104">\<configuration > élément</span><span class="sxs-lookup"><span data-stu-id="58247-104">\<configuration> Element</span></span>  
<span data-ttu-id="58247-105">\<runtime > élément</span><span class="sxs-lookup"><span data-stu-id="58247-105">\<runtime> Element</span></span>  
<span data-ttu-id="58247-106">\<gcAllowVeryLargeObjects > élément</span><span class="sxs-lookup"><span data-stu-id="58247-106">\<gcAllowVeryLargeObjects> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58247-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58247-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58247-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="58247-108">Attributes and Elements</span></span>  
 <span data-ttu-id="58247-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="58247-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58247-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="58247-110">Attributes</span></span>  
  
|<span data-ttu-id="58247-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="58247-111">Attribute</span></span>|<span data-ttu-id="58247-112">Description</span><span class="sxs-lookup"><span data-stu-id="58247-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="58247-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="58247-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="58247-114">Spécifie si les tableaux sont supérieures à 2 Go de taille totale sont activés sur des plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="58247-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="58247-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="58247-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="58247-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="58247-116">Value</span></span>|<span data-ttu-id="58247-117">Description</span><span class="sxs-lookup"><span data-stu-id="58247-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="58247-118">Supérieure à 2 Go de taille totale des tableaux ne sont pas activés.</span><span class="sxs-lookup"><span data-stu-id="58247-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="58247-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="58247-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="58247-120">Supérieure à 2 Go de taille totale des tableaux sont activés sur des plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="58247-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58247-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="58247-121">Child Elements</span></span>  
 <span data-ttu-id="58247-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="58247-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58247-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="58247-123">Parent Elements</span></span>  
  
|<span data-ttu-id="58247-124">Élément</span><span class="sxs-lookup"><span data-stu-id="58247-124">Element</span></span>|<span data-ttu-id="58247-125">Description</span><span class="sxs-lookup"><span data-stu-id="58247-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="58247-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="58247-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="58247-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="58247-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58247-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="58247-128">Remarks</span></span>  
 <span data-ttu-id="58247-129">Dans votre fichier de configuration d’application à l’aide de cet élément permet de tableaux supérieurs à 2 Go, mais ne modifie pas les autres limites sur la taille de l’objet ou de la taille du tableau :</span><span class="sxs-lookup"><span data-stu-id="58247-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
-   <span data-ttu-id="58247-130">Le nombre maximal d’éléments dans un tableau est <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="58247-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="58247-131">L’index maximal dans n’importe quelle dimension unique est 2,147,483,591 (0x7FFFFFC7) pour les tableaux d’octets et les tableaux de structures d’un octet et 2,146,435,071 (0X7FEFFFFF) pour les autres types.</span><span class="sxs-lookup"><span data-stu-id="58247-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
-   <span data-ttu-id="58247-132">La taille maximale pour les chaînes et autres objets non-tableau est inchangée.</span><span class="sxs-lookup"><span data-stu-id="58247-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="58247-133">Avant d’activer cette fonctionnalité, vérifiez que votre application n’inclut pas de code unsafe qui suppose que tous les tableaux sont inférieures à 2 Go.</span><span class="sxs-lookup"><span data-stu-id="58247-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="58247-134">Par exemple, du code qui utilise des tableaux en tant que les mémoires tampons unsafe peut-être susceptibles d’être dépassements de mémoire tampon si elle est écrite sur l’hypothèse que les tableaux ne dépassent pas 2 Go.</span><span class="sxs-lookup"><span data-stu-id="58247-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58247-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="58247-135">Example</span></span>  
 <span data-ttu-id="58247-136">L’exemple suivant montre comment activer cette fonctionnalité pour une application.</span><span class="sxs-lookup"><span data-stu-id="58247-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58247-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58247-137">See Also</span></span>  
 [<span data-ttu-id="58247-138">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="58247-138">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="58247-139">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="58247-139">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
