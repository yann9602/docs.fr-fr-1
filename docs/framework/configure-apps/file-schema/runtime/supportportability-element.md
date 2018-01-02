---
title: "&lt;supportPortability&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9776e900015dad8bce8c16991b8ce0aeb6067812
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsupportportabilitygt-element"></a><span data-ttu-id="64ecb-102">&lt;supportPortability&gt; élément</span><span class="sxs-lookup"><span data-stu-id="64ecb-102">&lt;supportPortability&gt; Element</span></span>
<span data-ttu-id="64ecb-103">Spécifie qu’une application peut référencer le même assembly dans deux implémentations différentes du .NET Framework, en désactivant le comportement par défaut qui traite les assemblys de façon équivalente à des fins de portabilité des applications.</span><span class="sxs-lookup"><span data-stu-id="64ecb-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
 <span data-ttu-id="64ecb-104">\<configuration > élément</span><span class="sxs-lookup"><span data-stu-id="64ecb-104">\<configuration> Element</span></span>  
<span data-ttu-id="64ecb-105">\<runtime > élément</span><span class="sxs-lookup"><span data-stu-id="64ecb-105">\<runtime> Element</span></span>  
<span data-ttu-id="64ecb-106">\<assemblyBinding > élément</span><span class="sxs-lookup"><span data-stu-id="64ecb-106">\<assemblyBinding> Element</span></span>  
<span data-ttu-id="64ecb-107">\<supportPortability > élément</span><span class="sxs-lookup"><span data-stu-id="64ecb-107">\<supportPortability> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64ecb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64ecb-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64ecb-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="64ecb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="64ecb-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="64ecb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64ecb-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="64ecb-111">Attributes</span></span>  
  
|<span data-ttu-id="64ecb-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="64ecb-112">Attribute</span></span>|<span data-ttu-id="64ecb-113">Description</span><span class="sxs-lookup"><span data-stu-id="64ecb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="64ecb-114">PKT</span><span class="sxs-lookup"><span data-stu-id="64ecb-114">PKT</span></span>|<span data-ttu-id="64ecb-115">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="64ecb-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="64ecb-116">Spécifie le jeton de clé publique de l’assembly affecté, sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="64ecb-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="64ecb-117">enabled</span><span class="sxs-lookup"><span data-stu-id="64ecb-117">enabled</span></span>|<span data-ttu-id="64ecb-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="64ecb-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="64ecb-119">Spécifie si la prise en charge pour la portabilité entre les implémentations de l’assembly .NET Framework spécifié doit être activée.</span><span class="sxs-lookup"><span data-stu-id="64ecb-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="64ecb-120">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="64ecb-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="64ecb-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="64ecb-121">Value</span></span>|<span data-ttu-id="64ecb-122">Description</span><span class="sxs-lookup"><span data-stu-id="64ecb-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="64ecb-123">true</span><span class="sxs-lookup"><span data-stu-id="64ecb-123">true</span></span>|<span data-ttu-id="64ecb-124">Activer la prise en charge pour la portabilité entre les implémentations de l’assembly .NET Framework spécifié.</span><span class="sxs-lookup"><span data-stu-id="64ecb-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="64ecb-125">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="64ecb-125">This is the default.</span></span>|  
|<span data-ttu-id="64ecb-126">False</span><span class="sxs-lookup"><span data-stu-id="64ecb-126">false</span></span>|<span data-ttu-id="64ecb-127">Désactiver la prise en charge pour la portabilité entre les implémentations de l’assembly .NET Framework spécifié.</span><span class="sxs-lookup"><span data-stu-id="64ecb-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="64ecb-128">Cela permet à l’application d’avoir des références à plusieurs implémentations de l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="64ecb-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64ecb-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="64ecb-129">Child Elements</span></span>  
 <span data-ttu-id="64ecb-130">Aucun.</span><span class="sxs-lookup"><span data-stu-id="64ecb-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64ecb-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="64ecb-131">Parent Elements</span></span>  
  
|<span data-ttu-id="64ecb-132">Élément</span><span class="sxs-lookup"><span data-stu-id="64ecb-132">Element</span></span>|<span data-ttu-id="64ecb-133">Description</span><span class="sxs-lookup"><span data-stu-id="64ecb-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="64ecb-134">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="64ecb-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="64ecb-135">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="64ecb-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="64ecb-136">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="64ecb-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64ecb-137">Notes</span><span class="sxs-lookup"><span data-stu-id="64ecb-137">Remarks</span></span>  
 <span data-ttu-id="64ecb-138">Compter les [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], prise en charge est fournie automatiquement pour les applications qui peuvent utiliser une des deux implémentations du .NET Framework, par exemple l’implémentation du .NET Framework ou .NET Framework pour l’implémentation Silverlight.</span><span class="sxs-lookup"><span data-stu-id="64ecb-138">Beginning with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="64ecb-139">Les deux implémentations d’un assembly .NET Framework particulier sont considérées comme équivalents par le binder d’assembly.</span><span class="sxs-lookup"><span data-stu-id="64ecb-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="64ecb-140">Dans certains scénarios, cette fonctionnalité de portabilité application pose des problèmes.</span><span class="sxs-lookup"><span data-stu-id="64ecb-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="64ecb-141">Dans ces scénarios, le `<supportPortability>` élément peut être utilisé pour désactiver la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="64ecb-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
 <span data-ttu-id="64ecb-142">Un tel scénario est un assembly qui doit faire référence à l’implémentation du .NET Framework et le .NET Framework pour l’implémentation Silverlight d’un assembly de référence particulier.</span><span class="sxs-lookup"><span data-stu-id="64ecb-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="64ecb-143">Par exemple, un concepteur XAML écrit dans Windows Presentation Foundation (WPF) devrez peut-être faire référence à la fois l’implémentation de bureau WPF pour l’interface d’utilisateur du concepteur et le sous-ensemble de WPF qui est inclus dans l’implémentation de Silverlight.</span><span class="sxs-lookup"><span data-stu-id="64ecb-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="64ecb-144">Par défaut, les références séparées provoquent une erreur du compilateur parce que la liaison d’assembly considère les deux assemblys comme équivalents.</span><span class="sxs-lookup"><span data-stu-id="64ecb-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="64ecb-145">Cet élément désactive le comportement par défaut et permet la compilation de réussir.</span><span class="sxs-lookup"><span data-stu-id="64ecb-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="64ecb-146">Afin que le compilateur passe les informations à la logique de liaison d’assembly du common language runtime, vous devez utiliser le `/appconfig` option du compilateur pour spécifier l’emplacement du fichier app.config qui contient cet élément.</span><span class="sxs-lookup"><span data-stu-id="64ecb-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64ecb-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="64ecb-147">Example</span></span>  
 <span data-ttu-id="64ecb-148">L’exemple suivant permet à une application d’avoir des références à l’implémentation du .NET Framework et le .NET Framework pour l’implémentation Silverlight de tout assembly .NET Framework qui existe dans les deux implémentations.</span><span class="sxs-lookup"><span data-stu-id="64ecb-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="64ecb-149">Le `/appconfig` option du compilateur doit être utilisée pour spécifier l’emplacement de ce fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="64ecb-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="64ecb-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64ecb-150">See Also</span></span>  
 [<span data-ttu-id="64ecb-151">/appconfig (Options du compilateur c#)</span><span class="sxs-lookup"><span data-stu-id="64ecb-151">/appconfig (C# Compiler Options)</span></span>](http://msdn.microsoft.com/library/ee523958.aspx)  
 [<span data-ttu-id="64ecb-152">Vue d’ensemble de .NET framework Assembly Unification</span><span class="sxs-lookup"><span data-stu-id="64ecb-152">.NET Framework Assembly Unification Overview</span></span>](http://msdn.microsoft.com/en-us/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
