---
title: "Hébergement de .NET Core"
description: "Hébergement du runtime .NET Core à partir du code natif"
keywords: ".NET, .NET Core, Hébergement, Hébergement de .NET Core"
author: mjrousos
ms.author: mikerou
ms.date: 2/3/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13edec8b-614d-47ed-9e95-ed6d3b94ec0c
ms.workload: dotnetcore
ms.openlocfilehash: 2f421c72e8099a328fbc255d51f77a9cd0724e58
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="hosting-net-core"></a>Hébergement de .NET Core

Comme tout code managé, les applications .NET Core sont exécutées par un hôte. L’hôte est chargé du démarrage du runtime (y compris des composants comme le JIT et le récupérateur de mémoire), de la création de domaines d’application et de l’appel de points d’entrée managés.

L’hébergement du runtime .NET Core est un scénario avancé et, dans la plupart des cas, les développeurs .NET Core n’ont pas à se soucier de l’hébergement, car les processus de génération .NET Core fournissent un hôte par défaut pour exécuter les applications .NET Core. Toutefois, dans certains cas spécifiques, il peut être utile d’héberger explicitement le runtime .NET Core, pour appeler le code managé dans un processus natif ou pour mieux contrôler le fonctionnement du runtime.

Cet article donne une vue d’ensemble des étapes nécessaires pour démarrer le runtime .NET Core à partir du code natif, créer un domaine d’application initial (<xref:System.AppDomain>) et y exécuter du code managé.

## <a name="prerequisites"></a>Prérequis

Comme les hôtes sont des applications natives, ce didacticiel aborde la construction d’une application C++ pour héberger .NET Core. Vous avez besoin d’un environnement de développement C++ (comme celui fourni par [Visual Studio](https://www.visualstudio.com/downloads/)).

Vous avez également besoin d’une application .NET Core simple pour tester l’hôte, vous devez donc installer le [SDK .NET Core](https://www.microsoft.com/net/core) et [créer une petite application de test .NET Core](../../core/tutorials/with-visual-studio.md) (par exemple, une application « Hello World »). L’application « Hello World » créée par le nouveau modèle de projet de console .NET Core est suffisante.

Ce didacticiel et son exemple associé génèrent un hôte Windows, mais nous vous recommandons de consulter les remarques à la fin de cet article concernant l’hébergement sur Unix.

## <a name="creating-the-host"></a>Création de l'hôte

Un [exemple d’hôte](https://github.com/dotnet/docs/tree/master/samples/core/hosting) illustrant les étapes décrites dans cet article est disponible dans le dépôt GitHub dotnet/docs. Les commentaires du fichier *host.cpp* de l’exemple associent clairement les étapes numérotées de ce didacticiel à l’endroit où elles sont exécutées dans l’exemple. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

N’oubliez pas que l’exemple d’hôte est destiné à être utilisé dans un contexte d’apprentissage, il ne s’attarde donc pas sur la vérification des erreurs et privilégie la lisibilité par rapport à l’efficacité. D’autres exemples d’hôtes réels sont disponibles dans le dépôt [dotnet/coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts). L’[hôte CoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun), en particulier, est un bon exemple d’hôte généraliste à étudier après avoir parcouru l’exemple simple.

### <a name="a-note-about-mscoreeh"></a>Remarque concernant mscoree.h
L’interface d’hébergement .NET Core principale (`ICLRRuntimeHost2`) est définie dans [MSCOREE. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Une version d’en-tête de ce fichier (mscoree.h), que votre hôte doit référencer, est produite via MIDL pendant la génération du [runtime .NET Core](https://github.com/dotnet/coreclr/). Si vous ne voulez pas générer le runtime .NET Core, mscoree.h est également disponible sous forme d’[en-tête prédéfini](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) dans le dépôt dotnet/coreclr. Des [instructions pour la génération du runtime .NET Core](https://github.com/dotnet/coreclr#building-the-repository) se trouvent dans le dépôt GitHub correspondant. 

### <a name="step-1---identify-the-managed-entry-point"></a>Étape 1 : Identifier le point d’entrée managé
Après avoir référencé les en-têtes nécessaires ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) et stdio.h, par exemple), l’une des premières choses que doit faire un hôte .NET Core est de localiser le point d’entrée managé à utiliser. Dans notre exemple d’hôte, il suffit de prendre le premier argument de ligne de commande de notre hôte comme chemin d’un fichier binaire managé dont la méthode `main` doit être exécutée.

[!code-cpp[NetCoreHost#1](../../../samples/core/hosting/host.cpp#1)]

### <a name="step-2---find-and-load-coreclrdll"></a>Étape 2 : Rechercher et charger CoreCLR.dll
Les API du runtime .NET Core se trouvent dans *CoreCLR.dll* (sur Windows). Pour obtenir l’interface d’hébergement (`ICLRRuntimeHost2`), vous devez rechercher et charger *CoreCLR.dll*. C’est à l’hôte de définir une convention de recherche de *CoreCLR.dll*. Certains hôtes s’attendent à trouver le fichier dans un emplacement connu sur l’ordinateur (par exemple, %programfiles%\dotnet\shared\Microsoft.NETCore.App\1.1.0). D’autres considèrent que *CoreCLR.dll* est chargé à partir d’un emplacement à côté de l’ordinateur lui-même ou de l’application à héberger. D’autres encore peuvent consulter une variable d’environnement pour rechercher la bibliothèque.

Sur Linux ou Mac, la bibliothèque de runtime principale est *libcoreclr.so* ou *libcoreclr.dylib*, respectivement.

Notre exemple d’hôte effectue la recherche dans certains emplacements courants pour *CoreCLR.dll*. Une fois le fichier trouvé, il doit être chargé via `LoadLibrary` (ou `dlopen` sur Linux/Mac).

[!code-cpp[NetCoreHost#2](../../../samples/core/hosting/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost2-instance"></a>Étape 3 : Obtenir une instance de ICLRRuntimeHost2
L’interface d’hébergement `ICLRRuntimeHost2` est récupérée en appelant `GetProcAddress` (ou `dlsym` sur Linux/Mac) sur `GetCLRRuntimeHost`, puis en appelant cette fonction. 

[!code-cpp[NetCoreHost#3](../../../samples/core/hosting/host.cpp#3)]

### <a name="step-4---setting-startup-flags-and-starting-the-runtime"></a>Étape 4 : Définir des indicateurs de démarrage et démarrer le runtime
Avec une interface `ICLRRuntimeHost2`, nous pouvons maintenant spécifier des indicateurs de démarrage pour le runtime et le démarrer. Les indicateurs de démarrage déterminent le récupérateur de mémoire à utiliser (concurrent ou serveur), s’il faut utiliser un ou plusieurs domaines d’application et la stratégie d’optimisation de chargeur à utiliser (pour le chargement d’assemblys indépendant du domaine).

[!code-cpp[NetCoreHost#4](../../../samples/core/hosting/host.cpp#4)]

Le runtime est démarré par un appel à la fonction `Start`.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Étape 5 : Préparer les paramètres AppDomain
Une fois le runtime démarré, nous devons configurer un AppDomain. Il existe un certain nombre d’options qui doivent être spécifiées pendant la création d’un AppDomain .NET, vous devez donc d’abord les préparer.

Les indicateurs AppDomain spécifient le comportement des domaines d’application en relation avec la sécurité et l’interopérabilité. Les anciens hôtes Silverlight utilisaient ces paramètres pour isoler le code utilisateur dans un bac à sable (sandbox), mais la plupart des hôtes .NET Core modernes exécutent le code utilisateur avec une confiance totale et activent l’interopérabilité.

[!code-cpp[NetCoreHost#5](../../../samples/core/hosting/host.cpp#5)]

Une fois que vous avez choisi les indicateurs AppDomain à utiliser, vous devez définir les propriétés AppDomain. Les propriétés sont des paires de chaînes clé/valeur. La plupart des propriétés gèrent la façon dont l’AppDomain charge les assemblys.

Propriétés AppDomain courantes :

* `TRUSTED_PLATFORM_ASSEMBLIES` Il s’agit d’une liste de chemins d’assemblys (séparés par « ; » sur Windows et « : » sur Unix) que l’AppDomain doit charger par ordre de priorité et à qui il doit accorder une confiance totale (même dans les domaines partiellement approuvés). Cette liste doit contenir des assemblys « Framework » et d’autres modules approuvés, similaires au Global Assembly Cache dans les scénarios .NET Framework. Certains hôtes placent toutes les bibliothèques à côté de *coreclr.dll* dans cette liste, d’autres ont des manifestes codés en dur qui répertorient les assemblys de confiance qui les concernent.
* `APP_PATHS` Il s’agit d’une liste de chemins où rechercher un assembly s’il est introuvable dans la liste TPA (liste d’assemblys de plateforme sécurisée). Ces chemins doivent correspondre à l’emplacement des assemblys d’utilisateurs. Dans un AppDomain bac à sable (sandbox), les assemblys chargés à partir de ces chemins ne reçoivent qu’une confiance partielle. Les chemins APP_PATH courants sont notamment le chemin à partir duquel l’application cible a été chargée ou d’autres emplacements où se trouvent généralement les ressources de l’utilisateur.
*  `APP_NI_PATHS` Cette liste est très similaire à APP_PATHS, sauf qu’il s’agit de chemins où rechercher des images natives.
*  `NATIVE_DLL_SEARCH_DIRECTORIES` Cette propriété est une liste de chemins où le chargeur doit rechercher les DLL natives appelées via p/invoke.
*  `PLATFORM_RESOURCE_ROOTS` Cette liste inclut des chemins où rechercher les assemblys satellites de ressources (dans les sous-répertoires spécifiques de la culture).
*  `AppDomainCompatSwitch` Cette chaîne spécifie les particularités de compatibilité qui doivent être utilisées pour les assemblys sans moniker de framework cible explicite (attribut de niveau assembly indiquant le framework dans lequel doit s’exécuter un assembly). En général, elle doit être définie sur `"UseLatestBehaviorWhenTFMNotSpecified"`, mais certains hôtes peuvent préférer obtenir d’anciennes particularités de compatibilité Silverlight ou Windows Phone à la place.

Dans notre [exemple d’hôte simple](https://github.com/dotnet/docs/tree/master/samples/core/hosting), ces propriétés sont configurées de la façon suivante :

[!code-cpp[NetCoreHost#6](../../../samples/core/hosting/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Étape 6 : Créer l’AppDomain
Une fois que tous les indicateurs et les propriétés AppDomain sont prêts, `ICLRRuntimeHost2::CreateAppDomainWithManager` peut être utilisé pour configurer l’AppDomain. Cette fonction prend éventuellement un nom d’assembly complet et un nom de type à utiliser comme gestionnaire AppDomain du domaine. Un gestionnaire AppDomain peut permettre à un hôte de contrôler certains aspects du comportement de l’AppDomain et peut fournir des points d’entrée pour le lancement du code managé si l’hôte ne souhaite pas directement appeler le code utilisateur.   

[!code-cpp[NetCoreHost#7](../../../samples/core/hosting/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Étape 7 : Exécuter le code managé.
Avec un AppDomain opérationnel, l’hôte peut maintenant exécuter du code managé. Le moyen le plus simple consiste à utiliser `ICLRRuntimeHost2::ExecuteAssembly` pour appeler la méthode de point d’entrée d’un assembly managé. Notez que cette fonction n’est valide que dans les scénarios de domaine unique.

[!code-cpp[NetCoreHost#8](../../../samples/core/hosting/host.cpp#8)]

Si `ExecuteAssembly` ne répond pas aux besoins de l’hôte, une autre option consiste à utiliser `CreateDelegate` pour créer un pointeur de fonction vers une méthode managée statique. Cette option implique que l’hôte connaisse la signature de la méthode qu’il appelle (afin de créer le type de pointeur de fonction), mais donne aux hôtes la possibilité d’appeler du code autre qu’un point d’entrée d’assembly.

```C++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
  domainId,
  L"HW, Version=1.0.0.0, Culture=neutral",  // Target managed assembly
  L"ConsoleApplication.Program",            // Target managed type
  L"Main",                                  // Target entry point (static method)
  (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a>Étape 8 : Nettoyer
Enfin, l’hôte doit effectuer un nettoyage en déchargeant les domaines d’application, en arrêtant le runtime et en libérant la référence `ICLRRuntimeHost2`.

[!code-cpp[NetCoreHost#9](../../../samples/core/hosting/host.cpp#9)]

## <a name="about-hosting-net-core-on-unix"></a>À propos de l’hébergement de .NET Core sur Unix
.NET Core est un produit multiplateforme qui s’exécute sur les systèmes d’exploitation Windows, Linux et Mac. Toutefois, les hôtes étant des applications natives, ils diffèrent les uns des autres selon la plateforme dont ils sont issus. Le processus, décrit ci-dessus, d’utilisation de `ICLRRuntimeHost2` pour démarrer le runtime, créer un AppDomain et exécuter le code managé doit fonctionner sur n’importe quel système d’exploitation pris en charge. Toutefois, les interfaces définies dans mscoree.h peuvent être lourdes à utiliser sur les plateformes Unix, car mscoree fait de nombreuses hypothèses Win32.

Pour faciliter l’hébergement sur les plateformes Unix, un ensemble de wrappers d’API d’hébergement plus indépendant de la plateforme est disponible dans [coreclrhost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h).

Un exemple d’utilisation de coreclrhost.h (au lieu de mscoree.h directement) peut être consulté dans l’[hôte UnixCoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts). La procédure d’utilisation des API de coreclrhost.h pour héberger le runtime est semblable à celle de mscoree.h :

1. Identifier le code managé à exécuter (à partir des paramètres de la ligne de commande, par exemple). 
2. Charger la bibliothèque CoreCLR.
    1. `dlopen("./libcoreclr.so", RTLD_NOW | RTLD_LOCAL);` 
3. Obtenir des pointeurs de fonction vers les fonctions `coreclr_initialize`, `coreclr_create_delegate`, `coreclr_execute_assembly` et `coreclr_shutdown` de CoreCLR à l’aide de `dlsym`
    1. `coreclr_initialize_ptr coreclr_initialize = (coreclr_initialize_ptr)dlsym(coreclrLib, "coreclr_initialize");`
4. Configurer les propriétés AppDomain (par exemple, la liste TPA). C’est la même étape que l’étape 5 du flux de travail mscoree, ci-dessus.
5. Utiliser `coreclr_initialize` pour démarrer le runtime et créer un AppDomain. Cette étape permet de créer également un pointeur `hostHandle` à utiliser dans les futurs appels d’hébergement.
    1. Notez que cette fonction exécute les rôles des étapes 4 et 6 du flux de travail précédent. 
6. Utiliser `coreclr_execute_assembly` ou `coreclr_create_delegate` pour exécuter le code managé. Ces fonctions sont analogues aux fonctions `ExecuteAssembly` et `CreateDelegate` de mscoree de l’étape 7 du flux de travail précédent.
7. Utiliser `coreclr_shutdown` pour décharger l’AppDomain et arrêter le runtime. 

## <a name="conclusion"></a>Conclusion
Une fois que votre hôte est créé, il peut être testé en l’exécutant à partir de la ligne de commande et en passant n’importe quel argument (comme l’application managée à exécuter) que l’hôte attend. Quand vous spécifiez l’application .NET Core que l’hôte doit exécuter, utilisez le fichier .dll généré par `dotnet build`. Les fichiers exécutables générés par `dotnet publish` pour les applications autonomes sont l’hôte .NET Core par défaut (pour que l’application puisse être lancée directement à partir de la ligne de commande dans les scénarios principaux) ; le code utilisateur est compilé dans un fichier dll du même nom. 

Si vous n’obtenez pas les résultats attendus, vérifiez que *coreclr.dll* est disponible dans l’emplacement attendu par l’hôte, que toutes les bibliothèques Framework nécessaires sont dans la liste TPA et que le nombre de bits de CoreCLR (32 ou 64 bits) correspond au mode de génération de l’hôte.

L’hébergement du runtime .NET Core est un scénario avancé sans utilité pour un grand nombre de développeurs, mais qui peut être très utile pour ceux qui doivent lancer du code managé à partir d’un processus natif ou qui ont besoin de davantage de contrôle sur le comportement du runtime .NET Core. Comme .NET Core est capable de s’exécuter côte à côte avec lui-même, il est même possible de créer des hôtes qui initialisent et démarrent plusieurs versions du runtime .NET Core et exécutent des applications sur chacun d'eux dans le même processus. 
