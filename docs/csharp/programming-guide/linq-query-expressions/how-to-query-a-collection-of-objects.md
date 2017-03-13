---
redirect_url: /dotnet/articles/csharp/linq/query-a-collection-of-objects
caps.handback.revision: 8
---
# Comment&#160;: interroger une collection d&#39;objets (Guide de programmation&#160;C#)
Cet exemple montre comment effectuer une requête simple sur une liste d'objets `Student`.  Chaque objet `Student` contient des informations de base à propos de l'étudiant, et une liste qui représente les notes de l'étudiant lors de quatre examens.  
  
 Cette application sert de cadre pour de nombreux autres exemples dans cette section qui utilisent la même source de données `students` .  
  
## Exemple  
 La requête suivante retourne les étudiants qui ont reçu une note supérieure ou égale à 90 lors de leur premier examen.  
  
 [!code-cs[csProgGuideLINQ#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-query-a-collection-of-objects_1.cs)]  
  
 Cette requête est volontairement simple pour vous permettre d'expérimenter.  Par exemple, vous pouvez essayer plus de prédicats dans la clause `where` ou utiliser une clause `orderby` pour trier les résultats.  
  
## Compilation du code  
  
-   Créez un projet [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] qui cible la version 3.5 du .NET Framework.  Par défaut, le projet possède une référence à System.Core.dll et une directive `using` pour l'espace de noms System.Linq.  
  
-   Copiez le code dans votre projet.  
  
-   Appuyez sur F5 pour compiler et exécuter le programme.  
  
-   Appuyez sur une touche pour quitter la fenêtre de console.  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)