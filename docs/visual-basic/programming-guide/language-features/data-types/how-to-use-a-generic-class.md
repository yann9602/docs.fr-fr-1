---
title: "Comment : utiliser une classe générique (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76383ae886a5e965c0daefc281c4842a4e563ec7
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="933d3-102">Comment : utiliser une classe générique (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="933d3-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="933d3-103">Une classe qui accepte des *paramètres de type* est appelée *classe générique*.</span><span class="sxs-lookup"><span data-stu-id="933d3-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="933d3-104">Si vous utilisez une classe générique, vous pouvez générer une *classe construite* à partir de celle-ci en fournissant un *argument de type* pour chacun de ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="933d3-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="933d3-105">Vous pouvez ensuite déclarer une variable du type classe construite, et vous pouvez créer une instance de la classe construite et l’assigner à cette variable.</span><span class="sxs-lookup"><span data-stu-id="933d3-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="933d3-106">En plus des classes, vous pouvez définir et utiliser des structures, interfaces, procédures et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="933d3-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="933d3-107">La procédure suivante prend une classe générique définie dans le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] et crée une instance à partir d’elle.</span><span class="sxs-lookup"><span data-stu-id="933d3-107">The following procedure takes a generic class defined in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="933d3-108">Pour utiliser une classe qui prend un paramètre de type</span><span class="sxs-lookup"><span data-stu-id="933d3-108">To use a class that takes a type parameter</span></span>  
  
1.  <span data-ttu-id="933d3-109">Au début de votre fichier source, incluez un [Imports, instruction (.NET Namespace et Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour importer le <xref:System.Collections.Generic?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="933d3-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="933d3-110">Cela vous permet de faire référence à la classe <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> sans avoir à la qualifier pleinement pour la différencier des autres classes de file d’attente, telles que <xref:System.Collections.Queue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="933d3-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2.  <span data-ttu-id="933d3-111">Créez l’objet de façon normale, mais ajoutez `(Of` `type``)` juste après le nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="933d3-111">Create the object in the normal way, but add `(Of` `type``)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="933d3-112">L’exemple suivant utilise la même classe (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) pour créer deux objets de file d’attente qui contiennent des éléments de différents types de données.</span><span class="sxs-lookup"><span data-stu-id="933d3-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="933d3-113">Il ajoute des éléments à la fin de chaque file d’attente, puis supprime et affiche les éléments du début de chaque file d’attente.</span><span class="sxs-lookup"><span data-stu-id="933d3-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="933d3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="933d3-114">See Also</span></span>  
 [<span data-ttu-id="933d3-115">Types de données</span><span class="sxs-lookup"><span data-stu-id="933d3-115">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="933d3-116">Types génériques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="933d3-116">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="933d3-117">Indépendance du langage et composants indépendants du langage</span><span class="sxs-lookup"><span data-stu-id="933d3-117">Language Independence and Language-Independent Components</span></span>](../../../../../docs/standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="933d3-118">Of</span><span class="sxs-lookup"><span data-stu-id="933d3-118">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="933d3-119">Imports (instruction) (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="933d3-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="933d3-120">Guide pratique : définir une classe qui fournisse des fonctionnalités identiques pour différents types de données</span><span class="sxs-lookup"><span data-stu-id="933d3-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="933d3-121">Itérateurs</span><span class="sxs-lookup"><span data-stu-id="933d3-121">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
