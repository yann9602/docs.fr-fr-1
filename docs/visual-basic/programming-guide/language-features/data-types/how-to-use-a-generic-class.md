---
title: "Comment : utiliser une classe générique (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- type parameters, defining
- data type arguments, defining
- arguments [Visual Basic], data types
- Of keyword, using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters, type
- types [Visual Basic], generic
- parameters, generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters, data type
- data type parameters, defining
- type arguments, defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d6f5f941887dfc1f93221be1c184f0dcc2789352
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="a7f05-102">Comment : utiliser une classe générique (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7f05-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="a7f05-103">Une classe qui accepte des *paramètres de type* est appelée *classe générique*.</span><span class="sxs-lookup"><span data-stu-id="a7f05-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="a7f05-104">Si vous utilisez une classe générique, vous pouvez générer une *classe construite* à partir de celle-ci en fournissant un *argument de type* pour chacun de ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="a7f05-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="a7f05-105">Vous pouvez ensuite déclarer une variable du type classe construite, et vous pouvez créer une instance de la classe construite et l’assigner à cette variable.</span><span class="sxs-lookup"><span data-stu-id="a7f05-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="a7f05-106">En plus des classes, vous pouvez définir et utiliser des structures, interfaces, procédures et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="a7f05-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="a7f05-107">La procédure suivante prend une classe générique définie dans le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] et crée une instance à partir d’elle.</span><span class="sxs-lookup"><span data-stu-id="a7f05-107">The following procedure takes a generic class defined in the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="a7f05-108">Pour utiliser une classe qui prend un paramètre de type</span><span class="sxs-lookup"><span data-stu-id="a7f05-108">To use a class that takes a type parameter</span></span>  
  
1.  <span data-ttu-id="a7f05-109">Au début de votre fichier source, incluez un [Imports, instruction (.NET Namespace et Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour importer le <xref:System.Collections.Generic?displayProperty=fullName>espace de noms.</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a7f05-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="a7f05-110">Cela vous permet de faire référence à la <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>classe sans devoir qualifier pleinement pour la différencier des autres classes de file d’attente telles que <xref:System.Collections.Queue?displayProperty=fullName>.</xref:System.Collections.Queue?displayProperty=fullName> </xref:System.Collections.Generic.Queue%601?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a7f05-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=fullName> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=fullName>.</span></span>  
  
2.  <span data-ttu-id="a7f05-111">Créez l’objet de façon normale, mais ajoutez `(Of` `type``)` juste après le nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="a7f05-111">Create the object in the normal way, but add `(Of` `type``)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="a7f05-112">L’exemple suivant utilise la même classe (<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>) pour créer deux objets de file d’attente qui contiennent des éléments de différents types de données.</xref:System.Collections.Generic.Queue%601?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a7f05-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="a7f05-113">Il ajoute des éléments à la fin de chaque file d’attente, puis supprime et affiche les éléments du début de chaque file d’attente.</span><span class="sxs-lookup"><span data-stu-id="a7f05-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     <span data-ttu-id="a7f05-114">[!code-vb[VbVbalrDataTypes&#9;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7f05-114">[!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f05-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7f05-115">See Also</span></span>  
 <span data-ttu-id="a7f05-116">[Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="a7f05-116">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="a7f05-117"> [Types génériques dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="a7f05-117"> [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="a7f05-118"> [Indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) </span><span class="sxs-lookup"><span data-stu-id="a7f05-118"> [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) </span></span>  
<span data-ttu-id="a7f05-119"> [Of](../../../../visual-basic/language-reference/statements/of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="a7f05-119"> [Of](../../../../visual-basic/language-reference/statements/of-clause.md) </span></span>  
<span data-ttu-id="a7f05-120"> [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="a7f05-120"> [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="a7f05-121"> [Comment : définir une classe qui peut fournir des fonctionnalités identiques pour différents types de données](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="a7f05-121"> [How to: Define a Class That Can Provide Identical Functionality on Different Data Types](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md) </span></span>  
<span data-ttu-id="a7f05-122"> [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)</span><span class="sxs-lookup"><span data-stu-id="a7f05-122"> [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)</span></span>
