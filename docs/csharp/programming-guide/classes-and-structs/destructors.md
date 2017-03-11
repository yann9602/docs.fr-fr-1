---
title: "Destructeurs (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "~ (C#), en destructeurs"
  - "langage C#, destructeurs"
  - "destructeurs (C#)"
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# Destructeurs (Guide de programmation C#)
Les destructeurs permettent de détruire les instances des classes.  
  
## Notes  
  
-   Les destructeurs ne peuvent pas être définis dans des struct.  Ils sont utilisés uniquement avec les classes.  
  
-   Une classe peut posséder un seul destructeur.  
  
-   Les destructeurs ne peuvent pas être hérités ou surchargés.  
  
-   Les destructeurs ne peuvent pas être appelés.  Ils sont appelés automatiquement.  
  
-   Un destructeur n'accepte pas de modificateurs ni de paramètres.  
  
 Par exemple, voici la déclaration d'un destructeur pour la classe `Car` :  
  
 [!code-cs[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/destructors_1.cs)]  
  
 Le destructeur appelle implicitement <xref:System.Object.Finalize%2A> sur la classe de base de l'objet.  Ainsi, le code du destructeur précédent est traduit implicitement dans le code suivant :  
  
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
  
 Cela signifie que la méthode `Finalize` est appelée itérativement pour toutes les instances dans la chaîne d'héritage, de la plus dérivée à la moins dérivée.  
  
> [!NOTE]
>  Les destructeurs vides ne doivent pas être utilisés.  Lorsqu'une classe contient un destructeur, une entrée est créée dans la file d'attente `Finalize`.  Lorsque le destructeur est appelé, le garbage collector est appelé pour traiter la file d'attente.  Si le destructeur est vide, cela provoque seulement une perte inutile de performance.  
  
 Le programmeur n'a aucun contrôle sur le moment où le destructeur est appelé car cela est déterminé par le garbage collector.  Le garbage collector recherche les objets qui ne sont plus utilisés par l'application.  S'il considère qu'un objet est candidat à la destruction, il appelle le destructeur \(s'il y a lieu\) et libère la mémoire utilisée pour stocker l'objet.  Les destructeurs sont également appelés à la fermeture du programme.  
  
 Il est possible de forcer l'exécution du garbage collection en appelant <xref:System.GC.Collect%2A>, mais cela doit être évité dans la plupart des cas, en raison des problèmes de performances qui peuvent survenir.  
  
## Utilisation de destructeurs pour libérer des ressources  
 En général, C\# ne nécessite pas autant de gestion de mémoire que lorsque vous développez avec un langage qui ne cible pas un runtime avec garbage collection.  En effet, le garbage collector .NET Framework gère implicitement l'allocation et la libération de mémoire pour vos objets.  Toutefois, lorsque votre application encapsule des ressources non gérées telles que des fenêtres, des fichiers ou des connexions réseau, vous devez utiliser des destructeurs pour libérer ces ressources.  Lorsque l'objet peut être détruit, le garbage collector en exécute la méthode `Finalize`.  
  
## Libération explicite de ressources  
 Si votre application utilise une ressource externe coûteuse, nous vous recommandons également de fournir un moyen de libérer explicitement la ressource avant que le garbage collector ne libère l'objet.  Pour cela, vous devez implémenter une méthode `Dispose` à partir de l'interface <xref:System.IDisposable> qui effectue le nettoyage nécessaire de l'objet.  Cela peut améliorer considérablement les performances de l'application.  Ce contrôle explicite sur les ressources permet au destructeur de garantir le nettoyage des ressources en cas d'échec de l'appel de la méthode `Dispose`.  
  
 Pour plus d'informations sur le nettoyage des ressources, consultez les rubriques suivantes :  
  
-   [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)  
  
-   [Implementing a Dispose Method](../Topic/Implementing%20a%20Dispose%20Method.md)  
  
-   [using, instruction](../../../csharp/language-reference/keywords/using-statement.md)  
  
## Exemple  
 Dans l'exemple suivant, trois classes sont créées qui forment une chaîne d'héritage.  La classe `First` est la classe de base, la classe `Second` est dérivée de la classe `First` et la classe `Third` est dérivée de la classe `Second`.  Tous les trois possèdent des destructeurs.  Dans `Main()`, une instance de la classe la plus dérivée est créée.  Lorsque le programme s'exécute, notez que les destructeurs sont appelés automatiquement pour les trois classes, dans l'ordre, du plus dérivé au moins dérivé.  
  
 [!code-cs[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/destructors_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 <xref:System.IDisposable>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)