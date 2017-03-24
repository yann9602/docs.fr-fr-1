---
title: "#line (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#line"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#line (directive C#)"
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# #line (r&#233;f&#233;rence C#)
`#line` vous permet de modifier le numéro de ligne du compilateur et \(de manière facultative\) la sortie du nom du fichier d'erreurs et d'avertissements.  Cet exemple montre comment signaler deux avertissements associés à des numéros de lignes.  La directive `#line 200` force le numéro de ligne sur 200 \(bien que la valeur par défaut soit \#7\) et jusqu'à la prochaine directive \#line, le nom de fichier sera signalé comme "Special".  La directive par défaut \#line retourne la numérotation des lignes à leur numérotation par défaut, qui compte les lignes renumérotées par la directive précédente.  
  
```  
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## Notes  
 La directive `#line` peut être utilisée dans une étape intermédiaire automatisée dans le processus de génération.  Par exemple, si des lignes sont supprimées du fichier de code source d'origine, mais que vous souhaitez que le compilateur génère des résultats fondés sur la numérotation des lignes d'origine dans le fichier, vous pouvez supprimer des lignes et simuler ensuite la numérotation des lignes d'origine à l'aide de `#line`.  
  
 La directive `#line hidden` masque les lignes suivantes du débogueur, de sorte que lorsque le développeur parcourt le code, toutes les lignes comprises entre `#line hidden` et la directive `#line` suivante \(en considérant qu'il ne s'agit pas d'une autre directive `#line hidden`\) sont ignorées.  Cette option peut aussi être utilisée pour permettre à ASP.NET de différencier du code défini par l'utilisateur de code généré par l'ordinateur.  Même si ASP.NET représente le consommateur principal de cette fonctionnalité, il est probable que d'autres générateurs sources l'utiliseront.  
  
 Une directive `#line hidden` n'affecte pas les noms de fichiers ni les numéros de lignes dans les rapports d'erreurs.  Ainsi, si une erreur est rencontrée dans un bloc masqué, le compilateur signale le nom du fichier en cours et le numéro de ligne de l'erreur.  
  
 La directive `#line filename` spécifie le nom de fichier que vous voulez faire apparaître dans le résultat de la compilation.  Par défaut, le nom réel du fichier de code source est utilisé.  Le nom de fichier doit être placé entre guillemets doubles \(""\) et doit être précédé par un numéro de ligne.  
  
 Un fichier de code source peut contenir un nombre quelconque de directives `#line`.  
  
## Exemple 1  
 Cet exemple montre comment le débogueur ignore les lignes masquées dans le code.  Lorsque vous exécutez l'exemple, trois lignes de texte sont affichées.  Toutefois, lorsque vous définissez un point de rupture, comme illustré dans cet exemple, et appuyez sur F10 pour progresser dans le code, vous remarquez que le débogueur ignore la ligne masquée.  Notez aussi que même si vous définissez un point de rupture sur la ligne masquée, le débogueur l'ignore.  
  
```  
// preprocessor_linehidden.cs  
using System;  
class MainClass   
{  
    static void Main()   
    {  
        Console.WriteLine("Normal line #1."); // Set break point here.  
#line hidden  
        Console.WriteLine("Hidden line.");  
#line default  
        Console.WriteLine("Normal line #2.");  
    }  
}  
```  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C\#](../../../csharp/language-reference/preprocessor-directives/index.md)