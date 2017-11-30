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
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>La première instruction de ce &#39; Sub nouveau &#39; doit être un appel explicite à &#39; MyBase.New &#39; ou &#39; MyClass.New &#39; Étant donné que le &#39; &lt;Nom_Constructeur&gt;&#39; dans la classe de base &#39;&lt; nom_classe_base&gt;&#39; de &#39;&lt; nom_classe_dérivée&gt;&#39; est marqué comme obsolète : &#39;&lt; message d’erreur&gt;&#39;
Un constructeur de classe n’appelle pas explicitement un constructeur de classe de base et le constructeur de classe de base implicite est marqué avec l’attribut <xref:System.ObsoleteAttribute> et la directive pour le traiter comme une erreur.  
  
 Quand un constructeur de classe dérivée n’appelle pas de constructeur de classe de base, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] essaie de générer un appel implicite à un constructeur de classe de base sans paramètre. S’il n’existe aucun constructeur accessible dans la classe de base qui peut être appelé sans arguments, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ne peut pas générer d’appel implicite. Dans ce cas, le constructeur nécessaire est marqué avec l’attribut <xref:System.ObsoleteAttribute> , et [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ne peut pas l’appeler.  
  
 Vous pouvez marquer un élément de programmation comme n’étant plus utilisé en lui appliquant <xref:System.ObsoleteAttribute> . Dans ce cas, vous pouvez affecter à la propriété <xref:System.ObsoleteAttribute.IsError%2A> de l’attribut la valeur `True` ou `False`. Si vous lui affectez la valeur `True`, le compilateur traite une tentative d’utilisation de l’élément comme une erreur. Si vous lui affectez la valeur `False`ou si vous laissez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d’utilisation de l’élément.  
  
 **ID d’erreur :** BC30920  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Examinez le message d’erreur mentionné et prenez les mesures nécessaires.  
  
2.  Incluez un appel à `MyBase.New()` ou `MyClass.New()` en tant que première instruction de `Sub New` dans la classe dérivée.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
