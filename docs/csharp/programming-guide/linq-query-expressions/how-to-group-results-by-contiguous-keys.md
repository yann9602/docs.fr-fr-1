---
redirect_url: /dotnet/articles/csharp/linq/group-results-by-contiguous-keys
caps.handback.revision: 11
---
# Comment&#160;: regrouper des r&#233;sultats par cl&#233;s contigu&#235;s (Guide de programmation&#160;C#)
L'exemple suivant indique comment regrouper des éléments dans des blocs qui représentent des sous\-séquences de clés contiguës.  Par exemple, supposons que vous êtes face à la séquence suivante de paires clé\-valeur :  
  
|Clé|Valeur|  
|---------|------------|  
|A|We|  
|A|think|  
|A|that|  
|B|Linq|  
|C|est|  
|A|really|  
|B|cool|  
|B|\!|  
  
 Les groupes suivants seront créés dans cet ordre :  
  
1.  We, think, that  
  
2.  Linq  
  
3.  est  
  
4.  really  
  
5.  cool, \!  
  
 La solution est implémentée comme une méthode d'extension thread\-safe qui retourne ses résultats en continu.  En d'autres termes, elle produit ses groupes au fur et à mesure qu'elle parcourt la séquence source.  Contrairement aux opérateurs `group` ou `orderby`, elle peut commencer à retourner des groupes à l'appelant avant que toute la séquence ait été lue.  
  
 La sécurité des threads est obtenue en faisant une copie de chaque groupe ou bloc pendant que la séquence source est itérée, comme l'expliquent les commentaires du code source.  Si la séquence source comporte une longue séquence d'éléments contigus, le Common Language Runtime risque de lever une <xref:System.OutOfMemoryException>.  
  
## Exemple  
 L'exemple suivant montre la méthode d'extension et le code client qui l'utilise.  
  
 [!code-cs[cscsrefContiguousGroups#1](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 Pour utiliser la méthode d'extension dans votre projet, copiez la classe statique `MyExtensions` vers un fichier de code source nouveau ou existant et, si nécessaire, ajoutez une directive `using` pour l'espace de noms où elle se trouve.  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Classification of Standard Query Operators by Manner of Execution](../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)