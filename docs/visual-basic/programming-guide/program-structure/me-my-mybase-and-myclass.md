---
title: Me, My, MyBase et MyClass dans Visual Basic | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
dev_langs:
- VB
helpviewer_keywords:
- My object
- self-reference, Me keyword
- MyClass keyword, relationship to similar programming elements
- Me keyword, relationship to similar programming elements
- Me keyword, referring to the current instance of an object
- Me keyword
- self-reference
- current instance, Me keyword
- MyBase keyword, relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: 15
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
ms.openlocfilehash: 3ba634eb28c25f47a0e88c856b916383b6ad15a2
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="d2aee-102">Me, My, MyBase et MyClass dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2aee-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="d2aee-103">`Me`, `My`, `MyBase`, et `MyClass` dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ont des noms semblables, mais à des fins différentes.</span><span class="sxs-lookup"><span data-stu-id="d2aee-103">`Me`, `My`, `MyBase`, and `MyClass` in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] have similar names, but different purposes.</span></span> <span data-ttu-id="d2aee-104">Cette rubrique décrit chacune de ces entités afin de les distinguer.</span><span class="sxs-lookup"><span data-stu-id="d2aee-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="d2aee-105">Me</span><span class="sxs-lookup"><span data-stu-id="d2aee-105">Me</span></span>  
 <span data-ttu-id="d2aee-106">Le `Me` mot clé permet de faire référence à l’instance spécifique d’une classe ou structure dans lequel le code est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d2aee-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="d2aee-107">`Me`se comporte comme une variable objet ou une variable de structure faisant référence à l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="d2aee-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="d2aee-108">À l’aide de `Me` est particulièrement utile pour transmettre des informations sur l’instance en cours d’exécution d’une classe ou structure à une procédure dans une autre classe, structure ou un module.</span><span class="sxs-lookup"><span data-stu-id="d2aee-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="d2aee-109">Par exemple, supposons que vous ayez la procédure suivante dans un module.</span><span class="sxs-lookup"><span data-stu-id="d2aee-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="d2aee-110">Vous pouvez appeler cette procédure et passer l’instance actuelle de la <xref:System.Windows.Forms.Form>classe en tant qu’argument à l’aide de l’instruction suivante.</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="d2aee-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="d2aee-111">My</span><span class="sxs-lookup"><span data-stu-id="d2aee-111">My</span></span>  
 <span data-ttu-id="d2aee-112">Le `My` fonctionnalité fournit un accès facile et intuitif à un nombre de [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes, ce qui le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] utilisateur d’interagir avec l’ordinateur, applications, paramètres, ressources et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="d2aee-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes, enabling the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="d2aee-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="d2aee-113">MyBase</span></span>  
 <span data-ttu-id="d2aee-114">Le `MyBase` (mot clé) se comporte comme une variable objet faisant référence à la classe de base de l’instance actuelle d’une classe.</span><span class="sxs-lookup"><span data-stu-id="d2aee-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="d2aee-115">`MyBase`est couramment utilisé pour accéder aux membres de classe de base qui sont substitués ou occultés dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="d2aee-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="d2aee-116">`MyBase.New`est utilisé pour appeler explicitement un constructeur de classe de base à partir d’un constructeur de classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="d2aee-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="d2aee-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="d2aee-117">MyClass</span></span>  
 <span data-ttu-id="d2aee-118">Le `MyClass` (mot clé) se comporte comme une variable objet qui fait référence à l’instance actuelle d’une classe implémentée comme à l’origine.</span><span class="sxs-lookup"><span data-stu-id="d2aee-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="d2aee-119">`MyClass`est semblable à `Me`, mais tous les appels de méthode sur celui-ci sont traités comme si la méthode était `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="d2aee-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2aee-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2aee-120">See Also</span></span>  
 [<span data-ttu-id="d2aee-121">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="d2aee-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
