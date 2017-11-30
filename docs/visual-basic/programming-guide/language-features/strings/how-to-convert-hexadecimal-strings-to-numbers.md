---
title: "Comment : convertir des chaînes hexadécimales en nombres (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6b1beae273fa737ca7c95a253d95c947e760f9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="a86e1-102">Comment : convertir des chaînes hexadécimales en nombres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a86e1-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="a86e1-103">Cet exemple convertit une chaîne hexadécimale à un entier à l’aide de la <xref:System.Convert.ToInt32%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="a86e1-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A> method.</span></span>  
  
### <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="a86e1-104">Pour convertir une chaîne hexadécimale en un nombre</span><span class="sxs-lookup"><span data-stu-id="a86e1-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="a86e1-105">Utilisez la <xref:System.Convert.ToInt32%2A> méthode pour convertir le nombre exprimé en base-16 en un entier.</span><span class="sxs-lookup"><span data-stu-id="a86e1-105">Use the <xref:System.Convert.ToInt32%2A> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="a86e1-106">Le premier argument de la <xref:System.Convert.ToInt32%2A> méthode est la chaîne à convertir.</span><span class="sxs-lookup"><span data-stu-id="a86e1-106">The first argument of the <xref:System.Convert.ToInt32%2A> method is the string to convert.</span></span> <span data-ttu-id="a86e1-107">Le deuxième argument décrit la base dans laquelle le nombre est exprimé ; hexadécimal est de base 16.</span><span class="sxs-lookup"><span data-stu-id="a86e1-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[VbVbalrStrings#62](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a86e1-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a86e1-108">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A>
