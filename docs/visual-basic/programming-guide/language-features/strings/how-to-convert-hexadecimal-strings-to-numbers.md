---
title: "Comment : convertir des chaînes hexadécimales en nombres (Visual Basic)"
ms.custom: 
ms.date: 01/31/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
author: petrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: c35ac615e3f87710f934a1cf66e6546625298bd0
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="c55b4-102">Comment : convertir des chaînes hexadécimales en nombres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c55b4-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="c55b4-103">Cet exemple convertit une chaîne hexadécimale à un entier à l’aide de la <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="c55b4-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="c55b4-104">Pour convertir une chaîne hexadécimale en un nombre</span><span class="sxs-lookup"><span data-stu-id="c55b4-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="c55b4-105">Utilisez la <xref:System.Convert.ToInt32(System.String,System.Int32)> méthode pour convertir le nombre exprimé en base-16 en un entier.</span><span class="sxs-lookup"><span data-stu-id="c55b4-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="c55b4-106">Le premier argument de la <xref:System.Convert.ToInt32(System.String,System.Int32)> méthode est la chaîne à convertir.</span><span class="sxs-lookup"><span data-stu-id="c55b4-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="c55b4-107">Le deuxième argument décrit la base dans laquelle le nombre est exprimé ; hexadécimal est de base 16.</span><span class="sxs-lookup"><span data-stu-id="c55b4-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- <span data-ttu-id="c55b4-108">Notez que la chaîne hexadécimale présente les restrictions suivantes :</span><span class="sxs-lookup"><span data-stu-id="c55b4-108">Note that the hexadecimal string has the following restrictions:</span></span>

   - <span data-ttu-id="c55b4-109">Il ne peut pas inclure le `&h` préfixe.</span><span class="sxs-lookup"><span data-stu-id="c55b4-109">It cannot include the `&h` prefix.</span></span>
   - <span data-ttu-id="c55b4-110">Il ne peut pas inclure le `_` séparateur numérique.</span><span class="sxs-lookup"><span data-stu-id="c55b4-110">It cannot include the `_` digit separator.</span></span>

   <span data-ttu-id="c55b4-111">Si le préfixe ou un séparateur numérique est présente, l’appel à la <xref:System.Convert.ToInt32(System.String,System.Int32)> méthode lève une exception un <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="c55b4-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c55b4-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c55b4-112">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
