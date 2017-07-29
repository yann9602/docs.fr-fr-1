---
title: Constructeurs statiques (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: 23
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 73df76c61f393bf5fe09af66935acfbac4b5663f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="static-constructors-c-programming-guide"></a>Constructeurs statiques (Guide de programmation C#)
Un constructeur statique est utilisé pour initialiser des données [statiques](../../../csharp/language-reference/keywords/static.md) ou pour effectuer une action particulière qui ne doit être effectuée qu’une seule fois. Il est automatiquement appelé avant la création de la première instance ou le référencement d’un membre statique.  
  
 [!code-cs[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 Les constructeurs statiques ont les propriétés suivantes :  
  
-   Un constructeur statique n’accepte pas de modificateur d’accès et n’a pas de paramètre.  
  
-   Un constructeur statique est automatiquement appelé pour initialiser la [classe](../../../csharp/language-reference/keywords/class.md) avant la création de la première instance ou le référencement d’un membre statique.  
  
-   Un constructeur statique ne peut pas être appelé directement.  
  
-   L’utilisateur n’a aucun contrôle sur le moment d’exécution du constructeur statique dans le programme.  
  
-   Généralement, on utilise des constructeurs statiques quand la classe utilise un fichier journal et que le constructeur sert à écrire des entrées dans ce fichier.  
  
-   Les constructeurs statiques sont également utiles pour la création de classes wrapper pour du code non managé, quand le constructeur peut appeler la méthode `LoadLibrary`.  
  
-   Si un constructeur statique lève une exception, le runtime ne l’appelle pas une deuxième fois et le type reste non initialisé pour la durée de vie du domaine d’application dans lequel votre programme s’exécute.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la classe `Bus` possède un constructeur statique. Quand la première instance de `Bus` est créée (`bus1`), le constructeur statique est appelé pour initialiser la classe. L’exemple de sortie vérifie que le constructeur statique s’exécute une seule fois, même si deux instances de `Bus` sont créées, et qu’il s’exécute avant le constructeur d’instance.  
  
 [!code-cs[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)

