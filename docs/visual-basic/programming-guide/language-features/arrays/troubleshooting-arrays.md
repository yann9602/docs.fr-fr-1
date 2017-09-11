---
title: "Dépannage des tableaux (Visual Basic) | Documents Microsoft"
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
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: 17
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
ms.openlocfilehash: 571731ae7066ba7ec52d4a2413b4d948f3f35bfe
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="0fc3c-102">Dépannage des tableaux (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fc3c-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="0fc3c-103">Cette page répertorie quelques problèmes courants qui peuvent se produire lorsque vous travaillez avec des tableaux.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="0fc3c-104">Erreurs de compilation déclarer et initialiser un tableau</span><span class="sxs-lookup"><span data-stu-id="0fc3c-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="0fc3c-105">Erreurs de compilation peuvent survenir à une mauvaise compréhension des règles de déclaration, la création et initialisation des tableaux.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="0fc3c-106">Les causes les plus courantes d’erreurs sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="0fc3c-106">The most common causes of errors are the following:</span></span>  
  
-   <span data-ttu-id="0fc3c-107">En fournissant un [nouveau opérateur](../../../../visual-basic/language-reference/operators/new-operator.md) clause après avoir spécifié les longueurs de dimensions dans la déclaration de variable tableau.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-107">Supplying a [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="0fc3c-108">Les lignes de code suivantes affichent des déclarations non valides de ce type.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   <span data-ttu-id="0fc3c-109">Spécification des longueurs de dimensions plus longtemps que le tableau de niveau supérieur d’un tableau en escalier.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="0fc3c-110">La ligne de code suivant montre une déclaration non valide de ce type.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   <span data-ttu-id="0fc3c-111">En omettant le `New` mot clé lorsque vous spécifiez les valeurs d’élément.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="0fc3c-112">La ligne de code suivant montre une déclaration non valide de ce type.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   <span data-ttu-id="0fc3c-113">En fournissant un `New` clause sans accolades (`{}`).</span><span class="sxs-lookup"><span data-stu-id="0fc3c-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="0fc3c-114">Les lignes de code suivantes affichent des déclarations non valides de ce type.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="0fc3c-115">Accès à un tableau hors limites</span><span class="sxs-lookup"><span data-stu-id="0fc3c-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="0fc3c-116">Le processus d’initialisation d’un tableau assigne une limite supérieure et inférieure à chaque dimension.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="0fc3c-117">Chaque accès à un élément du tableau doit spécifier un index valide ou un indice, pour chaque dimension.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="0fc3c-118">Si un index est inférieure à sa limite inférieure ou supérieure sa limite supérieure, une <xref:System.IndexOutOfRangeException>résultats de l’exception.</xref:System.IndexOutOfRangeException></span><span class="sxs-lookup"><span data-stu-id="0fc3c-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="0fc3c-119">Le compilateur ne peut pas détecter une telle erreur, donc une erreur se produit au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="0fc3c-120">Détermination des limites</span><span class="sxs-lookup"><span data-stu-id="0fc3c-120">Determining Bounds</span></span>  
 <span data-ttu-id="0fc3c-121">Si un autre composant passe un tableau à votre code, par exemple en tant qu’argument de procédure, vous ne connaissez pas la taille de ce tableau ni les longueurs de ses dimensions.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="0fc3c-122">Vous devez toujours déterminer la limite supérieure de chaque dimension d’un tableau avant de tenter d’accéder aux éléments.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="0fc3c-123">Si le tableau a été créé par un moyen autre qu’un [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `New` clause, la limite inférieure peut avoir une valeur différente de 0, et il est plus sûre pour déterminer cette limite inférieure.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-123">If the array has been created by some means other than a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="0fc3c-124">Spécification de la Dimension</span><span class="sxs-lookup"><span data-stu-id="0fc3c-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="0fc3c-125">Pour déterminer les limites d’un tableau multidimensionnel, veillez à vous spécifiez comment la dimension.</span><span class="sxs-lookup"><span data-stu-id="0fc3c-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="0fc3c-126">Le `dimension` paramètres de le <xref:System.Array.GetLowerBound%2A>et <xref:System.Array.GetUpperBound%2A>méthodes sont basées sur 0 lors de la `Rank` paramètres de le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A>et <xref:Microsoft.VisualBasic.Information.UBound%2A>fonctions sont de base 1.</xref:Microsoft.VisualBasic.Information.UBound%2A> </xref:Microsoft.VisualBasic.Information.LBound%2A> </xref:System.Array.GetUpperBound%2A> </xref:System.Array.GetLowerBound%2A></span><span class="sxs-lookup"><span data-stu-id="0fc3c-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc3c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fc3c-127">See Also</span></span>  
 <span data-ttu-id="0fc3c-128">[Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="0fc3c-128">[Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
<span data-ttu-id="0fc3c-129"> [Comment : initialiser une Variable tableau en Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span><span class="sxs-lookup"><span data-stu-id="0fc3c-129"> [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span></span>
