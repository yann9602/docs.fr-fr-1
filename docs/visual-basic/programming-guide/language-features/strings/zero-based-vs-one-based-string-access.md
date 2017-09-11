---
title: "Vs de base zéro. Accès d’une chaîne de base dans Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 11
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
ms.openlocfilehash: d8d1000f134fa8f99509d12727b9fbd84cb0e831
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="1c789-102">Vs de base zéro. Accès d’une chaîne de base dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c789-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="1c789-103">Cette rubrique compare comment [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] et [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] permettent d’accéder aux caractères dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="1c789-103">This topic compares how [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] and the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="1c789-104">Le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] fournit toujours un accès de base zéro aux caractères d’une chaîne, tandis que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit un accès de base zéro et basé sur un, selon la fonction.</span><span class="sxs-lookup"><span data-stu-id="1c789-104">The [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] always provides zero-based access to the characters in a string, whereas [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="1c789-105">Basé sur un</span><span class="sxs-lookup"><span data-stu-id="1c789-105">One-Based</span></span>  
 <span data-ttu-id="1c789-106">Pour obtenir un exemple d’une base [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] , prenez le `Mid` (fonction).</span><span class="sxs-lookup"><span data-stu-id="1c789-106">For an example of a one-based [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] function, consider the `Mid` function.</span></span> <span data-ttu-id="1c789-107">Elle accepte un argument qui indique la position de caractère à laquelle la sous-chaîne doit démarrer, commençant à la position 1.</span><span class="sxs-lookup"><span data-stu-id="1c789-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="1c789-108">Le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Substring%2A?displayProperty=fullName>méthode prend un index du caractère dans la chaîne où la sous-chaîne doit démarrer, en commençant à la position 0.</xref:System.String.Substring%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1c789-108">The [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Substring%2A?displayProperty=fullName> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="1c789-109">Par conséquent, si vous avez une chaîne « ABCDE », les caractères individuels sont numérotés 1,2,3,4,5 pour la `Mid` (fonction), mais 0,1,2,3,4 pour la <xref:System.String.Substring%2A?displayProperty=fullName>méthode.</xref:System.String.Substring%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1c789-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=fullName> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="1c789-110">Base zéro</span><span class="sxs-lookup"><span data-stu-id="1c789-110">Zero-Based</span></span>  
 <span data-ttu-id="1c789-111">Pour obtenir un exemple de base zéro [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] , prenez le `Split` (fonction).</span><span class="sxs-lookup"><span data-stu-id="1c789-111">For an example of a zero-based [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] function, consider the `Split` function.</span></span> <span data-ttu-id="1c789-112">Il fractionne une chaîne et retourne un tableau contenant les sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="1c789-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="1c789-113">Le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Split%2A?displayProperty=fullName>méthode également fractionne une chaîne et retourne un tableau contenant les sous-chaînes.</xref:System.String.Split%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1c789-113">The [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Split%2A?displayProperty=fullName> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="1c789-114">Étant donné que la `Split` (fonction) et <xref:System.String.Split%2A>retour de la méthode [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] tableaux, elles doivent être de base zéro.</xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="1c789-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c789-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c789-115">See Also</span></span>  
 <span data-ttu-id="1c789-116"><xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A></span><span class="sxs-lookup"><span data-stu-id="1c789-116"><xref:Microsoft.VisualBasic.Strings.Mid%2A></span></span>   
 <span data-ttu-id="1c789-117"><xref:Microsoft.VisualBasic.Strings.Split%2A></xref:Microsoft.VisualBasic.Strings.Split%2A></span><span class="sxs-lookup"><span data-stu-id="1c789-117"><xref:Microsoft.VisualBasic.Strings.Split%2A></span></span>   
 <span data-ttu-id="1c789-118"><xref:System.String.Substring%2A></xref:System.String.Substring%2A></span><span class="sxs-lookup"><span data-stu-id="1c789-118"><xref:System.String.Substring%2A></span></span>   
 <span data-ttu-id="1c789-119"><xref:System.String.Split%2A></xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="1c789-119"><xref:System.String.Split%2A></span></span>   
<span data-ttu-id="1c789-120"> [Introduction aux chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span><span class="sxs-lookup"><span data-stu-id="1c789-120"> [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span></span>
