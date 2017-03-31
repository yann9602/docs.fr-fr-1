---
title: Destructeurs (Guide de programmation C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- ~ [C#], in destructors
- C# language, destructors
- destructors [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
caps.latest.revision: 24
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
ms.openlocfilehash: 6940be34b6cc15f006901e6d14d2a38ebb5d012a
ms.lasthandoff: 03/13/2017

---
# <a name="destructors-c-programming-guide"></a>Destructeurs (Guide de programmation C#)
Les destructeurs permettent de détruire les instances des classes.  
  
## <a name="remarks"></a>Notes  
  
-   Les destructeurs ne peuvent pas être définis dans des structs. Ils sont utilisés uniquement avec les classes.  
  
-   Une classe ne peut avoir qu’un seul destructeur.  
  
-   Les destructeurs ne peuvent pas être hérités ou surchargés.  
  
-   Les destructeurs ne peuvent pas être appelés manuellement. Ils sont appelés automatiquement.  
  
-   Un destructeur ne prend pas de modificateur et n’a pas de paramètre.  
  
 Par exemple, voici une déclaration de destructeur pour la classe `Car` :  
  
 [!code-cs[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  
  
 Le destructeur appelle implicitement <xref:System.Object.Finalize%2A> sur la classe de base de l’objet. Ainsi, le code du destructeur précédent est traduit implicitement en ce code :  
  
```  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 Cela signifie que la méthode `Finalize` est appelée de manière récursive pour toutes les instances de la chaîne d’héritage, de la plus dérivée à la moins dérivée.  
  
> [!NOTE]
>  Les destructeurs vides ne doivent pas être utilisés. Quand une classe contient un destructeur, une entrée est créée dans la file d’attente `Finalize`. Quand le destructeur est appelé, le récupérateur de mémoire est appelé pour traiter la file d’attente. Si le destructeur est vide, cela ne fait que provoquer une dégradation des performances inutile.  
  
 Le programmeur n’a aucun contrôle sur le moment où le destructeur est appelé, car ce moment est déterminé par le récupérateur de mémoire. Le récupérateur de mémoire recherche les objets qui ne sont plus utilisés par l’application. S’il considère qu’un objet peut être détruit, il appelle le destructeur (s’il y en a un) et libère la mémoire utilisée pour stocker l’objet. Les destructeurs sont également appelés quand le programme s’arrête.  
  
 Il est possible de forcer le nettoyage de la mémoire en appelant <xref:System.GC.Collect%2A>, mais la plupart du temps c’est à éviter car cela peut créer des problèmes de performances.  
  
## <a name="using-destructors-to-release-resources"></a>Utilisation de destructeurs pour libérer des ressources  
 En général, C# ne nécessite pas autant de gestion de mémoire que quand vous développez avec un langage qui ne cible pas un runtime avec nettoyage de la mémoire. En effet, le récupérateur de mémoire .NET Framework gère implicitement l’allocation et la libération de la mémoire pour vos objets. Toutefois, quand votre application encapsule des ressources non managées, telles que des fenêtres, des fichiers et des connexions réseau, vous devez utiliser des destructeurs pour libérer ces ressources. Quand l’objet peut être détruit, le récupérateur de mémoire exécute la méthode `Finalize` de l’objet.  
  
## <a name="explicit-release-of-resources"></a>Libération explicite de ressources  
 Si votre application utilise une ressource externe coûteuse, nous vous recommandons également de proposer un moyen de libérer explicitement la ressource avant que le récupérateur de mémoire ne libère l’objet. Pour cela, vous devez implémenter une méthode `Dispose` à partir de l’interface <xref:System.IDisposable> qui effectue le nettoyage nécessaire pour l’objet. Cela peut améliorer considérablement les performances de l’application. Même avec ce contrôle explicite des ressources, le destructeur devient un dispositif de protection pour nettoyer les ressources si l’appel à la méthode `Dispose` a échoué.  
  
 Pour plus d’informations sur le nettoyage des ressources, consultez les rubriques suivantes :  
  
-   [Nettoyage de ressources non managées](http://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213)  
  
-   [Implémentation d’une méthode dispose](http://msdn.microsoft.com/library/eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9)  
  
-   [using, instruction](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée trois classes qui forment une chaîne d’héritage. La classe `First` est la classe de base, `Second` est dérivée de `First`, et `Third` est dérivée de `Second`. Toutes trois ont des destructeurs. Dans `Main()`, une instance de la classe la plus dérivée est créée. Quand le programme s’exécute, notez que les destructeurs des trois classes sont appelés automatiquement, et dans l’ordre, de la plus dérivée à la moins dérivée.  
  
 [!code-cs[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IDisposable>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Nettoyage de la mémoire](../../../standard/garbagecollection/index.md)
