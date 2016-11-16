---
title: "Bonnes pratiques pour les expressions régulières"
description: "Bonnes pratiques pour les expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 096fd614-91bf-4296-be24-12f62b062294
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 00c7228c5cb906f41df5e60a318721008ecf0bb7

---

# <a name="best-practices-for-regular-expressions"></a>Bonnes pratiques pour les expressions régulières

Le moteur d’expression régulière dans .NET est un outil puissant et complet. Il traite le texte en fonction de correspondances de modèle plutôt qu’en comparant et en faisant correspondre le texte littéral. Dans la plupart des cas, il exécute les critères spéciaux de façon rapide et efficace. Toutefois, dans certains cas, le moteur des expressions régulières peut sembler très lent. Dans des cas extrêmes, il semble même cesser de répondre. Il traite en effet peu d'entrées sur une période de plusieurs heures ou même de plusieurs jours. 

Cette rubrique décrit quelques-unes des meilleures pratiques que les développeurs peuvent adopter afin de garantir que les expressions régulières atteignent des performances optimales. Elle contient les sections suivantes :

* [Prise en compte de la source d’entrée](#consider-the-input-source)

* [Gestion correcte de l’instanciation d’objet](#handle-object-instantiation-appropriately)

* [Prise en charge de la rétroaction](#take-charge-of-backtracking)

* [Utilisation de valeurs de délai d’attente](#use-time-out-values)

* [Capture uniquement quand cela s’avère nécessaire](#capture-only-when-necessary)

* [Rubriques connexes](#related-topics)

## <a name="consider-the-input-source"></a>Prise en compte de la source d’entrée

En général, les expressions régulières peuvent accepter deux types d'entrée : avec contrainte ou sans contrainte. L'entrée avec contrainte est un texte provenant d'une source fiable ou connue, et qui suit un format prédéfini. L'entrée sans contrainte est un texte provenant d'une source non fiable, telle qu'un utilisateur web. Elle ne suit pas forcément un format prédéfini ou attendu.

Les modèles d'expressions régulières sont généralement écrits pour correspondre à une entrée valide. Autrement dit, les développeurs examinent le texte qu'ils souhaitent faire correspondre, puis ils écrivent un modèle d'expression régulière qui lui correspond. Les développeurs déterminent ensuite si ce modèle doit être corrigé ou approfondi en le testant à l'aide de plusieurs éléments d'entrée valides. Lorsque le modèle correspond à toutes les entrées valides supposées, il est déclaré prêt pour la production et peut être intégré à une application finale. Le modèle d'expression régulière est ainsi adapté à la mise en correspondance d'une entrée avec contrainte. Toutefois, il n'est pas adapté à la mise en correspondance d'une entrée sans contrainte.

Pour faire correspondre une entrée sans contrainte, une expression régulière doit pouvoir gérer efficacement trois types de texte :

• Texte correspondant au modèle d’expression régulière.

• Texte ne correspondant pas au modèle d’expression régulière.

• Texte correspondant presque au modèle d’expression régulière.

Le dernier type de texte est problématique pour une expression régulière écrite pour gérer les entrées avec contrainte. Si cette expression régulière repose également sur une [rétroaction](backtracking.md) complète, le traitement d’un texte apparemment anodin par le moteur d’expression régulière risque d’être extrêmement long (dans certains cas, un grand nombre d’heures ou de jours). 

> [!WARNING]
> L'exemple suivant utilise une expression régulière sujette à des rétroactions excessives et susceptible de rejeter des adresses e-mail valides. Vous ne devez pas l’utiliser dans une routine de validation d’e-mails. Si vous souhaitez une expression régulière qui valide des adresses e-mail, consultez [Guide pratique pour vérifier que des chaînes sont dans un format d’adresse e-mail valide](verify-format.md). 


Prenons l'exemple d'une expression régulière très fréquemment utilisée, mais extrêmement problématique, pour la validation de l'alias d'une adresse e-mail. L'expression régulière `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` est écrite pour traiter ce qui est considéré comme une adresse e-mail valide. Cette dernière se compose d'un caractère alphanumérique suivi de zéro, ou de plusieurs caractères (caractères alphanumériques, points ou traits d'union). L'expression régulière doit se terminer par un caractère alphanumérique. Toutefois, comme illustré dans l'exemple suivant, bien que cette expression régulière gère facilement une entrée valide, elle s'avère particulièrement inefficace lorsqu'il s'agit de traiter une entrée presque valide.

```csharp
using System;
using System.Diagnostics;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      Stopwatch sw;    
      string[] addresses = { "AAAAAAAAAAA@contoso.com", 
                             "AAAAAAAAAAaaaaaaaaaa!@contoso.com" };
      // The following regular expression should not actually be used to 
      // validate an email address.
      string pattern = @"^[0-9A-Z]([-.\w]*[0-9A-Z])*$";
      string input; 

      foreach (var address in addresses) {
         string mailBox = address.Substring(0, address.IndexOf("@"));       
         int index = 0;
         for (int ctr = mailBox.Length - 1; ctr >= 0; ctr--) {
            index++;

            input = mailBox.Substring(ctr, index); 
            sw = Stopwatch.StartNew();
            Match m = Regex.Match(input, pattern, RegexOptions.IgnoreCase);
            sw.Stop();
            if (m.Success)
               Console.WriteLine("{0,2}. Matched '{1,25}' in {2}", 
                                 index, m.Value, sw.Elapsed);
            else                     
               Console.WriteLine("{0,2}. Failed  '{1,25}' in {2}", 
                                 index, input, sw.Elapsed);
         }
         Console.WriteLine();
      }
   }
}

// The example displays output similar to the following:
//     1. Matched '                        A' in 00:00:00.0007122
//     2. Matched '                       AA' in 00:00:00.0000282
//     3. Matched '                      AAA' in 00:00:00.0000042
//     4. Matched '                     AAAA' in 00:00:00.0000038
//     5. Matched '                    AAAAA' in 00:00:00.0000042
//     6. Matched '                   AAAAAA' in 00:00:00.0000042
//     7. Matched '                  AAAAAAA' in 00:00:00.0000042
//     8. Matched '                 AAAAAAAA' in 00:00:00.0000087
//     9. Matched '                AAAAAAAAA' in 00:00:00.0000045
//    10. Matched '               AAAAAAAAAA' in 00:00:00.0000045
//    11. Matched '              AAAAAAAAAAA' in 00:00:00.0000045
//    
//     1. Failed  '                        !' in 00:00:00.0000447
//     2. Failed  '                       a!' in 00:00:00.0000071
//     3. Failed  '                      aa!' in 00:00:00.0000071
//     4. Failed  '                     aaa!' in 00:00:00.0000061
//     5. Failed  '                    aaaa!' in 00:00:00.0000081
//     6. Failed  '                   aaaaa!' in 00:00:00.0000126
//     7. Failed  '                  aaaaaa!' in 00:00:00.0000359
//     8. Failed  '                 aaaaaaa!' in 00:00:00.0000414
//     9. Failed  '                aaaaaaaa!' in 00:00:00.0000758
//    10. Failed  '               aaaaaaaaa!' in 00:00:00.0001462
//    11. Failed  '              aaaaaaaaaa!' in 00:00:00.0002885
//    12. Failed  '             Aaaaaaaaaaa!' in 00:00:00.0005780
//    13. Failed  '            AAaaaaaaaaaa!' in 00:00:00.0011628
//    14. Failed  '           AAAaaaaaaaaaa!' in 00:00:00.0022851
//    15. Failed  '          AAAAaaaaaaaaaa!' in 00:00:00.0045864
//    16. Failed  '         AAAAAaaaaaaaaaa!' in 00:00:00.0093168
//    17. Failed  '        AAAAAAaaaaaaaaaa!' in 00:00:00.0185993
//    18. Failed  '       AAAAAAAaaaaaaaaaa!' in 00:00:00.0366723
//    19. Failed  '      AAAAAAAAaaaaaaaaaa!' in 00:00:00.1370108
//    20. Failed  '     AAAAAAAAAaaaaaaaaaa!' in 00:00:00.1553966
//    21. Failed  '    AAAAAAAAAAaaaaaaaaaa!' in 00:00:00.3223372
```

```vb
Imports System.Diagnostics
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim sw As Stopwatch    
      Dim addresses() As String = { "AAAAAAAAAAA@contoso.com", 
                                 "AAAAAAAAAAaaaaaaaaaa!@contoso.com" }
      ' The following regular expression should not actually be used to 
      ' validate an email address.
      Dim pattern As String = "^[0-9A-Z]([-.\w]*[0-9A-Z])*$"
      Dim input As String 

      For Each address In addresses
         Dim mailBox As String = address.Substring(0, address.IndexOf("@"))       
         Dim index As Integer = 0
         For ctr As Integer = mailBox.Length - 1 To 0 Step -1
            index += 1
            input = mailBox.Substring(ctr, index) 
            sw = Stopwatch.StartNew()
            Dim m As Match = Regex.Match(input, pattern, RegexOptions.IgnoreCase)
            sw.Stop()
            if m.Success Then
               Console.WriteLine("{0,2}. Matched '{1,25}' in {2}", 
                                 index, m.Value, sw.Elapsed)
            Else                     
               Console.WriteLine("{0,2}. Failed  '{1,25}' in {2}", 
                                 index, input, sw.Elapsed)
            End If                  
         Next
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays output similar to the following:
'     1. Matched '                        A' in 00:00:00.0007122
'     2. Matched '                       AA' in 00:00:00.0000282
'     3. Matched '                      AAA' in 00:00:00.0000042
'     4. Matched '                     AAAA' in 00:00:00.0000038
'     5. Matched '                    AAAAA' in 00:00:00.0000042
'     6. Matched '                   AAAAAA' in 00:00:00.0000042
'     7. Matched '                  AAAAAAA' in 00:00:00.0000042
'     8. Matched '                 AAAAAAAA' in 00:00:00.0000087
'     9. Matched '                AAAAAAAAA' in 00:00:00.0000045
'    10. Matched '               AAAAAAAAAA' in 00:00:00.0000045
'    11. Matched '              AAAAAAAAAAA' in 00:00:00.0000045
'    
'     1. Failed  '                        !' in 00:00:00.0000447
'     2. Failed  '                       a!' in 00:00:00.0000071
'     3. Failed  '                      aa!' in 00:00:00.0000071
'     4. Failed  '                     aaa!' in 00:00:00.0000061
'     5. Failed  '                    aaaa!' in 00:00:00.0000081
'     6. Failed  '                   aaaaa!' in 00:00:00.0000126
'     7. Failed  '                  aaaaaa!' in 00:00:00.0000359
'     8. Failed  '                 aaaaaaa!' in 00:00:00.0000414
'     9. Failed  '                aaaaaaaa!' in 00:00:00.0000758
'    10. Failed  '               aaaaaaaaa!' in 00:00:00.0001462
'    11. Failed  '              aaaaaaaaaa!' in 00:00:00.0002885
'    12. Failed  '             Aaaaaaaaaaa!' in 00:00:00.0005780
'    13. Failed  '            AAaaaaaaaaaa!' in 00:00:00.0011628
'    14. Failed  '           AAAaaaaaaaaaa!' in 00:00:00.0022851
'    15. Failed  '          AAAAaaaaaaaaaa!' in 00:00:00.0045864
'    16. Failed  '         AAAAAaaaaaaaaaa!' in 00:00:00.0093168
'    17. Failed  '        AAAAAAaaaaaaaaaa!' in 00:00:00.0185993
'    18. Failed  '       AAAAAAAaaaaaaaaaa!' in 00:00:00.0366723
'    19. Failed  '      AAAAAAAAaaaaaaaaaa!' in 00:00:00.1370108
'    20. Failed  '     AAAAAAAAAaaaaaaaaaa!' in 00:00:00.1553966
'    21. Failed  '    AAAAAAAAAAaaaaaaaaaa!' in 00:00:00.3223372
```

Comme le montre la sortie de l'exemple, le moteur des expressions régulières traite l'alias de messagerie valide dans un intervalle de temps à peu près identique, indépendamment de sa longueur. En revanche, lorsque l'adresse e-mail presque valide comporte plus de cinq caractères, le temps de traitement est environ doublé pour chaque caractère supplémentaire de la chaîne. Cela signifie qu'une chaîne de 28 caractères presque valide serait traitée en plus d'une heure et qu'une chaîne de 33 caractères presque valide serait traitée en un peu moins d'un jour. 

Étant donné que cette expression régulière a été développée en prenant uniquement en considération le format de l'entrée à faire correspondre, elle ne tient pas compte des entrées qui ne correspondent pas au modèle. Une entrée sans contrainte correspondant presque au modèle d'expression régulière risque ainsi de nuire considérablement aux performances.

Pour résoudre ce problème, vous pouvez effectuer les opérations suivantes :

* Lorsque vous développez un modèle, vous devez réfléchir à la manière dont la rétroaction peut affecter les performances du moteur des expressions régulières, en particulier si votre expression régulière est conçue pour traiter des entrées sans contrainte. Pour plus d’informations, consultez la section [Prise en charge de la rétroaction](#take-charge-of-backtracking).

* Testez intégralement votre expression régulière à l'aide d'entrées non valides et presque valides, ainsi que d'entrées valides. Pour générer de manière aléatoire une entrée pour une expression régulière spécifique, vous pouvez utiliser [Rex](http://research.microsoft.com/en-us/projects/rex/), l’outil d’exploration d’expressions régulières de Microsoft Research.

## <a name="handle-object-instantiation-appropriately"></a>Gestion correcte de l’instanciation d’objet

Au cœur du modèle objet d’expression régulière de .NET se trouve la classe [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex), qui représente le moteur d’expression régulière. Souvent, la façon dont le moteur [Regex](xref:System.Text.RegularExpressions.Regex) est utilisé est le principal facteur qui exerce un impact sur les performances des expressions régulières. La définition d’une expression régulière implique une association étroite entre le moteur des expressions régulières et un modèle d’expression régulière. Ce processus d’association est forcément onéreux, qu’il implique l’instanciation d’un objet [Regex](xref:System.Text.RegularExpressions.Regex) en passant à son constructeur un modèle d’expression régulière ou l’appel d’une méthode statique en lui passant le modèle d’expression régulière avec la chaîne à analyser.

Vous pouvez associer le moteur des expressions régulières à un modèle d’expression régulière spécifique, puis utiliser le moteur pour faire correspondre du texte de plusieurs façons :

* Vous pouvez appeler une méthode statique de critères spéciaux, comme [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)). L'instanciation d'un objet d'expression régulière n'est pas nécessaire.

* Vous pouvez instancier un objet [Regex](xref:System.Text.RegularExpressions.Regex) et appeler une méthode d’instance de critères spéciaux d’une expression régulière interprétée. Il s’agit de la méthode par défaut pour lier le moteur des expressions régulières à un modèle d’expression régulière. Elle s’ensuit quand un objet [Regex](xref:System.Text.RegularExpressions.Regex) est instancié sans argument options qui inclut l’indicateur [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled).

* Vous pouvez instancier un objet [Regex](xref:System.Text.RegularExpressions.Regex) et appeler une méthode d’instance de critères spéciaux d’une expression régulière compilée. Les objets d’expression régulière représentent des modèles compilés lorsqu’un objet [Regex](xref:System.Text.RegularExpressions.Regex) est instancié avec un argument options incluant l’indicateur [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled).

> [!IMPORTANT]
> La forme de l'appel de méthode (statique, interprétée, compilée) affecte les performances si une même expression régulière est utilisée à plusieurs reprises dans les appels de méthode, ou si une application entraîne l'utilisation intensive d'objets d'expression régulière.
 
### <a name="static-regular-expressions"></a>Expressions régulières statiques

Les méthodes d'expression régulière statiques sont recommandées pour éviter d'instancier à plusieurs reprises un objet d'expression régulière avec la même expression régulière. À la différence des modèles d’expressions régulières utilisés par les objets d’expression régulière, les codes d’opération ou le langage compilé MSIL (Microsoft intermediate langage) des modèles utilisés dans les appels de méthode d’instance sont mis en cache en interne par le moteur des expressions régulières. 

Par exemple, vous pouvez appeler une méthode pour valider l’entrée d’utilisateur. Dans cet exemple, une méthode nommée `IsValidCurrency` vérifie si l’utilisateur a entré un symbole monétaire suivi d’au moins un chiffre décimal. L'exemple suivant illustre une implémentation très peu efficace de la méthode `IsValidCurrency`. Notez que chaque appel de méthode réinstancie un objet [Regex](xref:System.Text.RegularExpressions.Regex) avec le même modèle. Cela signifie ainsi que le modèle d’expression régulière doit être recompilé chaque fois que la méthode est appelée.

```csharp
using System;
using System.Text.RegularExpressions;

public class RegexLib
{
   public static bool IsValidCurrency(string currencyValue)
   {
      string pattern = @"\p{Sc}+\s*\d+";
      Regex currencyRegex = new Regex(pattern);
      return currencyRegex.IsMatch(currencyValue);
   }
}
```

```vb
Public Sub OKButton_Click(sender As Object, e As EventArgs) _ 
           Handles OKButton.Click

   If Not String.IsNullOrEmpty(sourceCurrency.Text) Then
      If RegexLib.IsValidCurrency(sourceCurrency.Text) Then
         PerformConversion()
      Else
         status.Text = "The source currency value is invalid."
      End If          
   End If
End Sub
```

Vous devez remplacer ce code peu efficace par un appel à la méthode [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)) statique. De cette manière, un objet [Regex](xref:System.Text.RegularExpressions.Regex) n’a pas besoin d’être instancié chaque fois que vous souhaitez appeler une méthode de critères spéciaux. En outre, le moteur d’expression régulière est alors en mesure de récupérer une version compilée de l’expression régulière depuis son cache.

```csharp
using System;
using System.Text.RegularExpressions;

public class RegexLib
{
   public static bool IsValidCurrency(string currencyValue)
   {
      string pattern = @"\p{Sc}+\s*\d+";
      return Regex.IsMatch(currencyValue, pattern); 
   }
}
```

```vb
Imports System.Text.RegularExpressions

Public Module RegexLib
   Public Function IsValidCurrency(currencyValue As String) As Boolean
      Dim pattern As String = "\p{Sc}+\s*\d+"
      Return Regex.IsMatch(currencyValue, pattern)
   End Function
End Module
```

Par défaut, les 15 derniers modèles d’expressions régulières statiques utilisés récemment sont mis en cache. Pour les applications qui requièrent un plus grand nombre d’expressions régulières statiques mises en cache, la taille du cache peut être ajustée en définissant la propriété [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize).

L'expression régulière `\p{Sc}+\s*\d+` utilisée dans cet exemple vérifie que la chaîne d'entrée se compose d'un symbole monétaire et d'au moins un chiffre décimal. Le modèle est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\p{Sc}+` | Mettre en correspondance un ou plusieurs caractères dans la catégorie Unicode symbole, devise.
`\s*` | Correspond à zéro, un ou plusieurs espaces blancs.
`\d+` | Mettre en correspondance un ou plusieurs chiffres décimaux.
 
### <a name="interpreted-vs-compiled-regular-expressions"></a>Expressions régulières interprétées ou compilées

Les modèles d’expression régulière qui ne sont pas associés au moteur d’expression régulière par la spécification de l’option [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) sont interprétés. Lorsqu'un objet d'expression régulière est instancié, le moteur des expressions régulières convertit l'expression régulière en un ensemble de codes d'opération. Lorsqu'une méthode d'instance est appelée, les codes d'opération sont convertis en langage MSIL et exécutés par le compilateur JIT. De même, lorsqu'une méthode d'expression régulière statique est appelée et que l'expression régulière ne peut pas être récupérée dans le cache, le moteur des expressions régulières convertit l'expression régulière en un ensemble de codes d'opération et les stocke dans le cache. Il convertit ensuite ces codes d'opération en langage MSIL afin que le compilateur JIT puisse les exécuter. Les expressions régulières interprétées réduisent le temps de démarrage, mais ralentissent le temps d'exécution. Pour cette raison, il est préférable de les utiliser lorsque l'expression régulière est utilisée dans un nombre d'appels de méthode restreint, ou lorsque le nombre exact d'appels de méthodes d'expression régulière est inconnu, mais qu'il est supposé être petit. À mesure que le nombre d'appels de méthode augmente, le ralentissement de la vitesse d'exécution l'emporte sur l'amélioration des performances liée à la réduction du temps de démarrage.

Les modèles d’expression régulière qui sont associés au moteur d’expression régulière par la spécification de l’option [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) sont compilés. Cela signifie que, lorsqu'un objet d'expression régulière est instancié ou lorsqu'une méthode d'expression régulière statique est appelée et que l'expression régulière ne peut pas être récupérée dans le cache, le moteur des expressions régulières convertit l'expression régulière en un ensemble de codes d'opération intermédiaire, qu'il convertit ensuite en langage MSIL. Lorsqu'une méthode est appelée, le compilateur JIT exécute le MSIL. Contrairement aux expressions régulières interprétées, les expressions régulières compilées augmentent le temps de démarrage, mais elles exécutent plus rapidement les méthodes de critères spéciaux individuelles. En conséquence, l'amélioration des performances due à la compilation de l'expression régulière augmente en fonction du nombre de méthodes d'expression régulières appelées.

Pour résumer, nous vous conseillons d'utiliser des expressions régulières interprétées lorsque vous appelez relativement peu souvent des méthodes d'expression régulières avec une expression régulière spécifique. Nous vous conseillons d'utiliser des expressions régulières compilées lorsque vous appelez relativement souvent des méthodes d'expression régulière avec une expression régulière spécifique. Il est difficile de déterminer le seuil exact auquel le ralentissement de la vitesse d'exécution des expressions normales interprétées l'emporte sur la réduction du temps de démarrage. Il est également difficile de déterminer le seuil auquel le ralentissement du temps de démarrage des expressions régulières compilées l'emporte sur l'amélioration des vitesses d'exécution. Différents facteurs doivent être pris en compte, notamment la complexité des expressions régulières et les données spécifiques qui sont traitées. Pour déterminer si ce sont les expressions régulières interprétées ou compilées qui offrent les meilleures performances pour votre scénario d’application spécifique, vous pouvez utiliser la classe [Stopwatch](xref:System.Diagnostics.Stopwatch) pour comparer les durées d’exécution.

L’exemple suivant compare les performances des expressions régulières compilées et interprétées lors de la lecture des dix premières phrases et lors de la lecture de toutes les phrases du texte de Theodore Dreiser, The Financier. Comme l'indique la sortie de l'exemple, lorsque les méthodes de correspondance d'expression régulière sont appelées seulement dix fois, une expression régulière interprétée offre de meilleures performances qu'une expression régulière compilée. Par contre, une expression régulière compilée offre de meilleures performances dans le cas d'un grand nombre d'appels (dans le cas présent, plus de 13 000). 

```csharp
using System;
using System.Diagnostics;
using System.IO;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]";
      Stopwatch sw;
      Match match;
      int ctr;

      StreamReader inFile = new StreamReader(@".\Dreiser_TheFinancier.txt");
      string input = inFile.ReadToEnd();
      inFile.Close();

      // Read first ten sentences with interpreted regex.
      Console.WriteLine("10 Sentences with Interpreted Regex:");
      sw = Stopwatch.StartNew();
      Regex int10 = new Regex(pattern, RegexOptions.Singleline);
      match = int10.Match(input);
      for (ctr = 0; ctr <= 9; ctr++) {
         if (match.Success)
            // Do nothing with the match except get the next match.
            match = match.NextMatch();
         else
            break;
      }
      sw.Stop();
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed);

      // Read first ten sentences with compiled regex.
      Console.WriteLine("10 Sentences with Compiled Regex:");
      sw = Stopwatch.StartNew();
      Regex comp10 = new Regex(pattern, 
                   RegexOptions.Singleline | RegexOptions.Compiled);
      match = comp10.Match(input);
      for (ctr = 0; ctr <= 9; ctr++) {
         if (match.Success)
            // Do nothing with the match except get the next match.
            match = match.NextMatch();
         else
            break;
      }
      sw.Stop();
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed);

      // Read all sentences with interpreted regex.
      Console.WriteLine("All Sentences with Interpreted Regex:");
      sw = Stopwatch.StartNew();
      Regex intAll = new Regex(pattern, RegexOptions.Singleline);
      match = intAll.Match(input);
      int matches = 0;
      while (match.Success) {
         matches++;
         // Do nothing with the match except get the next match.
         match = match.NextMatch();
      }
      sw.Stop();
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed);

      // Read all sentnces with compiled regex.
      Console.WriteLine("All Sentences with Compiled Regex:");
      sw = Stopwatch.StartNew();
      Regex compAll = new Regex(pattern, 
                      RegexOptions.Singleline | RegexOptions.Compiled);
      match = compAll.Match(input);
      matches = 0;
      while (match.Success) {
         matches++;
         // Do nothing with the match except get the next match.
         match = match.NextMatch();
      }
      sw.Stop();
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed);      
   }
}
// The example displays the following output:
//       10 Sentences with Interpreted Regex:
//          10 matches in 00:00:00.0047491
//       10 Sentences with Compiled Regex:
//          10 matches in 00:00:00.0141872
//       All Sentences with Interpreted Regex:
//          13,443 matches in 00:00:01.1929928
//       All Sentences with Compiled Regex:
//          13,443 matches in 00:00:00.7635869
//       
//       >compare1
//       10 Sentences with Interpreted Regex:
//          10 matches in 00:00:00.0046914
//       10 Sentences with Compiled Regex:
//          10 matches in 00:00:00.0143727
//       All Sentences with Interpreted Regex:
//          13,443 matches in 00:00:01.1514100
//       All Sentences with Compiled Regex:
//          13,443 matches in 00:00:00.7432921
```

```vb
Imports System.Diagnostics
Imports System.IO
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]"
      Dim sw As Stopwatch
      Dim match As Match
      Dim ctr As Integer

      Dim inFile As New StreamReader(".\Dreiser_TheFinancier.txt")
      Dim input As String = inFile.ReadToEnd()
      inFile.Close()

      ' Read first ten sentences with interpreted regex.
      Console.WriteLine("10 Sentences with Interpreted Regex:")
      sw = Stopwatch.StartNew()
      Dim int10 As New Regex(pattern, RegexOptions.SingleLine)
      match = int10.Match(input)
      For ctr = 0 To 9
         If match.Success Then
            ' Do nothing with the match except get the next match.
            match = match.NextMatch()
         Else
            Exit For
         End If
      Next
      sw.Stop()
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed)

      ' Read first ten sentences with compiled regex.
      Console.WriteLine("10 Sentences with Compiled Regex:")
      sw = Stopwatch.StartNew()
      Dim comp10 As New Regex(pattern, 
                   RegexOptions.SingleLine Or RegexOptions.Compiled)
      match = comp10.Match(input)
      For ctr = 0 To 9
         If match.Success Then
            ' Do nothing with the match except get the next match.
            match = match.NextMatch()
         Else
            Exit For
         End If
      Next
      sw.Stop()
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed)

      ' Read all sentences with interpreted regex.
      Console.WriteLine("All Sentences with Interpreted Regex:")
      sw = Stopwatch.StartNew()
      Dim intAll As New Regex(pattern, RegexOptions.SingleLine)
      match = intAll.Match(input)
      Dim matches As Integer = 0
      Do While match.Success
         matches += 1
         ' Do nothing with the match except get the next match.
         match = match.NextMatch()
      Loop
      sw.Stop()
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed)

      ' Read all sentnces with compiled regex.
      Console.WriteLine("All Sentences with Compiled Regex:")
      sw = Stopwatch.StartNew()
      Dim compAll As New Regex(pattern, 
                     RegexOptions.SingleLine Or RegexOptions.Compiled)
      match = compAll.Match(input)
      matches = 0
      Do While match.Success
         matches += 1
         ' Do nothing with the match except get the next match.
         match = match.NextMatch()
      Loop
      sw.Stop()
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed)      
   End Sub
End Module
' The example displays output like the following:
'       10 Sentences with Interpreted Regex:
'          10 matches in 00:00:00.0047491
'       10 Sentences with Compiled Regex:
'          10 matches in 00:00:00.0141872
'       All Sentences with Interpreted Regex:
'          13,443 matches in 00:00:01.1929928
'       All Sentences with Compiled Regex:
'          13,443 matches in 00:00:00.7635869
'       
'       >compare1
'       10 Sentences with Interpreted Regex:
'          10 matches in 00:00:00.0046914
'       10 Sentences with Compiled Regex:
'          10 matches in 00:00:00.0143727
'       All Sentences with Interpreted Regex:
'          13,443 matches in 00:00:01.1514100
'       All Sentences with Compiled Regex:
'          13,443 matches in 00:00:00.7432921
```

Le modèle d'expression régulière utilisé dans l'exemple, `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\b` | Commencer la correspondance à la limite d'un mot.
`\w+` | Mettre en correspondance un ou plusieurs caractères alphabétiques.
`(\r?\n)|,?\s)` | Mettre en correspondance un ou aucun retour chariot suivi d'un caractère de saut de ligne, ou une ou aucune virgule, suivie d'un espace blanc.
`(\w+((\r?\n)|,?\s))*` | Mettre en correspondance zéro, une ou plusieurs occurrences d'un ou plusieurs caractères alphabétiques qui sont suivis par un ou aucun retour chariot et un caractère de saut de ligne, ou par une ou aucune virgule, suivie d'un espace blanc.
`\w+` | Mettre en correspondance un ou plusieurs caractères alphabétiques.
`[.?:;!]` | Mettre en correspondance un point, un point d'interrogation, deux-points, un point-virgule ou un point d'exclamation.
 
## <a name="take-charge-of-backtracking"></a>Prise en charge de la rétroaction

Normalement, le moteur des expressions régulières utilise une progression linéaire pour se déplacer dans une chaîne d’entrée et pour la comparer à un modèle d’expression régulière. Toutefois, quand des quantificateurs indéterminés comme __*__, **+** et **?** sont utilisés dans un modèle d’expression régulière, le moteur d’expression régulière peut abandonner une partie des correspondances partielles trouvées et revenir à un état précédemment enregistré pour trouver une correspondance pour le modèle entier. Ce processus est appelé « rétroaction ».

> [!NOTE]
> Pour plus d’informations sur la rétroaction, consultez [Comportement détaillé des expressions régulières](regex-behavior.md) et [Rétroaction dans les expressions régulières](backtracking.md).
 
La prise en charge de la rétroaction confère aux expressions régulières leur puissance et leur flexibilité. La responsabilité de contrôle du fonctionnement du moteur des expressions régulières est alors confiée aux développeurs d'expressions régulières. Souvent, les développeurs ne sont pas conscients de cette responsabilité. Leur utilisation incorrecte de la rétroaction ou leur dépendance vis-à-vis d'une rétroaction excessive a souvent un impact négatif très important sur les performances des expressions régulières. Dans le pire des scénarios, la durée d'exécution peut doubler pour chaque caractère supplémentaire de la chaîne d'entrée. En réalité, lorsque la rétroaction est utilisée de manière excessive, il est facile de créer l'équivalent de programmation d'une boucle sans fin si l'entrée correspond presque au modèle d'expression régulière. Le moteur des expressions régulières peut alors traiter une chaîne d'entrée relativement courte en plusieurs heures, voire en plusieurs jours.

Les performances des applications sont souvent altérées par l'utilisation de la rétroaction, même si ce processus n'est pas essentiel pour une correspondance. Par exemple, l'expression régulière `\b\p{Lu}\w*\b` établit une correspondance entre tous les mots qui commencent par une majuscule, comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`\b` | Commencer la correspondance à la limite d'un mot.
`\p{Lu}` | Mettre en correspondance une majuscule.
`\w*` | Mettre en correspondance zéro, un ou plusieurs caractères alphabétiques.
`\b` | Terminer la correspondance à la limite d'un mot.
 
Étant donné qu'une limite de mot est différente d'un caractère alphabétique et qu'elle n'est pas un sous-ensemble de ce dernier, il est impossible que le moteur des expressions régulières franchisse une limite de mot lors de la mise en correspondance de caractères alphabétiques. Cela signifie que, pour cette expression régulière, une rétroaction ne peut jamais contribuer à la réussite globale d'une correspondance. Elle risque en revanche de diminuer les performances, étant donné que le moteur des expressions régulières doit impérativement enregistrer sont état pour chaque correspondance préliminaire d'un caractère alphabétique trouvée.

Si vous considérez que la rétroaction n’est pas nécessaire, vous pouvez la désactiver à l’aide de l’élément de langage **(?>**_sous-expression_**)**. L'exemple suivant analyse une chaîne d'entrée à l'aide de deux expressions régulières. La première, `\b\p{Lu}\w*\b`, utilise la rétroaction. La seconde, `\b\p{Lu}(?>\w*)\b`, désactive la rétroaction. Comme l'indique la sortie de l'exemple, les résultats obtenus sont identiques.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This this word Sentence name Capital";
      string pattern = @"\b\p{Lu}\w*\b";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);

      Console.WriteLine();

      pattern = @"\b\p{Lu}(?>\w*)\b";   
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       This
//       Sentence
//       Capital
//       
//       This
//       Sentence
//       Capital
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This this word Sentence name Capital"
      Dim pattern As String = "\b\p{Lu}\w*\b"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
      Console.WriteLine()

      pattern = "\b\p{Lu}(?>\w*)\b"   
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       This
'       Sentence
'       Capital
'       
'       This
'       Sentence
'       Capital
```

Dans de nombreux cas, la rétroaction est essentielle pour faire correspondre un modèle d’expression régulière à un texte d’entrée. Toutefois, une rétroaction excessive risque d'altérer considérablement les performances et de donner l'impression qu'une application a cessé de répondre. Cela se produit notamment lorsque les quantificateurs sont imbriqués et que le texte correspondant à la sous-expression externe est un sous-ensemble du texte correspondant à la sous-expression interne. 

> [!WARNING]
> En plus d’éviter une rétroaction excessive, vous devez utiliser la fonctionnalité de délai d’attente pour garantir qu’une rétroaction excessive n’altère pas considérablement les performances des expressions régulières. Pour plus d’informations, consultez la section [Utilisation de valeurs de délai d’attente](#use-time-out-values).
 
Par exemple, le modèle d'expression régulière `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` est conçu pour mettre en correspondance un numéro de référence composé d'au moins un caractère alphanumérique. Tous les caractères supplémentaires peuvent être composés d'un caractère alphanumérique, d'un trait d'union, d'un trait de soulignement ou d'un point. Toutefois, le dernier caractère doit impérativement être alphanumérique. Un signe dollar termine le numéro de référence. Dans certains cas, ce modèle d'expression régulière peut présenter des performances médiocres, si les quantificateurs sont imbriqués et que la sous-expression `[0-9A-Z]` est un sous-ensemble de la sous-expression `[-.\w]*`.

Dans ces cas, vous pouvez optimiser les performances des expressions régulières en supprimant les quantificateurs imbriqués et en remplaçant la sous-expression externe par une assertion de préanalyse ou de postanalyse de largeur nulle. Les assertions de préanalyse et de postanalyse sont des points d'ancrage. Elles ne déplacent pas le pointeur dans la chaîne d'entrée, mais elles vérifient en amont et en aval si une condition spécifiée est remplie. Par exemple, l'expression régulière de numéro de référence peut être réécrite sous la forme `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`. Ce modèle d'expression régulière est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | -----------
`^` | Commencer la correspondance au début de la chaîne d'entrée.
`[0-9A-Z]` | Mettre en correspondance un caractère alphanumérique. Le numéro de référence doit au minimum comporter ce caractère.
`[-.\w]*` | Mettre en correspondance zéro, une ou plusieurs occurrences de tout caractère alphabétique, trait d'union ou point.
`\$] | Mettre en correspondance un signe dollar.
`(?<=[0-9A-Z])` | Effectuer une préanalyse avancée du signe dollar de fin de s'assurer que le caractère précédent est un caractère alphanumérique.
`$` Terminer la correspondance à la fin de la chaîne d’entrée.
 
L'exemple suivant illustre l'utilisation de cette expression régulière pour faire correspondre un tableau pouvant contenir des numéros de référence potentiels.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$";
      string[] partNos = { "A1C$", "A4", "A4$", "A1603D$", "A1603D#" };

      foreach (var input in partNos) {
         Match match = Regex.Match(input, pattern);
         if (match.Success)
            Console.WriteLine(match.Value);
         else
            Console.WriteLine("Match not found.");
      }      
   }
}
// The example displays the following output:
//       A1C$
//       Match not found.
//       A4$
//       A1603D$
//       Match not found.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$"
      Dim partNos() As String = { "A1C$", "A4", "A4$", "A1603D$", 
                                  "A1603D#" }

      For Each input As String In partNos
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine(match.Value)
         Else
            Console.WriteLine("Match not found.")
         End If
      Next      
   End Sub
End Module
' The example displays the following output:
'       A1C$
'       Match not found.
'       A4$
'       A1603D$
'       Match not found.
```

Le langage d’expression régulière dans .NET comprend les éléments de langage suivants, que vous pouvez utiliser pour éliminer les quantificateurs imbriqués. Pour plus d’informations, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).

Élément du langage | Description
---------------- | ----------- 
**(?**=_sous-expression_**)** | Préanalyse positive de largeur nulle. Effectuer une préanalyse de la position actuelle pour déterminer si *sous-expression* correspond à la chaîne d’entrée.
**(?!**_sous-expression_**)** | Préanalyse négative de largeur nulle. Effectuer une préanalyse de la position actuelle pour déterminer si *sous-expression* ne correspond pas à la chaîne d’entrée.
**(?<**=_sous-expression_**)** | Postanalyse positive de largeur nulle. Effectuer une postanalyse de la position actuelle pour déterminer si *sous-expression* correspond à la chaîne d’entrée.
**(?<!**_sous-expression_**)** | Postanalyse négative de largeur nulle. Effectuer une postanalyse de la position actuelle pour déterminer si *sous-expression* ne correspond pas à la chaîne d’entrée.
 
## <a name="use-timeout-values"></a>Utilisation de valeurs de délai d’attente

Si une expression régulière traite une entrée qui correspond presque au modèle d'expression régulière, elle peut souvent se baser sur une rétroaction excessive, laquelle affecte considérablement ses performances. En plus d'envisager soigneusement l'utilisation de la rétroaction et de tester l'expression régulière sur une entrée presque correspondante, vous devez toujours définir une valeur de délai d'attente pour garantir la minimalisation de l'impact d'une rétroaction excessive, le cas échéant.

Le délai d'attente d'expression régulière définit le laps de temps pendant lequel le moteur des expressions régulières recherchera une correspondance unique avant d'expirer. L’intervalle de délai d’attente par défaut est [Regex.InfiniteMatchTimeout](xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout), ce qui signifie que l’expression régulière n’expire pas. Vous pouvez remplacer cette valeur et définir un délai d'attente comme suit : 

* En fournissant une valeur de délai d’attente quand vous instanciez un objet [Regex](xref:System.Text.RegularExpressions.Regex) en appelant le constructeur [Regex(String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)).

* En appelant une méthode de critères spéciaux statique (méthode), comme [Regex.Match(String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) ou [Regex.Replace(String, String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)), qui inclut un paramètre *matchTimeout*.

Si vous avez défini un intervalle de délai d’attente et qu’aucune correspondance n’est trouvée à l’issue de cet intervalle, la méthode d’expression régulière lève une exception [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException). Dans votre gestionnaire d'exceptions, vous pouvez choisir de réessayer la mise en correspondance avec un délai d'attente plus long, d'annuler la recherche de correspondance et de supposer l'absence de correspondance, ou encore d'annuler la recherche de correspondance et de consigner les informations sur les exceptions à des fins d'analyse ultérieure.

L'exemple ci-dessous définit une méthode `GetWordData` qui instancie une expression régulière avec un délai d'attente de 350 millisecondes pour calculer le nombre de mots dans un document texte et le nombre moyen de caractères par mot. Si le délai d’attente de l’opération de recherche de correspondance expire, il augmente de 350 millisecondes et l’objet [Regex](xref:System.Text.RegularExpressions.Regex) est réinstancié. Si le nouveau délai d'attente dépasse 1 seconde, la méthode lève de nouveau l'exception pour l'appelant.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      RegexUtilities util = new RegexUtilities();
      string title = "Doyle - The Hound of the Baskervilles.txt";
      try {
         var info = util.GetWordData(title);
         Console.WriteLine("Words:               {0:N0}", info.Item1);
         Console.WriteLine("Average Word Length: {0:N2} characters", info.Item2); 
      }
      catch (IOException e) {
         Console.WriteLine("IOException reading file '{0}'", title);
         Console.WriteLine(e.Message);
      }
      catch (RegexMatchTimeoutException e) {
         Console.WriteLine("The operation timed out after {0:N0} milliseconds", 
                           e.MatchTimeout.TotalMilliseconds);
      }
   }
}

public class RegexUtilities
{
   public Tuple<int, double> GetWordData(string filename)
   { 
      const int MAX_TIMEOUT = 1000;   // Maximum timeout interval in milliseconds.
      const int INCREMENT = 350;      // Milliseconds increment of timeout.

      List<string> exclusions = new List<string>( new string[] { "a", "an", "the" });
      int[] wordLengths = new int[29];        // Allocate an array of more than ample size.
      string input = null;
      StreamReader sr = null;
      try { 
         sr = new StreamReader(filename);
         input = sr.ReadToEnd();
      }
      catch (FileNotFoundException e) {
         string msg = String.Format("Unable to find the file '{0}'", filename);
         throw new IOException(msg, e);
      }
      catch (IOException e) {
         throw new IOException(e.Message, e);
      }
      finally {
         if (sr != null) sr.Close(); 
      }

      int timeoutInterval = INCREMENT;
      bool init = false;
      Regex rgx = null;
      Match m = null;
      int indexPos = 0;  
      do {
         try {
            if (! init) {
               rgx = new Regex(@"\b\w+\b", RegexOptions.None, 
                               TimeSpan.FromMilliseconds(timeoutInterval));
               m = rgx.Match(input, indexPos);
               init = true;
            }
            else { 
               m = m.NextMatch();
            }
            if (m.Success) {    
               if ( !exclusions.Contains(m.Value.ToLower()))
                  wordLengths[m.Value.Length]++;

               indexPos += m.Length + 1;   
            }
         }
         catch (RegexMatchTimeoutException e) {
            if (e.MatchTimeout.TotalMilliseconds < MAX_TIMEOUT) {
               timeoutInterval += INCREMENT;
               init = false;
            }
            else {
               // Rethrow the exception.
               throw; 
            }   
         }          
      } while (m.Success);

      // If regex completed successfully, calculate number of words and average length.
      int nWords = 0; 
      long totalLength = 0;

      for (int ctr = wordLengths.GetLowerBound(0); ctr <= wordLengths.GetUpperBound(0); ctr++) {
         nWords += wordLengths[ctr];
         totalLength += ctr * wordLengths[ctr];
      }
      return new Tuple<int, double>(nWords, totalLength/nWords);
   }
}
```

```vb
Imports System.Collections.Generic
Imports System.IO
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim util As New RegexUtilities()
      Dim title As String = "Doyle - The Hound of the Baskervilles.txt"
      Try
         Dim info = util.GetWordData(title)
         Console.WriteLine("Words:               {0:N0}", info.Item1)
         Console.WriteLine("Average Word Length: {0:N2} characters", info.Item2) 
      Catch e As IOException
         Console.WriteLine("IOException reading file '{0}'", title)
         Console.WriteLine(e.Message)
      Catch e As RegexMatchTimeoutException
         Console.WriteLine("The operation timed out after {0:N0} milliseconds", 
                           e.MatchTimeout.TotalMilliseconds)
      End Try
   End Sub
End Module

Public Class RegexUtilities
   Public Function GetWordData(filename As String) As Tuple(Of Integer, Double) 
      Const MAX_TIMEOUT As Integer = 1000  ' Maximum timeout interval in milliseconds.
      Const INCREMENT As Integer = 350     ' Milliseconds increment of timeout.

      Dim exclusions As New List(Of String)({"a", "an", "the" })
      Dim wordLengths(30) As Integer        ' Allocate an array of more than ample size.
      Dim input As String = Nothing
      Dim sr As StreamReader = Nothing
      Try 
         sr = New StreamReader(filename)
         input = sr.ReadToEnd()
      Catch e As FileNotFoundException
         Dim msg As String = String.Format("Unable to find the file '{0}'", filename)
         Throw New IOException(msg, e)
      Catch e As IOException
         Throw New IOException(e.Message, e)
      Finally
         If sr IsNot Nothing Then sr.Close() 
      End Try

      Dim timeoutInterval As Integer = INCREMENT
      Dim init As Boolean = False
      Dim rgx As Regex = Nothing
      Dim m As Match = Nothing
      Dim indexPos As Integer = 0  
      Do
         Try
            If Not init Then
               rgx = New Regex("\b\w+\b", RegexOptions.None, 
                               TimeSpan.FromMilliseconds(timeoutInterval))
               m = rgx.Match(input, indexPos)
               init = True
            Else 
               m = m.NextMatch()
            End If
            If m.Success Then    
               If Not exclusions.Contains(m.Value.ToLower()) Then
                  wordLengths(m.Value.Length) += 1
               End If
               indexPos += m.Length + 1   
            End If
         Catch e As RegexMatchTimeoutException
            If e.MatchTimeout.TotalMilliseconds < MAX_TIMEOUT Then
               timeoutInterval += INCREMENT
               init = False
            Else
               ' Rethrow the exception.
               Throw 
            End If   
         End Try          
      Loop While m.Success

      ' If regex completed successfully, calculate number of words and average length.
      Dim nWords As Integer
      Dim totalLength As Long

      For ctr As Integer = wordLengths.GetLowerBound(0) To wordLengths.GetUpperBound(0)
         nWords += wordLengths(ctr)
         totalLength += ctr * wordLengths(ctr)
      Next
      Return New Tuple(Of Integer, Double)(nWords, totalLength/nWords)
   End Function
End Class
```

## <a name="capture-only-when-necessary"></a>Capture uniquement quand cela s’avère nécessaire

Les expressions régulières dans .NET prennent en charge plusieurs constructions de regroupement, ce qui vous permet de regrouper un modèle d’expression régulière dans une ou plusieurs sous-expressions. Les constructions de regroupement les plus fréquemment utilisées dans le langage d’expression régulière .NET sont **(**_sous-expression_**)**, qui définit un groupe de capture numéroté et **(?<*_nom_**>**_sous-expression_**)**, qui définit un groupe de capture nommé. Les constructions de regroupement sont essentielles pour créer des références arrières et pour définir une sous-expression à laquelle un quantificateur est appliqué. 

Toutefois, l'utilisation de ces éléments de langage n'est pas sans effet. Ils entraînent le remplissage de l’objet [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) renvoyé par la propriété [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) avec les captures nommées ou sans nom les plus récentes. Si une seule construction de regroupement a capturé plusieurs sous-chaînes dans la chaîne d’entrée, ils remplissent également l’objet [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) renvoyé par la propriété [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) d’un groupe de capture particulier à l’aide de plusieurs objets [Capture](xref:System.Text.RegularExpressions.Capture).

Souvent, les constructions de regroupement sont utilisées dans une expression régulière uniquement pour que les quantificateurs puissent leur être appliqués. Les groupes capturés par ces sous-expressions ne sont alors pas utilisés par la suite. Par exemple, l'expression régulière `\b(\w+[;,]?\s?)+[.?!]` est conçue pour capturer une phrase entière. Le tableau suivant décrit les éléments de langage dans ce modèle d’expression régulière et leur effet sur les collections [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) et [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) de l’objet [Match](xref:System.Text.RegularExpressions.Match).

Modèle | Description
------- | -----------
`\b` | Commencer la correspondance à la limite d'un mot.
`\w+` | Mettre en correspondance un ou plusieurs caractères alphabétiques.
`[;,]?` | Mettre en correspondance zéro ou une virgule, ou zéro ou un point-virgule.
`\s?` | Mettre en correspondance zéro ou un espace blanc.
`(\w+[;,]?\s?)+` | Mettre en correspondance une ou plusieurs occurrences d'un ou plusieurs caractères alphabétiques suivis d'une virgule ou d'un point-virgule facultatif suivi d'un espace blanc facultatif. Cela définit le premier groupe de capture. Il est nécessaire pour que la combinaison de plusieurs caractères alphabétiques (autrement dit, un mot) suivis d'un signe de ponctuation facultatif soit répétée jusqu'à ce que le moteur des expressions régulières ait atteint la fin d'une phrase.
`[.?!]` | Mettre en correspondance un point, un point d'interrogation ou un point d'exclamation.
 
Comme l’indique l’exemple suivant, quand une correspondance est trouvée, les objets [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) et [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) sont tous les deux remplis avec les captures de la correspondance. Dans cet exemple, le groupe de capture `(\w+[;,]?\s?)` existe pour que le quantificateur **+** puisse lui être appliqué, ce qui permet au modèle d’expression régulière de correspondre à chaque mot d’une phrase. Sinon, elle correspondrait au dernier mot d'une phrase.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is one sentence. This is another.";
      string pattern = @"\b(\w+[;,]?\s?)+[.?!]";

      foreach (Match match in Regex.Matches(input, pattern)) {
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index);
         int grpCtr = 0;
         foreach (Group grp in match.Groups) {
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index);
            int capCtr = 0;
            foreach (Capture cap in grp.Captures) {
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index);
               capCtr++;
            }
            grpCtr++;
         }          
         Console.WriteLine();        
      }
   }
}
// The example displays the following output:
//       Match: 'This is one sentence.' at index 0.
//          Group 0: 'This is one sentence.' at index 0.
//             Capture 0: 'This is one sentence.' at 0.
//          Group 1: 'sentence' at index 12.
//             Capture 0: 'This ' at 0.
//             Capture 1: 'is ' at 5.
//             Capture 2: 'one ' at 8.
//             Capture 3: 'sentence' at 12.
//       
//       Match: 'This is another.' at index 22.
//          Group 0: 'This is another.' at index 22.
//             Capture 0: 'This is another.' at 22.
//          Group 1: 'another' at index 30.
//             Capture 0: 'This ' at 22.
//             Capture 1: 'is ' at 27.
//             Capture 2: 'another' at 30.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is one sentence. This is another."
      Dim pattern As String = "\b(\w+[;,]?\s?)+[.?!]"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index)
         Dim grpCtr As Integer = 0
         For Each grp As Group In match.Groups
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index)
            Dim capCtr As Integer = 0
            For Each cap As Capture In grp.Captures
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index)
               capCtr += 1
            Next
            grpCtr += 1
         Next          
         Console.WriteLine()        
      Next    
   End Sub
End Module
' The example displays the following output:
'       Match: 'This is one sentence.' at index 0.
'          Group 0: 'This is one sentence.' at index 0.
'             Capture 0: 'This is one sentence.' at 0.
'          Group 1: 'sentence' at index 12.
'             Capture 0: 'This ' at 0.
'             Capture 1: 'is ' at 5.
'             Capture 2: 'one ' at 8.
'             Capture 3: 'sentence' at 12.
'       
'       Match: 'This is another.' at index 22.
'          Group 0: 'This is another.' at index 22.
'             Capture 0: 'This is another.' at 22.
'          Group 1: 'another' at index 30.
'             Capture 0: 'This ' at 22.
'             Capture 1: 'is ' at 27.
'             Capture 2: 'another' at 30.
```

Lorsque vous utilisez des sous-expressions uniquement pour y appliquer des quantificateurs et que le texte capturé ne vous intéresse pas, vous devez désactiver les captures de groupe. Par exemple, l’élément de langage **(?:**_sous-expression_**)** empêche le groupe auquel il s’applique de capturer les sous-chaînes correspondantes. Dans l'exemple suivant, le modèle d'expression régulière de l'exemple précédent est remplacé par `\b(?:\w+[;,]?\s?)+[.?!]`. Comme le montre la sortie, il empêche le moteur d’expression régulière de remplir les collections [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) et [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is one sentence. This is another.";
      string pattern = @"\b(?:\w+[;,]?\s?)+[.?!]";

      foreach (Match match in Regex.Matches(input, pattern)) {
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index);
         int grpCtr = 0;
         foreach (Group grp in match.Groups) {
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index);
            int capCtr = 0;
            foreach (Capture cap in grp.Captures) {
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index);
               capCtr++;
            }
            grpCtr++;
         }          
         Console.WriteLine();        
      }
   }
}
// The example displays the following output:
//       Match: 'This is one sentence.' at index 0.
//          Group 0: 'This is one sentence.' at index 0.
//             Capture 0: 'This is one sentence.' at 0.
//       
//       Match: 'This is another.' at index 22.
//          Group 0: 'This is another.' at index 22.
//             Capture 0: 'This is another.' at 22.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is one sentence. This is another."
      Dim pattern As String = "\b(?:\w+[;,]?\s?)+[.?!]"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index)
         Dim grpCtr As Integer = 0
         For Each grp As Group In match.Groups
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index)
            Dim capCtr As Integer = 0
            For Each cap As Capture In grp.Captures
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index)
               capCtr += 1
            Next
            grpCtr += 1
         Next          
         Console.WriteLine()        
      Next    
   End Sub
End Module
' The example displays the following output:
'       Match: 'This is one sentence.' at index 0.
'          Group 0: 'This is one sentence.' at index 0.
'             Capture 0: 'This is one sentence.' at 0.
'       
'       Match: 'This is another.' at index 22.
'          Group 0: 'This is another.' at index 22.
'             Capture 0: 'This is another.' at 22.
```

Vous pouvez désactiver les captures de l'une des façons suivantes :

* Utilisez l’élément de langage **(?:**_sous-expression_**)**. Cet élément empêche la capture des sous-chaînes correspondantes dans le groupe auquel il s'applique. Il ne désactive pas les captures de la sous-chaîne dans les groupes imbriqués.

* Utilisez l’option [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture). Elle désactive toutes les captures implicites ou sans nom dans le modèle d’expression régulière. Lorsque vous utilisez cette option, seules les sous-chaînes qui correspondent à des groupes nommés définis avec l’élément de langage **(?<**_nom_**>**_sous-expression_**)** peuvent être capturées. L’indicateur [ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) peut être passé au paramètre options d’un constructeur de classe [Regex](xref:System.Text.RegularExpressions.Regex) ou au paramètre options d’une méthode de mise en correspondance statique [Regex](xref:System.Text.RegularExpressions.Regex).

* Utilisez l’option **n** dans l’élément de langage **(?imnsx)**. Cette option désactive toutes les captures implicites ou sans nom à partir du point où l’élément apparaît dans le modèle d’expression régulière. Les captures sont désactivées jusqu’à la fin du modèle ou jusqu’à ce que l’option **(-n)** active les captures implicites ou sans nom. Pour plus d’informations, consultez [Constructions diverses dans les expressions régulières](miscellaneous.md).

* Utilisez l’option **n** dans l’élément de langage **(?imnsx:**_sous-expression_**)**. Cette option désactive toutes les captures implicites ou sans nom dans *sous-expression*. Les captures effectuées par les groupes de capture imbriqués implicites ou sans nom sont également désactivées.

## <a name="related-topics"></a>Rubriques connexes

Titre | Description
----- | ----------- 
[Comportement détaillé des expressions régulières](regex-behavior.md) | Aborde l’implémentation du moteur d’expression régulière dans .NET. Cette rubrique traite de la flexibilité des expressions régulières. Elle explique la responsabilité du développeur pour que le fonctionnement efficace et fiable du moteur des expressions régulières soit garanti.
[Retour sur trace dans les expressions régulières](backtracking.md) | Aborde la rétroaction et la façon dont elle affecte les performances des expressions régulières, ainsi que les éléments de langage, qui offrent des alternatives à la rétroaction.
[Langage des expressions régulières - Aide-mémoire](quick-ref.md) | Décrit les éléments du langage d’expression régulière dans .NET et propose des liens vers la documentation détaillée pour chaque élément de langage.
 




<!--HONumber=Nov16_HO1-->


