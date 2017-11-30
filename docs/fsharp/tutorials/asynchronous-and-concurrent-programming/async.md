---
title: 'Programmation asynchrone en F #'
description: "Découvrez comment F # de programmation asynchrone est effectuée via un modèle de programmation au niveau du langage qui est facile à utiliser et naturelle à la langue."
keywords: .NET, .NET Core
author: cartermp
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9196bfc-b8a8-4d33-8b53-0dcbd58a69d8
ms.openlocfilehash: 23528d84d0f28283868a1ea316953543d0fd566a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="async-programming-in-f"></a>Programmation asynchrone en F # #

> [!NOTE]
> Certaines inexactitudes ont été détectés dans cet article.  Il est en cours de réécriture.  Consultez [problème #666](https://github.com/dotnet/docs/issues/666) pour en savoir plus sur les modifications.

Programmation F # asynchrone peut être obtenue via un modèle de programmation au niveau du langage conçu pour être facile à utiliser et naturelle à la langue.

Le cœur de la programmation asynchrone en F # est `Async<'T>`, une représentation sous forme de travail qui peut être déclenchée pour s’exécuter en arrière-plan, où `'T` est soit le type retourné via spéciale `return` mot clé ou `unit` si le flux de travail asynchrone n’a pas résultat à retourner.

Comprendre le concept essentiel est que le type d’une expression async est `Async<'T>`, qui est simplement un _spécification_ de travail à faire dans un contexte asynchrone. Il n’est pas exécuté jusqu'à ce que vous le démarrez explicitement avec une des fonctions de départ (tel que `Async.RunSynchronously`). Bien qu’il s’agit d’une autre façon de réfléchir à travailler, il finit par être très simple dans la pratique.

Par exemple, que vous vouliez télécharger le code HTML à partir de dotnetfoundation.org sans bloquer le thread principal. Vous pouvez l’atteindre comme suit :

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "http://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

C’est tout ! À l’exception de l’utilisation de `async`, `let!`, et `return`, il s’agit simplement normale du code F #.

Il existe quelques constructions syntaxiques qui sont à noter :

*   `let!`lie le résultat d’une expression async (qui s’exécute sur un autre contexte).
*   `use!`fonctionne comme `let!`, mais supprime ses ressources liées lorsqu’il devient hors de portée.
*   `do!`un flux de travail asynchrone qui ne retourne rien attendra.
*   `return`simplement retourne un résultat d’une expression asynchrone.
*   `return!`exécute un autre flux de travail asynchrone et retourne sa valeur de retour comme résultat.

En outre, normal `let`, `use`, et `do` mots clés peuvent être utilisés avec les versions asynchrones, comme ils le feraient dans une fonction normale.

## <a name="how-to-start-async-code-in-f"></a>Comment démarrer le Code asynchrone en F # #

Comme mentionné précédemment, code asynchrone est une spécification de travail à effectuer dans un autre contexte, qui doit être démarrée explicitement. Voici deux façons d’y parvenir :

1.  `Async.RunSynchronously`démarre un flux de travail asynchrone sur un autre thread et attend son résultat.

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

 // Execution will pause until fetchHtmlAsync finishes
 let html = "http://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2.  `Async.Start`démarre un flux de travail asynchrone sur un autre thread et seront **pas** attend son résultat.

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "http://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

Autres manières de démarrer un flux de travail asynchrones disponible pour des scénarios plus spécifiques. Elles sont décrites en détail [dans la référence Async](https://msdn.microsoft.com/library/ee370232.aspx).

### <a name="a-note-on-threads"></a>Remarque sur les Threads

La phrase « dans un autre thread » est mentionnée ci-dessus, mais il est important de savoir que **cela ne signifie pas que le flux de travail asynchrone est façade pour le multithreading**. Le flux de travail réellement « accède » entre les threads, les emprunts pour une petite quantité de temps nécessaire pour effectuer des tâches utiles. Lorsqu’un flux de travail asynchrone est effectivement « en attente » (par exemple, un appel réseau retourner un élément), n’importe quel thread qu'au moment où il a été d’emprunt est libérée jusqu'à accédez effectuez des tâches utiles sur autre chose. Cela permet aux workflows asynchrones d’utiliser le système, sur qu'elles s’exécutent aussi efficacement que possible et les rend particulièrement fort pour les scénarios d’e/s élevées.

## <a name="how-to-add-parallelism-to-async-code"></a>L’ajout de parallélisme à Code asynchrone

Parfois éventuellement besoin pour effectuer plusieurs tâches asynchrones en parallèle, collecter leurs résultats et les interpréter d’une certaine façon. `Async.Parallel`vous permet de faire sans devoir utiliser la bibliothèque parallèle de tâches, ce qui évite d’avoir à forcer `Task<'T>` et `Async<'T>` types.

L’exemple suivant utilise `Async.Parallel` pour télécharger le code HTML à partir de quatre sites populaires en parallèle, attendez que ces tâches à effectuer, puis l’imprimer le code HTML qui a été téléchargé.

```fsharp
open System
open System.Net

let urlList = 
    [ "http://www.microsoft.com"
      "http://www.google.com"
      "http://www.amazon.com"
      "http://www.facebook.com" ]

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a>Informations et conseils importants

*   Ajoutez « Async » à la fin de toutes les fonctions que vous allez utiliser

 Bien qu’il s’agit simplement d’une convention d’affectation de noms, elle simplifie choses comme les API détectabilité. En particulier s’il existe des versions synchrones et asynchrones de la routine de même, il est judicieux de déclarer explicitement qui est asynchrone via le nom.

*   Écouter le compilateur !

 Compilateur F # est très stricte, rend pratiquement impossible d’effectuer une action troubling comme exécuter « async » code synchrone. Si vous avez un avertissement, qui est un signe que le code ne sera pas exécuté comment vous pensez qu’il sera. Si le compilateur peut rendre heureux, votre code s’exécutera probablement comme prévu.

## <a name="for-the-cvb-programmer-looking-into-f"></a>Pour un programmeur C# /Visual Basic A-t-il F # #

Cette section suppose que vous êtes familiarisé avec le modèle asynchrone en C# / VB. Si vous n’êtes pas, [de programmation asynchrone en c#](../../../csharp/async.md) est un point de départ.

Il existe une différence fondamentale entre le modèle d’async C# /Visual Basic et le modèle asynchrone F #.

Lorsque vous appelez une fonction qui retourne un `Task` ou `Task<'T>`, que le travail a déjà commencé l’exécution. Le handle retourné représente une opération asynchrone en cours d’exécution. En revanche, lorsque vous appelez une fonction async en F #, le `Async<'a>` retourné représente une tâche qui sera **généré** à un moment donné. Présentation de ce modèle est puissante, car elle permet des tâches asynchrones dans F # pour être chaînés ensemble, exécutées de manière conditionnelle et être démarrée avec une granularité plus fine du contrôle.

Il existe quelques autres similitudes et différences à noter.

### <a name="similarities"></a>Similitudes

*   `let!`, `use!`, et `do!` sont analogues aux `await` lors de l’appel d’une tâche asynchrone à partir d’un `async{ }` bloc.

 Les trois mots clés ne peuvent être utilisées dans un `async { }` bloc, similaire à la `await` peut uniquement être appelée à l’intérieur d’un `async` (méthode). En bref, `let!` concerne lorsque vous souhaitez capturer et utiliser un résultat, `use!` est similaire, mais pour un élément dont les ressources doivent obtenir nettoyées après leur utilisation, et `do!` concerne lorsque vous souhaitez attendre d’un flux de travail asynchrone sans valeur de retour à la fin avant de continuer.

*   F # prend en charge de parallélisme de données de la même façon.

 Bien qu’il fonctionne très différemment, `Async.Parallel` correspond à `Task.WhenAll` pour le scénario de souhaitant les résultats d’un ensemble de travaux d’async lorsque toutes les fois terminées.

### <a name="differences"></a>Différences

*   Imbriqué `let!` n’est pas autorisé, contrairement aux imbriqué`await`

 Contrairement aux `await`, qui peut être imbriqué indéfiniment, `let!` ne peut pas et doit avoir son résultat à lié avant de l’utiliser à l’intérieur d’un autre `let!`, `do!`, ou `use!`.

*   Prise en charge l’annulation est plus simple en F # à en C# / VB.

 Prise en charge de l’annulation d’une tâche au milieu son exécution dans C# /Visual Basic requiert une vérification de la `IsCancellationRequested` propriété ou l’appel `ThrowIfCancellationRequested()` sur un `CancellationToken` objet qui est passé à la méthode async.

En revanche, les workflows asynchrones F # sont plus naturellement pouvant être annulés. L’annulation est un processus en trois étapes simple.

1.  Créez un `CancellationTokenSource`.
2.  Passer à une fonction de départ.
3.  Appeler `Cancel` sur le jeton.

Exemple :

```fsharp
open System
open System.Net

let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "http://url-to-upload-to.com" "hello, world!"

let token = new CancellationTokenSource()
Async.Start (workflow, token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

C’est tout !

## <a name="further-resources"></a>Ressources supplémentaires :

*   [Flux de travail asynchrone sur MSDN](https://msdn.microsoft.com/library/dd233250.aspx)
*   [Séquences asynchrones pour F #](http://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [Utilitaires de F # de données HTTP](https://fsharp.github.io/FSharp.Data/library/Http.html)
