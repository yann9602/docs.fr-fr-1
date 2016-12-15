---
title: "using, directive (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "using (directive C#)"
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# using, directive (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

La directive `using` a trois utilisations :  
  
-   Pour autoriser l'utilisation de types dans un espace de noms pour ne pas avoir à qualifier l'utilisation d'un type dans cet espace de noms :  
  
    ```c#  
    using System.Text;  
    ```  
  
-   Pour vous permettre d'accéder aux membres statiques d'un type sans devoir qualifier l'accès avec le nom du type :  
  
    ```c#  
    using static System.Math;  
    ```  
  
-   Pour créer un alias pour un espace de noms ou un type.  Il s'agit d'une *directive d'alias using*.  
  
    ```c#  
    using Project = PC.MyCompany.Project;  
    ```  
  
 Le mot clé `using` est également utilisé pour créer des *instructions using*, qui garantissent que les objets <xref:System.IDisposable> tels que les fichiers et les polices sont gérés correctement.  Pour plus d'informations, consultez [Instruction using](../../../csharp/language-reference/keywords/using-statement.md).  
  
## Utilisation du type static  
 Vous pouvez accéder aux membres statiques d'un type sans devoir qualifier l'accès avec le nom du type :  
  
```c#  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
  
```  
  
 `Using static` importe uniquement les membres statiques accessibles et les types imbriqués déclarés dans le type spécifié.  Les membres hérités ne sont pas importés.  Vous pouvez importer à partir de n'importe quel type nommé avec une directive static, notamment des modules Visual Basic.  Si des fonctions de niveau supérieur F\# apparaissent dans les métadonnées en tant que membres statiques d'un type nommé dont le nom est un identificateur C\# valide, alors les fonctions F\# peuvent être importées.  
  
 `Using static` rend les méthodes d'extension déclarées dans le type spécifié disponibles pour la recherche de méthode d'extension.  Toutefois, les noms des méthodes d'extension ne sont pas importés dans la portée pour la référence non qualifiée dans le code.  
  
 Les méthodes portant le même nom importées à partir de différents types par différentes directives using static dans la même unité de compilation ou le même espace de noms forment un groupe de méthodes.  La résolution de surcharge au sein de ces groupes de méthodes suit des règles C\# normales.  
  
## Notes  
 La portée d'une directive `using` se limite au fichier dans lequel elle apparaît.  
  
 Créez un alias `using` pour faciliter la qualification d'un identificateur pour un espace de noms ou un type.  Le côté droit d'une directives d'alias using doit toujours être un type complet quelles que soient les directives using placées avant.  
  
 Créez une directive `using` pour utiliser les types dans un espace de noms sans avoir à spécifier l'espace de noms.  Une directive `using` ne vous donne pas accès à des espaces de noms imbriqués dans l'espace de noms que vous spécifiez.  
  
 Les espaces de noms sont organisés en deux catégories : définis par l'utilisateur et définis par le système.  Les espaces de noms définis par l'utilisateur sont des espaces de noms définis dans votre code.  Pour obtenir la liste des espaces de noms définis par le système, consultez [Bibliothèque de classes .NET Framework](http://go.microsoft.com/fwlink/?LinkID=227195).  
  
 Pour obtenir des exemples de références de méthodes dans d'autres assemblys, consultez [Création et utilisation des DLL C\#](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Exemple 1  
  
### Description  
 L'exemple suivant montre comment définir et utiliser un alias `using` pour un espace de noms :  
  
### Code  
 [!code-cs[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
### Commentaires  
 Une directive d'alias using ne peut pas avoir un type générique ouvert sur le côté droit.  Par exemple, vous ne pouvez pas créer un alias using pour un List\<T\>, mais vous pouvez en créer un pour un List\<int\>.  
  
## Exemple 2  
  
### Description  
 L'exemple suivant montre comment définir une directive `using` et un alias `using` pour une classe :  
  
### Code  
 [!code-cs[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Utilisation d'espaces de noms](../../../csharp/programming-guide/namespaces/using-namespaces.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés d'espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [Espaces de noms](../../../csharp/programming-guide/namespaces/index.md)   
 [using, instruction](../../../csharp/language-reference/keywords/using-statement.md)