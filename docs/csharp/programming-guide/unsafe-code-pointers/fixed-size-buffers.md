---
title: "Mémoires tampons de taille fixe (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3f99c2c6d477fca988fcca77de5ca5c2f8addd4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Mémoires tampons de taille fixe (Guide de programmation C#)
En C#, vous pouvez utiliser l’instruction [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) pour créer une mémoire tampon avec un tableau de taille fixe dans une structure de données. Cela est utile lorsque vous utilisez du code existant, tel que du code écrit dans d’autres langages, des DLL préexistantes ou des projets COM. Le tableau fixe peut accepter tous les attributs ou modificateurs qui sont autorisés pour les membres de structures régulières. La seule restriction est que le tableau doit être de type `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a>Notes  
 Dans les versions antérieures de C#, il était difficile de déclarer une structure de taille fixe de style C++, car un struct C# qui contient un tableau ne contient pas les éléments du tableau. Le struct contient une référence aux éléments du tableau.  
  
 Avec le langage C# 2.0, il est désormais possible d’incorporer un tableau de taille fixe dans un [struct](../../../csharp/language-reference/keywords/struct.md) lorsqu’il est utilisé dans un bloc de code [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
 Par exemple, avant C# 2.0, le `struct` suivant avait une taille de 8 octets. Le tableau `pathName` est une référence au tableau alloué par tas :  
  
 [!code-csharp[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 Avec C# 2.0, un `struct` peut maintenant contenir un tableau incorporé. Dans l’exemple suivant, le tableau `fixedBuffer` a une taille fixe. Pour accéder aux éléments du tableau, vous devez utiliser une instruction `fixed` pour établir un pointeur vers le premier élément. L’instruction `fixed` épingle une instance de `fixedBuffer` à un emplacement spécifique de la mémoire.  
  
 [!code-csharp[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 La taille du tableau `char` de 128 éléments est de 256 octets. Les mémoires tampons [char](../../../csharp/language-reference/keywords/char.md) de taille fixe acceptent toujours deux octets par caractère, quel que soit l’encodage. Ceci est vrai même lorsque les mémoires tampons char sont marshalées vers des méthodes ou des structs d’API avec `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`. Pour plus d'informations, consultez <xref:System.Runtime.InteropServices.CharSet>.  
  
 Un autre tableau courant de taille fixe est le tableau [bool](../../../csharp/language-reference/keywords/bool.md). La taille des éléments d’un tableau `bool` est toujours d’un octet. Les tableaux `bool` ne conviennent pas à la création de tableaux d’octets ou de mémoires tampons.  
  
> [!NOTE]
>  Le compilateur C# et le common language runtime (CLR) ne contrôlent pas le dépassement de la mémoire tampon de sécurité, sauf pour la mémoire créée à l’aide de [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md). Comme toujours pour le code unsafe, la prudence est recommandée.  
  
 Les mémoires tampons unsafe diffèrent des tableaux normaux à différents niveaux :  
  
-   Les mémoires tampons unsafe peuvent uniquement être utilisées dans un contexte unsafe.  
  
-   Les mémoires tampons unsafe sont toujours des vecteurs ou des tableaux unidimensionnels.  
  
-   La déclaration du tableau doit inclure un nombre, tel que `char id[8]`. Vous ne pouvez pas utiliser `char id[]` à la place.  
  
-   Les mémoires tampons unsafe peuvent uniquement être des champs d’instance de structs dans un contexte unsafe.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [Interopérabilité](../../../csharp/programming-guide/interop/index.md)
