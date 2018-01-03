---
title: "&lt;enforceFIPSPolicy&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb8cb1ea4d011eb25aee14ddd53d3dc882f75d8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltenforcefipspolicygt-element"></a><span data-ttu-id="3368e-102">&lt;enforceFIPSPolicy&gt; élément</span><span class="sxs-lookup"><span data-stu-id="3368e-102">&lt;enforceFIPSPolicy&gt; Element</span></span>
<span data-ttu-id="3368e-103">Indique s’il faut appliquer la condition de configuration d’ordinateur selon laquelle les algorithmes de chiffrement doivent être conformes aux normes FIPS (Federal Information Processing Standard).</span><span class="sxs-lookup"><span data-stu-id="3368e-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="3368e-104">\<configuration > élément</span><span class="sxs-lookup"><span data-stu-id="3368e-104">\<configuration> Element</span></span>  
<span data-ttu-id="3368e-105">\<runtime > élément</span><span class="sxs-lookup"><span data-stu-id="3368e-105">\<runtime> Element</span></span>  
<span data-ttu-id="3368e-106">\<enforceFIPSPolicy > élément</span><span class="sxs-lookup"><span data-stu-id="3368e-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3368e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3368e-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3368e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3368e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3368e-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3368e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3368e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="3368e-110">Attributes</span></span>  
  
|<span data-ttu-id="3368e-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="3368e-111">Attribute</span></span>|<span data-ttu-id="3368e-112">Description</span><span class="sxs-lookup"><span data-stu-id="3368e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3368e-113">enabled</span><span class="sxs-lookup"><span data-stu-id="3368e-113">enabled</span></span>|<span data-ttu-id="3368e-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="3368e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="3368e-115">Spécifie s’il faut activer la mise en œuvre d’une spécification de configuration d’ordinateur que les algorithmes de chiffrement doivent être conformes à la norme FIPS.</span><span class="sxs-lookup"><span data-stu-id="3368e-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3368e-116">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="3368e-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="3368e-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="3368e-117">Value</span></span>|<span data-ttu-id="3368e-118">Description</span><span class="sxs-lookup"><span data-stu-id="3368e-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="3368e-119">Si votre ordinateur est configuré pour exiger des algorithmes de chiffrement conformes à FIPS, cette spécification est appliquée.</span><span class="sxs-lookup"><span data-stu-id="3368e-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="3368e-120">Si une classe implémente un algorithme qui n’est pas conforme à la norme FIPS, les constructeurs ou `Create` méthodes pour cette classe lever des exceptions lorsqu’elles sont exécutées sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3368e-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="3368e-121">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="3368e-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="3368e-122">Les algorithmes de chiffrement qui sont utilisés par l’application ne sont pas requis pour être conforme à la norme FIPS, quelle que soit la configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3368e-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3368e-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3368e-123">Child Elements</span></span>  
 <span data-ttu-id="3368e-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3368e-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3368e-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3368e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3368e-126">Élément</span><span class="sxs-lookup"><span data-stu-id="3368e-126">Element</span></span>|<span data-ttu-id="3368e-127">Description</span><span class="sxs-lookup"><span data-stu-id="3368e-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3368e-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3368e-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3368e-129">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="3368e-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3368e-130">Notes</span><span class="sxs-lookup"><span data-stu-id="3368e-130">Remarks</span></span>  
 <span data-ttu-id="3368e-131">À compter de .NET Framework 2.0, la création de classes qui implémentent des algorithmes de chiffrement est contrôlée par la configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3368e-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="3368e-132">Si l’ordinateur est configuré pour exiger des algorithmes pour être conforme à la norme FIPS, et une classe qui implémente un algorithme qui n’est pas conforme à la norme FIPS, toute tentative pour créer une instance de cette classe lève une exception.</span><span class="sxs-lookup"><span data-stu-id="3368e-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="3368e-133">Constructeurs lèvent une <xref:System.InvalidOperationException> exception, et `Create` méthodes lèvent une <xref:System.Reflection.TargetInvocationException> exception avec une exception interne <xref:System.InvalidOperationException> exception.</span><span class="sxs-lookup"><span data-stu-id="3368e-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="3368e-134">Si votre application s’exécute sur les ordinateurs dont les configurations requièrent une conformité à la norme FIPS et que votre application utilise un algorithme qui n’est pas conforme à la norme FIPS, vous pouvez utiliser cet élément dans votre fichier de configuration pour empêcher le common language runtime (CLR) à partir de appliquer la conformité FIPS.</span><span class="sxs-lookup"><span data-stu-id="3368e-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="3368e-135">Cet élément a été introduit dans le [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3368e-135">This element was introduced in the [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="3368e-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="3368e-136">Example</span></span>  
 <span data-ttu-id="3368e-137">L’exemple suivant montre comment empêcher le CLR d’appliquer la conformité FIPS.</span><span class="sxs-lookup"><span data-stu-id="3368e-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3368e-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3368e-138">See Also</span></span>  
 [<span data-ttu-id="3368e-139">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="3368e-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="3368e-140">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="3368e-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="3368e-141">Modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="3368e-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)
