---
title: "Comment&#160;: comparer des cha&#238;nes (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "comparer des chaînes (C#)"
  - "chaînes (C#), de comparaison"
ms.assetid: e1268e28-ee98-4695-98e9-92280f1c33c0
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# Comment&#160;: comparer des cha&#238;nes (Guide de programmation&#160;C#)
Lorsque vous comparez des chaînes, vous obtenez un résultat indiquant qu'une chaîne est supérieure ou inférieure à l'autre, ou que les deux chaînes sont égales.  Les règles qui déterminent le résultat sont différentes selon que vous effectuez une *comparaison ordinale* ou une *comparaison dépendante de la culture*.  Il est important d'utiliser le type correct de comparaison pour la tâche spécifique.  
  
 Utilisez la comparaison ordinale de base lorsque vous devez comparer ou trier les valeurs de deux chaînes sans tenir compte de conventions linguistiques.  Les comparaisons ordinales de base \(`System.StringComparison.Ordinal`\) respectent la casse, ce qui signifie que les caractères des deux chaînes doivent correspondre : « et » n'est pas l'équivalent de « Et » ni de « ET ».  Une variation fréquemment utilisée est  `System.StringComparison.OrdinalIgnoreCase`, qui correspond à « et », « Et » et « ET ».  `StringComparison.OrdinalIgnoreCase` est souvent utilisé pour comparer des noms de fichiers, des noms de chemins, des chemins d'accès réseau et d'autres chaînes dont la valeur ne change pas en fonction des paramètres régionaux de l'ordinateur de l'utilisateur.  Pour plus d'informations, consultez <xref:System.StringComparison?displayProperty=fullName>.  
  
 Les comparaisons dépendantes de la culture sont utilisées en général pour comparer et trier des chaînes entrées par les utilisateurs finals parce que les caractères et les conventions de tri de ces chaînes peuvent varier en fonction des paramètres régionaux de l'ordinateur de l'utilisateur.  Même les chaînes qui contiennent des caractères identiques peuvent être triées différemment selon la culture du thread actuel.  
  
> [!NOTE]
>  Lorsque vous comparez des chaînes, vous devez utiliser les méthodes qui spécifient explicitement le type de comparaison que vous projetez d'effectuer.  Cela rend votre code beaucoup plus facile à gérer et à lire.  Dans la mesure du possible, utilisez les surcharges des méthodes des classes <xref:System.String?displayProperty=fullName> et <xref:System.Array?displayProperty=fullName>, qui acceptent les paramètres d'énumération <xref:System.StringComparison>, afin que vous puissiez spécifier le type de comparaison à effectuer.  Il vaut mieux éviter d'utiliser les opérateurs `==` et `!=` lorsque vous comparez des chaînes.  Évitez également d'utiliser les méthodes d'instance <xref:System.String.CompareTo%2A?displayProperty=fullName> parce qu'aucune des surcharges n'accepte de <xref:System.StringComparison>.  
  
## Exemple  
 L'exemple suivant indique comment comparer correctement des chaînes dont les valeurs ne changent pas en fonction des paramètres régionaux de l'ordinateur de l'utilisateur.  De plus, il montre également la fonctionnalité d'*internement de chaîne* de C\#.  Lorsqu'un programme déclare plusieurs variables chaîne identiques, le compilateur les stocke toutes au même emplacement.  En appelant la méthode <xref:System.Object.ReferenceEquals%2A>, vous constatez que les deux chaînes font en fait référence au même objet en mémoire.  Utilisez la méthode <xref:System.String.Copy%2A?displayProperty=fullName> pour éviter l'internement, comme illustré dans l'exemple.  
  
 [!code-cs[csProgGuideStrings#11](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_1.cs)]  
  
## Exemple  
 L'exemple suivant indique comment comparer des chaînes de la façon voulue en utilisant les méthodes <xref:System.String?displayProperty=fullName>, qui acceptent les énumérations <xref:System.StringComparison>.  Notez que les méthodes d'instance <xref:System.String.CompareTo%2A?displayProperty=fullName> ne sont pas utilisées ici, parce qu'aucune des surcharges n'accepte de <xref:System.StringComparison>.  
  
 [!code-cs[csProgGuideStrings#31](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_2.cs)]  
  
## Exemple  
 L'exemple suivant indique comment trier et rechercher des chaînes dans un tableau d'une manière dépendante de la culture, en utilisant les méthodes <xref:System.Array> statiques, qui acceptent les paramètres <xref:System.StringComparer?displayProperty=fullName>.  
  
 [!code-cs[csProgGuideStrings#32](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_3.cs)]  
  
 Les classes de collection telles que <xref:System.Collections.Hashtable?displayProperty=fullName>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> et <xref:System.Collections.Generic.List%601?displayProperty=fullName> ont des constructeurs qui acceptent les paramètres <xref:System.StringComparer?displayProperty=fullName> lorsque le type des éléments ou des clés est `string`.  En général, vous devez utiliser ces constructeurs dès que cela est possible et spécifier `Ordinal` ou `OrdinalIgnoreCase`.  
  
## Voir aussi  
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.StringComparer?displayProperty=fullName>   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)   
 [Comparaison de chaînes](../Topic/Comparing%20Strings%20in%20the%20.NET%20Framework.md)   
 [Globalisation et localisation d'applications](/visual-studio/ide/globalizing-and-localizing-applications)