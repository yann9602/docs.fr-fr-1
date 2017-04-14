---
title: "Comment&#160;: d&#233;finir un type g&#233;n&#233;rique avec l&#39;&#233;mission de r&#233;flexion | Microsoft Docs"
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
  - "génériques (.NET Framework), types dynamic"
  - "génériques (.NET Framework), émission de réflexion"
  - "émission de réflexion, types génériques"
ms.assetid: 07d5f01a-7b5b-40ea-9b15-f21561098fe4
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: d&#233;finir un type g&#233;n&#233;rique avec l&#39;&#233;mission de r&#233;flexion
Cette rubrique explique comment créer un type générique simple avec deux paramètres de type, comment appliquer des contraintes de classe, des contraintes d'interface et des contraintes spéciales aux paramètres de type, et enfin comment créer des membres qui utilisent les paramètres de type de la classe comme types de paramètre et types de retour.  
  
> [!IMPORTANT]
>  Une méthode n'est pas générique simplement parce qu'elle appartient à un type générique et utilise les paramètres de type de ce type.  Une méthode est générique uniquement si elle possède sa propre liste de paramètres de type.  La plupart des méthodes sur les types génériques ne sont pas génériques, comme dans cet exemple.  Pour obtenir un exemple d'émission de méthode générique, consultez [Comment : définir une méthode générique avec l'émission de réflexion](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-method-with-reflection-emit.md).  
  
### Pour définir un type générique  
  
1.  Définissez un assembly dynamique nommé `GenericEmitExample1`.  Dans cet exemple, comme l'assembly est exécuté et enregistré sur le disque, <xref:System.Reflection.Emit.AssemblyBuilderAccess?displayProperty=fullName> est spécifié.  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2.  Définissez un module dynamique.  Un assembly est composé de modules exécutables.  Pour un assembly comportant un seul module, le nom du module est le même que celui de l'assembly, et le nom de fichier est le nom du module suivi d'une extension.  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3.  Définissez une classe.  Dans cet exemple, la classe s'appelle `Sample`.  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4.  Définissez les paramètres de type générique de `Sample` en passant un tableau de chaînes contenant les noms des paramètres à la méthode <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=fullName>.  Cela fait de la classe un type générique.  La valeur de retour est un tableau d'objets <xref:System.Reflection.Emit.GenericTypeParameterBuilder> représentant les paramètres de type, lesquels peuvent être utilisés dans le code que vous avez émis.  
  
     Dans le code suivant, `Sample` devient un type générique avec les paramètres de type `TFirst` et `TSecond`.  Pour simplifier la lecture du code, chaque <xref:System.Reflection.Emit.GenericTypeParameterBuilder> est placé dans une variable avec le même nom que le paramètre de type.  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5.  Ajoutez des contraintes spéciales aux paramètres de type.  Dans cet exemple, le paramètre de type `TFirst` est limité aux types qui possèdent des constructeurs sans paramètre et aux types référence.  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6.  Ajoutez éventuellement des contraintes de classe et d'interface aux paramètres de type.  Dans cet exemple, le paramètre de type `TFirst` est limité aux types qui dérivent de la classe de base représentée par l'objet <xref:System.Type> contenu dans la variable `baseType` et qui implémentent les interfaces dont les types sont contenus dans les variables `interfaceA` et `interfaceB`.  Consultez l'exemple de code relatif à la déclaration et à l'assignation de ces variables.  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7.  Définissez un champ.  Dans cet exemple, le type du champ est spécifié par le paramètre de type `TFirst`.  <xref:System.Reflection.Emit.GenericTypeParameterBuilder> dérive de <xref:System.Type>. Vous pouvez donc utiliser des paramètres de type générique partout où il est possible d'utiliser un type.  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8.  Définissez une méthode qui utilise les paramètres de type du type générique.  Notez que de telles méthodes ne sont pas génériques, sauf si elles possèdent leurs propres listes de paramètres de type.  Le code suivant définit une méthode `static` \(`Shared` en Visual Basic\) qui prend un tableau de `TFirst` et retourne un `List<TFirst>` \(`List(Of TFirst)` en Visual Basic\) contenant tous les éléments du tableau.  Pour définir cette méthode, il est nécessaire de créer le type `List<TFirst>` en appelant <xref:System.Type.MakeGenericType%2A> sur la définition de type générique, `List<T>`. \(`T` est omis lorsque vous utilisez l'opérateur `typeof` \(`GetType` en Visual Basic\) pour obtenir la définition de type générique.\) Le type de paramètres est créé en utilisant la méthode <xref:System.Type.MakeArrayType%2A>.  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. Émettez le corps de la méthode.  Le corps de la méthode se compose de trois opcodes qui chargent le tableau d'entrée sur la pile, appellent le constructeur `List<TFirst>` qui prend `IEnumerable<TFirst>` \(lequel se charge de placer les éléments d'entrée dans la liste\) et sont retournés \(en laissant le nouvel objet <xref:System.Collections.Generic.List%601> sur la pile\).  Dans l'émission de ce code, la difficulté consiste à obtenir le constructeur.  
  
     La méthode <xref:System.Type.GetConstructor%2A> n'étant pas prise en charge sur un <xref:System.Reflection.Emit.GenericTypeParameterBuilder>, il n'est pas possible d'obtenir directement le constructeur de `List<TFirst>`.  Tout d'abord, il est nécessaire d'obtenir le constructeur de la définition de type générique `List<T>`, puis d'appeler une méthode qui le convertit en constructeur correspondant de `List<TFirst>`.  
  
     Le constructeur utilisé pour cet exemple de code prend `IEnumerable<T>`.  Notez cependant qu'il ne s'agit pas de la définition de type générique de l'interface générique <xref:System.Collections.Generic.IEnumerable%601> ; au lieu de cela, le paramètre de type `T` de `List<T>` doit être substitué au paramètre de type `T` de `IEnumerable<T>`. \(Cela peut sembler confus, mais c'est uniquement parce que les deux types possèdent des paramètres de type nommés `T`.  C'est pourquoi cet exemple de code utilise les noms `TFirst` et `TSecond`.\) Pour obtenir le type de l'argument de constructeur, commencez avec la définition de type générique `IEnumerable<T>` et appelez <xref:System.Type.MakeGenericType%2A> avec le premier paramètre de type générique de `List<T>`.  La liste d'arguments de constructeur doit être passée en tant que tableau, avec un seul argument dans le cas présent.  
  
    > [!NOTE]
    >  La définition de type générique est exprimée en tant que `IEnumerable<>` lorsque vous utilisez l'opérateur `typeof` en C\#, ou en tant que `IEnumerable(Of )` lorsque vous utilisez l'opérateur `GetType` en Visual Basic.  
  
     Il est désormais possible d'obtenir le constructeur de `List<T>` en appelant <xref:System.Type.GetConstructor%2A> sur la définition de type générique.  Pour convertir ce constructeur en constructeur correspondant de `List<TFirst>`, passez `List<TFirst>` et le constructeur de `List<T>` à la méthode statique <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=fullName>.  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. Créez le type et enregistrez le fichier.  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. Appelez la méthode.  `ExampleMethod` n'est pas générique, mais le type auquel il appartient est générique, donc pour obtenir un <xref:System.Reflection.MethodInfo> qui peut être appelé, il est nécessaire de créer un type construit à partir de la définition de type pour `Sample`.  Le type construit utilise la classe `Example`, laquelle satisfait aux contraintes sur `TFirst` puisqu'il s'agit d'un type référence et qu'elle possède un constructeur sans paramètre par défaut, ainsi que la classe `ExampleDerived` qui satisfait aux contraintes sur `TSecond`. \(Vous pouvez consulter le code de `ExampleDerived` dans la section de l'exemple de code.\) Ces deux types sont passés à <xref:System.Type.MakeGenericType%2A> pour créer le type construit.  <xref:System.Reflection.MethodInfo> est ensuite obtenu à l'aide de la méthode <xref:System.Type.GetMethod%2A>.  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. Le code suivant crée un tableau d'objets `Example`, place ce tableau dans un tableau de type <xref:System.Object> représentant les arguments de la méthode à appeler, puis les passe à la méthode [Invoke\(Object, Object\<xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29>.  Le premier argument de la méthode <xref:System.Reflection.MethodBase.Invoke%2A> est une référence null car la méthode est `static`.  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## Exemple  
 L'exemple de code suivant définit une classe nommée `Sample`, ainsi qu'une classe de base et deux interfaces.  Le programme définit deux paramètres de type générique pour la classe `Sample`, et la change ainsi en type générique.  Les paramètres de type sont les seuls éléments qui rendent un type générique.  Le programme illustre cela en affichant un message de test avant et après la définition des paramètres de type.  
  
 Le paramètre de type `TSecond` est utilisé pour illustrer les contraintes de classe et d'interface, à l'aide de la classe de base et des interfaces, et le paramètre de type `TFirst` est utilisé pour illustrer des contraintes spéciales.  
  
 L'exemple de code définit un champ et une méthode à l'aide des paramètres de type de la classe pour le type de champ, pour le paramètre et pour le type de retour de la méthode.  
  
 Une fois la classe `Sample` créée, la méthode est appelée.  
  
 Le programme inclut une méthode qui répertorie des informations relatives à un type générique et une méthode qui répertorie les contraintes spéciales sur un paramètre de type.  Ces méthodes sont utilisées pour afficher des informations relatives à la classe `Sample` finie.  
  
 Le programme enregistre le module fini sur le disque en tant que `GenericEmitExample1.dll`. Vous pouvez donc l'ouvrir avec le désassembleur [Ildasm.exe \(IL Disassembler\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) et examiner le code MSIL pour la classe `Sample`.  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## Compilation du code  
  
-   Le code contient les instructions `using` C\# \(`Imports` en Visual Basic\) nécessaires à la compilation.  
  
-   Aucune référence d'assembly supplémentaire n'est requise.  
  
-   Compilez le code sur la ligne de commande à l'aide de csc.exe, vbc.exe ou cl.exe.  Pour compiler le code dans Visual Studio , placez\-le dans un modèle de projet d'application console.  
  
## Voir aussi  
 <xref:System.Reflection.Emit.GenericTypeParameterBuilder>   
 [Using Reflection Emit](http://msdn.microsoft.com/fr-fr/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)   
 [Reflection Emit Dynamic Assembly Scenarios](http://msdn.microsoft.com/fr-fr/e1cc6750-e20f-473b-bb4e-f43bc66aecce)