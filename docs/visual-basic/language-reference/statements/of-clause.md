---
title: Of, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ef3ac4ac88727b1dcae50fa14abde03f29a16fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="e0c9e-102">Of, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0c9e-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="e0c9e-103">Introduit un `Of` clause qui identifie un *le paramètre de type* sur un *générique* classe, structure, interface, délégué ou procédure.</span><span class="sxs-lookup"><span data-stu-id="e0c9e-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="e0c9e-104">Pour plus d’informations sur les types génériques, consultez [des Types génériques en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="e0c9e-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="e0c9e-105">À l’aide du mot clé</span><span class="sxs-lookup"><span data-stu-id="e0c9e-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="e0c9e-106">Le code suivant exemple utilise le `Of` mot clé pour définir le contour d’une classe qui prend deux paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="e0c9e-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="e0c9e-107">Il *contraint* le `keyType` paramètre par le <xref:System.IComparable> interface, ce qui signifie que le code utilisateur doit fournir un argument de type qui implémente <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="e0c9e-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="e0c9e-108">Cela est nécessaire afin que les `add` procédure peut appeler le <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="e0c9e-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e0c9e-109">Pour plus d’informations sur les contraintes, consultez [Type liste](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="e0c9e-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 <span data-ttu-id="e0c9e-110">Si vous terminez la définition de classe précédente, vous pouvez construire une variété de `dictionary` classes à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="e0c9e-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="e0c9e-111">Les types que vous fournissez à `entryType` et `keyType` déterminer quel type d’entrée de la classe contient et le type de clé associe à chaque entrée.</span><span class="sxs-lookup"><span data-stu-id="e0c9e-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="e0c9e-112">En raison de la contrainte, vous devez fournir au `keyType` un type qui implémente <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="e0c9e-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="e0c9e-113">L’exemple de code suivant crée un objet qui contient `String` entrées et associe un `Integer` clé avec chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="e0c9e-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="e0c9e-114">`Integer`implémente <xref:System.IComparable> et par conséquent satisfait la contrainte sur `keyType`.</span><span class="sxs-lookup"><span data-stu-id="e0c9e-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="e0c9e-115">Le mot clé `Of` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="e0c9e-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e0c9e-116">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="e0c9e-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="e0c9e-117">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="e0c9e-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="e0c9e-118">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="e0c9e-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="e0c9e-119">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="e0c9e-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="e0c9e-120">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="e0c9e-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="e0c9e-121">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="e0c9e-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e0c9e-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0c9e-122">See Also</span></span>  
 <xref:System.IComparable>  
 [<span data-ttu-id="e0c9e-123">Liste de types</span><span class="sxs-lookup"><span data-stu-id="e0c9e-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="e0c9e-124">Types génériques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e0c9e-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="e0c9e-125">In</span><span class="sxs-lookup"><span data-stu-id="e0c9e-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [<span data-ttu-id="e0c9e-126">Out</span><span class="sxs-lookup"><span data-stu-id="e0c9e-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
