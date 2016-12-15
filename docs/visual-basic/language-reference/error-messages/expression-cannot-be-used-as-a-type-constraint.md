---
title: "&#39;&lt;expression&gt;&#39; cannot be used as a type constraint | Microsoft Docs"
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
  - "bc32061"
  - "vbc32061"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32061"
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;expression&gt;&#39; cannot be used as a type constraint
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une liste de contraintes contient une expression qui ne représente pas une contrainte valide sur un paramètre de type.  
  
 Une liste de contraintes impose des exigences sur l'argument de type passé au paramètre de type.  Vous pouvez spécifier les éléments requis suivants selon n'importe quelle combinaison :  
  
-   L'argument de type doit implémenter une ou plusieurs interfaces  
  
-   L'argument de type doit hériter d'une classe au plus  
  
-   L'argument de type doit exposer un constructeur sans paramètre accessible par le code de création \(contrainte `New` à inclure\)  
  
 Si vous n'incluez aucune classe ou interface spécifique dans la liste de contraintes, vous pouvez imposer une condition plus générale en spécifiant l'un des éléments suivants :  
  
-   l'argument de type doit être un type valeur \(contrainte `Structure` à inclure\) ;  
  
-   l'argument de type doit être un type de référence \(contrainte `Class` à inclure\) ;  
  
 Vous ne pouvez pas spécifier `Structure` et `Class` pour le même paramètre de type, de même que vous ne pouvez pas spécifier l'un ou l'autre plusieurs fois.  
  
 **ID d'erreur :** BC32061  
  
### Pour corriger cette erreur  
  
-   Vérifiez que l'expression et ses éléments sont correctement orthographiés.  
  
-   Si l'expression ne répond pas à la précédente liste d'exigences, supprimez\-la de la liste des contraintes.  
  
-   Si l'expression fait référence à une interface ou une classe, vérifiez que le compilateur a accès à cette interface ou classe.  Vous devrez peut\-être qualifier son nom et ajouter une référence à votre projet.  Pour plus d'informations, consultez « Références aux projets » dans [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## Voir aussi  
 [Types génériques Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Value Types and Reference Types](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Comment : ajouter ou supprimer des références à l'aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)