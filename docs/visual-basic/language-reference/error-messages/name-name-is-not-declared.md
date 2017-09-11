---
title: "Nom de «&lt;nom&gt;&quot; n’est pas déclaré | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
dev_langs:
- VB
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
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
ms.openlocfilehash: 1396f24a34a37db064e73d7e259c04050f409ad2
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="name-39ltnamegt39-is-not-declared"></a><span data-ttu-id="3404e-102">Nom de «&lt;nom&gt;' n’est pas déclaré</span><span class="sxs-lookup"><span data-stu-id="3404e-102">Name &#39;&lt;name&gt;&#39; is not declared</span></span>
<span data-ttu-id="3404e-103">Une instruction fait référence à un élément de programmation, mais le compilateur ne peut pas trouver un élément portant ce nom exact.</span><span class="sxs-lookup"><span data-stu-id="3404e-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="3404e-104">**ID d’erreur :** BC30451</span><span class="sxs-lookup"><span data-stu-id="3404e-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3404e-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="3404e-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="3404e-106">Vérifiez l’orthographe du nom dans l’instruction de référence.</span><span class="sxs-lookup"><span data-stu-id="3404e-106">Check the spelling of the name in the referring statement.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="3404e-107">respecte la casse, mais toute autre variation dans l’orthographe est considérée comme un nom complètement différent.</span><span class="sxs-lookup"><span data-stu-id="3404e-107"> is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="3404e-108">Notez que le caractère de soulignement (`_`) fait partie du nom et donc de l’orthographe.</span><span class="sxs-lookup"><span data-stu-id="3404e-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2.  <span data-ttu-id="3404e-109">Vérifiez que vous disposez de l’opérateur d’accès aux membres (`.`) entre un objet et son membre.</span><span class="sxs-lookup"><span data-stu-id="3404e-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="3404e-110">Par exemple, si vous avez un <xref:System.Windows.Forms.TextBox>contrôle nommé `TextBox1`, pour accéder à ses <xref:System.Windows.Forms.TextBoxBase.Text%2A>propriété, vous devez taper `TextBox1.Text`.</xref:System.Windows.Forms.TextBoxBase.Text%2A> </xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="3404e-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="3404e-111">Si, au lieu de cela, vous tapez `TextBox1Text`, vous créez un nom différent.</span><span class="sxs-lookup"><span data-stu-id="3404e-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3.  <span data-ttu-id="3404e-112">Si l’orthographe est correcte et que la syntaxe n’importe quel objet d’accès de membre est correcte, vérifiez que l’élément a été déclaré.</span><span class="sxs-lookup"><span data-stu-id="3404e-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="3404e-113">Pour plus d’informations, consultez [éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="3404e-113">For more information, see [Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4.  <span data-ttu-id="3404e-114">Si l’élément de programmation a été déclaré, vérifiez qu’il est dans la portée.</span><span class="sxs-lookup"><span data-stu-id="3404e-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="3404e-115">Si l’instruction de référence est en dehors de la région qui déclare l’élément de programmation, vous devrez peut-être qualifier le nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="3404e-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="3404e-116">Pour plus d’informations, consultez [portée dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="3404e-116">For more information, see [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3404e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3404e-117">See Also</span></span>  
 <span data-ttu-id="3404e-118">[Liste des déclarations et des constantes](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md) </span><span class="sxs-lookup"><span data-stu-id="3404e-118">[Declarations and Constants Summary](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md) </span></span>  
<span data-ttu-id="3404e-119"> [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="3404e-119"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span></span>  
<span data-ttu-id="3404e-120"> [Noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="3404e-120"> [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="3404e-121"> [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span><span class="sxs-lookup"><span data-stu-id="3404e-121"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span></span>
