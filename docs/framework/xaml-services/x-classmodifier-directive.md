---
title: x:ClassModifier, directive
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
caps.latest.revision: "22"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 111c4a6ed78a908ae3b171dc9349a3c9b81750de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="3ebd3-102">x:ClassModifier, directive</span><span class="sxs-lookup"><span data-stu-id="3ebd3-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="3ebd3-103">Modifie le comportement de compilation XAML lorsque `x:Class` est également fourni.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="3ebd3-104">Plus précisément, au lieu de la création d’un partiel `class` qui a un `Public` (la valeur par défaut), de niveau d’accès fourni `x:Class` est créé avec un `NotPublic` niveau d’accès.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="3ebd3-105">Ce comportement affecte le niveau d’accès de la classe dans les assemblys générés.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="3ebd3-106">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="3ebd3-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="3ebd3-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="3ebd3-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ebd3-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="3ebd3-108">*NotPublic*</span></span>|<span data-ttu-id="3ebd3-109">La chaîne exacte à passer pour spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varie selon le langage de programmation de code-behind que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="3ebd3-110">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="3ebd3-111">Dépendances</span><span class="sxs-lookup"><span data-stu-id="3ebd3-111">Dependencies</span></span>  
 <span data-ttu-id="3ebd3-112">[x : Class](../../../docs/framework/xaml-services/x-class-directive.md) doit également être fourni sur le même élément, et cet élément doit être l’élément racine dans une page.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-112">[x:Class](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="3ebd3-113">Pour plus d’informations, consultez [ \[MS-XAML\] Section 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="3ebd3-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ebd3-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="3ebd3-114">Remarks</span></span>  
 <span data-ttu-id="3ebd3-115">La valeur de `x:ClassModifier` dans les Services XAML .NET Framework utilisation varie selon le langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="3ebd3-116">La chaîne à utiliser dépend de la façon dont chaque langage implémente ses <xref:System.CodeDom.Compiler.CodeDomProvider> et les convertisseurs de type qu’il retourne pour définir les significations de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, et si cette langue est respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
-   <span data-ttu-id="3ebd3-117">Pour [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], la chaîne à passer pour désigner <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est `internal`.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-117">For [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
-   <span data-ttu-id="3ebd3-118">Pour [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], la chaîne à passer pour désigner <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est `Friend`.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-118">For [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
-   <span data-ttu-id="3ebd3-119">Pour [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], qui prennent en charge la compilation XAML n’existe aucune cible ; par conséquent, la valeur à passer n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-119">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="3ebd3-120">Vous pouvez également spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` dans [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Public` dans [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]) ; Cependant, en spécifiant <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est rarement car <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est déjà le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Public` in [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="3ebd3-121">Autres valeurs avec le code utilisateur équivalente-niveau d’accès restrictions, tel que `private` dans [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], ne sont pas pertinentes pour `x:ClassModifier` , car les références de classe imbriquées ne sont pas pris en charge dans XAML et par conséquent, le <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modificateur a la même effet.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-121">Other values with equivalent user code access-level restrictions, such as `private` in [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="3ebd3-122">Notes de sécurité</span><span class="sxs-lookup"><span data-stu-id="3ebd3-122">Security Notes</span></span>  
 <span data-ttu-id="3ebd3-123">Le niveau d’accès tel que déclaré dans `x:ClassModifier` est toujours soumis à l’interprétation par les infrastructures particulières et leurs fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="3ebd3-124">WPF inclut des fonctions pour charger et instancier des types où `x:ClassModifier` est `internal`, si cette classe est référencée par une ressource WPF via une référence URI à en-tête pack.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="3ebd3-125">En raison de ce cas et potentiellement d’autres similaires implémentés par d’autres infrastructures, ne comptez pas exclusivement sur `x:ClassModifier` pour bloquer l’instanciation possible toutes les tentatives.</span><span class="sxs-lookup"><span data-stu-id="3ebd3-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ebd3-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ebd3-126">See Also</span></span>  
 [<span data-ttu-id="3ebd3-127">x:Class, directive</span><span class="sxs-lookup"><span data-stu-id="3ebd3-127">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="3ebd3-128">Code-behind et XAML dans WPF</span><span class="sxs-lookup"><span data-stu-id="3ebd3-128">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="3ebd3-129">x:FieldModifier, directive</span><span class="sxs-lookup"><span data-stu-id="3ebd3-129">x:FieldModifier Directive</span></span>](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [<span data-ttu-id="3ebd3-130">Sécurité (WPF)</span><span class="sxs-lookup"><span data-stu-id="3ebd3-130">Security (WPF)</span></span>](../../../docs/framework/wpf/security-wpf.md)  
 [<span data-ttu-id="3ebd3-131">Types migrés de WPF vers System.Xaml</span><span class="sxs-lookup"><span data-stu-id="3ebd3-131">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
