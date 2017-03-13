---
title: "M&#233;moires tampons de taille fixe (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "mémoires tampons de taille fixe (C#)"
  - "mémoires tampons unsafe (C#)"
  - "code unsafe (C#), mémoires tampons à taille fixe"
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# M&#233;moires tampons de taille fixe (Guide de programmation C#)
En C\#, vous pouvez utiliser l'instruction [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) pour créer un tampon avec un tableau de taille fixe dans une structure de données.  Cette action est utile lorsque vous utilisez un code existant, comme le code écrit dans d'autres langages, les DLL préexistantes ou les projets COM.  Le tableau fixe peut accepter tous les attributs ou modificateurs qui sont prévus pour les membres de structures régulières.  La seule restriction est que le type de tableau doit être `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.  
  
```  
private fixed char name[30];  
```  
  
## Notes  
 Dans les premières versions de C\#, la déclaration d'une structure de taille fixe de type C\+\+ s'avère difficile car un struct C\# qui contient un tableau n'inclut pas les éléments du tableau.  Au lieu de cela, le struct contient une référence aux éléments.  
  
 C\# 2.0 permet également d'incorporer un tableau de taille fixe dans un [struct](../../../csharp/language-reference/keywords/struct.md) en cas d'utilisation dans un bloc de code [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
 Par exemple, avant C\# 2.0, le `struct` suivant avait une taille de 8 octets.  Le tableau `pathName` est une référence au tableau alloué par tas :  
  
 [!code-cs[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 Avec C\# 2.0, un `struct` peut contenir un tableau intégré.  Dans l'exemple suivant, le tableau `fixedBuffer` a une taille fixe.  Pour accéder aux éléments du tableau, vous utilisez une instruction `fixed` pour établir un pointeur vers le premier élément.  L'instruction `fixed` épingle une instance de `fixedBuffer` à un emplacement spécifique en mémoire.  
  
 [!code-cs[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 La taille du tableau `char` de 128 éléments est de 256 octets.  Les mémoires tampons [char](../../../csharp/language-reference/keywords/char.md) de taille fixe occupent toujours deux octets par caractère, quel que soit l'encodage.  Cela est vrai même lorsque les mémoires tampons de caractères sont marshalées en fonction de méthodes API ou de structs avec `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`.  Pour plus d'informations, consultez <xref:System.Runtime.InteropServices.CharSet>.  
  
 Un autre tableau de taille fixe courant est le tableau [bool](../../../csharp/language-reference/keywords/bool.md).  Les éléments dans un tableau `bool` ont toujours une taille d'un octet.  Les tableaux `bool` ne sont pas appropriés pour la création de tableaux d'octets ou de mémoires tampons.  
  
> [!NOTE]
>  À l'exception de la mémoire créée à l'aide de [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), le compilateur C\# et le common language runtime \(CLR\) n'effectuent pas de contrôles du dépassement de mémoire tampon de la sécurité.  Comme avec le code unsafe, soyez prudent.  
  
 Les mémoires tampons unsafe sont différentes des tableaux normaux :  
  
-   Vous pouvez utiliser des mémoires tampons unsafe dans un contexte unsafe uniquement.  
  
-   Les mémoires tampons unsafe sont toujours des vecteurs, ou tableaux unidimensionnels.  
  
-   La déclaration du tableau doit inclure un compte, tel que `char id[8]`.  Vous ne pouvez pas utiliser `char id[]` à la place.  
  
-   Les mémoires tampons unsafe peuvent uniquement être des champs d'instance de structs dans un contexte unsafe.  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [Interopérabilité](../../../csharp/programming-guide/interop/interoperability.md)