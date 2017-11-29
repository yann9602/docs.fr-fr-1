---
title: Me, My, MyBase et MyClass dans Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
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
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bebf404cd65d1b3a2c4059d3a7c986f0157dfe2d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase et MyClass dans Visual Basic
`Me`, `My`, `MyBase`, et `MyClass` dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ont des noms semblables, mais à des fins différentes. Cette rubrique décrit chacune de ces entités afin de les distinguer.  
  
## <a name="me"></a>Me  
 Le `Me` mot clé permet de faire référence à l’instance spécifique d’une classe ou structure dans laquelle le code est en cours d’exécution. `Me`se comporte comme une variable objet ou une variable de structure faisant référence à l’instance actuelle. À l’aide de `Me` est particulièrement utile pour passer des informations sur l’instance en cours d’exécution d’une classe ou une structure à une procédure dans une autre classe, structure ou un module.  
  
 Par exemple, supposons que vous disposez de la procédure suivante dans un module.  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Vous pouvez appeler cette procédure et passer l’instance actuelle de la <xref:System.Windows.Forms.Form> classe en tant qu’argument à l’aide de l’instruction suivante.  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 Le `My` fonction fournit un accès facile et intuitif pour un certain nombre de [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes, ce qui le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] utilisateur d’interagir avec l’ordinateur, applications, paramètres, ressources et ainsi de suite.  
  
## <a name="mybase"></a>MyBase  
 Le `MyBase` (mot clé) se comporte comme une variable objet faisant référence à la classe de base de l’instance actuelle d’une classe. `MyBase`est couramment utilisé pour accéder aux membres de classe de base qui sont substitués ou occultés dans une classe dérivée. `MyBase.New`est utilisé pour appeler explicitement un constructeur de classe de base à partir d’un constructeur de classe dérivée.  
  
## <a name="myclass"></a>MyClass  
 Le `MyClass` (mot clé) se comporte comme une variable objet faisant référence à l’instance actuelle d’une classe implémentée à l’origine. `MyClass`est semblable à `Me`, mais tous les appels de méthode sur celui-ci sont traités comme si la méthode était `NotOverridable`.  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments fondamentaux de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
