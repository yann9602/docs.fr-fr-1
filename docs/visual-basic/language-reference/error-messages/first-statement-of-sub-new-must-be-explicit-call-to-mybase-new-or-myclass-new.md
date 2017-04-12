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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: feb04d426b7e050b7ad05cdfd4d481172dda3a49
ms.lasthandoff: 03/13/2017

---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>La première instruction de ce 'Sub New' doit être un appel explicite à 'MyBase.New' ou 'MyClass.New', car le '&lt;constructorname&gt;'dans la classe de base'&lt;baseclassname&gt;'de'&lt;derivedclassname&gt;' est marqué comme obsolète : '&lt;errormessage&gt;»
Un constructeur de classe n’appelle pas explicitement un constructeur de classe de base et le constructeur de classe de base implicite est marqué avec la <xref:System.ObsoleteAttribute>attribut et la directive pour le traiter comme une erreur.</xref:System.ObsoleteAttribute>  
  
 Lorsqu’un constructeur de classe dérivée n’appelle pas de constructeur de classe de base, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tente de générer un appel implicite à un constructeur de classe de base sans paramètre. S’il n’existe aucun constructeur accessible dans la classe de base qui peut être appelée sans arguments, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne peut pas générer un appel implicite. Dans ce cas, le constructeur requis est marqué avec la <xref:System.ObsoleteAttribute>attribut, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne peut pas appeler celui-ci.</xref:System.ObsoleteAttribute>  
  
 Vous pouvez marquer les éléments de programmation comme n’étant plus utilisé par l’application <xref:System.ObsoleteAttribute>à celui-ci.</xref:System.ObsoleteAttribute> Si vous procédez ainsi, vous pouvez définir l’attribut <xref:System.ObsoleteAttribute.IsError%2A>propriété `True` ou `False`.</xref:System.ObsoleteAttribute.IsError%2A> Si vous lui affectez la valeur `True`, le compilateur traite une tentative d’utilisation de l’élément comme une erreur. Si vous lui affectez la valeur `False`, ou si vous laissez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d’utilisation de l’élément.  
  
 **ID d’erreur :** BC30920  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Examinez le message d’erreur mentionné et prenez les mesures nécessaires.  
  
2.  Incluez un appel à `MyBase.New()` ou `MyClass.New()` en tant que première instruction de `Sub New` dans la classe dérivée.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
