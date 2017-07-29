---
title: 'Comment : initialiser un dictionnaire avec un initialiseur de collection (Guide de programmation C#)'
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 41d6a9934daaa1274901e20de58cfd480c904bfa
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Comment : initialiser un dictionnaire avec un initialiseur de collection (Guide de programmation C#)
Une méthode <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> prend deux paramètres, un pour la clé et l’autre pour la valeur. Pour initialiser un <xref:System.Collections.Generic.Dictionary`2>, or any collection whose ` ou toute collection dont la méthode Add prend plusieurs paramètres, mettez chaque jeu de paramètres entre accolades, comme illustré dans l’exemple suivant.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple de code suivant, un <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type ` est initialisé avec des instances de type StudentName`.  
  
 [!code-cs[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 Notez les deux paires d’accolades dans chaque élément de la collection. Les accolades les plus intérieures encadrent l’initialiseur d’objet pour le `StudentName`, et les accolades les plus extérieures encadrent l’initialiseur pour la paire clé/valeur qui sera ajoutée à `students`<xref:System.Collections.Generic.Dictionary`2>. Pour finir, l’initialiseur de collection entier pour le dictionnaire est placé entre accolades.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour exécuter ce code, copiez et collez la classe dans un projet d’application console Visual C# qui a été créé dans [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)]. Par défaut, ce projet cible la version 3.5 du [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], et il a une référence à System.Core.dll et une directive using pour System.Linq. Si un ou plusieurs de ces éléments requis sont manquants dans le projet, vous pouvez les ajouter manuellement.   
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Initialiseurs d’objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

