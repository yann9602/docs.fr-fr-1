---
title: "Comment&#160;: d&#233;clarer et utiliser des propri&#233;t&#233;s en lecture-&#233;criture (Guide de programmation&#160;C#) | Microsoft Docs"
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
  - "get (accesseur C#), déclarer des propriétés"
  - "set (accesseur C#)"
  - "propriétés (C#), déclarer"
  - "lecture/écriture (propriétés C#)"
  - "accesseurs (C#), déclarer des propriétés avec"
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: d&#233;clarer et utiliser des propri&#233;t&#233;s en lecture-&#233;criture (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les propriétés offrent la commodité des données membres publiques sans les risques liés à un accès non protégé, non contrôlé et non vérifié aux données d'un objet.  Cela se fait au moyen des *accesseurs* : méthodes spéciales qui assignent et récupèrent des valeurs de la donnée membre sous\-jacente.  L'accesseur [set](../../../csharp/language-reference/keywords/set.md) permet aux données membre d'être assignées, et l'accesseur [get](../../../csharp/language-reference/keywords/get.md) récupère des valeurs de donnée membre.  
  
 Cet exemple présente une classe `Person` qui possède deux propriétés : `Name` \(chaîne\) et `Age` \(entier\).  Les deux propriétés fournissant des accesseurs `get` et `set`, elles sont considérées comme des propriétés en lecture\/écriture.  
  
## Exemple  
 [!code-cs[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## Programmation fiable  
 Dans l'exemple précédent, les propriétés `Name` et `Age` sont [publiques](../../../csharp/language-reference/keywords/public.md) et incluent un accesseur  `get` et un accesseur `set`.  Cela permet à n'importe quel objet de lire et d'écrire ces propriétés.  Toutefois, il est quelquefois souhaitable d'exclure l'un des accesseurs.  L'omission de l'accesseur `set`, par exemple, rend la propriété en lecture seule :  
  
 [!code-cs[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 Vous pouvez également exposer publiquement un accesseur mais rendre l'autre privé ou protégé.  Pour plus d'informations, consultez [Accessibilité de l'accesseur asymétrique](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
 Une fois les propriétés déclarées, vous pouvez les utiliser comme s'il s'agissait de champs de la classe.  Il est ainsi possible d'employer une syntaxe très naturelle pour obtenir ou définir la valeur d'une propriété, comme dans les instructions suivantes :  
  
 [!code-cs[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 Notez qu'une variable `value` spéciale est disponible dans la méthode `set` d'une propriété.  Cette variable contient la valeur que l'utilisateur a spécifiée, par exemple :  
  
 [!code-cs[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 Notez la syntaxe correcte pour incrémenter la propriété `Age` sur un objet `Person` :  
  
 [!code-cs[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 Si des méthodes `set` et `get` distinctes ont été employées pour modeler les propriétés, le code équivalent peut avoir la forme suivante :  
  
```  
person.SetAge(person.GetAge() + 1);   
```  
  
 La méthode `ToString` est substituée dans cet exemple :  
  
 [!code-cs[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 Vous pouvez remarquer que `ToString` n'est pas utilisée de façon explicite dans le programme.  Elle est appelée par défaut par les appels `WriteLine`.  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)