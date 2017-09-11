---
title: "Guide pratique pour modifier du contenu de chaîne (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], modifying
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 114b6fdabd235d7e57947e77b672352e28aff11e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-modify-string-contents-c-programming-guide"></a><span data-ttu-id="2932f-102">Guide pratique pour modifier du contenu de chaîne (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2932f-102">How to: Modify String Contents (C# Programming Guide)</span></span>
<span data-ttu-id="2932f-103">Étant donné que les chaînes sont *immuables*, il n’est pas possible (sans utiliser du code unsafe) de modifier la valeur d’un objet string après sa création.</span><span class="sxs-lookup"><span data-stu-id="2932f-103">Because strings are *immutable*, it is not possible (without using unsafe code) to modify the value of a string object after it has been created.</span></span> <span data-ttu-id="2932f-104">Toutefois, il existe de nombreuses façons de modifier la valeur d’une chaîne et de stocker le résultat dans un nouvel objet string.</span><span class="sxs-lookup"><span data-stu-id="2932f-104">However, there are many ways to modify the value of a string and store the result in a new string object.</span></span> <span data-ttu-id="2932f-105">La classe <xref:System.String?displayProperty=fullName> fournit des méthodes qui fonctionnent sur une chaîne d’entrée et retournent un nouvel objet string.</span><span class="sxs-lookup"><span data-stu-id="2932f-105">The <xref:System.String?displayProperty=fullName> class provides methods that operate on an input string and return a new string object.</span></span> <span data-ttu-id="2932f-106">Dans de nombreux cas, vous pouvez affecter le nouvel objet à la variable qui contenait la chaîne d’origine.</span><span class="sxs-lookup"><span data-stu-id="2932f-106">In many cases, you can assign the new object to the variable that held the original string.</span></span> <span data-ttu-id="2932f-107">La classe <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> fournit des méthodes supplémentaires qui fonctionnent d’une manière similaire.</span><span class="sxs-lookup"><span data-stu-id="2932f-107">The <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> class provides additional methods that work in a similar manner.</span></span> <span data-ttu-id="2932f-108">La classe <xref:System.Text.StringBuilder?displayProperty=fullName> fournit une mémoire tampon de caractères que vous pouvez modifier « sur place ».</span><span class="sxs-lookup"><span data-stu-id="2932f-108">The <xref:System.Text.StringBuilder?displayProperty=fullName> class provides a character buffer that you can modify "in-place."</span></span> <span data-ttu-id="2932f-109">Vous appelez la méthode <xref:System.Text.StringBuilder.ToString%2A?displayProperty=fullName> pour créer un objet string qui contient le contenu actuel de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="2932f-109">You call the <xref:System.Text.StringBuilder.ToString%2A?displayProperty=fullName> method to create a new string object that contains the current contents of the buffer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2932f-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="2932f-110">Example</span></span>  
 <span data-ttu-id="2932f-111">L’exemple suivant indique différentes façons de remplacer ou de supprimer des sous-chaînes dans une chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2932f-111">The following example shows various ways to replace or remove substrings in a specified string.</span></span>  
  
 <span data-ttu-id="2932f-112">[!code-cs[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2932f-112">[!code-cs[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="2932f-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="2932f-113">Example</span></span>  
 <span data-ttu-id="2932f-114">Pour accéder aux caractères individuels d’une chaîne en utilisant la notation de tableau, vous pouvez utiliser l’objet <xref:System.Text.StringBuilder>, qui surcharge l’opérateur `[]` pour permettre d’accéder à sa mémoire tampon de caractères interne.</span><span class="sxs-lookup"><span data-stu-id="2932f-114">To access the individual characters in a string by using array notation, you can use the <xref:System.Text.StringBuilder> object, which overloads the `[]` operator to provide access to its internal character buffer.</span></span> <span data-ttu-id="2932f-115">Vous pouvez également convertir la chaîne en un tableau de caractères en utilisant la méthode <xref:System.String.ToCharArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="2932f-115">You can also convert the string to an array of chars by using the <xref:System.String.ToCharArray%2A> method.</span></span> <span data-ttu-id="2932f-116">L’exemple suivant utilise `ToCharArray` pour créer le tableau.</span><span class="sxs-lookup"><span data-stu-id="2932f-116">The following example uses `ToCharArray` to create the array.</span></span> <span data-ttu-id="2932f-117">Certains éléments de ce tableau sont ensuite modifiés.</span><span class="sxs-lookup"><span data-stu-id="2932f-117">Some elements of this array are then modified.</span></span> <span data-ttu-id="2932f-118">Un constructeur String prenant un tableau de caractères comme paramètres d’entrée est ensuite appelé pour créer une chaîne.</span><span class="sxs-lookup"><span data-stu-id="2932f-118">A string constructor that takes a char array as an input parameter is then called to create a new string.</span></span>  
  
 <span data-ttu-id="2932f-119">[!code-cs[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2932f-119">[!code-cs[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="2932f-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="2932f-120">Example</span></span>  
 <span data-ttu-id="2932f-121">L’exemple suivant est fourni pour les très rares cas où vous voulez modifier une chaîne sur place en utilisant du code unsafe, en procédant d’une façon similaire aux tableaux de caractères de style C.</span><span class="sxs-lookup"><span data-stu-id="2932f-121">The following example is provided for those very rare situations in which you may want to modify a string in-place by using unsafe code in a manner similar to C-style char arrays.</span></span> <span data-ttu-id="2932f-122">Il indique comment accéder aux différents caractères « sur place » en utilisant le mot clé fixed.</span><span class="sxs-lookup"><span data-stu-id="2932f-122">The example shows how to access the individual characters "in-place" by using the fixed keyword.</span></span> <span data-ttu-id="2932f-123">Il montre également un effet secondaire possible des opérations risquées effectuées sur les chaînes, lié à la façon dont le compilateur C# stocke (intègre) les chaînes en interne.</span><span class="sxs-lookup"><span data-stu-id="2932f-123">It also demonstrates one possible side effect of unsafe operations on strings that results from the way that the C# compiler stores (interns) strings internally.</span></span> <span data-ttu-id="2932f-124">En général, il est préférable de ne pas utiliser cette technique, sauf en cas d’absolue nécessité.</span><span class="sxs-lookup"><span data-stu-id="2932f-124">In general, you should not use this technique unless it is absolutely necessary.</span></span>  
  
 <span data-ttu-id="2932f-125">[!code-cs[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="2932f-125">[!code-cs[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2932f-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2932f-126">See Also</span></span>  
 <span data-ttu-id="2932f-127">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2932f-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="2932f-128">Chaînes</span><span class="sxs-lookup"><span data-stu-id="2932f-128">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

