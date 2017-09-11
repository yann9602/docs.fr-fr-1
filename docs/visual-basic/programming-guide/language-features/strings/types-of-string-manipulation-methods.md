---
title: "Types de méthodes de Manipulation de chaînes en Visual Basic | Documents Microsoft"
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
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: 12
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
ms.openlocfilehash: 9c63ad0931ae2f3760576a792795b9fe0ab6a409
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="ad50a-102">Types de méthodes de manipulation de chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad50a-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="ad50a-103">Il existe différentes méthodes pour analyser et manipuler des chaînes.</span><span class="sxs-lookup"><span data-stu-id="ad50a-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="ad50a-104">Certaines méthodes font partie de la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] langage et autres sont inhérentes à la `String` classe.</span><span class="sxs-lookup"><span data-stu-id="ad50a-104">Some of the methods are a part of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="ad50a-105">Langage Visual Basic et le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad50a-105">Visual Basic Language and the .NET Framework</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="ad50a-106">méthodes sont utilisées en tant que fonctions inhérentes du langage.</span><span class="sxs-lookup"><span data-stu-id="ad50a-106"> methods are used as inherent functions of the language.</span></span> <span data-ttu-id="ad50a-107">Ils peuvent être utilisés sans qualification dans votre code.</span><span class="sxs-lookup"><span data-stu-id="ad50a-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="ad50a-108">L’exemple suivant illustre une utilisation classique d’un [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] commande de manipulation de chaîne :</span><span class="sxs-lookup"><span data-stu-id="ad50a-108">The following example shows typical use of a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] string-manipulation command:</span></span>  
  
 <span data-ttu-id="ad50a-109">[!code-vb[VbVbalrStrings&#44;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ad50a-109">[!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]</span></span>  
  
 <span data-ttu-id="ad50a-110">Dans cet exemple, le `Mid` fonction effectue une opération directe sur `aString` et affecte la valeur à `bString`.</span><span class="sxs-lookup"><span data-stu-id="ad50a-110">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="ad50a-111">Pour obtenir la liste des méthodes de manipulation de chaîne Visual Basic, consultez [liste des manipulations de chaîne](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="ad50a-111">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="ad50a-112">Méthodes partagées et des méthodes d’Instance</span><span class="sxs-lookup"><span data-stu-id="ad50a-112">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="ad50a-113">Vous pouvez également manipuler des chaînes avec les méthodes de la `String` classe.</span><span class="sxs-lookup"><span data-stu-id="ad50a-113">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="ad50a-114">Il existe deux types de méthodes de `String`: *partagé* méthodes et *instance* méthodes.</span><span class="sxs-lookup"><span data-stu-id="ad50a-114">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="ad50a-115">Méthodes partagées</span><span class="sxs-lookup"><span data-stu-id="ad50a-115">Shared Methods</span></span>  
 <span data-ttu-id="ad50a-116">Une méthode partagée est une méthode qui provient de la `String` classe elle-même et ne nécessitent pas une instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="ad50a-116">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="ad50a-117">Ces méthodes peuvent être désignées par le nom de la classe (`String`) plutôt qu’avec une instance de la `String` classe.</span><span class="sxs-lookup"><span data-stu-id="ad50a-117">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="ad50a-118">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ad50a-118">For example:</span></span>  
  
 <span data-ttu-id="ad50a-119">[!code-vb[VbVbalrStrings n °&45;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ad50a-119">[!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]</span></span>  
  
 <span data-ttu-id="ad50a-120">Dans l’exemple précédent, la <xref:System.String.Copy%2A?displayProperty=fullName>méthode est une méthode statique, qui agit sur une expression qui lui est attribuée et assigne le résultat à `bString`.</xref:System.String.Copy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ad50a-120">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=fullName> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="ad50a-121">Méthodes d’instance</span><span class="sxs-lookup"><span data-stu-id="ad50a-121">Instance Methods</span></span>  
 <span data-ttu-id="ad50a-122">Les méthodes d’instance, en revanche, proviennent d’une instance particulière de `String` et doivent être qualifiés avec le nom d’instance.</span><span class="sxs-lookup"><span data-stu-id="ad50a-122">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="ad50a-123">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ad50a-123">For example:</span></span>  
  
 <span data-ttu-id="ad50a-124">[!code-vb[VbVbalrStrings&#46;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="ad50a-124">[!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]</span></span>  
  
 <span data-ttu-id="ad50a-125">Dans cet exemple, le <xref:System.String.Substring%2A?displayProperty=fullName>méthode est une méthode de l’instance de `String` (c'est-à-dire, `aString`).</xref:System.String.Substring%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ad50a-125">In this example, the <xref:System.String.Substring%2A?displayProperty=fullName> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="ad50a-126">Elle effectue une opération sur `aString` et assigne la valeur à `bString`.</span><span class="sxs-lookup"><span data-stu-id="ad50a-126">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="ad50a-127">Pour plus d’informations, consultez la documentation de la <xref:System.String>classe.</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ad50a-127">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad50a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad50a-128">See Also</span></span>  
 [<span data-ttu-id="ad50a-129">Introduction aux chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad50a-129">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
