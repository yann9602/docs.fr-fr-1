---
title: "Comment&#160;: modifier du contenu de cha&#238;ne (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "chaînes (C#), modifier"
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# Comment&#160;: modifier du contenu de cha&#238;ne (Guide de programmation&#160;C#)
Parce que les chaînes sont *immuables*, il n'est pas possible \(sans utiliser du code non sécurisé\) de modifier la valeur d'un objet chaîne après qu'il a été créé.  Toutefois, il y a de nombreuses façons de modifier la valeur d'une chaîne et de stocker le résultat dans un nouvel objet chaîne.  La classe <xref:System.String?displayProperty=fullName> fournit des méthodes qui utilisent une chaîne d'entrée et retournent un nouvel objet chaîne.  Dans de nombreux cas, vous pouvez assigner le nouvel objet à la variable qui contenait la chaîne d'origine.  La classe <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> fournit des méthodes supplémentaires qui fonctionnent de façon semblable.  La classe <xref:System.Text.StringBuilder?displayProperty=fullName> fournit une mémoire tampon de caractères que vous pouvez modifier « sur place ». Vous appelez la méthode <xref:System.Text.StringBuilder.ToString%2A?displayProperty=fullName> pour créer un objet chaîne qui contient le contenu actuel de la mémoire tampon.  
  
## Exemple  
 L'exemple suivant indique différentes façons de remplacer ou de supprimer des sous\-chaînes dans une chaîne spécifiée.  
  
 [!code-cs[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/csharp/CSRefStrings/Strings.cs#28)]  
  
## Exemple  
 Pour accéder aux différents caractères d'une chaîne en utilisant la notation de tableau, vous pouvez utiliser l'objet <xref:System.Text.StringBuilder>, qui surcharge l'opérateur `[]` pour permettre l'accès à la mémoire tampon de caractères interne.  Vous pouvez également convertir la chaîne en un tableau de caractères en utilisant la méthode <xref:System.String.ToCharArray%2A>.  L'exemple suivant utilise `ToCharArray` pour créer le tableau.  Certains éléments de ce tableau sont ensuite modifiés.  Un constructeur String prenant les tableaux de caractères comme paramètres d'entrée est alors appelé pour créer une chaîne.  
  
 [!code-cs[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/csharp/CSRefStrings/Strings.cs#24)]  
  
## Exemple  
 L'exemple suivant est fourni pour les cas très rares où vous voulez modifier une chaîne sur place en utilisant du code non sécurisé, procédant ainsi comme avec les tableaux de caractères de style C.  L'exemple indique comment accéder aux différents caractères « sur place » en utilisant le mot clé fixed.  Il montre également un effet secondaire possible des opérations risquées réalisées sur les chaînes, lié à la façon dont le compilateur C\# stocke \(interne\) les chaînes en interne.  En général, il est préférable de ne pas utiliser cette technique, sauf en cas d'absolue nécessité.  
  
 [!code-cs[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/csharp/CSRefStrings/Strings.cs#29)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)