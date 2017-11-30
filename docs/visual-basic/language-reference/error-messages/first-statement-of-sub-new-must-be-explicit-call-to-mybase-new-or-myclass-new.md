---
title: "La première instruction de ce &#39; Sub nouveau &#39; doit être un appel explicite à &#39; MyBase.New &#39; ou &#39; MyClass.New &#39; Étant donné que le &#39; &lt;Nom_Constructeur&gt;&#39; dans la classe de base &#39;&lt; nom_classe_base&gt;&#39; de &#39;&lt; nom_classe_dérivée&gt;&#39; est marqué comme obsolète : &#39;&lt; message d’erreur&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords: BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8882acd947251d85804fbefd54267ce078e31b95
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a><span data-ttu-id="3aef9-102">La première instruction de ce &#39; Sub nouveau &#39; doit être un appel explicite à &#39; MyBase.New &#39; ou &#39; MyClass.New &#39; Étant donné que le &#39; &lt;Nom_Constructeur&gt;&#39; dans la classe de base &#39;&lt; nom_classe_base&gt;&#39; de &#39;&lt; nom_classe_dérivée&gt;&#39; est marqué comme obsolète : &#39;&lt; message d’erreur&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="3aef9-102">First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;</span></span>
<span data-ttu-id="3aef9-103">Un constructeur de classe n’appelle pas explicitement un constructeur de classe de base et le constructeur de classe de base implicite est marqué avec l’attribut <xref:System.ObsoleteAttribute> et la directive pour le traiter comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="3aef9-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="3aef9-104">Quand un constructeur de classe dérivée n’appelle pas de constructeur de classe de base, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] essaie de générer un appel implicite à un constructeur de classe de base sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="3aef9-104">When a derived class constructor does not call a base class constructor, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="3aef9-105">S’il n’existe aucun constructeur accessible dans la classe de base qui peut être appelé sans arguments, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ne peut pas générer d’appel implicite.</span><span class="sxs-lookup"><span data-stu-id="3aef9-105">If there is no accessible constructor in the base class that can be called without arguments, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot generate an implicit call.</span></span> <span data-ttu-id="3aef9-106">Dans ce cas, le constructeur nécessaire est marqué avec l’attribut <xref:System.ObsoleteAttribute> , et [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ne peut pas l’appeler.</span><span class="sxs-lookup"><span data-stu-id="3aef9-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot call it.</span></span>  
  
 <span data-ttu-id="3aef9-107">Vous pouvez marquer un élément de programmation comme n’étant plus utilisé en lui appliquant <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="3aef9-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="3aef9-108">Dans ce cas, vous pouvez affecter à la propriété <xref:System.ObsoleteAttribute.IsError%2A> de l’attribut la valeur `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="3aef9-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="3aef9-109">Si vous lui affectez la valeur `True`, le compilateur traite une tentative d’utilisation de l’élément comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="3aef9-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="3aef9-110">Si vous lui affectez la valeur `False`ou si vous laissez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d’utilisation de l’élément.</span><span class="sxs-lookup"><span data-stu-id="3aef9-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="3aef9-111">**ID d’erreur :** BC30920</span><span class="sxs-lookup"><span data-stu-id="3aef9-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3aef9-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="3aef9-112">To correct this error</span></span>  
  
1.  <span data-ttu-id="3aef9-113">Examinez le message d’erreur mentionné et prenez les mesures nécessaires.</span><span class="sxs-lookup"><span data-stu-id="3aef9-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2.  <span data-ttu-id="3aef9-114">Incluez un appel à `MyBase.New()` ou `MyClass.New()` en tant que première instruction de `Sub New` dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="3aef9-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aef9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3aef9-115">See Also</span></span>  
 [<span data-ttu-id="3aef9-116">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="3aef9-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
