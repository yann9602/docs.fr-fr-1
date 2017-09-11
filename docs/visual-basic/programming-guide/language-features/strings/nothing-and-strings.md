---
title: "Nothing et les chaînes en Visual Basic | Documents Microsoft"
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
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2d7685c688e96b506cfc2ddddc44ce534625e3b7
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="25196-102">Nothing et les chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25196-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="25196-103">Le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] runtime et le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] évaluer `Nothing` différemment lorsqu’il s’agit de chaînes.</span><span class="sxs-lookup"><span data-stu-id="25196-103">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] runtime and the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="25196-104">Runtime Visual Basic et le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="25196-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="25196-105">Prenons l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="25196-105">Consider the following example:</span></span>  
  
 <span data-ttu-id="25196-106">[!code-vb[VbVbalrStrings&#47;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="25196-106">[!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]</span></span>  
  
 <span data-ttu-id="25196-107">Le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] runtime prend généralement la valeur `Nothing` comme une chaîne vide (« »).</span><span class="sxs-lookup"><span data-stu-id="25196-107">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="25196-108">Le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] ne supprime pas, toutefois et lève une exception lorsqu’une tentative est faite pour effectuer une opération de chaîne sur `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="25196-108">The [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25196-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25196-109">See Also</span></span>  
 [<span data-ttu-id="25196-110">Introduction aux chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25196-110">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
