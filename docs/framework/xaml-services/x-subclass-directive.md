---
title: x:Subclass, directive
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d620b59208b9dc852abee3dd2e4d6c58b223d70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xsubclass-directive"></a><span data-ttu-id="37cab-102">x:Subclass, directive</span><span class="sxs-lookup"><span data-stu-id="37cab-102">x:Subclass Directive</span></span>
<span data-ttu-id="37cab-103">Modifie le comportement de compilation du balisage XAML lorsque `x:Class` est également fourni.</span><span class="sxs-lookup"><span data-stu-id="37cab-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="37cab-104">Au lieu de créer une classe partielle qui est basée sur `x:Class`, fourni `x:Class` est créée comme une classe intermédiaire, et ensuite votre classe dérivée fournie est censée être basée sur `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="37cab-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="37cab-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="37cab-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="37cab-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="37cab-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`namespace`|<span data-ttu-id="37cab-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="37cab-107">Optional.</span></span> <span data-ttu-id="37cab-108">Spécifie un espace de noms CLR contenant `classname`.</span><span class="sxs-lookup"><span data-stu-id="37cab-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="37cab-109">Si `namespace` est spécifié, un point (.) sépare `namespace` et `classname`.</span><span class="sxs-lookup"><span data-stu-id="37cab-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|  
|`classname`|<span data-ttu-id="37cab-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="37cab-110">Required.</span></span> <span data-ttu-id="37cab-111">Spécifie le nom CLR de la classe partielle qui connecte le XAML chargé et votre code-behind pour ce XAML.</span><span class="sxs-lookup"><span data-stu-id="37cab-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="37cab-112">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="37cab-112">See Remarks.</span></span>|  
|`subclassNamespace`|<span data-ttu-id="37cab-113">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="37cab-113">Optional.</span></span> <span data-ttu-id="37cab-114">Peut être différent de `namespace` si chaque espace de noms peut résoudre l’autre.</span><span class="sxs-lookup"><span data-stu-id="37cab-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="37cab-115">Spécifie un espace de noms CLR contenant `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="37cab-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="37cab-116">Si `subclassName` est spécifié, un point (.) sépare `subclassNamespace` et `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="37cab-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|  
|`subclassName`|<span data-ttu-id="37cab-117">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="37cab-117">Required.</span></span> <span data-ttu-id="37cab-118">Spécifie le nom CLR de la sous-classe.</span><span class="sxs-lookup"><span data-stu-id="37cab-118">Specifies the CLR name of the subclass.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="37cab-119">Dépendances</span><span class="sxs-lookup"><span data-stu-id="37cab-119">Dependencies</span></span>  
 <span data-ttu-id="37cab-120">[x : Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) doit également être fourni sur le même objet, et cet objet doit être l’élément racine de la production XAML.</span><span class="sxs-lookup"><span data-stu-id="37cab-120">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37cab-121">Notes</span><span class="sxs-lookup"><span data-stu-id="37cab-121">Remarks</span></span>  
 <span data-ttu-id="37cab-122">`x:Subclass`l’utilisation est principalement utilisée pour les langages qui ne prennent pas en charge les déclarations de classe partielle.</span><span class="sxs-lookup"><span data-stu-id="37cab-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>  
  
 <span data-ttu-id="37cab-123">La classe utilisée comme le `x:Subclass` ne peut pas être une classe imbriquée, et `x:Subclass` doit faire référence à l’objet racine, comme expliqué dans la section « Dépendances ».</span><span class="sxs-lookup"><span data-stu-id="37cab-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>  
  
 <span data-ttu-id="37cab-124">Dans le cas contraire, la signification conceptuelle de `x:Subclass` n’est pas définie par une implémentation de Services XAML .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37cab-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET Framework XAML Services implementation.</span></span> <span data-ttu-id="37cab-125">Il s’agit, car le comportement des Services XAML .NET Framework ne spécifie pas le modèle de programmation général en XAML balisage et le code de stockage sont connectés.</span><span class="sxs-lookup"><span data-stu-id="37cab-125">This is because .NET Framework XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="37cab-126">Les implémentations de concepts supplémentaires liés à `x:Class` et `x:Subclass` sont effectuées par les infrastructures spécifiques qui utilisent des modèles de programmation ou des modèles d’application pour définir comment connecter le balisage XAML compilé de balisage et code-behind basé sur CLR.</span><span class="sxs-lookup"><span data-stu-id="37cab-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="37cab-127">Chacune de ces infrastructures peut avoir ses propres actions de génération qui activent une partie du comportement, ou des composants spécifiques qui doivent être inclus dans l’environnement de génération.</span><span class="sxs-lookup"><span data-stu-id="37cab-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="37cab-128">Dans une infrastructure, les actions de génération peuvent également varier selon le langage CLR spécifique qui est utilisé pour le code-behind.</span><span class="sxs-lookup"><span data-stu-id="37cab-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="37cab-129">Notes d’utilisation WPF</span><span class="sxs-lookup"><span data-stu-id="37cab-129">WPF Usage Notes</span></span>  
 <span data-ttu-id="37cab-130">`x:Subclass`peut être sur une racine de page ou le <xref:System.Windows.Application> racine dans la définition d’application, qui a déjà `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="37cab-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="37cab-131">Déclaration `x:Subclass` sur tout élément autre qu’une racine de page ou d’une application, ou sa spécification lorsqu’aucun `x:Class` existe, provoque une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="37cab-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>  
  
 <span data-ttu-id="37cab-132">Création de classes dérivées qui fonctionnent correctement pour le `x:Subclass` scénario est relativement complexe.</span><span class="sxs-lookup"><span data-stu-id="37cab-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="37cab-133">Vous devrez peut-être examiner les fichiers intermédiaires (les fichiers .g produits dans le dossier obj de votre projet par la compilation de balisage, avec des noms qui incorporent les noms de fichier .xaml).</span><span class="sxs-lookup"><span data-stu-id="37cab-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="37cab-134">Ces fichiers intermédiaires peuvent vous aider à déterminer l’origine de certaines constructions de programmation dans les classes partielles jointes dans l’application compilée.</span><span class="sxs-lookup"><span data-stu-id="37cab-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>  
  
 <span data-ttu-id="37cab-135">Gestionnaires d’événements dans la classe dérivée doivent être `internal override` (`Friend Overrides` dans [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) afin de substituer les stubs pour les gestionnaires créés dans la classe intermédiaire au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="37cab-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="37cab-136">Sinon, les implémentations de classe dérivée masqueront l’implémentation de la classe intermédiaire et les gestionnaires de classe intermédiaire ne sont pas appelés.</span><span class="sxs-lookup"><span data-stu-id="37cab-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>  
  
 <span data-ttu-id="37cab-137">Lorsque vous définissez `x:Class` et `x:Subclass`, vous n’avez pas besoin de fournir d’implémentation pour la classe qui est référencée par `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="37cab-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="37cab-138">Vous devez uniquement afin de lui donner un nom via le `x:Class` attribut afin que le compilateur dispose de quelques conseils pour la classe qu’il crée dans les fichiers intermédiaires (dans ce cas, le compilateur ne sélectionne pas de nom par défaut).</span><span class="sxs-lookup"><span data-stu-id="37cab-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="37cab-139">Vous pouvez donner le `x:Class` une implémentation de la classe ; Toutefois, cela n’est pas le scénario classique pour l’utilisation `x:Class` et `x:Subclass`.</span><span class="sxs-lookup"><span data-stu-id="37cab-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37cab-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37cab-140">See Also</span></span>  
 [<span data-ttu-id="37cab-141">x:Class, directive</span><span class="sxs-lookup"><span data-stu-id="37cab-141">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="37cab-142">XAML et classes personnalisées pour WPF</span><span class="sxs-lookup"><span data-stu-id="37cab-142">XAML and Custom Classes for WPF</span></span>](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
