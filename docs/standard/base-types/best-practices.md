---
title: "Bonnes pratiques pour les expressions régulières"
description: "Bonnes pratiques pour les expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 096fd614-91bf-4296-be24-12f62b062294
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: cf9c83de791fa4990a991689a26d4bbdd84cfe7d
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="best-practices-for-regular-expressions"></a><span data-ttu-id="d5967-104">Bonnes pratiques pour les expressions régulières</span><span class="sxs-lookup"><span data-stu-id="d5967-104">Best practices for regular expressions</span></span>

<span data-ttu-id="d5967-105">Le moteur d’expression régulière dans .NET est un outil puissant et complet. Il traite le texte en fonction de correspondances de modèle plutôt qu’en comparant et en faisant correspondre le texte littéral.</span><span class="sxs-lookup"><span data-stu-id="d5967-105">The regular expression engine in .NET is a powerful, full-featured tool that processes text based on pattern matches rather than on comparing and matching literal text.</span></span> <span data-ttu-id="d5967-106">Dans la plupart des cas, il exécute les critères spéciaux de façon rapide et efficace.</span><span class="sxs-lookup"><span data-stu-id="d5967-106">In most cases, it performs pattern matching rapidly and efficiently.</span></span> <span data-ttu-id="d5967-107">Toutefois, dans certains cas, le moteur des expressions régulières peut sembler très lent.</span><span class="sxs-lookup"><span data-stu-id="d5967-107">However, in some cases, the regular expression engine can appear to be very slow.</span></span> <span data-ttu-id="d5967-108">Dans des cas extrêmes, il semble même cesser de répondre. Il traite en effet peu d'entrées sur une période de plusieurs heures ou même de plusieurs jours.</span><span class="sxs-lookup"><span data-stu-id="d5967-108">In extreme cases, it can even appear to stop responding as it processes a relatively small input over the course of hours or even days.</span></span> 

<span data-ttu-id="d5967-109">Cette rubrique décrit quelques-unes des meilleures pratiques que les développeurs peuvent adopter afin de garantir que les expressions régulières atteignent des performances optimales.</span><span class="sxs-lookup"><span data-stu-id="d5967-109">This topic outlines some of the best practices that developers can adopt to ensure that their regular expressions achieve optimal performance.</span></span> <span data-ttu-id="d5967-110">Elle contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="d5967-110">It contains the following sections:</span></span>

* [<span data-ttu-id="d5967-111">Prise en compte de la source d’entrée</span><span class="sxs-lookup"><span data-stu-id="d5967-111">Consider the input source</span></span>](#consider-the-input-source)

* [<span data-ttu-id="d5967-112">Gestion correcte de l’instanciation d’objet</span><span class="sxs-lookup"><span data-stu-id="d5967-112">Handle object instantiation appropriately</span></span>](#handle-object-instantiation-appropriately)

* [<span data-ttu-id="d5967-113">Prise en charge de la rétroaction</span><span class="sxs-lookup"><span data-stu-id="d5967-113">Take charge of backtracking</span></span>](#take-charge-of-backtracking)

* [<span data-ttu-id="d5967-114">Utilisation de valeurs de délai d’attente</span><span class="sxs-lookup"><span data-stu-id="d5967-114">Use time-out values</span></span>](#use-time-out-values)

* [<span data-ttu-id="d5967-115">Capture uniquement quand cela s’avère nécessaire</span><span class="sxs-lookup"><span data-stu-id="d5967-115">Capture only when necessary</span></span>](#capture-only-when-necessary)

* [<span data-ttu-id="d5967-116">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d5967-116">Related topics</span></span>](#related-topics)

## <a name="consider-the-input-source"></a><span data-ttu-id="d5967-117">Prise en compte de la source d’entrée</span><span class="sxs-lookup"><span data-stu-id="d5967-117">Consider the input source</span></span>

<span data-ttu-id="d5967-118">En général, les expressions régulières peuvent accepter deux types d'entrée : avec contrainte ou sans contrainte.</span><span class="sxs-lookup"><span data-stu-id="d5967-118">In general, regular expressions can accept two types of input: constrained or unconstrained.</span></span> <span data-ttu-id="d5967-119">L'entrée avec contrainte est un texte provenant d'une source fiable ou connue, et qui suit un format prédéfini.</span><span class="sxs-lookup"><span data-stu-id="d5967-119">Constrained input is text that originates from a known or reliable source and follows a predefined format.</span></span> <span data-ttu-id="d5967-120">L'entrée sans contrainte est un texte provenant d'une source non fiable, telle qu'un utilisateur web. Elle ne suit pas forcément un format prédéfini ou attendu.</span><span class="sxs-lookup"><span data-stu-id="d5967-120">Unconstrained input is text that originates from an unreliable source, such as a web user, and may not follow a predefined or expected format.</span></span>

<span data-ttu-id="d5967-121">Les modèles d'expressions régulières sont généralement écrits pour correspondre à une entrée valide.</span><span class="sxs-lookup"><span data-stu-id="d5967-121">Regular expression patterns are typically written to match valid input.</span></span> <span data-ttu-id="d5967-122">Autrement dit, les développeurs examinent le texte qu'ils souhaitent faire correspondre, puis ils écrivent un modèle d'expression régulière qui lui correspond.</span><span class="sxs-lookup"><span data-stu-id="d5967-122">That is, developers examine the text that they want to match and then write a regular expression pattern that matches it.</span></span> <span data-ttu-id="d5967-123">Les développeurs déterminent ensuite si ce modèle doit être corrigé ou approfondi en le testant à l'aide de plusieurs éléments d'entrée valides.</span><span class="sxs-lookup"><span data-stu-id="d5967-123">Developers then determine whether this pattern requires correction or further elaboration by testing it with multiple valid input items.</span></span> <span data-ttu-id="d5967-124">Lorsque le modèle correspond à toutes les entrées valides supposées, il est déclaré prêt pour la production et peut être intégré à une application finale.</span><span class="sxs-lookup"><span data-stu-id="d5967-124">When the pattern matches all presumed valid inputs, it is declared to be production-ready and can be included in a released application.</span></span> <span data-ttu-id="d5967-125">Le modèle d'expression régulière est ainsi adapté à la mise en correspondance d'une entrée avec contrainte.</span><span class="sxs-lookup"><span data-stu-id="d5967-125">This makes a regular expression pattern suitable for matching constrained input.</span></span> <span data-ttu-id="d5967-126">Toutefois, il n'est pas adapté à la mise en correspondance d'une entrée sans contrainte.</span><span class="sxs-lookup"><span data-stu-id="d5967-126">However, it does not make it suitable for matching unconstrained input.</span></span>

<span data-ttu-id="d5967-127">Pour faire correspondre une entrée sans contrainte, une expression régulière doit pouvoir gérer efficacement trois types de texte :</span><span class="sxs-lookup"><span data-stu-id="d5967-127">To match unconstrained input, a regular expression must be able to efficiently handle three kinds of text:</span></span>

<span data-ttu-id="d5967-128">• Texte correspondant au modèle d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="d5967-128">• Text that matches the regular expression pattern.</span></span>

<span data-ttu-id="d5967-129">• Texte ne correspondant pas au modèle d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="d5967-129">• Text that does not match the regular expression pattern.</span></span>

<span data-ttu-id="d5967-130">• Texte correspondant presque au modèle d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="d5967-130">• Text that nearly matches the regular expression pattern.</span></span>

<span data-ttu-id="d5967-131">Le dernier type de texte est problématique pour une expression régulière écrite pour gérer les entrées avec contrainte.</span><span class="sxs-lookup"><span data-stu-id="d5967-131">The last text type is especially problematic for a regular expression that has been written to handle constrained input.</span></span> <span data-ttu-id="d5967-132">Si cette expression régulière repose également sur une [rétroaction](backtracking.md) complète, le traitement d’un texte apparemment anodin par le moteur d’expression régulière risque d’être extrêmement long (dans certains cas, un grand nombre d’heures ou de jours).</span><span class="sxs-lookup"><span data-stu-id="d5967-132">If that regular expression also relies on extensive [backtracking](backtracking.md), the regular expression engine can spend an inordinate amount of time (in some cases, many hours or days) processing seemingly innocuous text.</span></span> 

> [!WARNING]
> <span data-ttu-id="d5967-133">L'exemple suivant utilise une expression régulière sujette à des rétroactions excessives et susceptible de rejeter des adresses e-mail valides.</span><span class="sxs-lookup"><span data-stu-id="d5967-133">The following example uses a regular expression that is prone to excessive backtracking and that is likely to reject valid email addresses.</span></span> <span data-ttu-id="d5967-134">Vous ne devez pas l’utiliser dans une routine de validation d’e-mails.</span><span class="sxs-lookup"><span data-stu-id="d5967-134">You should not use it in an email validation routine.</span></span> <span data-ttu-id="d5967-135">Si vous souhaitez une expression régulière qui valide des adresses e-mail, consultez [Guide pratique pour vérifier que des chaînes sont dans un format d’adresse e-mail valide](verify-format.md).</span><span class="sxs-lookup"><span data-stu-id="d5967-135">If you would like a regular expression that validates email addresses, see [How to: Verify that strings are in valid email format](verify-format.md).</span></span> 


<span data-ttu-id="d5967-136">Prenons l'exemple d'une expression régulière très fréquemment utilisée, mais extrêmement problématique, pour la validation de l'alias d'une adresse e-mail.</span><span class="sxs-lookup"><span data-stu-id="d5967-136">For example, consider a very commonly used but extremely problematic regular expression for validating the alias of an email address.</span></span> <span data-ttu-id="d5967-137">L'expression régulière `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` est écrite pour traiter ce qui est considéré comme une adresse e-mail valide. Cette dernière se compose d'un caractère alphanumérique suivi de zéro, ou de plusieurs caractères (caractères alphanumériques, points ou traits d'union).</span><span class="sxs-lookup"><span data-stu-id="d5967-137">The regular expression `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` is written to process what is considered to be a valid email address, which consists of an alphanumeric character, followed by zero or more characters that can be alphanumeric, periods, or hyphens.</span></span> <span data-ttu-id="d5967-138">L'expression régulière doit se terminer par un caractère alphanumérique.</span><span class="sxs-lookup"><span data-stu-id="d5967-138">The regular expression must end with an alphanumeric character.</span></span> <span data-ttu-id="d5967-139">Toutefois, comme illustré dans l'exemple suivant, bien que cette expression régulière gère facilement une entrée valide, elle s'avère particulièrement inefficace lorsqu'il s'agit de traiter une entrée presque valide.</span><span class="sxs-lookup"><span data-stu-id="d5967-139">However, as the following example shows, although this regular expression handles valid input easily, its performance is very inefficient when it is processing nearly valid input.</span></span>

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

<span data-ttu-id="d5967-140">Comme le montre la sortie de l'exemple, le moteur des expressions régulières traite l'alias de messagerie valide dans un intervalle de temps à peu près identique, indépendamment de sa longueur.</span><span class="sxs-lookup"><span data-stu-id="d5967-140">As the output from the example shows, the regular expression engine processes the valid email alias in about the same time interval regardless of its length.</span></span> <span data-ttu-id="d5967-141">En revanche, lorsque l'adresse e-mail presque valide comporte plus de cinq caractères, le temps de traitement est environ doublé pour chaque caractère supplémentaire de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="d5967-141">On the other hand, when the nearly valid email address has more than five characters, processing time approximately doubles for each additional character in the string.</span></span> <span data-ttu-id="d5967-142">Cela signifie qu'une chaîne de 28 caractères presque valide serait traitée en plus d'une heure et qu'une chaîne de 33 caractères presque valide serait traitée en un peu moins d'un jour.</span><span class="sxs-lookup"><span data-stu-id="d5967-142">This means that a nearly valid 28-character string would take over an hour to process, and a nearly valid 33-character string would take nearly a day to process.</span></span> 

<span data-ttu-id="d5967-143">Étant donné que cette expression régulière a été développée en prenant uniquement en considération le format de l'entrée à faire correspondre, elle ne tient pas compte des entrées qui ne correspondent pas au modèle.</span><span class="sxs-lookup"><span data-stu-id="d5967-143">Because this regular expression was developed solely by considering the format of input to be matched, it fails to take account of input that does not match the pattern.</span></span> <span data-ttu-id="d5967-144">Une entrée sans contrainte correspondant presque au modèle d'expression régulière risque ainsi de nuire considérablement aux performances.</span><span class="sxs-lookup"><span data-stu-id="d5967-144">This, in turn, can allow unconstrained input that nearly matches the regular expression pattern to significantly degrade performance.</span></span>

<span data-ttu-id="d5967-145">Pour résoudre ce problème, vous pouvez effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d5967-145">To solve this problem, you can do the following:</span></span>

* <span data-ttu-id="d5967-146">Lorsque vous développez un modèle, vous devez réfléchir à la manière dont la rétroaction peut affecter les performances du moteur des expressions régulières, en particulier si votre expression régulière est conçue pour traiter des entrées sans contrainte.</span><span class="sxs-lookup"><span data-stu-id="d5967-146">When developing a pattern, you should consider how backtracking might affect the performance of the regular expression engine, particularly if your regular expression is designed to process unconstrained input.</span></span> <span data-ttu-id="d5967-147">Pour plus d’informations, consultez la section [Prise en charge de la rétroaction](#take-charge-of-backtracking).</span><span class="sxs-lookup"><span data-stu-id="d5967-147">For more information, see the [Take charge of backtracking](#take-charge-of-backtracking) section.</span></span>

* <span data-ttu-id="d5967-148">Testez intégralement votre expression régulière à l'aide d'entrées non valides et presque valides, ainsi que d'entrées valides.</span><span class="sxs-lookup"><span data-stu-id="d5967-148">Thoroughly test your regular expression using invalid and near-valid input as well as valid input.</span></span> <span data-ttu-id="d5967-149">Pour générer de manière aléatoire une entrée pour une expression régulière spécifique, vous pouvez utiliser [Rex](http://research.microsoft.com/en-us/projects/rex/), l’outil d’exploration d’expressions régulières de Microsoft Research.</span><span class="sxs-lookup"><span data-stu-id="d5967-149">To generate input for a particular regular expression randomly, you can use [Rex](http://research.microsoft.com/en-us/projects/rex/), which is a regular expression exploration tool from Microsoft Research.</span></span>

## <a name="handle-object-instantiation-appropriately"></a><span data-ttu-id="d5967-150">Gestion correcte de l’instanciation d’objet</span><span class="sxs-lookup"><span data-stu-id="d5967-150">Handle object instantiation appropriately</span></span>

<span data-ttu-id="d5967-151">Au cœur du modèle objet d’expression régulière de .NET se trouve la classe [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex), qui représente le moteur d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="d5967-151">At the heart of .NET’s regular expression object model is the [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) class, which represents the regular expression engine.</span></span> <span data-ttu-id="d5967-152">Souvent, la façon dont le moteur [Regex](xref:System.Text.RegularExpressions.Regex) est utilisé est le principal facteur qui exerce un impact sur les performances des expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="d5967-152">Often, the single greatest factor that affects regular expression performance is the way in which the [Regex](xref:System.Text.RegularExpressions.Regex) engine is used.</span></span> <span data-ttu-id="d5967-153">La définition d’une expression régulière implique une association étroite entre le moteur des expressions régulières et un modèle d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="d5967-153">Defining a regular expression involves tightly coupling the regular expression engine with a regular expression pattern.</span></span> <span data-ttu-id="d5967-154">Ce processus d’association est forcément onéreux, qu’il implique l’instanciation d’un objet [Regex](xref:System.Text.RegularExpressions.Regex) en passant à son constructeur un modèle d’expression régulière ou l’appel d’une méthode statique en lui passant le modèle d’expression régulière avec la chaîne à analyser.</span><span class="sxs-lookup"><span data-stu-id="d5967-154">That coupling process, whether it involves instantiating a [Regex](xref:System.Text.RegularExpressions.Regex) object by passing its constructor a regular expression pattern or calling a static method by passing it the regular expression pattern along with the string to be analyzed, is by necessity an expensive one.</span></span>

<span data-ttu-id="d5967-155">Vous pouvez associer le moteur des expressions régulières à un modèle d’expression régulière spécifique, puis utiliser le moteur pour faire correspondre du texte de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="d5967-155">You can couple the regular expression engine with a particular regular expression pattern and then use the engine to match text in several ways:</span></span>

* <span data-ttu-id="d5967-156">Vous pouvez appeler une méthode statique de critères spéciaux, comme [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)).</span><span class="sxs-lookup"><span data-stu-id="d5967-156">You can call a static pattern-matching method, such as [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)).</span></span> <span data-ttu-id="d5967-157">L'instanciation d'un objet d'expression régulière n'est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d5967-157">This does not require instantiation of a regular expression object.</span></span>

* <span data-ttu-id="d5967-158">Vous pouvez instancier un objet [Regex](xref:System.Text.RegularExpressions.Regex) et appeler une méthode d’instance de critères spéciaux d’une expression régulière interprétée.</span><span class="sxs-lookup"><span data-stu-id="d5967-158">You can instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object and call an instance pattern-matching method of an interpreted regular expression.</span></span> <span data-ttu-id="d5967-159">Il s’agit de la méthode par défaut pour lier le moteur des expressions régulières à un modèle d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="d5967-159">This is the default method for binding the regular expression engine to a regular expression pattern.</span></span> <span data-ttu-id="d5967-160">Elle s’ensuit quand un objet [Regex](xref:System.Text.RegularExpressions.Regex) est instancié sans argument options qui inclut l’indicateur [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled).</span><span class="sxs-lookup"><span data-stu-id="d5967-160">It results when a [Regex](xref:System.Text.RegularExpressions.Regex) object is instantiated without an options argument that includes the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) flag.</span></span>

* <span data-ttu-id="d5967-161">Vous pouvez instancier un objet [Regex](xref:System.Text.RegularExpressions.Regex) et appeler une méthode d’instance de critères spéciaux d’une expression régulière compilée.</span><span class="sxs-lookup"><span data-stu-id="d5967-161">You can instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object and call an instance pattern-matching method of a compiled regular expression.</span></span> <span data-ttu-id="d5967-162">Les objets d’expression régulière représentent des modèles compilés lorsqu’un objet [Regex](xref:System.Text.RegularExpressions.Regex) est instancié avec un argument options incluant l’indicateur [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled).</span><span class="sxs-lookup"><span data-stu-id="d5967-162">Regular expression objects represent compiled patterns when a [Regex](xref:System.Text.RegularExpressions.Regex) object is instantiated with an options argument that includes the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) flag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d5967-163">La forme de l'appel de méthode (statique, interprétée, compilée) affecte les performances si une même expression régulière est utilisée à plusieurs reprises dans les appels de méthode, ou si une application entraîne l'utilisation intensive d'objets d'expression régulière.</span><span class="sxs-lookup"><span data-stu-id="d5967-163">The form of the method call (static, interpreted, compiled) affects performance if the same regular expression is used repeatedly in method calls, or if an application makes extensive use of regular expression objects.</span></span>
 
### <a name="static-regular-expressions"></a><span data-ttu-id="d5967-164">Expressions régulières statiques</span><span class="sxs-lookup"><span data-stu-id="d5967-164">Static regular expressions</span></span>

<span data-ttu-id="d5967-165">Les méthodes d'expression régulière statiques sont recommandées pour éviter d'instancier à plusieurs reprises un objet d'expression régulière avec la même expression régulière.</span><span class="sxs-lookup"><span data-stu-id="d5967-165">Static regular expression methods are recommended as an alternative to repeatedly instantiating a regular expression object with the same regular expression.</span></span> <span data-ttu-id="d5967-166">À la différence des modèles d’expressions régulières utilisés par les objets d’expression régulière, les codes d’opération ou le langage compilé MSIL (Microsoft intermediate langage) des modèles utilisés dans les appels de méthode d’instance sont mis en cache en interne par le moteur des expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="d5967-166">Unlike regular expression patterns used by regular expression objects, either the operation codes or the compiled Microsoft intermediate language (MSIL) from patterns used in instance method calls is cached internally by the regular expression engine.</span></span> 

<span data-ttu-id="d5967-167">Par exemple, vous pouvez appeler une méthode pour valider l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d5967-167">For example, you might call a method to validate user input.</span></span> <span data-ttu-id="d5967-168">Dans cet exemple, une méthode nommée `IsValidCurrency` vérifie si l’utilisateur a entré un symbole monétaire suivi d’au moins un chiffre décimal.</span><span class="sxs-lookup"><span data-stu-id="d5967-168">In this example, a method named `IsValidCurrency` checks whether the user has entered a currency symbol followed by at least one decimal digit.</span></span> <span data-ttu-id="d5967-169">L'exemple suivant illustre une implémentation très peu efficace de la méthode `IsValidCurrency`.</span><span class="sxs-lookup"><span data-stu-id="d5967-169">A very inefficient implementation of the `IsValidCurrency` method is shown in the following example.</span></span> <span data-ttu-id="d5967-170">Notez que chaque appel de méthode réinstancie un objet [Regex](xref:System.Text.RegularExpressions.Regex) avec le même modèle.</span><span class="sxs-lookup"><span data-stu-id="d5967-170">Note that each method call reinstantiates a [Regex](xref:System.Text.RegularExpressions.Regex) object with the same pattern.</span></span> <span data-ttu-id="d5967-171">Cela signifie ainsi que le modèle d’expression régulière doit être recompilé chaque fois que la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="d5967-171">This, in turn, means that the regular expression pattern must be recompiled each time the method is called.</span></span>

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

<span data-ttu-id="d5967-172">Vous devez remplacer ce code peu efficace par un appel à la méthode [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)) statique.</span><span class="sxs-lookup"><span data-stu-id="d5967-172">You should replace this inefficient code with a call to the static [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)) method.</span></span> <span data-ttu-id="d5967-173">De cette manière, un objet [Regex](xref:System.Text.RegularExpressions.Regex) n’a pas besoin d’être instancié chaque fois que vous souhaitez appeler une méthode de critères spéciaux. En outre, le moteur d’expression régulière est alors en mesure de récupérer une version compilée de l’expression régulière depuis son cache.</span><span class="sxs-lookup"><span data-stu-id="d5967-173">This eliminates the need to instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object each time you want to call a pattern-matching method, and enables the regular expression engine to retrieve a compiled version of the regular expression from its cache.</span></span>

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

<span data-ttu-id="d5967-174">Par défaut, les 15 derniers modèles d’expressions régulières statiques utilisés récemment sont mis en cache.</span><span class="sxs-lookup"><span data-stu-id="d5967-174">By default, the last 15 most recently used static regular expression patterns are cached.</span></span> <span data-ttu-id="d5967-175">Pour les applications qui requièrent un plus grand nombre d’expressions régulières statiques mises en cache, la taille du cache peut être ajustée en définissant la propriété [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize).</span><span class="sxs-lookup"><span data-stu-id="d5967-175">For applications that require a larger number of cached static regular expressions, the size of the cache can be adjusted by setting the [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize) property.</span></span>

<span data-ttu-id="d5967-176">L'expression régulière `\p{Sc}+\s*\d+` utilisée dans cet exemple vérifie que la chaîne d'entrée se compose d'un symbole monétaire et d'au moins un chiffre décimal.</span><span class="sxs-lookup"><span data-stu-id="d5967-176">The regular expression `\p{Sc}+\s*\d+` that is used in this example verifies that the input string consists of a currency symbol and at least one decimal digit.</span></span> <span data-ttu-id="d5967-177">Le modèle est défini comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d5967-177">The pattern is defined as shown in the following table.</span></span>

<span data-ttu-id="d5967-178">Modèle</span><span class="sxs-lookup"><span data-stu-id="d5967-178">Pattern</span></span> | <span data-ttu-id="d5967-179">Description</span><span class="sxs-lookup"><span data-stu-id="d5967-179">Description</span></span>
------- | -----------
`\p{Sc}+` | <span data-ttu-id="d5967-180">Mettre en correspondance un ou plusieurs caractères dans la catégorie Unicode symbole, devise.</span><span class="sxs-lookup"><span data-stu-id="d5967-180">Match one or more characters in the Unicode Symbol, Currency category.</span></span>
`\s*` | <span data-ttu-id="d5967-181">Correspond à zéro, un ou plusieurs espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="d5967-181">Match zero or more white-space characters.</span></span>
`\d+` | <span data-ttu-id="d5967-182">Mettre en correspondance un ou plusieurs chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="d5967-182">Match one or more decimal digits.</span></span>
 
### <a name="interpreted-vs-compiled-regular-expressions"></a><span data-ttu-id="d5967-183">Expressions régulières interprétées ou compilées</span><span class="sxs-lookup"><span data-stu-id="d5967-183">Interpreted vs. compiled regular expressions</span></span>

<span data-ttu-id="d5967-184">Les modèles d’expression régulière qui ne sont pas associés au moteur d’expression régulière par la spécification de l’option [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) sont interprétés.</span><span class="sxs-lookup"><span data-stu-id="d5967-184">Regular expression patterns that are not bound to the regular expression engine through the specification of the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) option are interpreted.</span></span> <span data-ttu-id="d5967-185">Lorsqu'un objet d'expression régulière est instancié, le moteur des expressions régulières convertit l'expression régulière en un ensemble de codes d'opération.</span><span class="sxs-lookup"><span data-stu-id="d5967-185">When a regular expression object is instantiated, the regular expression engine converts the regular expression to a set of operation codes.</span></span> <span data-ttu-id="d5967-186">Lorsqu'une méthode d'instance est appelée, les codes d'opération sont convertis en langage MSIL et exécutés par le compilateur JIT.</span><span class="sxs-lookup"><span data-stu-id="d5967-186">When an instance method is called, the operation codes are converted to MSIL and executed by the JIT compiler.</span></span> <span data-ttu-id="d5967-187">De même, lorsqu'une méthode d'expression régulière statique est appelée et que l'expression régulière ne peut pas être récupérée dans le cache, le moteur des expressions régulières convertit l'expression régulière en un ensemble de codes d'opération et les stocke dans le cache.</span><span class="sxs-lookup"><span data-stu-id="d5967-187">Similarly, when a static regular expression method is called and the regular expression cannot be found in the cache, the regular expression engine converts the regular expression to a set of operation codes and stores them in the cache.</span></span> <span data-ttu-id="d5967-188">Il convertit ensuite ces codes d'opération en langage MSIL afin que le compilateur JIT puisse les exécuter.</span><span class="sxs-lookup"><span data-stu-id="d5967-188">It then converts these operation codes to MSIL so that the JIT compiler can execute them.</span></span> <span data-ttu-id="d5967-189">Les expressions régulières interprétées réduisent le temps de démarrage, mais ralentissent le temps d'exécution.</span><span class="sxs-lookup"><span data-stu-id="d5967-189">Interpreted regular expressions reduce startup time at the cost of slower execution time.</span></span> <span data-ttu-id="d5967-190">Pour cette raison, il est préférable de les utiliser lorsque l'expression régulière est utilisée dans un nombre d'appels de méthode restreint, ou lorsque le nombre exact d'appels de méthodes d'expression régulière est inconnu, mais qu'il est supposé être petit.</span><span class="sxs-lookup"><span data-stu-id="d5967-190">Because of this, they are best used when the regular expression is used in a small number of method calls, or if the exact number of calls to regular expression methods is unknown but is expected to be small.</span></span> <span data-ttu-id="d5967-191">À mesure que le nombre d'appels de méthode augmente, le ralentissement de la vitesse d'exécution l'emporte sur l'amélioration des performances liée à la réduction du temps de démarrage.</span><span class="sxs-lookup"><span data-stu-id="d5967-191">As the number of method calls increases, the performance gain from reduced startup time is outstripped by the slower execution speed.</span></span>

<span data-ttu-id="d5967-192">Les modèles d’expression régulière qui sont associés au moteur d’expression régulière par la spécification de l’option [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) sont compilés.</span><span class="sxs-lookup"><span data-stu-id="d5967-192">Regular expression patterns that are bound to the regular expression engine through the specification of the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) option are compiled.</span></span> <span data-ttu-id="d5967-193">Cela signifie que, lorsqu'un objet d'expression régulière est instancié ou lorsqu'une méthode d'expression régulière statique est appelée et que l'expression régulière ne peut pas être récupérée dans le cache, le moteur des expressions régulières convertit l'expression régulière en un ensemble de codes d'opération intermédiaire, qu'il convertit ensuite en langage MSIL.</span><span class="sxs-lookup"><span data-stu-id="d5967-193">This means that, when a regular expression object is instantiated, or when a static regular expression method is called and the regular expression cannot be found in the cache, the regular expression engine converts the regular expression to an intermediary set of operation codes, which it then converts to MSIL.</span></span> <span data-ttu-id="d5967-194">Lorsqu'une méthode est appelée, le compilateur JIT exécute le MSIL.</span><span class="sxs-lookup"><span data-stu-id="d5967-194">When a method is called, the JIT compiler executes the MSIL.</span></span> <span data-ttu-id="d5967-195">Contrairement aux expressions régulières interprétées, les expressions régulières compilées augmentent le temps de démarrage, mais elles exécutent plus rapidement les méthodes de critères spéciaux individuelles.</span><span class="sxs-lookup"><span data-stu-id="d5967-195">In contrast to interpreted regular expressions, compiled regular expressions increase startup time but execute individual pattern-matching methods faster.</span></span> <span data-ttu-id="d5967-196">En conséquence, l'amélioration des performances due à la compilation de l'expression régulière augmente en fonction du nombre de méthodes d'expression régulières appelées.</span><span class="sxs-lookup"><span data-stu-id="d5967-196">As a result, the performance benefit that results from compiling the regular expression increases in proportion to the number of regular expression methods called.</span></span>

<span data-ttu-id="d5967-197">Pour résumer, nous vous conseillons d'utiliser des expressions régulières interprétées lorsque vous appelez relativement peu souvent des méthodes d'expression régulières avec une expression régulière spécifique.</span><span class="sxs-lookup"><span data-stu-id="d5967-197">To summarize, we recommend that you use interpreted regular expressions when you call regular expression methods with a specific regular expression relatively infrequently.</span></span> <span data-ttu-id="d5967-198">Nous vous conseillons d'utiliser des expressions régulières compilées lorsque vous appelez relativement souvent des méthodes d'expression régulière avec une expression régulière spécifique.</span><span class="sxs-lookup"><span data-stu-id="d5967-198">You should use compiled regular expressions when you call regular expression methods with a specific regular expression relatively frequently.</span></span> <span data-ttu-id="d5967-199">Il est difficile de déterminer le seuil exact auquel le ralentissement de la vitesse d'exécution des expressions normales interprétées l'emporte sur la réduction du temps de démarrage. Il est également difficile de déterminer le seuil auquel le ralentissement du temps de démarrage des expressions régulières compilées l'emporte sur l'amélioration des vitesses d'exécution.</span><span class="sxs-lookup"><span data-stu-id="d5967-199">The exact threshold at which the slower execution speeds of interpreted regular expressions outweigh gains from their reduced startup time, or the threshold at which the slower startup times of compiled regular expressions outweigh gains from their faster execution speeds, is difficult to determine.</span></span> <span data-ttu-id="d5967-200">Différents facteurs doivent être pris en compte, notamment la complexité des expressions régulières et les données spécifiques qui sont traitées.</span><span class="sxs-lookup"><span data-stu-id="d5967-200">It depends on a variety of factors, including the complexity of the regular expression and the specific data that it processes.</span></span> <span data-ttu-id="d5967-201">Pour déterminer si ce sont les expressions régulières interprétées ou compilées qui offrent les meilleures performances pour votre scénario d’application spécifique, vous pouvez utiliser la classe [Stopwatch](xref:System.Diagnostics.Stopwatch) pour comparer les durées d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d5967-201">To determine whether interpreted or compiled regular expressions offer the best performance for your particular application scenario, you can use the [Stopwatch](xref:System.Diagnostics.Stopwatch) class to compare their execution times.</span></span>

<span data-ttu-id="d5967-202">L’exemple suivant compare les performances des expressions régulières compilées et interprétées lors de la lecture des dix premières phrases et lors de la lecture de toutes les phrases du texte de Theodore Dreiser, The Financier.</span><span class="sxs-lookup"><span data-stu-id="d5967-202">The following example compares the performance of compiled and interpreted regular expressions when reading the first ten sentences and when reading all the sentences in the text of Theodore Dreiser's The Financier.</span></span> <span data-ttu-id="d5967-203">Comme l'indique la sortie de l'exemple, lorsque les méthodes de correspondance d'expression régulière sont appelées seulement dix fois, une expression régulière interprétée offre de meilleures performances qu'une expression régulière compilée.</span><span class="sxs-lookup"><span data-stu-id="d5967-203">As the output from the example shows, when only ten calls are made to regular expression matching methods, an interpreted regular expression offers better performance than a compiled regular expression.</span></span> <span data-ttu-id="d5967-204">Par contre, une expression régulière compilée offre de meilleures performances dans le cas d'un grand nombre d'appels (dans le cas présent, plus de 13 000).</span><span class="sxs-lookup"><span data-stu-id="d5967-204">However, a compiled regular expression offers better performance when a large number of calls (in this case, over 13,000) are made.</span></span> 

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

<span data-ttu-id="d5967-205">Le modèle d'expression régulière utilisé dans l'exemple, `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, est défini comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d5967-205">The regular expression pattern used in the example, `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, is defined as shown in the following table.</span></span>

<span data-ttu-id="d5967-206">Modèle</span><span class="sxs-lookup"><span data-stu-id="d5967-206">Pattern</span></span> | <span data-ttu-id="d5967-207">Description</span><span class="sxs-lookup"><span data-stu-id="d5967-207">Description</span></span>
------- | -----------
`\b` | <span data-ttu-id="d5967-208">Commencer la correspondance à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="d5967-208">Begin the match at a word boundary.</span></span>
`\w+` | <span data-ttu-id="d5967-209">Mettre en correspondance un ou plusieurs caractères alphabétiques.</span><span class="sxs-lookup"><span data-stu-id="d5967-209">Match one or more word characters.</span></span>
<span data-ttu-id="d5967-210">\`(\r?\n)</span><span class="sxs-lookup"><span data-stu-id="d5967-210">\`(\r?\n)</span></span>|<span data-ttu-id="d5967-211">,?\s)\`</span><span class="sxs-lookup"><span data-stu-id="d5967-211">,?\s)\`</span></span> | <span data-ttu-id="d5967-212">Mettre en correspondance un ou aucun retour chariot suivi d'un caractère de saut de ligne, ou une ou aucune virgule, suivie d'un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="d5967-212">Match either zero or one carriage return followed by a newline character, or zero or one comma followed by a white-space character.</span></span>
<span data-ttu-id="d5967-213">\`(\w+((\r?\n)</span><span class="sxs-lookup"><span data-stu-id="d5967-213">\`(\w+((\r?\n)</span></span>|<span data-ttu-id="d5967-214">,?\s))*\`</span><span class="sxs-lookup"><span data-stu-id="d5967-214">,?\s))*\`</span></span> | <span data-ttu-id="d5967-215">Mettre en correspondance zéro, une ou plusieurs occurrences d'un ou plusieurs caractères alphabétiques qui sont suivis par un ou aucun retour chariot et un caractère de saut de ligne, ou par une ou aucune virgule, suivie d'un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="d5967-215">Match zero or more occurrences of one or more word characters that are followed either by zero or one carriage return and a newline character, or by zero or one comma followed by a white-space character.</span></span>
`\w+` | <span data-ttu-id="d5967-216">Mettre en correspondance un ou plusieurs caractères alphabétiques.</span><span class="sxs-lookup"><span data-stu-id="d5967-216">Match one or more word characters.</span></span>
`[.?:;!]` | <span data-ttu-id="d5967-217">Mettre en correspondance un point, un point d'interrogation, deux-points, un point-virgule ou un point d'exclamation.</span><span class="sxs-lookup"><span data-stu-id="d5967-217">Match a period, question mark, colon, semicolon, or exclamation point.</span></span>
 
## <a name="take-charge-of-backtracking"></a><span data-ttu-id="d5967-218">Prise en charge de la rétroaction</span><span class="sxs-lookup"><span data-stu-id="d5967-218">Take charge of backtracking</span></span>

<span data-ttu-id="d5967-219">Normalement, le moteur des expressions régulières utilise une progression linéaire pour se déplacer dans une chaîne d’entrée et pour la comparer à un modèle d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="d5967-219">Ordinarily, the regular expression engine uses linear progression to move through an input string and compare it to a regular expression pattern.</span></span> <span data-ttu-id="d5967-220">Toutefois, quand des quantificateurs indéterminés comme __*__, **+** et **?**</span><span class="sxs-lookup"><span data-stu-id="d5967-220">However, when indeterminate quantifiers such as __*__, **+**, and **?**</span></span> <span data-ttu-id="d5967-221">sont utilisés dans un modèle d’expression régulière, le moteur d’expression régulière peut abandonner une partie des correspondances partielles trouvées et revenir à un état précédemment enregistré pour trouver une correspondance pour le modèle entier.</span><span class="sxs-lookup"><span data-stu-id="d5967-221">are used in a regular expression pattern, the regular expression engine may give up a portion of successful partial matches and return to a previously saved state in order to search for a successful match for the entire pattern.</span></span> <span data-ttu-id="d5967-222">Ce processus est appelé « rétroaction ».</span><span class="sxs-lookup"><span data-stu-id="d5967-222">This process is known as backtracking.</span></span>

> [!NOTE]
> <span data-ttu-id="d5967-223">Pour plus d’informations sur la rétroaction, consultez [Comportement détaillé des expressions régulières](regex-behavior.md) et [Rétroaction dans les expressions régulières](backtracking.md).</span><span class="sxs-lookup"><span data-stu-id="d5967-223">For more information on backtracking, see [Details of regular expression behavior](regex-behavior.md) and [Backtracking in regular expressions](backtracking.md).</span></span>
 
<span data-ttu-id="d5967-224">La prise en charge de la rétroaction confère aux expressions régulières leur puissance et leur flexibilité.</span><span class="sxs-lookup"><span data-stu-id="d5967-224">Support for backtracking gives regular expressions power and flexibility.</span></span> <span data-ttu-id="d5967-225">La responsabilité de contrôle du fonctionnement du moteur des expressions régulières est alors confiée aux développeurs d'expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="d5967-225">It also places the responsibility for controlling the operation of the regular expression engine in the hands of regular expression developers.</span></span> <span data-ttu-id="d5967-226">Souvent, les développeurs ne sont pas conscients de cette responsabilité. Leur utilisation incorrecte de la rétroaction ou leur dépendance vis-à-vis d'une rétroaction excessive a souvent un impact négatif très important sur les performances des expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="d5967-226">Because developers are often not aware of this responsibility, their misuse of backtracking or reliance on excessive backtracking often plays the most significant role in degrading regular expression performance.</span></span> <span data-ttu-id="d5967-227">Dans le pire des scénarios, la durée d'exécution peut doubler pour chaque caractère supplémentaire de la chaîne d'entrée.</span><span class="sxs-lookup"><span data-stu-id="d5967-227">In a worst-case scenario, execution time can double for each additional character in the input string.</span></span> <span data-ttu-id="d5967-228">En réalité, lorsque la rétroaction est utilisée de manière excessive, il est facile de créer l'équivalent de programmation d'une boucle sans fin si l'entrée correspond presque au modèle d'expression régulière. Le moteur des expressions régulières peut alors traiter une chaîne d'entrée relativement courte en plusieurs heures, voire en plusieurs jours.</span><span class="sxs-lookup"><span data-stu-id="d5967-228">In fact, by using backtracking excessively, it is easy to create the programmatic equivalent of an endless loop if input nearly matches the regular expression pattern; the regular expression engine may take hours or even days to process a relatively short input string.</span></span>

<span data-ttu-id="d5967-229">Les performances des applications sont souvent altérées par l'utilisation de la rétroaction, même si ce processus n'est pas essentiel pour une correspondance.</span><span class="sxs-lookup"><span data-stu-id="d5967-229">Often, applications pay a performance penalty for using backtracking despite the fact that backtracking is not essential for a match.</span></span> <span data-ttu-id="d5967-230">Par exemple, l'expression régulière `\b\p{Lu}\w*\b` établit une correspondance entre tous les mots qui commencent par une majuscule, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d5967-230">For example, the regular expression `\b\p{Lu}\w*\b` matches all words that begin with an uppercase character, as the following table shows.</span></span>

<span data-ttu-id="d5967-231">Modèle</span><span class="sxs-lookup"><span data-stu-id="d5967-231">Pattern</span></span> | <span data-ttu-id="d5967-232">Description</span><span class="sxs-lookup"><span data-stu-id="d5967-232">Description</span></span>
------- | -----------
`\b` | <span data-ttu-id="d5967-233">Commencer la correspondance à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="d5967-233">Begin the match at a word boundary.</span></span>
`\p{Lu}` | <span data-ttu-id="d5967-234">Mettre en correspondance une majuscule.</span><span class="sxs-lookup"><span data-stu-id="d5967-234">Match an uppercase character.</span></span>
`\w*` | <span data-ttu-id="d5967-235">Mettre en correspondance zéro, un ou plusieurs caractères alphabétiques.</span><span class="sxs-lookup"><span data-stu-id="d5967-235">Match zero or more word characters.</span></span>
`\b` | <span data-ttu-id="d5967-236">Terminer la correspondance à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="d5967-236">End the match at a word boundary.</span></span>
 
<span data-ttu-id="d5967-237">Étant donné qu'une limite de mot est différente d'un caractère alphabétique et qu'elle n'est pas un sous-ensemble de ce dernier, il est impossible que le moteur des expressions régulières franchisse une limite de mot lors de la mise en correspondance de caractères alphabétiques.</span><span class="sxs-lookup"><span data-stu-id="d5967-237">Because a word boundary is not the same as, or a subset of, a word character, there is no possibility that the regular expression engine will cross a word boundary when matching word characters.</span></span> <span data-ttu-id="d5967-238">Cela signifie que, pour cette expression régulière, une rétroaction ne peut jamais contribuer à la réussite globale d'une correspondance. Elle risque en revanche de diminuer les performances, étant donné que le moteur des expressions régulières doit impérativement enregistrer sont état pour chaque correspondance préliminaire d'un caractère alphabétique trouvée.</span><span class="sxs-lookup"><span data-stu-id="d5967-238">This means that for this regular expression, backtracking can never contribute to the overall success of any match -- it can only degrade performance, because the regular expression engine is forced to save its state for each successful preliminary match of a word character.</span></span>

<span data-ttu-id="d5967-239">Si vous considérez que la rétroaction n’est pas nécessaire, vous pouvez la désactiver à l’aide de l’élément de langage **(?>**_sous-expression_**)**.</span><span class="sxs-lookup"><span data-stu-id="d5967-239">If you determine that backtracking is not necessary, you can disable it by using the **(?>**_subexpression_**)** language element.</span></span> <span data-ttu-id="d5967-240">L'exemple suivant analyse une chaîne d'entrée à l'aide de deux expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="d5967-240">The following example parses an input string by using two regular expressions.</span></span> <span data-ttu-id="d5967-241">La première, `\b\p{Lu}\w*\b`, utilise la rétroaction.</span><span class="sxs-lookup"><span data-stu-id="d5967-241">The first, `\b\p{Lu}\w*\b`, relies on backtracking.</span></span> <span data-ttu-id="d5967-242">La seconde, `\b\p{Lu}(?>\w*)\b`, désactive la rétroaction.</span><span class="sxs-lookup"><span data-stu-id="d5967-242">The second, `\b\p{Lu}(?>\w*)\b`, disables backtracking.</span></span> <span data-ttu-id="d5967-243">Comme l'indique la sortie de l'exemple, les résultats obtenus sont identiques.</span><span class="sxs-lookup"><span data-stu-id="d5967-243">As the output from the example shows, they both produce the same result.</span></span>

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

<span data-ttu-id="d5967-244">Dans de nombreux cas, la rétroaction est essentielle pour faire correspondre un modèle d’expression régulière à un texte d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d5967-244">In many cases, backtracking is essential for matching a regular expression pattern to input text.</span></span> <span data-ttu-id="d5967-245">Toutefois, une rétroaction excessive risque d'altérer considérablement les performances et de donner l'impression qu'une application a cessé de répondre.</span><span class="sxs-lookup"><span data-stu-id="d5967-245">However, excessive backtracking can severely degrade performance and create the impression that an application has stopped responding.</span></span> <span data-ttu-id="d5967-246">Cela se produit notamment lorsque les quantificateurs sont imbriqués et que le texte correspondant à la sous-expression externe est un sous-ensemble du texte correspondant à la sous-expression interne.</span><span class="sxs-lookup"><span data-stu-id="d5967-246">In particular, this happens when quantifiers are nested and the text that matches the outer subexpression is a subset of the text that matches the inner subexpression.</span></span> 

> [!WARNING]
> <span data-ttu-id="d5967-247">En plus d’éviter une rétroaction excessive, vous devez utiliser la fonctionnalité de délai d’attente pour garantir qu’une rétroaction excessive n’altère pas considérablement les performances des expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="d5967-247">In addition to avoiding excessive backtracking, you should use the timeout feature to ensure that excessive backtracking does not severely degrade regular expression performance.</span></span> <span data-ttu-id="d5967-248">Pour plus d’informations, consultez la section [Utilisation de valeurs de délai d’attente](#use-time-out-values).</span><span class="sxs-lookup"><span data-stu-id="d5967-248">For more information, see the [Use time-out values](#use-time-out-values) section.</span></span>
 
<span data-ttu-id="d5967-249">Par exemple, le modèle d'expression régulière `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` est conçu pour mettre en correspondance un numéro de référence composé d'au moins un caractère alphanumérique.</span><span class="sxs-lookup"><span data-stu-id="d5967-249">For example, the regular expression pattern `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` is intended to match a part number that consists of at least one alphanumeric character.</span></span> <span data-ttu-id="d5967-250">Tous les caractères supplémentaires peuvent être composés d'un caractère alphanumérique, d'un trait d'union, d'un trait de soulignement ou d'un point. Toutefois, le dernier caractère doit impérativement être alphanumérique.</span><span class="sxs-lookup"><span data-stu-id="d5967-250">Any additional characters can consist of an alphanumeric character, a hyphen, an underscore, or a period, though the last character must be alphanumeric.</span></span> <span data-ttu-id="d5967-251">Un signe dollar termine le numéro de référence.</span><span class="sxs-lookup"><span data-stu-id="d5967-251">A dollar sign terminates the part number.</span></span> <span data-ttu-id="d5967-252">Dans certains cas, ce modèle d'expression régulière peut présenter des performances médiocres, si les quantificateurs sont imbriqués et que la sous-expression `[0-9A-Z]` est un sous-ensemble de la sous-expression `[-.\w]*`.</span><span class="sxs-lookup"><span data-stu-id="d5967-252">In some cases, this regular expression pattern can exhibit extremely poor performance because quantifiers are nested, and because the subexpression `[0-9A-Z]` is a subset of the subexpression `[-.\w]*`.</span></span>

<span data-ttu-id="d5967-253">Dans ces cas, vous pouvez optimiser les performances des expressions régulières en supprimant les quantificateurs imbriqués et en remplaçant la sous-expression externe par une assertion de préanalyse ou de postanalyse de largeur nulle.</span><span class="sxs-lookup"><span data-stu-id="d5967-253">In these cases, you can optimize regular expression performance by removing the nested quantifiers and replacing the outer subexpression with a zero-width lookahead or lookbehind assertion.</span></span> <span data-ttu-id="d5967-254">Les assertions de préanalyse et de postanalyse sont des points d'ancrage. Elles ne déplacent pas le pointeur dans la chaîne d'entrée, mais elles vérifient en amont et en aval si une condition spécifiée est remplie.</span><span class="sxs-lookup"><span data-stu-id="d5967-254">Lookahead and lookbehind assertions are anchors; they do not move the pointer in the input string, but instead look ahead or behind to check whether a specified condition is met.</span></span> <span data-ttu-id="d5967-255">Par exemple, l'expression régulière de numéro de référence peut être réécrite sous la forme `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`.</span><span class="sxs-lookup"><span data-stu-id="d5967-255">For example, the part number regular expression can be rewritten as `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`.</span></span> <span data-ttu-id="d5967-256">Ce modèle d'expression régulière est défini comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d5967-256">This regular expression pattern is defined as shown in the following table.</span></span>

<span data-ttu-id="d5967-257">Modèle</span><span class="sxs-lookup"><span data-stu-id="d5967-257">Pattern</span></span> | <span data-ttu-id="d5967-258">Description</span><span class="sxs-lookup"><span data-stu-id="d5967-258">Description</span></span>
------- | -----------
`^` | <span data-ttu-id="d5967-259">Commencer la correspondance au début de la chaîne d'entrée.</span><span class="sxs-lookup"><span data-stu-id="d5967-259">Begin the match at the beginning of the input string.</span></span>
`[0-9A-Z]` | <span data-ttu-id="d5967-260">Mettre en correspondance un caractère alphanumérique.</span><span class="sxs-lookup"><span data-stu-id="d5967-260">Match an alphanumeric character.</span></span> <span data-ttu-id="d5967-261">Le numéro de référence doit au minimum comporter ce caractère.</span><span class="sxs-lookup"><span data-stu-id="d5967-261">The part number must consist of at least this character.</span></span>
`[-.\w]*` | <span data-ttu-id="d5967-262">Mettre en correspondance zéro, une ou plusieurs occurrences de tout caractère alphabétique, trait d'union ou point.</span><span class="sxs-lookup"><span data-stu-id="d5967-262">Match zero or more occurrences of any word character, hyphen, or period.</span></span>
<span data-ttu-id="d5967-263">\`\$]</span><span class="sxs-lookup"><span data-stu-id="d5967-263">\`\$]</span></span> | <span data-ttu-id="d5967-264">Mettre en correspondance un signe dollar.</span><span class="sxs-lookup"><span data-stu-id="d5967-264">Match a dollar sign.</span></span>
`(?<=[0-9A-Z])` | <span data-ttu-id="d5967-265">Effectuer une préanalyse avancée du signe dollar de fin de s'assurer que le caractère précédent est un caractère alphanumérique.</span><span class="sxs-lookup"><span data-stu-id="d5967-265">Look ahead of the ending dollar sign to ensure that the previous character is alphanumeric.</span></span>
<span data-ttu-id="d5967-266">`$` Terminer la correspondance à la fin de la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d5967-266">`$` End the match at the end of the input string.</span></span>
 
<span data-ttu-id="d5967-267">L'exemple suivant illustre l'utilisation de cette expression régulière pour faire correspondre un tableau pouvant contenir des numéros de référence potentiels.</span><span class="sxs-lookup"><span data-stu-id="d5967-267">The following example illustrates the use of this regular expression to match an array containing possible part numbers.</span></span>

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

<span data-ttu-id="d5967-268">Le langage d’expression régulière dans .NET comprend les éléments de langage suivants, que vous pouvez utiliser pour éliminer les quantificateurs imbriqués.</span><span class="sxs-lookup"><span data-stu-id="d5967-268">The regular expression language in .NET includes the following language elements that you can use to eliminate nested quantifiers.</span></span> <span data-ttu-id="d5967-269">Pour plus d’informations, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).</span><span class="sxs-lookup"><span data-stu-id="d5967-269">For more information, see [Grouping constructs in regular expressions](grouping.md).</span></span>

<span data-ttu-id="d5967-270">Élément du langage</span><span class="sxs-lookup"><span data-stu-id="d5967-270">Language element</span></span> | <span data-ttu-id="d5967-271">Description</span><span class="sxs-lookup"><span data-stu-id="d5967-271">Description</span></span>
---------------- | ----------- 
<span data-ttu-id="d5967-272">**(?**=_sous-expression_**)**</span><span class="sxs-lookup"><span data-stu-id="d5967-272">**(?**=_subexpression_**)**</span></span> | <span data-ttu-id="d5967-273">Préanalyse positive de largeur nulle.</span><span class="sxs-lookup"><span data-stu-id="d5967-273">Zero-width positive lookahead.</span></span> <span data-ttu-id="d5967-274">Effectuer une préanalyse de la position actuelle pour déterminer si *sous-expression* correspond à la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d5967-274">Look ahead of the current position to determine whether *subexpression* matches the input string.</span></span>
<span data-ttu-id="d5967-275">**(?!**_sous-expression_**)**</span><span class="sxs-lookup"><span data-stu-id="d5967-275">**(?!**_subexpression_**)**</span></span> | <span data-ttu-id="d5967-276">Préanalyse négative de largeur nulle.</span><span class="sxs-lookup"><span data-stu-id="d5967-276">Zero-width negative lookahead.</span></span> <span data-ttu-id="d5967-277">Effectuer une préanalyse de la position actuelle pour déterminer si *sous-expression* ne correspond pas à la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d5967-277">Look ahead of the current position to determine whether *subexpression* does not match the input string.</span></span>
<span data-ttu-id="d5967-278">**(?<**=_sous-expression_**)**</span><span class="sxs-lookup"><span data-stu-id="d5967-278">**(?<**=_subexpression_**)**</span></span> | <span data-ttu-id="d5967-279">Postanalyse positive de largeur nulle.</span><span class="sxs-lookup"><span data-stu-id="d5967-279">Zero-width positive lookbehind.</span></span> <span data-ttu-id="d5967-280">Effectuer une postanalyse de la position actuelle pour déterminer si *sous-expression* correspond à la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d5967-280">Look behind the current position to determine whether *subexpression* matches the input string.</span></span>
<span data-ttu-id="d5967-281">**(?<!**_sous-expression_**)**</span><span class="sxs-lookup"><span data-stu-id="d5967-281">**(?<!**_subexpression_**)**</span></span> | <span data-ttu-id="d5967-282">Postanalyse négative de largeur nulle.</span><span class="sxs-lookup"><span data-stu-id="d5967-282">Zero-width negative lookbehind.</span></span> <span data-ttu-id="d5967-283">Effectuer une postanalyse de la position actuelle pour déterminer si *sous-expression* ne correspond pas à la chaîne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d5967-283">Look behind the current position to determine whether *subexpression* does not match the input string.</span></span>
 
## <a name="use-time-out-values"></a><span data-ttu-id="d5967-284">Utilisation de valeurs de délai d’attente</span><span class="sxs-lookup"><span data-stu-id="d5967-284">Use time-out values</span></span>

<span data-ttu-id="d5967-285">Si une expression régulière traite une entrée qui correspond presque au modèle d'expression régulière, elle peut souvent se baser sur une rétroaction excessive, laquelle affecte considérablement ses performances.</span><span class="sxs-lookup"><span data-stu-id="d5967-285">If your regular expressions processes input that nearly matches the regular expression pattern, it can often rely on excessive backtracking, which impacts its performance significantly.</span></span> <span data-ttu-id="d5967-286">En plus d'envisager soigneusement l'utilisation de la rétroaction et de tester l'expression régulière sur une entrée presque correspondante, vous devez toujours définir une valeur de délai d'attente pour garantir la minimalisation de l'impact d'une rétroaction excessive, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="d5967-286">In addition to carefully considering your use of backtracking and testing the regular expression against near-matching input, you should always set a time-out value to ensure that the impact of excessive backtracking, if it occurs, is minimized.</span></span>

<span data-ttu-id="d5967-287">Le délai d'attente d'expression régulière définit le laps de temps pendant lequel le moteur des expressions régulières recherchera une correspondance unique avant d'expirer.</span><span class="sxs-lookup"><span data-stu-id="d5967-287">The regular expression time-out interval defines the period of time that the regular expression engine will look for a single match before it times out.</span></span> <span data-ttu-id="d5967-288">L’intervalle de délai d’attente par défaut est [Regex.InfiniteMatchTimeout](xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout), ce qui signifie que l’expression régulière n’expire pas.</span><span class="sxs-lookup"><span data-stu-id="d5967-288">The default time-out interval is [Regex.InfiniteMatchTimeout](xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout), which means that the regular expression will not time out.</span></span> <span data-ttu-id="d5967-289">Vous pouvez remplacer cette valeur et définir un délai d'attente comme suit :</span><span class="sxs-lookup"><span data-stu-id="d5967-289">You can override this value and define a time-out interval as follows:</span></span> 

* <span data-ttu-id="d5967-290">En fournissant une valeur de délai d’attente quand vous instanciez un objet [Regex](xref:System.Text.RegularExpressions.Regex) en appelant le constructeur [Regex(String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)).</span><span class="sxs-lookup"><span data-stu-id="d5967-290">By providing a time-out value when you instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object by calling the [Regex(String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) constructor.</span></span>

* <span data-ttu-id="d5967-291">En appelant une méthode de critères spéciaux statique (méthode), comme [Regex.Match(String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) ou [Regex.Replace(String, String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)), qui inclut un paramètre *matchTimeout*.</span><span class="sxs-lookup"><span data-stu-id="d5967-291">By calling a static pattern matching method, such as [Regex.Match(String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) or [Regex.Replace(String, String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)), that includes a *matchTimeout* parameter.</span></span>

<span data-ttu-id="d5967-292">Si vous avez défini un intervalle de délai d’attente et qu’aucune correspondance n’est trouvée à l’issue de cet intervalle, la méthode d’expression régulière lève une exception [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException).</span><span class="sxs-lookup"><span data-stu-id="d5967-292">If you have defined a time-out interval and a match is not found at the end of that interval, the regular expression method throws a [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException) exception.</span></span> <span data-ttu-id="d5967-293">Dans votre gestionnaire d'exceptions, vous pouvez choisir de réessayer la mise en correspondance avec un délai d'attente plus long, d'annuler la recherche de correspondance et de supposer l'absence de correspondance, ou encore d'annuler la recherche de correspondance et de consigner les informations sur les exceptions à des fins d'analyse ultérieure.</span><span class="sxs-lookup"><span data-stu-id="d5967-293">In your exception handler, you can choose to retry the match with a longer time-out interval, abandon the match attempt and assume that there is no match, or abandon the match attempt and log the exception information for future analysis.</span></span>

<span data-ttu-id="d5967-294">L'exemple ci-dessous définit une méthode `GetWordData` qui instancie une expression régulière avec un délai d'attente de 350 millisecondes pour calculer le nombre de mots dans un document texte et le nombre moyen de caractères par mot.</span><span class="sxs-lookup"><span data-stu-id="d5967-294">The following example defines a `GetWordData` method that instantiates a regular expression with a time-out interval of 350 milliseconds to calculate the number of words and average number of characters in a word in a text document.</span></span> <span data-ttu-id="d5967-295">Si le délai d’attente de l’opération de recherche de correspondance expire, il augmente de 350 millisecondes et l’objet [Regex](xref:System.Text.RegularExpressions.Regex) est réinstancié.</span><span class="sxs-lookup"><span data-stu-id="d5967-295">If the matching operation times out, the time-out interval is increased by 350 milliseconds and the [Regex](xref:System.Text.RegularExpressions.Regex) object is re-instantiated.</span></span> <span data-ttu-id="d5967-296">Si le nouveau délai d'attente dépasse 1 seconde, la méthode lève de nouveau l'exception pour l'appelant.</span><span class="sxs-lookup"><span data-stu-id="d5967-296">If the new time-out interval exceeds 1 second, the method re-throws the exception to the caller.</span></span>

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

## <a name="capture-only-when-necessary"></a><span data-ttu-id="d5967-297">Capture uniquement quand cela s’avère nécessaire</span><span class="sxs-lookup"><span data-stu-id="d5967-297">Capture only when necessary</span></span>

<span data-ttu-id="d5967-298">Les expressions régulières dans .NET prennent en charge plusieurs constructions de regroupement, ce qui vous permet de regrouper un modèle d’expression régulière dans une ou plusieurs sous-expressions.</span><span class="sxs-lookup"><span data-stu-id="d5967-298">Regular expressions in .NET support a number of grouping constructs, which let you group a regular expression pattern into one or more subexpressions.</span></span> <span data-ttu-id="d5967-299">Les constructions de regroupement les plus fréquemment utilisées dans le langage d’expression régulière .NET sont **(**_sous-expression_**)**, qui définit un groupe de capture numéroté et **(?<*_nom_**>**_sous-expression_**)**, qui définit un groupe de capture nommé.</span><span class="sxs-lookup"><span data-stu-id="d5967-299">The most commonly used grouping constructs in .NET regular expression language are **(**_subexpression_**)**, which defines a numbered capturing group, and **(?<*_name_**>**_subexpression_**)**, which defines a named capturing group.</span></span> <span data-ttu-id="d5967-300">Les constructions de regroupement sont essentielles pour créer des références arrières et pour définir une sous-expression à laquelle un quantificateur est appliqué.</span><span class="sxs-lookup"><span data-stu-id="d5967-300">Grouping constructs are essential for creating backreferences and for defining a subexpression to which a quantifier is applied.</span></span> 

<span data-ttu-id="d5967-301">Toutefois, l'utilisation de ces éléments de langage n'est pas sans effet.</span><span class="sxs-lookup"><span data-stu-id="d5967-301">However, the use of these language elements has a cost.</span></span> <span data-ttu-id="d5967-302">Ils entraînent le remplissage de l’objet [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) renvoyé par la propriété [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) avec les captures nommées ou sans nom les plus récentes. Si une seule construction de regroupement a capturé plusieurs sous-chaînes dans la chaîne d’entrée, ils remplissent également l’objet [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) renvoyé par la propriété [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) d’un groupe de capture particulier à l’aide de plusieurs objets [Capture](xref:System.Text.RegularExpressions.Capture).</span><span class="sxs-lookup"><span data-stu-id="d5967-302">They cause the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) object returned by the [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) property to be populated with the most recent unnamed or named captures, and if a single grouping construct has captured multiple substrings in the input string, they also populate the [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) object returned by the [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) property of a particular capturing group with multiple [Capture](xref:System.Text.RegularExpressions.Capture) objects.</span></span>

<span data-ttu-id="d5967-303">Souvent, les constructions de regroupement sont utilisées dans une expression régulière uniquement pour que les quantificateurs puissent leur être appliqués. Les groupes capturés par ces sous-expressions ne sont alors pas utilisés par la suite.</span><span class="sxs-lookup"><span data-stu-id="d5967-303">Often, grouping constructs are used in a regular expression only so that quantifiers can be applied to them, and the groups captured by these subexpressions are not subsequently used.</span></span> <span data-ttu-id="d5967-304">Par exemple, l'expression régulière `\b(\w+[;,]?\s?)+[.?!]` est conçue pour capturer une phrase entière.</span><span class="sxs-lookup"><span data-stu-id="d5967-304">For example, the regular expression `\b(\w+[;,]?\s?)+[.?!]` is designed to capture an entire sentence.</span></span> <span data-ttu-id="d5967-305">Le tableau suivant décrit les éléments de langage dans ce modèle d’expression régulière et leur effet sur les collections [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) et [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) de l’objet [Match](xref:System.Text.RegularExpressions.Match).</span><span class="sxs-lookup"><span data-stu-id="d5967-305">The following table describes the language elements in this regular expression pattern and their effect on the [Match](xref:System.Text.RegularExpressions.Match) object's [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) and [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) collections.</span></span>

<span data-ttu-id="d5967-306">Modèle</span><span class="sxs-lookup"><span data-stu-id="d5967-306">Pattern</span></span> | <span data-ttu-id="d5967-307">Description</span><span class="sxs-lookup"><span data-stu-id="d5967-307">Description</span></span>
------- | -----------
`\b` | <span data-ttu-id="d5967-308">Commencer la correspondance à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="d5967-308">Begin the match at a word boundary.</span></span>
`\w+` | <span data-ttu-id="d5967-309">Mettre en correspondance un ou plusieurs caractères alphabétiques.</span><span class="sxs-lookup"><span data-stu-id="d5967-309">Match one or more word characters.</span></span>
`[;,]?` | <span data-ttu-id="d5967-310">Mettre en correspondance zéro ou une virgule, ou zéro ou un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="d5967-310">Match zero or one comma or semicolon.</span></span>
`\s?` | <span data-ttu-id="d5967-311">Mettre en correspondance zéro ou un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="d5967-311">Match zero or one white-space character.</span></span>
`(\w+[;,]?\s?)+` | <span data-ttu-id="d5967-312">Mettre en correspondance une ou plusieurs occurrences d'un ou plusieurs caractères alphabétiques suivis d'une virgule ou d'un point-virgule facultatif suivi d'un espace blanc facultatif.</span><span class="sxs-lookup"><span data-stu-id="d5967-312">Match one or more occurrences of one or more word characters followed by an optional comma or semicolon followed by an optional white-space character.</span></span> <span data-ttu-id="d5967-313">Cela définit le premier groupe de capture. Il est nécessaire pour que la combinaison de plusieurs caractères alphabétiques (autrement dit, un mot) suivis d'un signe de ponctuation facultatif soit répétée jusqu'à ce que le moteur des expressions régulières ait atteint la fin d'une phrase.</span><span class="sxs-lookup"><span data-stu-id="d5967-313">This defines the first capturing group, which is necessary so that the combination of multiple word characters (that is, a word) followed by an optional punctuation symbol will be repeated until the regular expression engine reaches the end of a sentence.</span></span>
`[.?!]` | <span data-ttu-id="d5967-314">Mettre en correspondance un point, un point d'interrogation ou un point d'exclamation.</span><span class="sxs-lookup"><span data-stu-id="d5967-314">Match a period, question mark, or exclamation point.</span></span>
 
<span data-ttu-id="d5967-315">Comme l’indique l’exemple suivant, quand une correspondance est trouvée, les objets [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) et [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) sont tous les deux remplis avec les captures de la correspondance.</span><span class="sxs-lookup"><span data-stu-id="d5967-315">As the following example shows, when a match is found, both the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) and [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) objects are populated with captures from the match.</span></span> <span data-ttu-id="d5967-316">Dans cet exemple, le groupe de capture `(\w+[;,]?\s?)` existe pour que le quantificateur **+** puisse lui être appliqué, ce qui permet au modèle d’expression régulière de correspondre à chaque mot d’une phrase.</span><span class="sxs-lookup"><span data-stu-id="d5967-316">In this case, the capturing group `(\w+[;,]?\s?)` exists so that the **+** quantifier can be applied to it, which enables the regular expression pattern to match each word in a sentence.</span></span> <span data-ttu-id="d5967-317">Sinon, elle correspondrait au dernier mot d'une phrase.</span><span class="sxs-lookup"><span data-stu-id="d5967-317">Otherwise, it would match the last word in a sentence.</span></span>

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

<span data-ttu-id="d5967-318">Lorsque vous utilisez des sous-expressions uniquement pour y appliquer des quantificateurs et que le texte capturé ne vous intéresse pas, vous devez désactiver les captures de groupe.</span><span class="sxs-lookup"><span data-stu-id="d5967-318">When you use subexpressions only to apply quantifiers to them, and you are not interested in the captured text, you should disable group captures.</span></span> <span data-ttu-id="d5967-319">Par exemple, l’élément de langage **(?:**_sous-expression_**)** empêche le groupe auquel il s’applique de capturer les sous-chaînes correspondantes.</span><span class="sxs-lookup"><span data-stu-id="d5967-319">For example, the **(?:**_subexpression_**)** language element prevents the group to which it applies from capturing matched substrings.</span></span> <span data-ttu-id="d5967-320">Dans l'exemple suivant, le modèle d'expression régulière de l'exemple précédent est remplacé par `\b(?:\w+[;,]?\s?)+[.?!]`.</span><span class="sxs-lookup"><span data-stu-id="d5967-320">In the following example, the regular expression pattern from the previous example is changed to `\b(?:\w+[;,]?\s?)+[.?!]`.</span></span> <span data-ttu-id="d5967-321">Comme le montre la sortie, il empêche le moteur d’expression régulière de remplir les collections [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) et [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection).</span><span class="sxs-lookup"><span data-stu-id="d5967-321">As the output shows, it prevents the regular expression engine from populating the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) and [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) collections.</span></span>

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

<span data-ttu-id="d5967-322">Vous pouvez désactiver les captures de l'une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="d5967-322">You can disable captures in one of the following ways:</span></span>

* <span data-ttu-id="d5967-323">Utilisez l’élément de langage **(?:**_sous-expression_**)**.</span><span class="sxs-lookup"><span data-stu-id="d5967-323">Use the **(?:**_subexpression_**)** language element.</span></span> <span data-ttu-id="d5967-324">Cet élément empêche la capture des sous-chaînes correspondantes dans le groupe auquel il s'applique.</span><span class="sxs-lookup"><span data-stu-id="d5967-324">This element prevents the capture of matched substrings in the group to which it applies.</span></span> <span data-ttu-id="d5967-325">Il ne désactive pas les captures de la sous-chaîne dans les groupes imbriqués.</span><span class="sxs-lookup"><span data-stu-id="d5967-325">It does not disable substring captures in any nested groups.</span></span>

* <span data-ttu-id="d5967-326">Utilisez l’option [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture).</span><span class="sxs-lookup"><span data-stu-id="d5967-326">Use the [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) option.</span></span> <span data-ttu-id="d5967-327">Elle désactive toutes les captures implicites ou sans nom dans le modèle d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="d5967-327">It disables all unnamed or implicit captures in the regular expression pattern.</span></span> <span data-ttu-id="d5967-328">Lorsque vous utilisez cette option, seules les sous-chaînes qui correspondent à des groupes nommés définis avec l’élément de langage **(?<**_nom_**>**_sous-expression_**)** peuvent être capturées.</span><span class="sxs-lookup"><span data-stu-id="d5967-328">When you use this option, only substrings that match named groups defined with the **(?<**_name_**>**_subexpression_**)** language element can be captured.</span></span> <span data-ttu-id="d5967-329">L’indicateur [ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) peut être passé au paramètre options d’un constructeur de classe [Regex](xref:System.Text.RegularExpressions.Regex) ou au paramètre options d’une méthode de mise en correspondance statique [Regex](xref:System.Text.RegularExpressions.Regex).</span><span class="sxs-lookup"><span data-stu-id="d5967-329">The [ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) flag can be passed to the options parameter of a [Regex](xref:System.Text.RegularExpressions.Regex) class constructor or to the options parameter of a [Regex](xref:System.Text.RegularExpressions.Regex) static matching method.</span></span>

* <span data-ttu-id="d5967-330">Utilisez l’option **n** dans l’élément de langage **(?imnsx)**.</span><span class="sxs-lookup"><span data-stu-id="d5967-330">Use the **n** option in the **(?imnsx)** language element.</span></span> <span data-ttu-id="d5967-331">Cette option désactive toutes les captures implicites ou sans nom à partir du point où l’élément apparaît dans le modèle d’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="d5967-331">This option disables all unnamed or implicit captures from the point in the regular expression pattern at which the element appears.</span></span> <span data-ttu-id="d5967-332">Les captures sont désactivées jusqu’à la fin du modèle ou jusqu’à ce que l’option **(-n)** active les captures implicites ou sans nom.</span><span class="sxs-lookup"><span data-stu-id="d5967-332">Captures are disabled either until the end of the pattern or until the **(-n)** option enables unnamed or implicit captures.</span></span> <span data-ttu-id="d5967-333">Pour plus d’informations, consultez [Constructions diverses dans les expressions régulières](miscellaneous.md).</span><span class="sxs-lookup"><span data-stu-id="d5967-333">For more information, see [Miscellaneous constructs in regular expressions](miscellaneous.md).</span></span>

* <span data-ttu-id="d5967-334">Utilisez l’option **n** dans l’élément de langage **(?imnsx:**_sous-expression_**)**.</span><span class="sxs-lookup"><span data-stu-id="d5967-334">Use the **n** option in the **(?imnsx:**_subexpression_**)** language element.</span></span> <span data-ttu-id="d5967-335">Cette option désactive toutes les captures implicites ou sans nom dans *sous-expression*.</span><span class="sxs-lookup"><span data-stu-id="d5967-335">This option disables all unnamed or implicit captures in *subexpression*.</span></span> <span data-ttu-id="d5967-336">Les captures effectuées par les groupes de capture imbriqués implicites ou sans nom sont également désactivées.</span><span class="sxs-lookup"><span data-stu-id="d5967-336">Captures by any unnamed or implicit nested capturing groups are disabled as well.</span></span>

## <a name="related-topics"></a><span data-ttu-id="d5967-337">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d5967-337">Related topics</span></span>

<span data-ttu-id="d5967-338">Titre</span><span class="sxs-lookup"><span data-stu-id="d5967-338">Title</span></span> | <span data-ttu-id="d5967-339">Description</span><span class="sxs-lookup"><span data-stu-id="d5967-339">Description</span></span>
----- | ----------- 
[<span data-ttu-id="d5967-340">Comportement détaillé des expressions régulières</span><span class="sxs-lookup"><span data-stu-id="d5967-340">Details of regular expression behavior</span></span>](regex-behavior.md) | <span data-ttu-id="d5967-341">Aborde l’implémentation du moteur d’expression régulière dans .NET.</span><span class="sxs-lookup"><span data-stu-id="d5967-341">Examines the implementation of the regular expression engine in .NET.</span></span> <span data-ttu-id="d5967-342">Cette rubrique traite de la flexibilité des expressions régulières. Elle explique la responsabilité du développeur pour que le fonctionnement efficace et fiable du moteur des expressions régulières soit garanti.</span><span class="sxs-lookup"><span data-stu-id="d5967-342">The topic focuses on the flexibility of regular expressions and explains the developer's responsibility for ensuring the efficient and robust operation of the regular expression engine.</span></span>
[<span data-ttu-id="d5967-343">Retour sur trace dans les expressions régulières</span><span class="sxs-lookup"><span data-stu-id="d5967-343">Backtracking in regular expressions</span></span>](backtracking.md) | <span data-ttu-id="d5967-344">Aborde la rétroaction et la façon dont elle affecte les performances des expressions régulières, ainsi que les éléments de langage, qui offrent des alternatives à la rétroaction.</span><span class="sxs-lookup"><span data-stu-id="d5967-344">Explains what backtracking is and how it affects regular expression performance, and examines language elements that provide alternatives to backtracking.</span></span>
[<span data-ttu-id="d5967-345">Langage des expressions régulières - Aide-mémoire</span><span class="sxs-lookup"><span data-stu-id="d5967-345">Regular expression language - quick reference</span></span>](quick-ref.md) | <span data-ttu-id="d5967-346">Décrit les éléments du langage d’expression régulière dans .NET et propose des liens vers la documentation détaillée pour chaque élément de langage.</span><span class="sxs-lookup"><span data-stu-id="d5967-346">Describes the elements of the regular expression language in .NET and provides links to detailed documentation for each language element.</span></span>
 


