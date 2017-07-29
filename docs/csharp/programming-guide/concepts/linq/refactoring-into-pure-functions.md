---
title: Refactorisation dans des fonctions pures (C#)
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
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e3bb704cab77d4ad9895624bf7f721920000378
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="refactoring-into-pure-functions-c"></a>Refactorisation dans des fonctions pures (C#)
L'un des aspects importants des transformations fonctionnelles pures consiste à apprendre à refactoriser le code à l'aide de fonctions pures.  
  
> [!NOTE]
>  La nomenclature courante dans la programmation fonctionnelle consiste à refactoriser les programmes à l'aide de fonctions pures. En Visual Basic et C++, cela correspond à l'utilisation des fonctions dans les langages respectifs. Toutefois, en C#, les fonctions portent le nom de méthodes. Pour les besoins de cette discussion, une fonction pure est implémentée en tant que méthode en C#.  
  
 Comme mentionné précédemment dans cette section, une fonction pure présente deux caractéristiques utiles :  
  
-   Elle n'a aucun effet secondaire. La fonction ne change aucune variable et aucune donnée de tout type en dehors de la fonction.  
  
-   Elle est cohérente. Étant donné le même ensemble de données d'entrée, elle retournera toujours la même valeur de sortie.  
  
 L'une des manières de basculer vers la programmation fonctionnelle consiste à refactoriser le code existant afin d'éliminer les effets secondaires indésirables et les dépendances externes. De cette manière, vous pouvez créer des versions avec fonctions pures du code existant.  
  
 Cette rubrique explique ce qu'est et ce que n'est pas une fonction pure. Le [Didacticiel : manipulation de contenu dans un document WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) montre comment manipuler un document WordprocessingML et inclut deux exemples illustrant comment refactoriser à l’aide d’une fonction pure.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Suppression des effets secondaires et des dépendances externes  
 Les exemples suivants comparent deux fonctions non pures et une fonction pure.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Fonction non pure qui modifie un membre de classe  
 Dans le code suivant, la fonction `HypenatedConcat` n'est pas pure car elle modifie le membre de données `aMember` dans la classe :  
  
```csharp  
public class Program  
{  
    private static string aMember = "StringOne";  
  
    public static void HypenatedConcat(string appendStr)  
    {  
        aMember += '-' + appendStr;  
    }  
  
    public static void Main()  
    {  
        HypenatedConcat("StringTwo");  
        Console.WriteLine(aMember);  
    }  
}  
```  
  
 Ce code génère la sortie suivante :  
  
```  
StringOne-StringTwo  
```  
  
 Notez qu’il importe peu que les données modifiées aient un accès `public` ou `private`, ou qu’elles correspondent à un membre `static` ou à un membre d’instance. Une fonction pure ne change aucune donnée en dehors de la fonction.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Fonction non pure qui modifie un argument  
 En outre, la version suivante de cette même fonction n'est pas pure car elle modifie le contenu de son paramètre, `sb`.  
  
```csharp  
public class Program  
{  
    public static void HypenatedConcat(StringBuilder sb, String appendStr)  
    {  
        sb.Append('-' + appendStr);  
    }  
  
    public static void Main()  
    {  
        StringBuilder sb1 = new StringBuilder("StringOne");  
        HypenatedConcat(sb1, "StringTwo");  
        Console.WriteLine(sb1);  
    }  
}  
```  
  
 Cette version du programme génère la même sortie que la première version, car la fonction `HypenatedConcat` a modifié la valeur (l'état) de son premier paramètre en appelant la fonction membre <xref:System.Text.StringBuilder.Append%2A>. Notez que cette altération a lieu en dépit du fait que `HypenatedConcat` utilise le passage de paramètre avec appel par valeur.  
  
> [!IMPORTANT]
>  Pour les types de référence, si vous passez un paramètre par valeur, une copie de la référence à un objet est passée. Cette copie est toujours associée aux mêmes données d'instance que la référence d'origine (jusqu'à ce que la variable de référence soit assignée à un nouvel objet). L'appel par référence n'est pas forcément nécessaire pour qu'une fonction modifie un paramètre.  
  
### <a name="pure-function"></a>Fonction pure  
 Cette autre version du programme montre comment implémenter la fonction `HypenatedConcat` en tant que fonction pure.  
  
```csharp  
class Program  
{  
    public static string HyphenatedConcat(string s, string appendStr)  
    {  
        return (s + '-' + appendStr);  
    }  
  
    public static void Main(string[] args)  
    {  
        string s1 = "StringOne";  
        string s2 = HyphenatedConcat(s1, "StringTwo");  
        Console.WriteLine(s2);  
    }  
}  
```  
  
 Là encore, cette version génère la même ligne de sortie : `StringOne-StringTwo`. Notez que pour conserver la valeur concaténée, elle est stockée dans la variable intermédiaire `s2`.  
  
 L'une des approches qui peuvent se révéler très utiles consiste à écrire des fonctions localement impures (à savoir, qui déclarent et modifient des variables locales) mais globalement pures. Ces fonctions possèdent une grande partie des caractéristiques de composabilité requises, mais elles évitent certaines des tâches de programmation fonctionnelle plus compliquées, telles que l'utilisation de la récursivité lorsqu'une simple boucle génèrerait le même résultat.  
  
## <a name="standard-query-operators"></a>Opérateurs de requête standard  
 L'une des caractéristiques importantes des opérateurs de requête standard est qu'ils sont implémentés en tant que fonctions pures.  
  
 Pour plus d’informations, consultez [Présentation des opérateurs de requête standard (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction aux transformations fonctionnelles pures (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)   
 [Comparaison de la programmation fonctionnelle et de la programmation impérative (C#)](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)

