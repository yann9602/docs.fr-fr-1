---
title: "Portage vers le .NET Core - le Pack de compatibilité de Windows"
description: "En savoir plus sur le Pack de compatibilité de Windows et comment utiliser pour porter du code .NET Framework existant vers le .NET Core"
keywords: ".NET, .NET core, Windows, compatibilité"
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 5094baee77aba4d1e148f807d842a4a2d3405cf7
ms.sourcegitcommit: 86cf9b4c7104485a9870645705b9a1a4b6ca8e2b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2017
---
# <a name="using-the-windows-compatibility-pack"></a>Le Pack de compatibilité de Windows

Un des problèmes plus courants auxquels les développeurs sont confrontés lors du portage de leur code existant vers le .NET Core est que celles-ci dépendent API et des technologies qui existent uniquement dans le .NET Framework. Le *Pack de compatibilité Windows* est sur la fourniture de ces technologies, afin que la création d’applications de base de .NET, ainsi que les bibliothèques .NET Standard redevient beaucoup plus de code existant.

Ce package est un opérateur logique [extension Standard de .NET 2.0](../whats-new/index.md#api-changes-and-library-support) que considérablement ensemble d’API augmente et le code existant se compile presque sans modification. Mais pour maintenir la promesse de .NET Standard (« il est le jeu d’API qui permettent de toutes les implémentations de .NET »), cela n’a pas été inclut des technologies qui peuvent ne pas fonctionner sur toutes les plateformes, telles que le Registre, Windows Management Instrumentation (WMI), ou l’émission de réflexion API.

Le *Pack de compatibilité Windows* reposant sur .NET Standard et donne accès aux technologies Windows uniquement. Il est particulièrement utile pour les clients want déplacer vers le .NET Core mais plan à rester sur Windows en tant que première étape. Dans ce scénario, n’est ne pas en mesure d’utiliser les technologies Windows uniquement est uniquement un obstacle migration avec zéro avantages architecturales.

## <a name="package-contents"></a>Contenu du package

Le *Pack de compatibilité Windows* est fourni via le NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) et peut être référencée à partir de projets ciblant .NET Core ou .NET Standard.

Il fournit environ 20 000 API, y compris les API Windows uniquement, ainsi qu’inter-plateformes dans les domaines technologiques suivants :

* Pages de codes
* CodeDom
* Configuration
* Services d'annuaire
* dessin
* ODBC
* Autorisations
* Ports
* Listes de contrôle d’accès (ACL) Windows
* Windows Communication Foundation (WCF)
* Chiffrement de Windows
* Journal des événements Windows
* WMI (Windows Management Instrumentation)
* Compteurs de performances Windows
* Registre Windows
* La mise en cache du Runtime Windows
* services Windows

Pour plus d’informations, consultez la [spec du pack de compatibilité](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Prise en main

1. Avant de porter, veillez à examiner le [processus de portage](index.md).

2. Lors du portage du code existant vers .NET Core ou .NET Standard, installez le package NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

3. Si vous souhaitez rester sur Windows, vous êtes prêt.

4. Si vous souhaitez exécuter l’application .NET Core ou une bibliothèque .NET Standard sur Linux ou macOS, utilisez le [API analyseur](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) pour rechercher l’utilisation des API qui ne fonctionne pas inter-plateformes.

5. Supprimez les utilisations de ces API, remplacez-les par inter-plateformes alternatives ou protéger à l’aide d’une vérification de la plateforme, telles que :

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

Pour une démonstration, passez en revue les [vidéo de Channel 9 du Pack de compatibilité Windows](https://channel9.msdn.com/Events/Connect/2017/T123).

