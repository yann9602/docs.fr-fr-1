---
title: "First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30920"
  - "bc30920"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30920"
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Un constructeur de classe n'appelle pas explicitement un constructeur de classe de base, et le constructeur de classe de base implicite est marqué avec l'attribut <xref:System.ObsoleteAttribute> et la directive de le traiter comme une erreur.  
  
 Lorsqu'un constructeur de classe dérivée n'appelle pas de constructeur de classe de base, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] essaie de générer un appel implicite à un constructeur de classe de base sans paramètre.  Si aucun constructeur n'est accessible dans la classe de base qui peut être appelée sans arguments, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ne peut pas générer un appel implicite.  Dans ce cas, le constructeur requis est marqué avec l'attribut <xref:System.ObsoleteAttribute> et, de ce fait, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ne peut pas l'appeler.  
  
 Vous pouvez marquer les éléments de programmation comme n'étant plus utilisés en leur appliquant <xref:System.ObsoleteAttribute>.  Dans ce cas, vous pouvez affecter à la propriété <xref:System.ObsoleteAttribute.IsError%2A> de l'attribut la valeur `True` ou `False`.  Si vous affectez la valeur `True`, le compilateur traite une tentative d'utilisation de l'élément comme une erreur.  Si vous affectez la valeur `False` ou laissez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d'utilisation de l'élément.  
  
 **ID d'erreur :** BC30920  
  
### Pour corriger cette erreur  
  
1.  Examinez le message d'erreur cité et prenez les mesures qui s'imposent.  
  
2.  Incluez un appel à `MyBase.New()` ou `MyClass.New()` comme première instruction du `Sub New` dans la classe dérivée.  
  
## Voir aussi  
 [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)