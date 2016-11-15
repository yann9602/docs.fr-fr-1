---
title: "Caractères d’échappement dans les expressions régulières"
description: "Caractères d’échappement dans les expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 41d35531-2af9-47d4-9780-fbc1e682fbc2
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 08a781be74120d26b8408ee8e9b12051b005ad54

---

# <a name="character-escapes-in-regular-expressions"></a>Caractères d’échappement dans les expressions régulières

La barre oblique inverse (\) dans une expression régulière indique une des possibilités suivantes : 

* Le caractère qui la suit est un caractère spécial, comme indiqué dans le tableau de la section suivante. Par exemple, **\b** est une ancre qui indique qu’une correspondance d’expression régulière doit commencer sur une limite de mot, **\t** représente une tabulation et **\x020** représente un espace.

* Un caractère qui doit être interprété littéralement, et qui sans cela serait interprété comme une construction du langage sans séquence d'échappement. Par exemple, une accolade (**{**) commence la définition d’un quantificateur, mais une barre oblique inverse suivie d’une accolade (**\{**) indique que le moteur d’expression régulière doit rechercher une correspondance avec l’accolade. De la même façon, une seule barre oblique inverse marque le début d’une construction du langage avec échappement, mais deux barres obliques inverses (**\\**) indiquent que le moteur d’expression régulière doit chercher une correspondance avec la barre oblique inverse.

> [!NOTE]
> Les séquences d’échappement des caractères sont reconnues dans les modèles d’expressions régulières, mais pas dans les modèles de remplacement. 
 
## <a name="character-escapes-in-net"></a>Caractères d’échappement dans .NET

Le tableau suivant répertorie les séquences d’échappement des caractères prises en charge par les expressions régulières dans .NET.

Caractère ou séquence | Description
--------------------- | ----------- 
Tous les caractères à l’exception des suivants : **. $ ^ { [ ( &#124; ) * + ? \** | Les caractères autres que ceux répertoriés dans la colonne **Caractère ou séquence** n’ont pas de signification spéciale dans les expressions régulières ; ils ne correspondent qu’à eux-mêmes. Les caractères inclus dans la colonne **Caractère ou séquence** sont des éléments spéciaux du langage des expressions régulières. Pour les faire correspondre dans une expression régulière, ils doivent être utilisés avec un caractère d’échappement ou inclus dans un groupe de caractères positif. Par exemple, l’expression régulière `\$\d+ or [$]\d+` est en correspondance avec « $1200 ». 
**\a** | Correspond à un caractère représentant une cloche (alarme), **\u0007**.
**\b** | Dans une classe de caractères __[__*groupe*_*caractères*__]_, correspond à un retour arrière, **\u0008**. (Consultez [Classes de caractères dans les expressions régulières](classes.md).) En dehors d’une classe de caractères, **\b** est une ancre qui correspond à une limite de mot. (Consultez [Ancres dans les expressions régulières](anchors.md).)
**\t** | Correspond à une tabulation, **\u0009**.
**\r** | Correspond à un retour chariot, **\u000D**. Notez que **\r** n’est pas équivalent au caractère de nouvelle ligne, **\n**.
**\v** | Correspond à une tabulation verticale, **\u000B**.
**\f** | Correspond à un saut de page, **\u000C**.
**\n** | Correspond à une nouvelle ligne, **\u000A**.
**\e** | Correspond à un caractère d’échappement, **\u001B**.
**\**_nnn_ | Correspond à un caractère ASCII, où nnn est constitué de deux ou trois chiffres qui représentent le code octal du caractère. Par exemple, `\040` représente un espace. Cette construction est interprétée comme une référence arrière si elle a un seul chiffre (par exemple `\2`) ou si elle correspond au nombre d'un groupe de capture. (Consultez [Constructions de références arrière dans les expressions régulières](backreference.md).) 
**\x**_nn_ | Correspond à un caractère ASCII, où *nn* est un code hexadécimal à deux chiffres d’un caractère.
**\c**_X_ | Correspond à un caractère de contrôle ASCII, où *X* est la lettre du caractère de contrôle. Par exemple, `\cC` est Ctrl-C.
**\u**_nnnn_ | Correspond à une unité de code UTF-16 dont la valeur est *nnnn* en hexadécimal. **Remarque** La séquence d’échappement des caractères de Perl 5 utilisée pour spécifier Unicode n’est pas prise en charge par .NET. La séquence d’échappement des caractères de Perl 5 a la forme **\x{####…}**, où **####…** est une série de chiffres hexadécimaux. Utilisez plutôt **\u**_nnnn_. 
**\** | Quand ce caractère d'échappement est suivi d'un caractère non reconnu comme caractère d'échappement, correspond au caractère lui-même. Par exemple, `\*` correspond à un astérisque (*) et est identique à `\x2A`.
 
## <a name="example"></a>Exemple

L'exemple suivant montre l'utilisation de caractères d'échappement dans une expression régulière. Il analyse une chaîne qui contient les noms des plus grandes villes du monde et leur population en 2009. Chaque nom de ville est séparé de sa population par une tabulation (**\t**) ou par une barre verticale (| ou `\u007c`). Les villes individuelles et leur population sont séparées les unes des autres par un retour chariot et un saut de ligne. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string delimited = @"\G(.+)[\t\u007c](.+)\r?\n";
      string input = "Mumbai, India|13,922,125\t\n" + 
                            "Shanghai, China\t13,831,900\n" + 
                            "Karachi, Pakistan|12,991,000\n" + 
                            "Delhi, India\t12,259,230\n" + 
                            "Istanbul, Turkey|11,372,613\n";
      Console.WriteLine("Population of the World's Largest Cities, 2009");
      Console.WriteLine();
      Console.WriteLine("{0,-20} {1,10}", "City", "Population");
      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, delimited))
         Console.WriteLine("{0,-20} {1,10}", match.Groups[1].Value, 
                                            match.Groups[2].Value);
   }
}
// The example displyas the following output:
//       Population of the World's Largest Cities, 2009
//       
//       City                 Population
//       
//       Mumbai, India        13,922,125
//       Shanghai, China      13,831,900
//       Karachi, Pakistan    12,991,000
//       Delhi, India         12,259,230
//       Istanbul, Turkey     11,372,613
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim delimited As String = "\G(.+)[\t\u007c](.+)\r?\n"
      Dim input As String = "Mumbai, India|13,922,125" + vbCrLf + _
                            "Shanghai, China" + vbTab + "13,831,900" + vbCrLf + _
                            "Karachi, Pakistan|12,991,000" + vbCrLf + _
                            "Delhi, India" + vbTab + "12,259,230" + vbCrLf + _
                            "Istanbul, Turkey|11,372,613" + vbCrLf
      Console.WriteLine("Population of the World's Largest Cities, 2009")
      Console.WriteLine()
      Console.WriteLine("{0,-20} {1,10}", "City", "Population")
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, delimited)
         Console.WriteLine("{0,-20} {1,10}", match.Groups(1).Value, _
                                            match.Groups(2).Value)
      Next                         
   End Sub
End Module
' The example displays the following output:
'       Population of the World's Largest Cities, 2009
'       
'       City                 Population
'       
'       Mumbai, India        13,922,125
'       Shanghai, China      13,831,900
'       Karachi, Pakistan    12,991,000
'       Delhi, India         12,259,230
'       Istanbul, Turkey     11,372,613
```

L'expression régulière `\G(.+)[\t|\u007c](.+)\r?\n` est interprétée comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`\G` | Commencer la correspondance là où la dernière correspondance s'est terminée.
`(.+)` | Faire correspondre à n'importe quel caractère une ou plusieurs fois. Il s'agit du premier groupe de capture.
`[\t\u007c]` | Faire correspondre à une tabulation (**\t**) ou à une barre verticale (&#124;).
`(.+)` | Faire correspondre à n'importe quel caractère une ou plusieurs fois. Il s'agit du deuxième groupe de capture.
`\r?\n` | Faire correspondre à zéro ou à une occurrence d'un retour chariot suivi d'une nouvelle ligne.
 
## <a name="see-also"></a>Voir aussi

[Langage des expressions régulières - Aide-mémoire](quick-ref.md)




<!--HONumber=Nov16_HO1-->


