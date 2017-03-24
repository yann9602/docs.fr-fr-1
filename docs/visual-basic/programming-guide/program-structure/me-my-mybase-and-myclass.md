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
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 59dba8961712537367db9a60e8b8ba68bcb6a1ea
ms.lasthandoff: 03/13/2017

---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase et MyClass dans Visual Basic
`Me`, `My`, `MyBase`, et `MyClass` dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ont des noms semblables, mais à des fins différentes. Cette rubrique décrit chacune de ces entités afin de les distinguer.  
  
## <a name="me"></a>Me  
 Le `Me` mot clé permet de faire référence à l’instance spécifique d’une classe ou structure dans lequel le code est en cours d’exécution. `Me`se comporte comme une variable objet ou une variable de structure faisant référence à l’instance actuelle. À l’aide de `Me` est particulièrement utile pour transmettre des informations sur l’instance en cours d’exécution d’une classe ou structure à une procédure dans une autre classe, structure ou un module.  
  
 Par exemple, supposons que vous ayez la procédure suivante dans un module.  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Vous pouvez appeler cette procédure et passer l’instance actuelle de la <xref:System.Windows.Forms.Form>classe en tant qu’argument à l’aide de l’instruction suivante.</xref:System.Windows.Forms.Form>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 Le `My` fonctionnalité fournit un accès facile et intuitif à un nombre de [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes, ce qui le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] utilisateur d’interagir avec l’ordinateur, applications, paramètres, ressources et ainsi de suite.  
  
## <a name="mybase"></a>MyBase  
 Le `MyBase` (mot clé) se comporte comme une variable objet faisant référence à la classe de base de l’instance actuelle d’une classe. `MyBase`est couramment utilisé pour accéder aux membres de classe de base qui sont substitués ou occultés dans une classe dérivée. `MyBase.New`est utilisé pour appeler explicitement un constructeur de classe de base à partir d’un constructeur de classe dérivée.  
  
## <a name="myclass"></a>MyClass  
 Le `MyClass` (mot clé) se comporte comme une variable objet qui fait référence à l’instance actuelle d’une classe implémentée comme à l’origine. `MyClass`est semblable à `Me`, mais tous les appels de méthode sur celui-ci sont traités comme si la méthode était `NotOverridable`.  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments fondamentaux de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
