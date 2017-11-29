---
title: "Comment : déterminer si deux objets sont liés (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7824742459fca355c0043ad8ed20a26330402c05
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="c86b8-102">Comment : déterminer si deux objets sont liés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c86b8-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>
<span data-ttu-id="c86b8-103">Vous pouvez comparer deux objets pour déterminer la relation, le cas échéant, entre les classes à partir de laquelle ils sont créés.</span><span class="sxs-lookup"><span data-stu-id="c86b8-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="c86b8-104">Le <xref:System.Type.IsInstanceOfType%2A> méthode de la <xref:System.Type?displayProperty=nameWithType> classe retourne `True` si la classe actuelle hérite de la classe spécifiée, ou si le type actuel est une interface prise en charge par la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c86b8-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="c86b8-105">Pour déterminer si un objet hérite de la classe ou une interface d’un autre objet</span><span class="sxs-lookup"><span data-stu-id="c86b8-105">To determine if one object inherits from another object's class or interface</span></span>  
  
1.  <span data-ttu-id="c86b8-106">Sur l’objet que vous pensez peut être du type de base, appellent la <xref:System.Object.GetType%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="c86b8-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>  
  
2.  <span data-ttu-id="c86b8-107">Sur le <xref:System.Type?displayProperty=nameWithType> objet retourné par <xref:System.Object.GetType%2A>, appelez le <xref:System.Type.IsInstanceOfType%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="c86b8-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
3.  <span data-ttu-id="c86b8-108">Dans la liste d’arguments <xref:System.Type.IsInstanceOfType%2A>, spécifiez l’objet que vous pensez être du type dérivé.</span><span class="sxs-lookup"><span data-stu-id="c86b8-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>  
  
     <span data-ttu-id="c86b8-109"><xref:System.Type.IsInstanceOfType%2A>Retourne `True` si son type d’argument hérite le <xref:System.Type?displayProperty=nameWithType> type d’objet.</span><span class="sxs-lookup"><span data-stu-id="c86b8-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c86b8-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="c86b8-110">Example</span></span>  
 <span data-ttu-id="c86b8-111">L’exemple suivant détermine si un objet représente une classe dérivée de la classe d’un autre objet.</span><span class="sxs-lookup"><span data-stu-id="c86b8-111">The following example determines whether one object represents a class derived from another object's class.</span></span>  
  
```  
Public Class baseClass  
End Class  
Public Class derivedClass : Inherits baseClass  
End Class  
Public Class testTheseClasses  
    Public Sub seeIfRelated()  
        Dim baseObj As Object = New baseClass()  
        Dim derivedObj As Object = New derivedClass()  
        Dim related As Boolean  
        related = baseObj.GetType().IsInstanceOfType(derivedObj)  
        MsgBox(CStr(related))  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="c86b8-112">Notez l’emplacement inattendu des deux variables objets dans l’appel à <xref:System.Type.IsInstanceOfType%2A>.</span><span class="sxs-lookup"><span data-stu-id="c86b8-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="c86b8-113">Le type de base supposé est utilisé pour générer le <xref:System.Type?displayProperty=nameWithType> classe et le type dérivé supposé est passée comme argument à la <xref:System.Type.IsInstanceOfType%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="c86b8-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c86b8-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c86b8-114">See Also</span></span>  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.IsInstanceOfType%2A>  
 [<span data-ttu-id="c86b8-115">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="c86b8-115">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="c86b8-116">Variables objets</span><span class="sxs-lookup"><span data-stu-id="c86b8-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="c86b8-117">Valeurs des variables objets</span><span class="sxs-lookup"><span data-stu-id="c86b8-117">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="c86b8-118">Guide pratique : déterminer si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="c86b8-118">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
