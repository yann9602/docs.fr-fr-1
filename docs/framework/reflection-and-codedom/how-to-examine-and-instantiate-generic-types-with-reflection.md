---
title: "Comment&#160;: examiner et instancier des types g&#233;n&#233;riques avec la r&#233;flexion | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "génériques (.NET Framework), réflexion"
  - "réflexion, types génériques"
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: examiner et instancier des types g&#233;n&#233;riques avec la r&#233;flexion
Les informations sur des types génériques sont obtenues de la même façon que les informations sur les autres types : par l'examen d'un objet <xref:System.Type> qui représente le type générique.  La principale différence réside dans le fait qu'un type générique possède une liste d'objets <xref:System.Type> qui représentent ses paramètres de type générique.  La première procédure de cette section examine des types génériques.  
  
 Vous pouvez créer un objet <xref:System.Type> qui représente un type construit en liant des arguments de type aux paramètres de type d'une définition de type générique.  Cette action est illustrée dans la deuxième procédure.  
  
### Pour examiner un type générique et ses paramètres de type  
  
1.  Obtenez une instance de <xref:System.Type> qui représente le type générique.  Dans le code suivant, le type est obtenu à l'aide de l'opérateur `typeof` C\# \(`GetType` en Visual Basic, `typeid` en Visual C\+\+\).  Consultez la rubrique de la classe <xref:System.Type> pour connaître d'autres moyens d'obtenir un objet <xref:System.Type>.  Notez que dans le reste de cette procédure, le type est contenu dans un paramètre de méthode nommé `t`.  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2.  Utilisez la propriété <xref:System.Type.IsGenericType%2A> pour déterminer si le type est générique et utilisez la propriété <xref:System.Type.IsGenericTypeDefinition%2A> pour déterminer si le type est une définition de type générique.  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3.  Obtenez un tableau qui contient les arguments de type générique, à l'aide de la méthode <xref:System.Type.GetGenericArguments%2A>.  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4.  Pour chaque argument de type, déterminez s'il s'agit d'un paramètre de type \(par exemple, dans une définition de type générique\) ou d'un type spécifié pour un paramètre de type \(par exemple, dans un type construit\), à l'aide de la propriété <xref:System.Type.IsGenericParameter%2A>.  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5.  Dans le système de types, un paramètre de type générique est représenté par une instance de <xref:System.Type>, de la même façon que les types ordinaires.  Le code suivant affiche le nom et la position de paramètre d'un objet <xref:System.Type> qui représente un paramètre de type générique.  La position de paramètre est ici sans importance ; elle est plus utile lorsque vous examinez un paramètre de type qui a été utilisé comme argument de type d'un autre type générique.  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6.  Déterminez la contrainte du type de base et les contraintes d'interface d'un paramètre de type générique en utilisant la méthode <xref:System.Type.GetGenericParameterConstraints%2A> pour obtenir toutes les contraintes dans un seul tableau.  Rien ne garantit que les contraintes respectent un ordre particulier.  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7.  Utilisez la propriété <xref:System.Type.GenericParameterAttributes%2A> pour découvrir les contraintes spéciales d'un paramètre de type, par exemple l'obligation d'être un type référence.  La propriété inclut également des valeurs qui représentent la variance, que vous pouvez masquer comme l'illustre le code suivant.  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8.  Les attributs de contrainte spéciaux sont des indicateurs, et le même indicateur \(<xref:System.Reflection.GenericParameterAttributes?displayProperty=fullName>\) qui ne représente aucune contrainte spéciale ne représente non plus aucune covariance ou contravariance.  Par conséquent, pour tester l'un ou l'autre de ces conditions vous devez utiliser le masque approprié.  Dans ce cas, utilisez <xref:System.Reflection.GenericParameterAttributes?displayProperty=fullName> pour isoler les indicateurs de contrainte spéciaux.  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## Construction d'une instance d'un type générique  
 Un type générique est similaire à un modèle.  Vous ne pouvez pas créer d'instances du type générique à moins de spécifier des types réels en tant que paramètres de type générique de celui\-ci.  Pour le faire au moment de l'exécution, à l'aide de la réflexion, vous avez besoin de la méthode <xref:System.Type.MakeGenericType%2A>.  
  
#### Pour construire une instance d'un type générique  
  
1.  Obtenez un objet <xref:System.Type> qui représente le type spécifié.  Le code suivant obtient le type <xref:System.Collections.Generic.Dictionary%602> générique de deux façons différentes : en utilisant la méthode surchargée <xref:System.Type.GetType%28System.String%29?displayProperty=fullName> avec une chaîne qui décrit le type, et en appelant la méthode <xref:System.Type.GetGenericTypeDefinition%2A> sur le type construit `Dictionary\<String, Example>` \(`Dictionary(Of String, Example)` en Visual Basic\).  La méthode <xref:System.Type.MakeGenericType%2A> exige une définition de type générique.  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2.  Construisez un tableau des arguments de type pour substituer les paramètres de type.  Le tableau doit contenir le nombre correct d'objets <xref:System.Type>, et respecter l'ordre de la liste des paramètres de type.  Dans ce cas, la clé \(premier paramètre de type\) est de type <xref:System.String>, et les valeurs du dictionnaire sont des instances d'une classe nommée `Example`.  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3.  Appelez la méthode <xref:System.Type.MakeGenericType%2A> pour lier les arguments de type aux paramètres de type et construire le type.  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4.  Utilisez la méthode surchargée <xref:System.Activator.CreateInstance%28System.Type%29> pour créer un objet du type construit.  Le code suivant stocke deux instances de la classe `Example` dans l'objet `Dictionary<String, Example>` résultant.  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## Exemple  
 L'exemple de code suivant définit une méthode `DisplayGenericType` pour examiner les définitions de types génériques et les types construits utilisés dans le code et afficher leurs informations.  La méthode `DisplayGenericType` montre comment utiliser les propriétés <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A> et <xref:System.Type.GenericParameterPosition%2A> et la méthode <xref:System.Type.GetGenericArguments%2A>.  
  
 L'exemple définit également une méthode `DisplayGenericParameter` pour examiner un paramètre de type générique et afficher ses contraintes.  
  
 L'exemple de code définit un ensemble de types de test, y compris un type générique qui illustre des contraintes de paramètre de type, et montre comment afficher les informations sur ces types.  
  
 L'exemple construit un type de la classe <xref:System.Collections.Generic.Dictionary%602> en créant un tableau des arguments de type et appelant la méthode <xref:System.Type.MakeGenericType%2A>.  Le programme compare l'objet <xref:System.Type> construit à l'aide de la méthode <xref:System.Type.MakeGenericType%2A> à un objet <xref:System.Type> obtenu à l'aide de `typeof` \(`GetType` en Visual Basic\), démontrant qu'ils sont identiques.  De la même façon, le programme utilise la méthode <xref:System.Type.GetGenericTypeDefinition%2A> pour obtenir la définition de type générique du type construit et la compare à l'objet <xref:System.Type> qui représente la classe <xref:System.Collections.Generic.Dictionary%602>.  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## Compilation du code  
  
-   Le code contient les instructions `using` C\# \(`Imports` en Visual Basic\) nécessaires à la compilation.  
  
-   Aucune référence d'assembly supplémentaire n'est requise.  
  
-   Compilez le code sur la ligne de commande à l'aide de csc.exe, vbc.exe ou cl.exe.  Pour compiler le code dans Visual Studio , placez\-le dans un modèle de projet d'application console.  
  
## Voir aussi  
 <xref:System.Type>   
 <xref:System.Reflection.MethodInfo>   
 [Réflexion et types génériques](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)   
 [Affichage des informations de type](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)   
 [Génériques](../../../docs/standard/generics/index.md)