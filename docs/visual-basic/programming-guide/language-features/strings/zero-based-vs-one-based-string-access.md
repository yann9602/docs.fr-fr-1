---
title: "Vs de base zéro. Accès d’une chaîne de base en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 911f063d6ca9a3f5d88a1f50d9df7f908a488f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="5efe5-102">Vs de base zéro. Accès d’une chaîne de base en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5efe5-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="5efe5-103">Cette rubrique compare comment [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] et [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] fournissent l’accès aux caractères dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5efe5-103">This topic compares how [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="5efe5-104">Le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] fournit toujours un accès de base zéro pour les caractères dans une chaîne, tandis que [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fournit un accès de base zéro et basé sur un, selon la fonction.</span><span class="sxs-lookup"><span data-stu-id="5efe5-104">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] always provides zero-based access to the characters in a string, whereas [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="5efe5-105">Basé sur un</span><span class="sxs-lookup"><span data-stu-id="5efe5-105">One-Based</span></span>  
 <span data-ttu-id="5efe5-106">Pour obtenir un exemple d’une base d’un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] , prenez le `Mid` (fonction).</span><span class="sxs-lookup"><span data-stu-id="5efe5-106">For an example of a one-based [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function, consider the `Mid` function.</span></span> <span data-ttu-id="5efe5-107">Il prend un argument qui indique la position de caractère à laquelle la sous-chaîne démarrera, en commençant à la position 1.</span><span class="sxs-lookup"><span data-stu-id="5efe5-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="5efe5-108">Le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> méthode prend un index du caractère dans la chaîne à laquelle la sous-chaîne doit démarrer, en commençant à la position 0.</span><span class="sxs-lookup"><span data-stu-id="5efe5-108">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="5efe5-109">Par conséquent, si vous avez une chaîne « ABCDE », les caractères sont numérotés 1,2,3,4,5 pour la `Mid` (fonction), mais 0,1,2,3,4 pour une utilisation avec le <xref:System.String.Substring%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="5efe5-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="5efe5-110">Base zéro</span><span class="sxs-lookup"><span data-stu-id="5efe5-110">Zero-Based</span></span>  
 <span data-ttu-id="5efe5-111">Pour obtenir un exemple de base zéro [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] , prenez le `Split` (fonction).</span><span class="sxs-lookup"><span data-stu-id="5efe5-111">For an example of a zero-based [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function, consider the `Split` function.</span></span> <span data-ttu-id="5efe5-112">Il fractionne une chaîne et retourne un tableau contenant les sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="5efe5-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="5efe5-113">Le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> méthode également fractionne une chaîne et retourne un tableau contenant les sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="5efe5-113">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="5efe5-114">Étant donné que la `Split` (fonction) et <xref:System.String.Split%2A> retour de la méthode [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tableaux, ils doivent être de base zéro.</span><span class="sxs-lookup"><span data-stu-id="5efe5-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5efe5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5efe5-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [<span data-ttu-id="5efe5-116">Introduction aux chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5efe5-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
