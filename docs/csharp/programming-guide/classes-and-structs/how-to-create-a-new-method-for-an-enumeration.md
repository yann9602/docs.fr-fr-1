---
title: "Guide pratique pour créer une méthode pour une énumération (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
caps.latest.revision: 7
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
ms.openlocfilehash: 3d15cbcdd81584ea5c6ab40d231183f883a7a805
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Guide pratique pour créer une méthode pour une énumération (Guide de programmation C#) 
Vous pouvez utiliser des méthodes d’extension pour ajouter des fonctionnalités propres à un type enum particulier.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, l’énumération `Grades` représente les notes qu’un étudiant peut obtenir dans une classe. Une méthode d’extension nommée `Passing` est ajoutée au type `Grades` pour que chaque instance de ce type « sache » maintenant si elle représente une note au-dessus de la moyenne.  
  
 [!code-cs[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 Notez que la classe `Extensions` contient également une variable statique qui est mise à jour de manière dynamique, et que la valeur de retour de la méthode d’extension reflète la valeur actuelle de cette variable. Cela démontre que, dans les coulisses, les méthodes d’extension sont appelées directement sur la classe statique dans laquelle elles sont définies.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour exécuter ce code, copiez et collez-le dans un projet d’application console Visual C# qui a été créé dans [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)]. Par défaut, ce projet cible la version 3.5 du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], et il a une référence à System.Core.dll et une directive `using` pour System.Linq. Si un ou plusieurs de ces éléments requis sont manquants dans le projet, vous pouvez les ajouter manuellement.   
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Méthodes d’extension](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
