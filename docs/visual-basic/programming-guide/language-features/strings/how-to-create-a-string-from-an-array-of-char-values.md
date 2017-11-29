---
title: "Comment : créer une chaîne à partir d'un tableau de valeurs Char (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06e5c6923c26f3cb84b38475d6680523853d727d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="c3418-102">Comment : créer une chaîne à partir d'un tableau de valeurs Char (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3418-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="c3418-103">Cet exemple crée la chaîne « abcd » à partir de différents caractères.</span><span class="sxs-lookup"><span data-stu-id="c3418-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3418-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3418-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c3418-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="c3418-105">Compiling the Code</span></span>  
 <span data-ttu-id="c3418-106">Cette méthode n’a pas d’exigences particulières.</span><span class="sxs-lookup"><span data-stu-id="c3418-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="c3418-107">La syntaxe `"a"c`, où un seul `c` suit un caractère unique entre guillemets, est utilisé pour créer un caractère littéral.</span><span class="sxs-lookup"><span data-stu-id="c3418-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c3418-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="c3418-108">Robust Programming</span></span>  
 <span data-ttu-id="c3418-109">Les caractères null (équivalent à `Chr(0)`) dans la chaîne de produire des résultats inattendus lors de l’utilisation de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="c3418-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="c3418-110">Le caractère null sera inclus dans la chaîne, mais pas les caractères suivant le caractère null seront affichera dans certaines situations.</span><span class="sxs-lookup"><span data-stu-id="c3418-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3418-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3418-111">See Also</span></span>  
 <xref:System.String>  
 [<span data-ttu-id="c3418-112">Char (type de données)</span><span class="sxs-lookup"><span data-stu-id="c3418-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [<span data-ttu-id="c3418-113">Types de données</span><span class="sxs-lookup"><span data-stu-id="c3418-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
