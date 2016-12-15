---
title: "First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30148"
  - "vbc30148"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30148"
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

La première instruction de ce 'Sub New' doit être un appel à 'MyBase.New' ou 'MyClass.New', car la classe de base '\<nombase\>' de '\<nomdérivé\>' n'a pas de 'Sub New' accessible pouvant être appelé sans argument.  
  
 Dans une classe dérivée, chaque constructeur doit appeler un constructeur de classe de base \(`MyBase.New`\).  Si la classe de base a un constructeur sans paramètres accessible aux classes dérivées, `MyBase.New` peut être appelé automatiquement.  Dans le cas contraire, un constructeur de classe de base doit être appelé avec des paramètres et cela ne peut pas se faire automatiquement.  Dans ce cas, la première instruction de chaque constructeur de classe dérivée doit appeler un constructeur paramétré sur la classe de base ou appeler un autre constructeur de la classe dérivée qui effectue un appel de constructeur de classe de base.  
  
 **ID d'erreur :** BC30148  
  
### Pour corriger cette erreur  
  
-   Appelez `MyBase.New` en fournissant les paramètres requis ou appelez un constructeur homologue qui effectuera cet appel.  
  
     Par exemple, si la classe de base a un constructeur qui est déclaré comme `Public Sub New(ByVal index as Integer)`, la première instruction dans le constructeur de classe dérivée peut être `MyBase.New(100)`.  
  
## Voir aussi  
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)