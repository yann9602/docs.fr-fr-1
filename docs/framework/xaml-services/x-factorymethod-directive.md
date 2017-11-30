---
title: x:FactoryMethod, directive
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 0d53db49961c2a75e4547f6b57240cefd2cc17c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="44c38-102">x:FactoryMethod, directive</span><span class="sxs-lookup"><span data-stu-id="44c38-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="44c38-103">Spécifie une méthode autre qu’un constructeur qu’un processeur XAML doit utiliser pour initialiser un objet après avoir résolu son type de stockage.</span><span class="sxs-lookup"><span data-stu-id="44c38-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="44c38-104">Utilisation d’attributs XAML, aucune x : Arguments</span><span class="sxs-lookup"><span data-stu-id="44c38-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="44c38-105">Utilisation d’attribut XAML, x : Arguments comme élément (s)</span><span class="sxs-lookup"><span data-stu-id="44c38-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="44c38-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="44c38-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="44c38-107">Le nom de méthode de chaîne d’une méthode qui appellent des processeurs XAML pour initialiser l’instance spécifié comme `object`.</span><span class="sxs-lookup"><span data-stu-id="44c38-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="44c38-108">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="44c38-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="44c38-109">Un ou plusieurs éléments objet pour les objets qui spécifient les paramètres de méthode de fabrique.</span><span class="sxs-lookup"><span data-stu-id="44c38-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="44c38-110">Ordre est significatif ; Il désigne l’ordre dans lequel les arguments doivent être passés à la méthode de fabrique.</span><span class="sxs-lookup"><span data-stu-id="44c38-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44c38-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="44c38-111">Remarks</span></span>  
 <span data-ttu-id="44c38-112">Si `methodname` est une méthode d’instance, il ne peut pas être qualifié.</span><span class="sxs-lookup"><span data-stu-id="44c38-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="44c38-113">Les méthodes statiques en tant que méthodes de fabrique sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="44c38-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="44c38-114">Si `methodname` est une méthode statique, `methodname` est fournie comme un *typeName*. *methodName* combinaison, où *typeName* nomme la classe qui définit la méthode de fabrique statique.</span><span class="sxs-lookup"><span data-stu-id="44c38-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="44c38-115">*nom de type* peut être qualifié par un préfixe s’il fait référence à un type dans un xmlns mappé.</span><span class="sxs-lookup"><span data-stu-id="44c38-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="44c38-116">*typeName* peut être un type différent de `typeof(``object``)`.</span><span class="sxs-lookup"><span data-stu-id="44c38-116">*typeName* can be a different type than `typeof(``object``)`.</span></span>  
  
 <span data-ttu-id="44c38-117">La méthode de fabrique doit être une méthode publique déclarée du type qui stocke l’élément objet appropriée.</span><span class="sxs-lookup"><span data-stu-id="44c38-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="44c38-118">La méthode de fabrique doit retourner une instance ne peut être assignée à l’objet correspondant.</span><span class="sxs-lookup"><span data-stu-id="44c38-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="44c38-119">Méthodes de fabrique ne doivent jamais retourner null.</span><span class="sxs-lookup"><span data-stu-id="44c38-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="44c38-120">`x:Arguments`fonctionne sur un principe de meilleure correspondance pour les signatures des méthodes de fabrique.</span><span class="sxs-lookup"><span data-stu-id="44c38-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="44c38-121">Mise en correspondance évalue d’abord le nombre de paramètres.</span><span class="sxs-lookup"><span data-stu-id="44c38-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="44c38-122">S’il existe plusieurs correspondances possibles pour un nombre de paramètres, le type de paramètre est évaluée et la meilleure correspondance est déterminée.</span><span class="sxs-lookup"><span data-stu-id="44c38-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="44c38-123">S’il reste une ambiguïté après cette phase d’évaluation, le comportement du processeur XAML est non défini.</span><span class="sxs-lookup"><span data-stu-id="44c38-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="44c38-124">Le `x:FactoryMethod` utilisation de l’élément n’est pas utilisation des éléments de propriété dans le sens classique, étant donné que le balisage de la directive ne référence pas de type de l’élément objet contenant.</span><span class="sxs-lookup"><span data-stu-id="44c38-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="44c38-125">Il est probable que l’utilisation d’élément est moins courant que l’utilisation d’attributs.</span><span class="sxs-lookup"><span data-stu-id="44c38-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="44c38-126">`x:Arguments`(utilisation d’attribut ou élément) peut être utilisée avec `x:FactoryMethod` utilisation de l’élément, mais ce n’est pas affiché spécifiquement dans les sections d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="44c38-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="44c38-127">`x:FactoryMethod`comme un élément doit précéder tous les autres éléments de propriété, doit précéder tout `x:Arguments` également fourni en tant qu’éléments et doit précéder tout contenu/interne texte/texte d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="44c38-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44c38-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44c38-128">See Also</span></span>  
 [<span data-ttu-id="44c38-129">x:Arguments (directive)</span><span class="sxs-lookup"><span data-stu-id="44c38-129">x:Arguments Directive</span></span>](../../../docs/framework/xaml-services/x-arguments-directive.md)
