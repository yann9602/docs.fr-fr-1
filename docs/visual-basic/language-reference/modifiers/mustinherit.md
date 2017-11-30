---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d384986e42ee69a0f425c1590599aa2c82bc856
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="9d905-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d905-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="9d905-103">Spécifie qu’une classe peut être utilisée uniquement comme classe de base et que vous ne pouvez pas créer un objet directement à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="9d905-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d905-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="9d905-104">Remarks</span></span>  
 <span data-ttu-id="9d905-105">L’objectif d’un *classe de base* (également appelé un *classe abstraite*) consiste à définir des fonctionnalités communes à toutes les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="9d905-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="9d905-106">Cela permet d’économiser les classes dérivées de devoir redéfinir les éléments communs.</span><span class="sxs-lookup"><span data-stu-id="9d905-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="9d905-107">Dans certains cas, cette fonctionnalité commune n’est pas suffisamment complète afin de rendre un objet utilisable, et chaque classe dérivée définit la fonctionnalité manquante.</span><span class="sxs-lookup"><span data-stu-id="9d905-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="9d905-108">Dans ce cas, vous souhaitez le code de consommation pour créer des objets qu’à partir de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="9d905-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="9d905-109">Vous utilisez `MustInherit` sur la classe de base pour appliquer ceci.</span><span class="sxs-lookup"><span data-stu-id="9d905-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="9d905-110">Une autre utilisation d’un `MustInherit` classe consiste à restreindre une variable à un ensemble de classes connexes.</span><span class="sxs-lookup"><span data-stu-id="9d905-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="9d905-111">Vous pouvez définir une classe de base et dérivent toutes ces classes connexes.</span><span class="sxs-lookup"><span data-stu-id="9d905-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="9d905-112">La classe de base ne devez pas fournir toutes les fonctionnalités communes à toutes les classes dérivées, mais il peut servir d’un filtre pour assigner des valeurs aux variables.</span><span class="sxs-lookup"><span data-stu-id="9d905-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="9d905-113">Si votre code de consommation déclare une variable comme classe de base, Visual Basic permet de vous permettent d’attribuer uniquement à un objet à partir d’une des classes dérivées à cette variable.</span><span class="sxs-lookup"><span data-stu-id="9d905-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="9d905-114">Le .NET Framework définit plusieurs `MustInherit` classes <xref:System.Array>, <xref:System.Enum>, et <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="9d905-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="9d905-115"><xref:System.ValueType>est un exemple de classe de base qui restreint une variable.</span><span class="sxs-lookup"><span data-stu-id="9d905-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="9d905-116">Tous les types valeur dérivent <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="9d905-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="9d905-117">Si vous déclarez une variable en tant que <xref:System.ValueType>, vous pouvez affecter uniquement des types valeur à cette variable.</span><span class="sxs-lookup"><span data-stu-id="9d905-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9d905-118">Règles</span><span class="sxs-lookup"><span data-stu-id="9d905-118">Rules</span></span>  
  
-   <span data-ttu-id="9d905-119">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="9d905-119">**Declaration Context.**</span></span> <span data-ttu-id="9d905-120">Vous pouvez utiliser `MustInherit` uniquement dans un `Class` instruction.</span><span class="sxs-lookup"><span data-stu-id="9d905-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
-   <span data-ttu-id="9d905-121">**Modificateurs combinés.**</span><span class="sxs-lookup"><span data-stu-id="9d905-121">**Combined Modifiers.**</span></span> <span data-ttu-id="9d905-122">Vous ne pouvez pas spécifier `MustInherit` avec `NotInheritable` dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="9d905-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d905-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="9d905-123">Example</span></span>  
 <span data-ttu-id="9d905-124">L’exemple suivant illustre l’héritage et la substitution forcés.</span><span class="sxs-lookup"><span data-stu-id="9d905-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="9d905-125">La classe de base `shape` définit une variable `acrossLine`.</span><span class="sxs-lookup"><span data-stu-id="9d905-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="9d905-126">Les classes `circle` et `square` dérivent `shape`.</span><span class="sxs-lookup"><span data-stu-id="9d905-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="9d905-127">Ils héritent de la définition de `acrossLine`, mais elles doivent définir la fonction `area` parce que ce calcul est différent pour chaque type de forme.</span><span class="sxs-lookup"><span data-stu-id="9d905-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 <span data-ttu-id="9d905-128">Vous pouvez déclarer `shape1` et `shape2` de type `shape`.</span><span class="sxs-lookup"><span data-stu-id="9d905-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="9d905-129">Toutefois, vous ne peut pas créer un objet à partir de `shape` , car il ne dispose pas de la fonctionnalité de la fonction `area` et est marqué comme `MustInherit`.</span><span class="sxs-lookup"><span data-stu-id="9d905-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="9d905-130">Puisqu’elles sont déclarées en tant que `shape`, les variables `shape1` et `shape2` sont restreintes aux objets des classes dérivées `circle` et `square`.</span><span class="sxs-lookup"><span data-stu-id="9d905-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="9d905-131">Visual Basic ne permet pas assigner de tout autre objet à ces variables, qui vous offre un niveau élevé de sécurité de type.</span><span class="sxs-lookup"><span data-stu-id="9d905-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="9d905-132">Utilisation</span><span class="sxs-lookup"><span data-stu-id="9d905-132">Usage</span></span>  
 <span data-ttu-id="9d905-133">Le `MustInherit` modificateur peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="9d905-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="9d905-134">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="9d905-134">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9d905-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d905-135">See Also</span></span>  
 [<span data-ttu-id="9d905-136">Inherits (instruction)</span><span class="sxs-lookup"><span data-stu-id="9d905-136">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="9d905-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="9d905-137">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [<span data-ttu-id="9d905-138">Mots clés</span><span class="sxs-lookup"><span data-stu-id="9d905-138">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="9d905-139">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="9d905-139">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
