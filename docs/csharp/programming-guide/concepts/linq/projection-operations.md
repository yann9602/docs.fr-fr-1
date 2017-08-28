---
title: "Opérations de projection (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2b95072bf6e53ef090a7a7b398fa873bb0bf5b46
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="projection-operations-c"></a>Opérations de projection (C#)
La projection désigne l’opération de transformation d’un objet en une nouvelle forme qui se compose souvent uniquement des propriétés à utiliser ensuite. À l'aide de la projection, vous pouvez créer un nouveau type qui est généré à partir de chaque objet. Vous pouvez projeter une propriété et effectuer une fonction mathématique sur celle-ci. Vous pouvez également projeter l’objet d’origine sans le modifier.  
  
 Les méthodes d’opérateurs de requête standard qui effectuent des opérations de projection sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d'expression de requête C#|Informations complémentaires|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Select|Projette les valeurs qui sont basées sur une fonction de transformation.|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=fullName>|  
|SelectMany|Projette les séquences de valeurs qui sont basées sur une fonction de transformation, puis les aplatit en une seule séquence.|Utilisation de plusieurs clauses `from`|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>Exemples de syntaxe d'expression de requête  
  
### <a name="select"></a>Select  
 L’exemple suivant utilise la clause `select` pour projeter la première lettre de chaque chaîne dans une liste de chaînes.  
  
```csharp  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### <a name="selectmany"></a>SelectMany  
 L’exemple suivant utilise plusieurs clauses `from` pour projeter tous les mots de chaque chaîne dans une liste de chaînes.  
  
```csharp  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## <a name="select-versus-selectmany"></a>Comparaison de Select et SelectMany  
 Les deux clauses `Select()` et `SelectMany()` retournent une valeur de résultat (ou des valeurs) à partir des valeurs sources. `Select()` retourne une seule valeur de résultat pour chaque valeur source. Le résultat global est donc une collection qui a le même nombre d’éléments que la collection source. En revanche, `SelectMany()` retourne un résultat global unique qui contient des sous-collections concaténées à partir de chaque valeur source. La fonction de transformation qui est passée comme argument à `SelectMany()` doit retourner une séquence énumérable de valeurs pour chaque valeur source. Ces séquences énumérables sont ensuite concaténées par `SelectMany()` pour créer une seule grande séquence.  
  
 Les deux illustrations suivantes montrent en quoi les actions de ces deux méthodes sont différentes d’un point de vue conceptuel. Dans chaque cas, supposons que la fonction (de transformation) du sélecteur sélectionne le tableau de fleurs (Flowers) à partir de chaque valeur source.  
  
 Cette illustration montre de quelle manière `Select()` retourne une collection qui a le même nombre d’éléments que la collection source.  
  
 ![Illustration de l’action de la clause Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 Cette illustration montre de quelle façon `SelectMany()` concatène la séquence intermédiaire de tableaux en une seule valeur de résultat final qui contient chaque valeur de chaque tableau intermédiaire.  
  
 ![Graphique montrant l’action de SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")  
  
### <a name="code-example"></a>Exemple de code  
 L’exemple suivant compare le comportement de `Select()` et de `SelectMany()`. Le code crée un « bouquet » de fleurs en prenant les deux premiers éléments de chaque liste de noms de fleurs de la collection source. Dans cet exemple, la « valeur unique » que la fonction de transformation <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> utilise est elle-même une collection de valeurs. Cela nécessite d’utiliser la boucle `foreach` supplémentaire pour énumérer chaque chaîne dans chaque sous-séquence.  
  
```csharp  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********              
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq>   
 [Présentation des opérateurs de requête standard (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [select, clause](../../../../csharp/language-reference/keywords/select-clause.md)   
 [Guide pratique pour remplir des collections d’objets issues de plusieurs sources (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)   
 [Guide pratique pour fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)

