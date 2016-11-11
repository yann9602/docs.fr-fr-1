---
title: "Portage vers .NET Core - Bibliothèques"
description: "Portage vers .NET Core - Bibliothèques"
keywords: .NET, .NET Core
author: cartermp
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a0fd860d-d6b6-4659-b325-8a6e6f5fa4a1
translationtype: Human Translation
ms.sourcegitcommit: 46061efa8e33c6a73befa5181eb33b8deb2fa637
ms.openlocfilehash: 051c8d46abdafe722eec77a440e384efbae0e70a

---

# <a name="porting-to-net-core-libraries"></a>Portage vers .NET Core - Bibliothèques

Avec la version de .NET Core 1.0, vous avez la possibilité de porter le code des bibliothèques existantes pour qu’il puisse s’exécuter sur différentes plateformes.  Cet article traite des points suivants : la bibliothèque .NET Standard, les technologies non disponibles, comment faire pour tenir compte du nombre plus réduit d’API disponibles sur .NET Core 1.0, comment utiliser les outils fournis avec .NET Core SDK Preview 2, et les approches recommandées pour le portage de votre code.

Le portage est une tâche qui peut prendre du temps, en particulier si vous avez un code base de grande taille.  Vous devez également être prêt à adapter les conseils donnés ici pour les faire correspondre au mieux à votre code.  Chaque code base est différent : cet article tente donc de structurer les éléments de façon souple, mais il peut être nécessaire de vous éloigner des conseils donnés.

## <a name="prerequisites"></a>Prérequis

Cet article suppose que vous utilisez Visual Studio 2015 ou ultérieur sur Windows.  Les bits nécessaires pour générer le code .NET Core ne sont pas disponibles dans les versions précédentes de Visual Studio.

Cet article suppose également que vous comprenez le [processus de portage recommandé](index.md) et que vous avez résolu les problèmes liés aux [dépendances tierces](third-party-deps.md).

## <a name="targeting-the-net-standard-library"></a>Ciblage de la bibliothèque .NET Standard

La meilleure façon de générer une bibliothèque multiplateforme pour .NET Core est de cibler la [bibliothèque .NET Standard](../../standard/library.md).  La bibliothèque .NET Standard est la spécification formelle des API .NET qui sont destinées à être disponibles sur tous les runtimes .NET.  Elle est prise en charge par le runtime .NET Core.

Cela signifie que vous devez trouver un compromis entre les API que vous pouvez utiliser et les plateformes que vous pouvez prendre en charge, et choisir la version de la plateforme .NET Standard qui est la mieux adaptée au compromis que vous voulez faire.

Pour l’instant, il existe 7 versions différentes à considérer : .NET Standard 1.0 à 1.6.  Si vous choisissez une version ultérieure, vous pouvez accéder à plus d’API avec comme contrepartie une exécution sur moins de cibles.  Si vous choisissez une version antérieure, votre code peut s’exécuter sur plus de cibles, mais avec moins d’API à votre disposition.

Voici une matrice de chaque version de .NET Standard et de chaque plateforme spécifique sur laquelle elle s’exécute :

| Nom de la plateforme | Alias |  |  |  |  |  | | |
| :---------- | :--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |
|.NET Standard | netstandard | 1.0 | 1.1 | 1.2 | 1.3 | 1.4 | 1,5 | 1.6 |
|.NET Core|netcoreapp|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|1.0|
|.NET Framework|net|&rarr;|4.5|4.5.1|4.6|4.6.1|4.6.2|4.6.3|
|Plateformes Mono/Xamarin||&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|*|
|Plateforme Windows universelle|uap|&rarr;|&rarr;|&rarr;|&rarr;|10.0|||
|Windows|win|&rarr;|8.0|8.1|||||
|Windows Phone|wpa|&rarr;|&rarr;|8.1|||||
|Windows Phone Silverlight|wp|8.0|||||||

Un point clé à comprendre est qu’**un projet ciblant une version antérieure ne peut pas faire référence à un projet ciblant une version ultérieure**.  Par exemple, un projet ciblant .NET Platform Standard version 1.2 ne peut pas faire référence à des projets qui ciblent .NET Platform Standard version 1.3 ou ultérieure.  Les projets **peuvent** cependant faire référence à des versions antérieures : un projet ciblant .NET Platform Standard 1.3 peut donc faire référence à un projet ciblant .NET Platform Standard 1.2 ou antérieur.

Il est recommandé de choisir la version de .NET Standard la plus ancienne et de l’utiliser dans tout votre projet.

Pour plus d’informations, consultez [Bibliothèque .NET Platform Standard](../../standard/library.md).

## <a name="key-technologies-not-yet-available-on-the-net-standard-or-net-core"></a>Technologies clés non encore disponibles sur .NET Standard ou .NET Core

Vous utilisez peut-être certaines technologies disponibles pour le .NET Framework qui ne sont pas actuellement disponibles pour .NET Core.  Chacune des sous-sections suivantes correspond à l’une de ces technologies.  Les options alternatives sont répertoriées s’il est possible pour vous de les adopter.

### <a name="app-domains"></a>Domaines de l'application

Les AppDomains peuvent être utilisés avec différents buts sur le .NET Framework. Pour l’isolation du code, nous recommandons des processus distincts et/ou des conteneurs comme alternative. Pour le chargement dynamique d’assemblys, nous vous recommandons de la nouvelle classe @System.Runtime.Loader.AssemblyLoadContext.

### <a name="remoting"></a>Communication à distance

Pour la communication entre processus, les mécanismes de communication entre processus (IPC) peuvent être utilisés comme alternative à la communication à distance, comme les [canaux](https://docs.microsoft.com/dotnet/core/api/system.io.pipes) ou les [fichiers mappés en mémoire](https://docs.microsoft.com/dotnet/core/api/system.io.memorymappedfiles.memorymappedfile).

Entre les machines, vous pouvez utiliser une solution réseau comme alternative, de préférence un protocole en texte brut avec une faible charge, comme HTTP.  [KestrelHttpServer](https://github.com/aspnet/KestrelHttpServer), le serveur web utilisé par ASP.NET Core, est une option ici.  La génération de proxy distant via [Castle.Core](https://github.com/castleproject/Core) est également une option à considérer.

### <a name="binary-serialization"></a>Sérialisation binaire

Comme alternative à la sérialisation binaire, vous pouvez choisir entre plusieurs technologies de sérialisation différentes.  Vous devez en choisir une qui correspond à vos objectifs de mise en forme et d’encombrement.  Les choix les plus habituels sont :

* [JSON.NET](http://www.newtonsoft.com/json) pour JSON
* @System.Runtime.Serialization.DataContractSerializer pour XML et JSON
* @System.Xml.Serialization.XmlSerializer pour XML
* [protobuf-net](https://github.com/mgravell/protobuf-net) pour les mémoires tampons des protocoles

Reportez-vous aux ressources liées pour en savoir plus sur leurs avantages et choisir celles convenant à vos besoins.  Il existe de nombreux autres formats et technologies de sérialisation, dont bon nombre sont en open source.

### <a name="sandboxes"></a>Bacs à sable

Comme alternative à l’utilisation d’un bac à sable, vous pouvez utiliser des limites de sécurité fournies par le système d’exploitation, comme les comptes d’utilisateur pour exécuter des processus avec l’ensemble minimal de privilèges.

## <a name="overview-of-projectjson"></a>Vue d’ensemble de `project.json`

Le [modèle de projet project.json](../tools/project-json.md) est un modèle de projet fourni avec .NET Core SDK 1.0 Preview 2.  Il offre certains avantages dont vous pouvez tirer parti aujourd’hui :

* Multiciblage simple où les assemblys spécifiques à une cible peuvent être générés à partir d’une même build.
* Possibilité de générer facilement un package NuGet avec une build du projet.
* Il n’est pas nécessaire de répertorier les fichiers de votre fichier projet.
* Unification des dépendances de package NuGet et dépendances de projet à projet.

> Alors que `project.json` sera finalement bientôt déconseillé, il peut être utilisé aujourd’hui pour générer des bibliothèques sur .NET Standard.

### <a name="the-project-file-projectjson"></a>Le fichier de projet : `project.json`

Les projets .NET Core sont définis par un répertoire contenant un fichier `project.json`.  Ce fichier est l’endroit où les aspects du projet sont déclarées, comme les dépendances du package, la configuration du compilateur, la configuration du runtime, etc.

La commande `dotnet restore`lit ce fichier de projet, restaure toutes les dépendances du projet et génère un fichier `project.lock.json`.  Ce fichier contient toutes les informations nécessaires dont a besoin le système de génération pour générer le projet.

Pour en savoir plus sur le fichier `project.json`, lisez les [informations de référence sur project.json](../tools/project-json.md).

### <a name="the-solution-file-globaljson"></a>Le fichier de solution : `global.json`

Le fichier `global.json` est un fichier facultatif à inclure dans une solution qui contient plusieurs projets.  Il se trouve généralement dans le répertoire racine d’un ensemble de projets.  Il peut être utilisé pour informer le système de génération des différents sous-répertoires qui peuvent contenir des projets.  Ceci est destiné aux systèmes de grande taille composés de plusieurs projets.

Par exemple, vous pouvez organiser votre code dans le dossier de plus haut niveau `/src` et `/test` comme ceci :

```json
{
    "projects":[ "src", "test" ]
}
```

Vous pouvez ensuite avoir plusieurs fichiers `project.json` sous leurs propres sous-dossiers dans `/src` et `/test`.

### <a name="how-to-multitarget-with-projectjson"></a>Comment réaliser un multiciblage avec `project.json`

De nombreuses bibliothèques intègrent le multiciblage de façon à avoir une portée aussi étendue que possible.  Avec .NET Core, le multiciblage est un « citoyen de première classe », ce qui signifie que vous pouvez facilement générer des assemblys spécifiques à une plateforme avec une même build.

Le multiciblage consiste simplement à ajouter le moniker du Framework cible à votre fichier `project.json`, à utiliser les dépendances appropriées pour chaque cible (`dependencies` pour .NET Core et `frameworkAssemblies` pour le .NET Framework) et éventuellement à utiliser des directives `#if` de compilation conditionnelle du code source pour une utilisation de l’API spécifique à la plateforme.

Par exemple, imaginez que vous créez une bibliothèque où vous voulez réaliser des opérations réseau, et que vous voulez que la bibliothèque s’exécute sur toutes les versions du .NET Framework, sur un profil de bibliothèque de classes portable et sur .NET Core.  Pour les cibles .NET Core et .NET Framework 4.5+, vous pouvez utiliser la bibliothèque `System.Net.Http` et `async`/`await`.  Cependant, pour les versions antérieures du .NET Framework, ces API ne sont pas disponibles.

Voici un exemple de section `frameworks` pour un fichier `project.json` qui cible le .NET Framework versions 2.0, 3.5, 4.0, 4.5 et .NET Standard 1.6 :

```javascript
{
    "frameworks":{
        "net20":{
            "frameworkAssemblies":{
                "System.Net":""
            }
        },
        "net35":{
            "frameworkAssemblies":{
                "System.Net":""
            }
        },
        "net40":{
            "frameworkAssemblies":{
                "System.Net":""
            }
        },
        "net45":{
            "frameworkAssemblies":{
                "System.Net.Http":"",
                "System.Threading.Tasks":""
            }
        },
        ".NETPortable,Version=v4.5,Profile=Profile259": {
            "buildOptions": {
                "define": [ "PORTABLE" ]
             },
             "frameworkAssemblies":{
                 "mscorlib":"",
                 "System":"",
                 "System.Core":"",
                 "System.Net.Http":""
             }
        },
        "netstandard16":{
            "dependencies":{
                "NETStandard.Library":"1.6.0",
                "System.Net.Http":"4.0.1",
                "System.Threading.Tasks":"4.0.11"
            }
        },
    }
}
```

Notez que les cibles de la bibliothèque de classes portable sont spéciales : elles nécessitent la spécification d’une définition de build que le compilateur doit reconnaître, ainsi que de tous les assemblys que vous utilisez, notamment `mscorlib`.  

Votre code source peut alors utiliser les dépendances comme suit :

```csharp
#if (NET20 || NET35 || NET40 || PORTABLE)
using System.Net;
#else
using System.Net.Http;
using System.Threading.Tasks;
#endif
```

Notez que toutes les cibles .NET Framework et .NET Standard ont des noms reconnus par le compilateur :

```
.NET Framework 2.0   --> NET20
.NET Framework 3.5   --> NET35
.NET Framework 4.0   --> NET40
.NET Framework 4.5   --> NET45
.NET Framework 4.5.1 --> NET451
.NET Framework 4.5.2 --> NET452
.NET Framework 4.6   --> NET46
.NET Framework 4.6.1 --> NET461
.NET Framework 4.6.2 --> NET462
.NET Standard 1.0    --> NETSTANDARD1_0
.NET Standard 1.1    --> NETSTANDARD1_1
.NET Standard 1.2    --> NETSTANDARD1_2
.NET Standard 1.3    --> NETSTANDARD1_3
.NET Standard 1.4    --> NETSTANDARD1_4
.NET Standard 1.5    --> NETSTANDARD1_5
.NET Standard 1.6    --> NETSTANDARD1_6
```

Comme mentionné ci-dessus, si vous ciblez une bibliothèque de classes portable, vous devez spécifier une définition de build que le compilateur doit comprendre.  Il n’existe pas définition par défaut que le compilateur peut utiliser.

### <a name="using-projectjson-in-visual-studio"></a>Utilisation de `project.json` dans Visual Studio

Vous avez deux options pour utiliser `project.json` dans Visual Studio :

1. Un nouveau type de projet xproj.
2. Un projet de bibliothèque de classes portable reciblé qui prend en charge .NET Standard.

Il y a différents avantages et inconvénients pour chacune de ces options.

#### <a name="when-to-pick-an-xproj-project"></a>Quand choisir un projet Xproj

Le nouveau système de projet Xproj dans Visual Studio utilise les fonctionnalités du modèle de projet basé sur `project.json` pour offrir deux fonctionnalités majeures sur les types de projets existants : le multiciblage intégré via la génération de plusieurs assemblys et la possibilité de générer directement un package NuGet sur la build.

Il présente cependant l’inconvénient de ne pas avoir certaines fonctionnalités que vous pourriez utiliser, comme :

- Prise en charge de F# ou de Visual Basic
- Génération d’assemblys satellites avec des chaînes de ressources localisées
- Référencement direct d’un fichier `.dll` sur le système de fichiers
- La possibilité de faire référence à un projet csproj dans le gestionnaire de références (la dépendance directe d’un fichier `.dll` est cependant prise en charge)

Si les besoins de votre projet sont relativement réduites et que vous pouvez tirer parti des nouvelles fonctionnalités de xproj, vous devez le sélectionner comme système de projet.  Ceci peut être fait dans Visual Studio comme ceci :

1. Vérifiez que vous utilisez Visual Studio 2015 ou ultérieur.
2. Sélectionnez Fichier | Nouveau projet.
3. Sélectionnez « .NET Core » sous Visual C#.
4. Sélectionnez le modèle « Bibliothèque de classes (.NET Core) ». 

#### <a name="when-to-pick-a-pcl-project"></a>Quand choisir un projet de bibliothèque de classes portable

Vous pouvez cibler .NET Core avec le système de projet traditionnel dans Visual Studio en créant une bibliothèque de classes portable et en sélectionnant « .NET Core » dans la boîte de dialogue de configuration du projet.  Vous devez ensuite recibler le projet pour qu’il soit basé sur .NET Standard :

1. Cliquez avec le bouton droit sur le fichier projet dans Visual Studio et sélectionnez Propriétés.
2. Sous Build, sélectionnez « Convertir vers .NET Standard ».

Si vous avez des besoins plus avancés en système de projet, ceci doit être votre choix.  Notez que si vous voulez multicibler en générant des assemblys spécifiques aux plateformes, par exemple avec le système de projet `xproj`, vous devez créer une bibliothèque de classes portable qui soit une forme de « leurre », comme décrit dans [How to Make Portable Class Libraries Work for You](https://blogs.msdn.microsoft.com/dsplaisted/2012/08/27/how-to-make-portable-class-libraries-work-for-you/).

## <a name="retargeting-your-net-framework-code-to-net-framework-462"></a>Reciblage de votre code .NET Framework vers le .NET Framework 4.6.2

Si votre code ne cible pas le .NET Framework 4.6.2, il est recommandé de recibler.  Ceci garantit que vous pouvez utiliser les API alternatives les plus récentes pour les cas où .NET Standard ne peut pas prendre en charge les API existantes.

Pour chacun de vos projets dans Visual Studio que vous voulez porter, procédez comme suit :

1. Cliquez avec le bouton droit sur le projet et sélectionnez Propriétés.
2. Dans la liste déroulante Framework cible, sélectionnez « .NET Framework 4.6.2 ».
3. Recompilez vos projets.

Et voilà !  Comme vos projets ciblent maintenant le .NET Framework 4.6.2, vous pouvez utiliser cette version du .NET Framework comme base pour le portage du code.

## <a name="determining-the-portability-of-your-code"></a>Détermination de la portabilité de votre code

L’étape suivante consiste à exécuter l’outil API Portability Analyzer (ApiPort) pour générer un rapport de portabilité que vous pouvez commencer à analyser.

Vérifiez que vous comprenez bien l’[outil API Portability (ApiPort)](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) et que vous pouvez générer des rapports de portabilité pour le ciblage de .NET Core.  La façon dont faites cela va probablement varier selon vos besoins et vos préférences personnelles.  Voici quelques approches différentes : vous pouvez les mélanger en fonction de la structure de votre code.

### <a name="dealing-primarily-with-the-compiler"></a>Approche centrée sur le compilateur

Cette approche peut être la meilleure pour les petits projets ou les projets qui n’utilisent pas beaucoup d’API du .NET Framework.  Elle est très simple :

1. Exécutez éventuellement ApiPort sur votre projet.
2. Si ApiPort a été exécuté, regardez rapidement le rapport.
3. Recopiez tout votre code dans un nouveau projet .NET Core.
4. Résolvez les erreurs du compilateur jusqu’à ce qu’il compile, en vous référant au rapport de portabilité si nécessaire.
5. Répétez autant de fois que nécessaire.

Bien que cette approche soit très structurée, l’approche centrée sur le code peut permettre de résoudre les problèmes rapidement et peut être la meilleure approche pour les projets ou les bibliothèques de petite taille.  Un projet qui contient seulement des modèles de données peut être ici un candidat idéal.

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>Rester sur le .NET Framework jusqu’à la résolution des problèmes de portabilité

Cette approche peut être la meilleure si vous préférez avoir du code compilé pendant tout le processus.  L’approche est la suivante :

1. Exécutez ApiPort sur un projet.
2. Résolvez les problèmes en utilisant des API différentes qui sont portables.
3. Prenez note de tous les endroits où vous ne pouvez pas utiliser une alternative directe.
4. Répétez les étapes 1 à 3 pour tous les projets que vous portez jusqu’à ce que vous soyez certain que chacun est prêt à être copié dans un projet .NET Core.
5. Copiez le code dans un nouveau projet .NET Core.
6. Résolvez les problèmes que vous avez notés.

Cette approche prudente est plus structurée que simplement solutionner les erreurs de compilation, mais elle est encore relativement centrée sur le code et a comme avantage que le code peut toujours être compilé.  La façon dont vous résolvez certains problèmes qui n’ont pas pu être traités en utilisant une autre API peut varier considérablement.  Il peut être nécessaire de développer un plan plus complet pour certains projets, ce qui est couvert par l’approche suivante.

### <a name="developing-a-comprehensive-plan-of-attack"></a>Développement d’un plan d’attaque complet

Cette approche peut être la meilleure pour les projets plus grands et plus complexes, où la restructuration du code ou la réécriture de certains éléments peut être nécessaire pour prendre en charge .NET Core.  L’approche est la suivante :

1. Exécutez ApiPort sur un projet.
2. Déterminez les endroits dans votre code où chaque type non portable est utilisé et comment cela affecte la portabilité globale.

   a.  Déterminez la nature de ces types.  Sont-ils peu nombreux mais fréquemment utilisés ?  Sont-ils nombreux mais peu fréquemment utilisés ?  Leur utilisation est-elle concentrée ou est-elle répartie à travers tout le code ?
   
   b. Est-il facile d’isoler le code qui n’est pas portable ? Si oui, vous pouvez donc le traiter plus facilement.
   
   c. Devez-vous refactoriser votre code ?
   
   d. Pour les types qui ne sont pas portables, y a-t-il des API alternatives qui accomplissent la même tâche ?  Par exemple, si vous utilisez la classe `WebClient`, vous pouvez peut-être utiliser la classe `HttpClient` à la place.
   
   e. Existe-t-il des API portables différentes que vous pouvez utiliser pour accomplir une tâche, même si ce n’est pas un remplacement immédiat à opérer ?  Par exemple, si vous utilisez `XmlSchema` pour analyser du code XML, mais vous n’avez pas besoin de la découverte du schéma XML, vous pouvez utiliser `System.Linq.Xml` et analyser vous-même les données.

3. Si vous avez des assemblys difficiles à porter, est-il intéressant de les laisser sur le .NET Framework pour l’instant ?  Voici quelques éléments à prendre en compte :

   a. Vous pouvez avoir des fonctionnalités dans votre bibliothèque qui ne sont pas compatibles avec .NET Core car elles s’appuient de façon trop importante sur des fonctionnalités spécifiques au .NET Framework ou à Windows.  Est-il intéressant de laisser cette fonctionnalité de côté pour l’instant et de publier une version .NET Core de votre bibliothèque avec moins de fonctionnalités pour le moment ?
   
   b. Une refactorisation serait-elle utile ici ?
   
4. Est-il raisonnable d’écrire votre propre implémentation d’une API .NET Framework non disponible ?

   Vous pouvez envisager à la place de copier, de modifier et d’utiliser du code provenant de la [source de référence du .NET Framework](https://github.com/Microsoft/referencesource).  Il est concédé sous licence [MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), de sorte que vous disposez d’une liberté significative pour faire cela.  Veillez simplement à mentionner correctement ce qui est propriété de Microsoft dans votre code !
   
5. Répétez ce processus si nécessaire pour les différents projets.
6. Une fois que vous avez un plan, exécutez-le.
 
La phase d’analyse peut prendre un certain temps, selon la taille de votre code base.  Passer du temps sur cette phase pour déterminer précisément l’étendue des modifications nécessaires et pour développer un plan peut vous économiser beaucoup de temps sur le long terme, en particulier si vous avez un code base plus complexe.

Votre plan peut impliquer des modifications importantes à votre code base tout en continuant à cibler le .NET Framework 4.6.2, ce qui fait de ceci une version plus structurée de l’approche précédente.  La façon dont vous allez exécuter votre plan dépend de votre code base.

### <a name="mixing-approaches"></a>Combinaison des approches

Il est probable que vous allez combiner les approches ci-dessus de façon différente selon les projets.  Vous devez faire ce qui a le plus de sens pour vous et pour votre code base.

## <a name="porting-your-tests"></a>Portage de vos tests

La meilleure façon de vérifier que tout fonctionne quand vous avez porté votre code est de tester votre code quand vous l’avez porté sur .NET Core.  Pour cela, vous devez utiliser un framework de test qui crée et exécute des tests pour .NET Core.  Vous avez actuellement trois options :

* [xUnit](https://xunit.github.io/)
   - [Prise en main](http://xunit.github.io/docs/getting-started-dnx.html)
   - [Outil pour convertir un projet MSTest en xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
* [NUnit](http://www.nunit.org/)
  - [Prise en main](https://github.com/nunit/docs/wiki/Installation)
  - [Billet de blog sur la migration de MSTest vers NUnit](http://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
* [MSTest](https://msdn.microsoft.com/library/ms243147.aspx)

## <a name="recommended-approach-to-porting"></a>Approche recommandée pour le portage

Enfin, le portage du code lui-même !  Au final, le travail de portage réel dépend fortement la structure de votre code .NET Framework.  Ceci dit, voici une approche recommandée qui peut bien fonctionner avec votre code base.

Une bonne façon de porter votre code est de commencer par la « base » de votre bibliothèque.  Il peut s’agir des modèles de données ou bien d’autres classes et méthodes fondamentales utilisées directement ou indirectement par tout le reste.

1. Portez le projet de test qui teste la couche de votre bibliothèque que vous portez actuellement.
2. Copiez la « base » de votre bibliothèque dans un nouveau projet .NET Core et sélectionnez la version de .NET Standard que vous voulez prendre en charge.
3. Apportez les modifications nécessaires pour obtenir le code à compiler.  La plupart de ces modifications peuvent nécessiter l’ajout de dépendances de package NuGet à votre fichier `project.json`.
4. Exécutez les tests et procédez aux ajustements nécessaires.
5. Sélectionnez la couche de code suivante à porter et répétez les étapes 2 et 3.

Si vous vous déplacez méthodiquement vers l’extérieur depuis la base de votre bibliothèque et que vous testez chaque couche selon ce qui est nécessaire, le portage devient un processus systématique où les problèmes sont isolés dans une seule couche de code à la fois.



<!--HONumber=Nov16_HO1-->


