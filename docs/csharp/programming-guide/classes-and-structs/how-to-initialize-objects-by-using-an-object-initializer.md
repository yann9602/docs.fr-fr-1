---
title: "Guide pratique pour initialiser des objets à l’aide d’un initialiseur d’objet (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9d6537332b4ddcca185a0ac3039a925e0b3fcef2
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Guide pratique pour initialiser des objets à l'aide d'un initialiseur d'objet (Guide de programmation C#)
Vous pouvez utiliser des initialiseurs d’objets pour initialiser des objets de type de façon déclarative sans appeler explicitement un constructeur pour le type.  
  
 Les exemples suivants montrent comment utiliser des initialiseurs d’objets avec des objets nommés. Le compilateur traite les initialiseurs d’objets en accédant d’abord au constructeur d’instance par défaut, puis en traitant les initialisations des membres. Ainsi, si le constructeur par défaut est déclaré comme `private` dans la classe, les initialiseurs d’objets qui nécessitent un accès public échoueront.  
  
 Vous devez utiliser un initialiseur d’objet si vous définissez un type anonyme. Pour plus d’informations, consultez [Guide pratique pour retourner des sous-ensembles de propriétés d’éléments dans une requête](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment initialiser un nouveau type `StudentName` à l’aide d’initialiseurs d’objets.  
  
 [!code-cs[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment initialiser une collection de types `StudentName` à l’aide d’un initialiseur de collection. Notez qu’un initialiseur de collection est une série d’initialiseurs d’objets séparés par des virgules.  
  
 [!code-cs[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour exécuter ce code, copiez et collez la classe dans un projet d’application console Visual C# qui a été créé dans [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)].   
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Initialiseurs d’objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
