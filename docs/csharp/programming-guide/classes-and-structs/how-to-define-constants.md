---
title: "Comment&#160;: d&#233;finir des constantes en C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, constantes"
  - "constantes (C#)"
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: d&#233;finir des constantes en C# #
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les constantes sont des champs dont les valeurs sont définies à la compilation et ne sont pas modifiables.  Utilisez des constantes pour fournir des noms explicites au lieu de littéraux numériques \(« nombres magiques »\) pour les valeurs spéciales.  
  
> [!NOTE]
>  En C\#, la directive de préprocesseur[\#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) ne peut pas être utilisée pour définir des constantes de la manière utilisée en général dans C et C\+\+.  
  
 Pour définir des valeurs constantes de types intégraux \(`int`, `byte`, etc.\), utilisez un type énuméré.  Pour plus d'informations, consultez [enum](../../../csharp/language-reference/keywords/enum.md).  
  
 Pour définir des constantes non intégrales, une approche consiste à les regrouper dans une classe static unique nommée `Constants`.  Cela requiert que toutes les références aux constantes soient précédées par le nom de classe, comme dans l'exemple suivant.  
  
## Exemple  
 [!code-cs[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 L'utilisation du qualificateur de nom de classe permet de garantir que les personnes qui utilisent la constante, y compris vous\-même, comprennent qu'elle est fixe et qu'elle ne peut pas être modifiée.  
  
## Voir aussi  
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)