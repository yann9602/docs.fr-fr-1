---
title: "La première instruction de ce &quot;Sub New&quot; doit être un appel explicite à &quot;MyBase.New&quot; ou &quot;MyClass.New&quot;, car le &quot;&lt;constructorname&gt;&quot;dans la classe de base&quot;&lt;baseclassname&gt;&quot;de&quot;&lt;derivedclassname&gt;&quot; est marqué comme obsolète : &quot;&lt;errormessage&gt;&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
dev_langs:
- VB
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
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
ms.openlocfilehash: d46192bc9a9f2807f56cbdd7bdd4fd21f6c9a7b0
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a><span data-ttu-id="def1b-102">La première instruction de ce 'Sub New' doit être un appel explicite à 'MyBase.New' ou 'MyClass.New', car le '&lt;constructorname&gt;'dans la classe de base'&lt;baseclassname&gt;'de'&lt;derivedclassname&gt;' est marqué comme obsolète : '&lt;errormessage&gt;»</span><span class="sxs-lookup"><span data-stu-id="def1b-102">First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;</span></span>
<span data-ttu-id="def1b-103">Un constructeur de classe n’appelle pas explicitement un constructeur de classe de base et le constructeur de classe de base implicite est marqué avec la <xref:System.ObsoleteAttribute>attribut et la directive pour le traiter comme une erreur.</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="def1b-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="def1b-104">Lorsqu’un constructeur de classe dérivée n’appelle pas de constructeur de classe de base, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tente de générer un appel implicite à un constructeur de classe de base sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="def1b-104">When a derived class constructor does not call a base class constructor, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="def1b-105">S’il n’existe aucun constructeur accessible dans la classe de base qui peut être appelée sans arguments, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne peut pas générer un appel implicite.</span><span class="sxs-lookup"><span data-stu-id="def1b-105">If there is no accessible constructor in the base class that can be called without arguments, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot generate an implicit call.</span></span> <span data-ttu-id="def1b-106">Dans ce cas, le constructeur requis est marqué avec la <xref:System.ObsoleteAttribute>attribut, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne peut pas appeler celui-ci.</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="def1b-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot call it.</span></span>  
  
 <span data-ttu-id="def1b-107">Vous pouvez marquer les éléments de programmation comme n’étant plus utilisé par l’application <xref:System.ObsoleteAttribute>à celui-ci.</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="def1b-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="def1b-108">Si vous procédez ainsi, vous pouvez définir l’attribut <xref:System.ObsoleteAttribute.IsError%2A>propriété `True` ou `False`.</xref:System.ObsoleteAttribute.IsError%2A></span><span class="sxs-lookup"><span data-stu-id="def1b-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="def1b-109">Si vous lui affectez la valeur `True`, le compilateur traite une tentative d’utilisation de l’élément comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="def1b-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="def1b-110">Si vous lui affectez la valeur `False`, ou si vous laissez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d’utilisation de l’élément.</span><span class="sxs-lookup"><span data-stu-id="def1b-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="def1b-111">**ID d’erreur :** BC30920</span><span class="sxs-lookup"><span data-stu-id="def1b-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="def1b-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="def1b-112">To correct this error</span></span>  
  
1.  <span data-ttu-id="def1b-113">Examinez le message d’erreur mentionné et prenez les mesures nécessaires.</span><span class="sxs-lookup"><span data-stu-id="def1b-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2.  <span data-ttu-id="def1b-114">Incluez un appel à `MyBase.New()` ou `MyClass.New()` en tant que première instruction de `Sub New` dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="def1b-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def1b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="def1b-115">See Also</span></span>  
 [<span data-ttu-id="def1b-116">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="def1b-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
