---
title: "Comment : convertir un objet en un autre type dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 053c93e7cf842138f5b9299cd2fcfa56342dd40b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="814e4-102">Comment : convertir un objet en un autre type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="814e4-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="814e4-103">Vous convertissez un `Object` variable à un autre type de données à l’aide d’un mot clé de conversion comme [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="814e4-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="814e4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="814e4-104">Example</span></span>  
 <span data-ttu-id="814e4-105">L’exemple suivant convertit un `Object` variable à un `Integer` et un `String`.</span><span class="sxs-lookup"><span data-stu-id="814e4-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="814e4-106">Si vous savez que le contenu d’un `Object` variable sont d’un type de données particulier, il est préférable de convertir la variable de ce type de données.</span><span class="sxs-lookup"><span data-stu-id="814e4-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="814e4-107">Si vous continuez à utiliser le `Object` variable, vous encourez soit *boxing* et *unboxing* (pour un type valeur) ou *liaison tardive* (pour un type de référence).</span><span class="sxs-lookup"><span data-stu-id="814e4-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="814e4-108">Ces opérations tous de prendre du temps d’exécution et ralentissent les performances.</span><span class="sxs-lookup"><span data-stu-id="814e4-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="814e4-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="814e4-109">Compiling the Code</span></span>  
 <span data-ttu-id="814e4-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="814e4-110">This example requires:</span></span>  
  
-   <span data-ttu-id="814e4-111">une référence à l'espace de noms <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="814e4-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="814e4-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="814e4-112">See Also</span></span>  
 <xref:System.Object>  
 [<span data-ttu-id="814e4-113">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="814e4-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="814e4-114">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="814e4-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="814e4-115">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="814e4-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="814e4-116">Conversion entre des chaînes et d’autres types</span><span class="sxs-lookup"><span data-stu-id="814e4-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="814e4-117">Conversions de tableau</span><span class="sxs-lookup"><span data-stu-id="814e4-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="814e4-118">Structures</span><span class="sxs-lookup"><span data-stu-id="814e4-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="814e4-119">Types de données</span><span class="sxs-lookup"><span data-stu-id="814e4-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="814e4-120">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="814e4-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
