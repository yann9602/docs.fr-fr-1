---
title: "Rétroaction dans les expressions régulières"
description: "Rétroaction dans les expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8a3e6298-26b7-4c99-bd97-c9892f6c9418
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 00e324803cf5c57eab1cc71eb819949247131479

---

# <a name="backtracking-in-regular-expressions"></a>Rétroaction dans les expressions régulières

La rétroaction se produit quand un modèle d’expression régulière contient des [quantificateurs](quantifiers.md) ou des [constructions d’alternative](alternation.md) facultatifs, et que le moteur d’expression régulière retourne à un état enregistré précédent pour poursuivre la recherche d’une correspondance. La rétroaction est essentielle à la puissance des expressions régulières ; elle permet aux expressions d'être puissantes et flexibles et de correspondre à des modèles très complexes. Cependant, cette puissance a un coût. La rétroaction est souvent le facteur le plus important qui affecte les performances du moteur des expressions régulières. Heureusement, le développeur contrôle le comportement du moteur des expressions régulières et comment il utilise la rétroaction. Cette rubrique explique comment la rétroaction fonctionne et comment elle peut être activée.

> [!NOTE]
> En général, un moteur NFA (Nondeterministic Finite Automaton) tel que le moteur d’expression régulière fait peser la responsabilité de la conception d’expressions régulières efficaces et rapides sur le développeur.
 
Cette rubrique contient les sections suivantes :

* [Comparaison linéaire sans rétroaction](#linear-comparison-without-backtracking)

* [Rétroaction avec des quantificateurs facultatifs ou des constructions d’alternative](#backtracking-with-optional-quantifiers-or-alternation-constructs)

* [Rétroaction avec des quantificateurs facultatifs imbriqués](#backtracking-with-nested-optional-quantifiers)

* [Contrôle de la rétroaction](#controlling-backtracking)

## <a name="linear-comparison-without-backtracking"></a>Comparaison linéaire sans rétroaction

Si un modèle d'expression régulière ne possède pas de quantificateur facultatif ou de construction d'alternative, le moteur des expressions régulières s'exécute en temps linéaire. Autrement dit, une fois que le moteur des expressions régulières correspond au premier élément de langage dans le modèle avec du texte dans la chaîne d'entrée, il tente de correspondre à l'élément de langage suivant dans le modèle avec le caractère ou le groupe suivant de caractères dans la chaîne d'entrée. Cela se poursuit jusqu'à ce que la correspondance réussisse ou échoue. Dans les deux cas, le moteur des expressions régulières avance d'un caractère à la fois dans la chaîne d'entrée.

L'exemple suivant illustre cette situation. L'expression régulière `e{2}\w\b` recherche deux occurrences de la lettre « e » suivie de n'importe quel caractère de mot suivi d'une limite de mot.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "needing a reed";
      string pattern = @"e{2}\w\b";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("{0} found at position {1}", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       eed found at position 11
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "needing a reed"
      Dim pattern As String = "e{2}\w\b"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("{0} found at position {1}", _
                           match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       eed found at position 11
```

Bien que cette expression régulière inclue le quantificateur `{2}`, elle est évaluée de façon linéaire. Le moteur des expressions régulières ne revient pas en arrière, car `{2}` n'est pas un quantificateur facultatif ; il spécifie un nombre exact et pas un nombre variable de fois que la sous-expression précédente doit correspondre. Par conséquent, le moteur des expressions régulières tente de correspondre au modèle d'expression régulière avec la chaîne d'entrée comme indiqué dans le tableau suivant.

Opération | Position dans le modèle | Position dans la chaîne | Résultat
--------- | ------------------- | ------------------ | ------ 
1 | e | "besoin d'un roseau" (index 0) | Pas de correspondance. 
2 | e | "esoin d'un roseau" (index 1) | Correspondance possible. 
3 | e{2} | "soin d'un roseau" (index 2) | Correspondance possible. 
4 | \w | "oin d'un roseau" (index 3) | Correspondance possible.
5 | \b | "in d'un roseau" (index 4) | Échecs de correspondance possibles. 
6 | e | "soin d'un roseau" (index 2) | Correspondance possible. 
7 | e{2} | "oin d'un roseau" (index 3) | Échecs de correspondance possibles. 
8 | e | "oin d'un roseau" (index 3) | Échec de la correspondance. 
9 | e | "in d'un roseau" (index 4) | Pas de correspondance.
10 | e | "n d'un roseau" (index 5) | Pas de correspondance.
11 | e | "d'un roseau" (index 6) | Pas de correspondance.
12 | e | " un roseau" (index 7) | Pas de correspondance.
13 | e | "un roseau" (index 8) | Pas de correspondance.
14 | e | " roseau" (index 9) | Pas de correspondance.
15 | e | "roseau" (index 10) | Pas de correspondance
16 | e | "seau" (index 11) | Correspondance possible.
17 | e{2} | "au" (index 12) | Correspondance possible.
18 | \w | "u" (index 13) | Correspondance possible.
19 | \b | "" (index 14) | Correspondance
 

Si un modèle d'expression régulière n'inclut aucun quantificateur facultatif ou construction d'alternative, le nombre maximal de comparaisons requises pour correspondre au modèle d'expression régulière avec la chaîne d'entrée équivaut à peu près au nombre de caractères dans la chaîne d'entrée. Dans ce cas, le moteur des expressions régulières utilise 19 comparaisons pour identifier les correspondances possibles dans cette chaîne de 13 caractères. En d'autres termes, le moteur des expressions régulières s'exécute en temps quasi linéaire s'il ne contient pas de quantificateur facultatif ou de construction d'alternative.

## <a name="backtracking-with-optional-quantifiers-or-alternation-constructs"></a>Rétroaction avec des quantificateurs facultatifs ou des constructions d’alternative

Lorsqu'une expression régulière inclut des quantificateurs facultatifs ou des constructions d'alternative, l'évaluation de la chaîne d'entrée n'est plus linéaire. Les critères spéciaux avec un moteur NFA sont pilotés par les éléments de langage dans l'expression régulière et non par des caractères de correspondance dans la chaîne d'entrée. Par conséquent, le moteur des expressions régulières tente de correspondre complètement aux sous-expressions facultatives ou alternatives. Lorsqu'il avance à l'élément de langage suivant dans la sous-expression et que la correspondance échoue, le moteur des expressions régulières peut abandonner une partie de sa correspondance trouvée et retourner à un état enregistré précédent afin de mettre en correspondance l'expression régulière dans son ensemble avec la chaîne d'entrée. Ce processus de retour à un état enregistré précédent pour rechercher une correspondance est appelé rétroaction.

Considérons, par exemple, le modèle d'expression régulière `.*(es)`, qui correspond aux caractères « es » et tous caractères qui précèdent. Comme l'exemple suivant l'indique, si la chaîne d'entrée est « Des services essentiels sont fournis par les expressions régulières. », le modèle correspond à la chaîne entière jusqu'à « es » dans « expressions ».

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "Essential services are provided by regular expressions.";
      string pattern = ".*(es)"; 
      Match m = Regex.Match(input, pattern, RegexOptions.IgnoreCase);
      if (m.Success) {
         Console.WriteLine("'{0}' found at position {1}", 
                           m.Value, m.Index);
         Console.WriteLine("'es' found at position {0}", 
                           m.Groups[1].Index);      
      } 
   }
}
//    'Essential services are provided by regular expres' found at position 0
//    'es' found at position 47
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "Essential services are provided by regular expressions."
      Dim pattern As String = ".*(es)" 
      Dim m As Match = Regex.Match(input, pattern, RegexOptions.IgnoreCase)
      If m.Success Then
         Console.WriteLine("'{0}' found at position {1}", _
                           m.Value, m.Index)
         Console.WriteLine("'es' found at position {0}", _
                           m.Groups(1).Index)                  
      End If     
   End Sub
End Module
'    'Essential services are provided by regular expres' found at position 0
'    'es' found at position 47
```

Pour cela, le moteur des expressions régulières utilise la rétroaction comme suit :

* Il établit une correspondance entre `.*` (qui correspond à zéro, une ou plusieurs occurrences d'un caractère) et la chaîne d'entrée entière.

* Il tente de faire correspondre « e » dans le modèle d'expression régulière. Toutefois, il ne reste aucun caractère disponible pour la correspondance dans la chaîne d'entrée.

* Il revient en arrière à la dernière correspondance trouvée, « Des services essentiels sont fournis par les expressions régulières » et tente de faire correspondre « e » avec le point à la fin de la phrase. La correspondance échoue.

* Il continue à revenir en arrière à la correspondance précédente caractère après caractère jusqu'à ce qu'à ce que la sous-chaîne en correspondance provisoire soit « Des services essentiels sont fournis par le les expr ». Il compare ensuite le « e » dans le modèle avec le second « e » dans « expressions » et trouve une correspondance.

* Il compare le « s » dans le modèle avec le « s » qui suit le « e » mis en correspondance (le premier « s » dans « expressions »). La correspondance réussit.

Lorsque vous utilisez la rétroaction, la mise en correspondance du modèle d'expression régulière avec la chaîne d'entrée, qui comporte 55 caractères, requiert 67 opérations de comparaison. Chose intéressante, si le modèle d’expression régulière comprenait un quantificateur paresseux, `.*?(es),`, la mise en correspondance de l’expression normale nécessiterait des comparaisons supplémentaires. Dans ce cas, au lieu de devoir revenir en arrière à la fin de la chaîne à « r » dans « expressions », le moteur des expressions régulières devrait revenir en arrière complètement au début de la chaîne pour établir une correspondance avec « es » et nécessiterait 113 comparaisons. En général, si un modèle d'expression régulière a une seule construction d'alternative ou un seul quantificateur facultatif, le nombre d'opérations de comparaison requises pour correspondre au modèle est supérieur au double du nombre de caractères dans la chaîne d'entrée.

## <a name="backtracking-with-nested-optional-quantifiers"></a>Rétroaction avec des quantificateurs facultatifs imbriqués

Le nombre d'opérations de comparaison requises pour correspondre à un modèle d'expression régulière peut augmenter de façon exponentielle si le modèle se compose d'un grand nombre de constructions d'alternative, s'il est constitué de constructions d'alternative imbriquées ou, le plus souvent, s'il inclut des quantificateurs facultatifs imbriqués. Par exemple, le modèle d'expression régulière `^(a+)+$` est conçu pour une correspondance avec une chaîne complète qui contient un ou plusieurs caractères « a ». L'exemple fournit deux chaînes d'entrée de longueurs identiques, mais seule la première chaîne correspond au modèle. La classe [System.Diagnostics.Stopwatch](xref:System.Diagnostics.Stopwatch) est utilisée pour déterminer la durée de l’opération de correspondance. 

```csharp
using System;
using System.Diagnostics;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "^(a+)+$";
      string[] inputs = { "aaaaaa", "aaaaa!" };
      Regex rgx = new Regex(pattern);
      Stopwatch sw;

      foreach (string input in inputs) {
         sw = Stopwatch.StartNew();   
         Match match = rgx.Match(input);
         sw.Stop();
         if (match.Success)
            Console.WriteLine("Matched {0} in {1}", match.Value, sw.Elapsed);
         else
            Console.WriteLine("No match found in {0}", sw.Elapsed);
      }
   }
}
```

```vb
Imports System.Diagnostics
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^(a+)+$"
      Dim inputs() As String = { "aaaaaa", "aaaaa!" }
      Dim rgx As New Regex(pattern)
      Dim sw As Stopwatch

      For Each input As String In inputs
         sw = Stopwatch.StartNew()   
         Dim match As Match = rgx.Match(input)
         sw.Stop()
         If match.Success Then
            Console.WriteLine("Matched {0} in {1}", match.Value, sw.Elapsed)
         Else
            Console.WriteLine("No match found in {0}", sw.Elapsed)
         End If      
      Next
   End Sub
End Module
```

Comme la sortie de l'exemple indique, il a fallu presque deux fois plus de temps au moteur des expressions régulières pour constater qu'une chaîne d'entrée ne correspondait pas au modèle que pour identifier une chaîne correspondante. Cela est dû au fait qu'une correspondance infructueuse représente toujours le pire des scénarios. Le moteur des expressions régulières doit utiliser l'expression régulière pour suivre tous les chemins d'accès possibles dans les données avant qu'il puisse conclure que la correspondance est infructueuse, et les parenthèses imbriquées créent plusieurs chemins d'accès supplémentaires dans les données. Le moteur des expressions régulières conclut que la deuxième chaîne ne correspondait pas au modèle en procédant comme suit :

* Il vérifie qu’il était au début de la chaîne, puis fait correspondre les cinq premiers caractères dans la chaîne avec le modèle a+. Il détermine ensuite qu'il n'y a aucun groupe supplémentaire de caractères « a » dans la chaîne. Enfin, il effectue en test pour déterminer la fin de la chaîne. Étant donné qu'il reste un caractère supplémentaire dans la chaîne, la correspondance échoue. Cette correspondance infructueuse requiert 9 comparaisons. Le moteur des expressions régulières enregistre également des informations d'état de ses correspondances de « a » (que nous appellerons correspondance 1), « aa » (correspondance 2), « aaa » (correspondance 3) et « aaaa » (correspondance 4).

* Il revient à la correspondance 4 enregistrée précédemment. Il détermine qu'il y a un caractère « a » supplémentaire à assigner à un groupe capturé supplémentaire. Enfin, il effectue en test pour déterminer la fin de la chaîne. Étant donné qu'il reste un caractère supplémentaire dans la chaîne, la correspondance échoue. Cette correspondance infructueuse requiert 4 comparaisons. Jusqu'à présent, un total de 13 comparaisons ont été effectuées.

* Il revient à la correspondance 3 enregistrée précédemment. Il détermine qu'il y a deux caractères « a » supplémentaires à assigner à un groupe capturé supplémentaire. Toutefois, le test de fin de chaîne échoue. Il revient ensuite à la correspondance 3 et tente de faire correspondre les deux caractères « a » supplémentaire dans deux groupes capturés supplémentaires. Le test de fin de chaîne échoue encore. Ces correspondances infructueuses requièrent 12 comparaisons. Jusqu'à présent, un total de 25 comparaisons ont été effectuées. 

La comparaison de la chaîne d'entrée avec l'expression régulière continue de cette façon jusqu'à ce que le moteur des expressions régulières ait tenté toutes les combinaisons possibles des correspondances et conclue qu'il n'existe aucune correspondance. À cause des quantificateurs imbriqués, cette comparaison correspond à un O(2n) ou une opération exponentielle, où n est le nombre de caractères dans la chaîne d’entrée. Cela signifie que dans le pire des cas, une chaîne d'entrée de 30 caractères requiert environ 1 073 741 824 comparaisons et une chaîne d'entrée de 40 caractères requiert environ 1 099 511 627 776 comparaisons. Si vous utilisez des chaînes de longueurs identiques ou supérieures, l'exécution des méthodes d'expression régulières peut prendre très longtemps lorsqu'elles traitent une entrée qui ne correspond pas au modèle d'expression régulière.

## <a name="controlling-backtracking"></a>Contrôle de la rétroaction

La rétroaction vous permet de créer des expressions régulières puissantes et flexibles. Toutefois, comme la section précédente l'indiquait, ces avantages peuvent s'accompagner de performances médiocres. Pour empêcher une rétroaction excessive, vous devez définir un intervalle de délai d’attente quand vous instanciez un objet [Regex](xref:System.Text.RegularExpressions.Regex) ou appelez une méthode de mise en correspondance statique d’expression régulière. Cette situation est présentée dans la section suivante. Par ailleurs, .NET Core prend en charge trois éléments de langage d’expression régulière qui limitent ou suppriment la rétroaction et prennent en charge des expressions régulières complexes avec une perte de performances faible ou nulle : [sous-expressions non rétroactives](#nonbacktracking-subexpression), [assertions de postanalyse](#lookbehind-assertions) et [assertions de préanalyse](#lookahead-assertions). Pour plus d’informations sur chaque élément de langage, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).

### <a name="defining-a-timeout-interval"></a>Définir un intervalle de délai d’attente

Vous pouvez définir un intervalle de délai d’attente qui représente la durée maximale pendant laquelle le moteur d’expression régulière recherche une correspondance avant d’abandonner la tentative et de lever une exception [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException). Vous spécifiez l’intervalle de délai d’attente en donnant une valeur [TimeSpan](xref:System.TimeSpan) au constructeur `Regex(String, RegexOptions, TimeSpan)` pour les expressions régulières d’instances. En outre, chaque méthode de mise en correspondance de modèle statique possède une surcharge avec une valeur [TimeSpan](xref:System.TimeSpan) pour le paramètre [Regex.Regex(String, RegexOptions, TimeSpan)] qui vous permet de spécifier une valeur de délai d’attente. Par défaut, l’intervalle de délai d’attente est défini sur [Regex.InfiniteMatchTimeout](xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout) et le moteur d’expression régulière n’expire pas. 

> [!IMPORTANT]
> Il est recommandé de toujours définir un intervalle de délai d’attente si votre expression régulière utilise la rétroaction.
 
Une exception [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException) indique que le moteur d’expression régulière n’a pas pu trouver de correspondance dans l’intervalle de délai d’attente spécifié mais n’indique pas pourquoi l’exception a été levée. Cela peut provenir de la rétroaction excessive, mais il est possible que l'intervalle de délai d'attente était trop faible étant donné la charge système au moment où l'exception a été levée. Lorsque vous gérez l'exception, vous pouvez choisir d'abandonner d'autres correspondances avec la chaîne d'entrée ou augmenter l'intervalle de délai d'attente et de retenter l'opération de mise en correspondance. 

Par exemple, le code suivant appelle le constructeur `Regex(String, RegexOptions, TimeSpan)` pour instancier un objet Regex avec un délai d’attente d’une seconde. Le modèle d'expression régulière `(a+)+$`, qui correspond à une ou plusieurs séquences d'un ou plusieurs caractères « a » à la fin d'une ligne, est soumis à une rétroaction excessive. Si une exception [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException) est levée, l’exemple augmente la valeur du délai d’attente jusqu’à un intervalle maximal de trois secondes. Après cela, il abandonne la tentative pour mettre en correspondance le modèle.

```csharp
using System;
using System.ComponentModel;
using System.Diagnostics;
using System.Security;
using System.Text.RegularExpressions;
using System.Threading; 

public class Example
{
   const int MaxTimeoutInSeconds = 3;

   public static void Main()
   {
      string pattern = @"(a+)+$";    // DO NOT REUSE THIS PATTERN.
      Regex rgx = new Regex(pattern, RegexOptions.IgnoreCase, TimeSpan.FromSeconds(1));       
      Stopwatch sw = null;

      string[] inputs= { "aa", "aaaa>", 
                         "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
                         "aaaaaaaaaaaaaaaaaaaaaa>",
                         "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa>" };

      foreach (var inputValue in inputs) {
         Console.WriteLine("Processing {0}", inputValue);
         bool timedOut = false;
         do { 
            try {
               sw = Stopwatch.StartNew();
               // Display the result.
               if (rgx.IsMatch(inputValue)) {
                  sw.Stop();
                  Console.WriteLine(@"Valid: '{0}' ({1:ss\.fffffff} seconds)", 
                                    inputValue, sw.Elapsed); 
               }
               else {
                  sw.Stop();
                  Console.WriteLine(@"'{0}' is not a valid string. ({1:ss\.fffff} seconds)", 
                                    inputValue, sw.Elapsed);
               }
            }
            catch (RegexMatchTimeoutException e) {   
               sw.Stop();
               // Display the elapsed time until the exception.
               Console.WriteLine(@"Timeout with '{0}' after {1:ss\.fffff}", 
                                 inputValue, sw.Elapsed);
               Thread.Sleep(1500);       // Pause for 1.5 seconds.

               // Increase the timeout interval and retry.
               TimeSpan timeout = e.MatchTimeout.Add(TimeSpan.FromSeconds(1));
               if (timeout.TotalSeconds > MaxTimeoutInSeconds) {
                  Console.WriteLine("Maximum timeout interval of {0} seconds exceeded.",
                                    MaxTimeoutInSeconds);
                  timedOut = false;
               }
               else {               
                  Console.WriteLine("Changing the timeout interval to {0}", 
                                    timeout); 
                  rgx = new Regex(pattern, RegexOptions.IgnoreCase, timeout);
                  timedOut = true;
               }
            }
         } while (timedOut);
         Console.WriteLine();
      }   
   }
}
// The example displays output like the following :
//    Processing aa
//    Valid: 'aa' (00.0000779 seconds)
//    
//    Processing aaaa>
//    'aaaa>' is not a valid string. (00.00005 seconds)
//    
//    Processing aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
//    Valid: 'aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa' (00.0000043 seconds)
//    
//    Processing aaaaaaaaaaaaaaaaaaaaaa>
//    Timeout with 'aaaaaaaaaaaaaaaaaaaaaa>' after 01.00469
//    Changing the timeout interval to 00:00:02
//    Timeout with 'aaaaaaaaaaaaaaaaaaaaaa>' after 02.01202
//    Changing the timeout interval to 00:00:03
//    Timeout with 'aaaaaaaaaaaaaaaaaaaaaa>' after 03.01043
//    Maximum timeout interval of 3 seconds exceeded.
//    
//    Processing aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa>
//    Timeout with 'aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa>' after 03.01018
//    Maximum timeout interval of 3 seconds exceeded.
```

```vb
Imports System.ComponentModel
Imports System.Diagnostics
Imports System.Security
Imports System.Text.RegularExpressions
Imports System.Threading 

Module Example
   Const MaxTimeoutInSeconds As Integer = 3

   Public Sub Main()
      Dim pattern As String = "(a+)+$"    ' DO NOT REUSE THIS PATTERN.
      Dim rgx As New Regex(pattern, RegexOptions.IgnoreCase, TimeSpan.FromSeconds(1))       
      Dim sw As Stopwatch = Nothing

      Dim inputs() As String = { "aa", "aaaa>", 
                                 "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
                                 "aaaaaaaaaaaaaaaaaaaaaa>",
                                 "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa>" }

      For Each inputValue In inputs
         Console.WriteLine("Processing {0}", inputValue)
         Dim timedOut As Boolean = False
         Do 
            Try
               sw = Stopwatch.StartNew()
               ' Display the result.
               If rgx.IsMatch(inputValue) Then
                  sw.Stop()
                  Console.WriteLine("Valid: '{0}' ({1:ss\.fffffff} seconds)", 
                                    inputValue, sw.Elapsed) 
               Else
                  sw.Stop()
                  Console.WriteLine("'{0}' is not a valid string. ({1:ss\.fffff} seconds)", 
                                    inputValue, sw.Elapsed)
               End If
            Catch e As RegexMatchTimeoutException   
               sw.Stop()
               ' Display the elapsed time until the exception.
               Console.WriteLine("Timeout with '{0}' after {1:ss\.fffff}", 
                                 inputValue, sw.Elapsed)
               Thread.Sleep(1500)       ' Pause for 1.5 seconds.

               ' Increase the timeout interval and retry.
               Dim timeout As TimeSpan = e.MatchTimeout.Add(TimeSpan.FromSeconds(1))
               If timeout.TotalSeconds > MaxTimeoutInSeconds Then
                  Console.WriteLine("Maximum timeout interval of {0} seconds exceeded.",
                                    MaxTimeoutInSeconds)
                  timedOut = False
               Else                
                  Console.WriteLine("Changing the timeout interval to {0}", 
                                    timeout) 
                  rgx = New Regex(pattern, RegexOptions.IgnoreCase, timeout)
                  timedOut = True
               End If
            End Try
         Loop While timedOut
         Console.WriteLine()
      Next   
   End Sub 
End Module
' The example displays output like the following:
'    Processing aa
'    Valid: 'aa' (00.0000779 seconds)
'    
'    Processing aaaa>
'    'aaaa>' is not a valid string. (00.00005 seconds)
'    
'    Processing aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
'    Valid: 'aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa' (00.0000043 seconds)
'    
'    Processing aaaaaaaaaaaaaaaaaaaaaa>
'    Timeout with 'aaaaaaaaaaaaaaaaaaaaaa>' after 01.00469
'    Changing the timeout interval to 00:00:02
'    Timeout with 'aaaaaaaaaaaaaaaaaaaaaa>' after 02.01202
'    Changing the timeout interval to 00:00:03
'    Timeout with 'aaaaaaaaaaaaaaaaaaaaaa>' after 03.01043
'    Maximum timeout interval of 3 seconds exceeded.
'    
'    Processing aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa>
'    Timeout with 'aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa>' after 03.01018
'    Maximum timeout interval of 3 seconds exceeded.
```

### <a name="nonbacktracking-subexpression"></a>Sous-expression non rétroactive

L’élément de langage **(?>** _sous-expression_**)** supprime la rétroaction dans une sous-expression. Cela permet d'éviter les problèmes de performances associés liés à des correspondances infructueuses. 

L'exemple suivant montre comment la suppression de la rétroaction améliore les performances lors de l'utilisation de quantificateurs imbriqués. Il mesure le temps nécessaire pour que le moteur des expressions régulières détermine qu'une chaîne d'entrée ne correspond pas à deux expressions régulières. La première expression régulière utilise la rétroaction pour tenter de mettre en correspondance une chaîne qui contient une ou plusieurs occurrences d'un ou plusieurs chiffres hexadécimaux, suivi d'un signe deux-points, suivi d'un ou plusieurs chiffres hexadécimaux, suivi de deux signes deux-points. La seconde expression régulière est identique à la première, à ceci près qu'elle désactive la rétroaction. Comme la sortie de l'exemple l'indique, l'amélioration des performances due à la désactivation de la rétroaction est considérable.

```csharp
using System;
using System.Diagnostics;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "b51:4:1DB:9EE1:5:27d60:f44:D4:cd:E:5:0A5:4a:D24:41Ad:";
      bool matched;
      Stopwatch sw;

      Console.WriteLine("With backtracking:");
      string backPattern = "^(([0-9a-fA-F]{1,4}:)*([0-9a-fA-F]{1,4}))*(::)$";
      sw = Stopwatch.StartNew();
      matched = Regex.IsMatch(input, backPattern);
      sw.Stop();
      Console.WriteLine("Match: {0} in {1}", Regex.IsMatch(input, backPattern), sw.Elapsed);
      Console.WriteLine();

      Console.WriteLine("Without backtracking:");
      string noBackPattern = "^((?>[0-9a-fA-F]{1,4}:)*(?>[0-9a-fA-F]{1,4}))*(::)$";
      sw = Stopwatch.StartNew();
      matched = Regex.IsMatch(input, noBackPattern);
      sw.Stop();
      Console.WriteLine("Match: {0} in {1}", Regex.IsMatch(input, noBackPattern), sw.Elapsed);
   }
}
// The example displays output like the following:
//       With backtracking:
//       Match: False in 00:00:27.4282019
//       
//       Without backtracking:
//       Match: False in 00:00:00.0001391
```

```vb
Imports System.Diagnostics
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "b51:4:1DB:9EE1:5:27d60:f44:D4:cd:E:5:0A5:4a:D24:41Ad:"
      Dim matched As Boolean
      Dim sw As Stopwatch

      Console.WriteLine("With backtracking:")
      Dim backPattern As String = "^(([0-9a-fA-F]{1,4}:)*([0-9a-fA-F]{1,4}))*(::)$"
      sw = Stopwatch.StartNew()
      matched = Regex.IsMatch(input, backPattern)
      sw.Stop()
      Console.WriteLine("Match: {0} in {1}", Regex.IsMatch(input, backPattern), sw.Elapsed)
      Console.WriteLine()

      Console.WriteLine("Without backtracking:")
      Dim noBackPattern As String = "^((?>[0-9a-fA-F]{1,4}:)*(?>[0-9a-fA-F]{1,4}))*(::)$"
      sw = Stopwatch.StartNew()
      matched = Regex.IsMatch(input, noBackPattern)
      sw.Stop()
      Console.WriteLine("Match: {0} in {1}", Regex.IsMatch(input, noBackPattern), sw.Elapsed)
   End Sub
End Module
' The example displays the following output:
'       With backtracking:
'       Match: False in 00:00:27.4282019
'       
'       Without backtracking:
'       Match: False in 00:00:00.0001391
```

### <a name="lookbehind-assertions"></a>Assertions de postanalyse

.NET inclut deux éléments de langage, **(?<**=_sous-expression_**)** et **(?<!**_sous-expression_**)**, qui correspondent aux caractères précédents dans la chaîne d’entrée. Les deux éléments de langage sont des assertions de largeur nulle ; c’est-à-dire qu’ils déterminent si le ou les caractères qui précèdent immédiatement le caractère actuel peuvent être mis en correspondance par la *sous-expression*, sans avancer ou utiliser la rétroaction. 

**(?<**=_sous-expression_**)** est une assertion de postanalyse positive ; c’est-à-dire que le ou les caractères situés avant la position actuelle doivent correspondre à la *sous-expression*. **(?<!**_sous-expression_**)** est une assertion de postanalyse négative ; c’est-à-dire que le ou les caractères situés avant la position actuelle ne doivent pas correspondre à la *sous-expression*. Les assertions de postanalyse positive et négative sont très utiles quand la *sous-expression* est un sous-ensemble de la *sous-expression* précédente. 

L'exemple suivant utilise deux modèles d'expressions régulières équivalents qui valident le nom d'utilisateur dans une adresse e-mail. Le premier modèle est sujet à des performances médiocres dues à une rétroaction excessive. Le second modèle modifie la première expression régulière en remplaçant un quantificateur imbriqué par une assertion de postanalyse positive. La sortie de l’exemple indique la durée d’exécution de la méthode [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)).

```csharp
using System;
using System.Diagnostics;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      Stopwatch sw;
      string input = "aaaaaaaaaaaaaaaaaaaa";
      bool result;

      string pattern = @"^[0-9A-Z]([-.\w]*[0-9A-Z])?@";
      sw = Stopwatch.StartNew();
      result = Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase);
      sw.Stop();
      Console.WriteLine("Match: {0} in {1}", result, sw.Elapsed);

      string behindPattern = @"^[0-9A-Z][-.\w]*(?<=[0-9A-Z])@";
      sw = Stopwatch.StartNew();
      result = Regex.IsMatch(input, behindPattern, RegexOptions.IgnoreCase);
      sw.Stop();
      Console.WriteLine("Match with Lookbehind: {0} in {1}", result, sw.Elapsed);
   }
}
// The example displays output similar to the following:
//       Match: True in 00:00:00.0017549
//       Match with Lookbehind: True in 00:00:00.0000659
```

```vb
Module Example
   Public Sub Main()
      Dim sw As Stopwatch
      Dim input As String = "aaaaaaaaaaaaaaaaaaaa"
      Dim result As Boolean

      Dim pattern As String = "^[0-9A-Z]([-.\w]*[0-9A-Z])?@"
      sw = Stopwatch.StartNew()
      result = Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase)
      sw.Stop()
      Console.WriteLine("Match: {0} in {1}", result, sw.Elapsed)

      Dim behindPattern As String = "^[0-9A-Z][-.\w]*(?<=[0-9A-Z])@"
      sw = Stopwatch.StartNew()
      result = Regex.IsMatch(input, behindPattern, RegexOptions.IgnoreCase)
      sw.Stop()
      Console.WriteLine("Match with Lookbehind: {0} in {1}", result, sw.Elapsed)
   End Sub
End Module
' The example displays output similar to the following:
'       Match: True in 00:00:00.0017549
'       Match with Lookbehind: True in 00:00:00.0000659
```

Le premier modèle d’expression régulière, `^[0-9A-Z]([-.\w]*[0-9A-Z])*@, is defined as shown in the following table.`

Modèle | Description
------- | ----------- 
`^` | Démarrer la correspondance au début de la chaîne.
`[0-9A-Z]` | Mettre en correspondance un caractère alphanumérique. Cette comparaison ne respecte pas la casse car la méthode [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) est appelée avec l’option [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase).
`[-.\w]*` | Mettre en correspondance zéro, une ou plusieurs occurrences d'un trait d'union, d'un point ou d'un caractère alphabétique. 
`[0-9A-Z]` | Mettre en correspondance un caractère alphanumérique. 
`([-.\w]*[0-9A-Z])*` | Mettre en correspondance zéro, une ou plusieurs occurrences de la combinaison de zéro ou plus traits d'union, points ou caractères alphabétiques, suivis d'un caractère alphanumérique. Il s'agit du premier groupe de capture.
`@` | Mettre en correspondance un arobase (« @ »).
 
Le second modèle d'expression régulière, `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])@`, utilise une assertion de postanalyse positive. Il est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`^` | Démarrer la correspondance au début de la chaîne.
`[0-9A-Z]` | Mettre en correspondance un caractère alphanumérique. Cette comparaison ne respecte pas la casse car la méthode [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) est appelée avec l’option [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase).
`[-.\w]*` | Mettre en correspondance zéro, une ou plusieurs occurrences d'un trait d'union, d'un point ou d'un caractère alphabétique.
`(?<=[0-9A-Z])` | Remonter au dernier caractère mis en correspondance et continuer la mise en correspondances si elle est alphanumérique. Notez que les caractères alphanumériques sont un sous-ensemble du jeu qui se compose de points, de traits d'union et de tous les caractères alphabétiques.
`@` | Mettre en correspondance un arobase (« @ »).
 
### <a name="lookahead-assertions"></a>Assertions de préanalyse

.NET inclut deux éléments de langage, **(?**=_sous-expression_**)** et **(?!**_sous-expression_**)**, qui correspondent aux caractères suivants dans la chaîne d’entrée. Les deux éléments de langage sont des assertions de largeur nulle ; c’est-à-dire qu’ils déterminent si le ou les caractères qui suivent immédiatement le caractère actuel peuvent être mis en correspondance par la *sous-expression*, sans avancer ou utiliser la rétroaction. 

**(?**=_sous-expression_**)** est une assertion de préanalyse positive ; c’est-à-dire que le ou les caractères situés après la position actuelle doivent correspondre à la *sous-expression*. **(?!**_sous-expression_**)** est une assertion de préanalyse négative ; c’est-à-dire que le ou les caractères situés après la position actuelle ne doivent pas correspondre à la *sous-expression*. Les assertions de préanalyse positive et négative sont très utiles quand la *sous-expression* est un sous-ensemble de la *sous-expression* suivante. 

L'exemple suivant utilise deux modèles d'expressions régulières équivalentes qui valident un nom de type qualifié complet. Le premier modèle est sujet à des performances médiocres dues à une rétroaction excessive. Le second modifie la première expression régulière en remplaçant un quantificateur imbriqué par une assertion de préanalyse positive. La sortie de l’exemple indique la durée d’exécution de la méthode [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)).

```csharp
using System;
using System.Diagnostics;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "aaaaaaaaaaaaaaaaaaaaaa.";
      bool result;
      Stopwatch sw;

      string pattern = @"^(([A-Z]\w*)+\.)*[A-Z]\w*$";
      sw = Stopwatch.StartNew();
      result = Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase);
      sw.Stop();
      Console.WriteLine("{0} in {1}", result, sw.Elapsed);

      string aheadPattern = @"^((?=[A-Z])\w+\.)*[A-Z]\w*$";
      sw = Stopwatch.StartNew();
      result = Regex.IsMatch(input, aheadPattern, RegexOptions.IgnoreCase);
      sw.Stop();
      Console.WriteLine("{0} in {1}", result, sw.Elapsed);
   }
}
// The example displays the following output:
//       False in 00:00:03.8003793
//       False in 00:00:00.0000866
```

```vb
Imports System.Diagnostics
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "aaaaaaaaaaaaaaaaaaaaaa."
      Dim result As Boolean
      Dim sw As Stopwatch

      Dim pattern As String = "^(([A-Z]\w*)+\.)*[A-Z]\w*$"
      sw = Stopwatch.StartNew()
      result = Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase)
      sw.Stop()
      Console.WriteLine("{0} in {1}", result, sw.Elapsed)

      Dim aheadPattern As String = "^((?=[A-Z])\w+\.)*[A-Z]\w*$"
      sw = Stopwatch.StartNew()
      result = Regex.IsMatch(input, aheadPattern, RegexOptions.IgnoreCase)
      sw.Stop()
      Console.WriteLine("{0} in {1}", result, sw.Elapsed)
   End Sub
End Module
' The example displays the following output:
'       False in 00:00:03.8003793
'       False in 00:00:00.0000866
```

Le premier modèle d'expression régulière, `^(([A-Z]\w*)+\.)*[A-Z]\w*$`, est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`^` | Démarrer la correspondance au début de la chaîne.
`([A-Z]\w*)+\.` | Mettre en correspondance un caractère alphabétique (A-Z) suivi de zéro, un ou plusieurs caractères alphabétiques une ou plusieurs fois, suivi d'un point. Cette comparaison ne respecte pas la casse car la méthode [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) est appelée avec l’option [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase).
`(([A-Z]\w*)+\.)*` | Mettre en correspondance le modèle précédent, zéro, une ou plusieurs fois. 
`[A-Z]\w*` | Mettre en correspondance un caractère alphabétique suivi de zéro, un ou plusieurs caractères alphabétiques.
`$` | Terminer la correspondance à la fin de la chaîne d'entrée.
 

Le second modèle d'expression régulière, `^((?=[A-Z])\w+\.)*[A-Z]\w*$`, utilise une assertion de préanalyse positive. Il est défini comme indiqué dans le tableau suivant.

Modèle | Description
------- | ----------- 
`^` | Démarrer la correspondance au début de la chaîne.
`(?=[A-Z])` | Effectuer une préanalyse du premier caractère et continuer la mise en correspondance s'il est alphabétique (A-Z). Cette comparaison ne respecte pas la casse car la méthode [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) est appelée avec l’option [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase).
`\w+\.` | Mettre en correspondance un ou plusieurs caractères alphabétiques suivis d'un point.
`((?=[A-Z])\w+\.)*` | Mettre en correspondance un ou plusieurs caractères alphabétiques suivis d'un point zéro, une ou plusieurs fois. Le caractère alphabétique initial doit être alphabétique. 
`[A-Z]\w*` | Mettre en correspondance un caractère alphabétique suivi de zéro, un ou plusieurs caractères alphabétiques.
`$` | Terminer la correspondance à la fin de la chaîne d'entrée.
 
## <a name="see-also"></a>Voir aussi

[Expressions régulières .NET](regular-expressions.md)

[Langage des expressions régulières - Aide-mémoire](quick-ref.md)

[Quantificateurs dans les expressions régulières](quantifiers.md)

[Constructions d’alternative dans les expressions régulières](alternation.md)

[Constructions de regroupement dans les expressions régulières](grouping.md)




<!--HONumber=Nov16_HO1-->


