---
title: "Portage vers .NET Core - Utilisation du pack de compatibilité Windows"
description: "Découvrez le pack de compatibilité Windows et comment l’utiliser pour déplacer du code .NET Framework existant vers .NET Core"
keywords: ".NET, .NET Core, Windows, compatibilité"
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 3b1fe02aad4f78499158ecb7fa9b8521cb7d992e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="using-the-windows-compatibility-pack"></a>Utilisation du pack de compatibilité Windows

L’un des problèmes les plus courants auxquels les développeurs sont confrontés lors du portage de leur code existant vers .NET Core est qu’ils dépendent des API et des technologies qui existent uniquement dans le .NET Framework. Le *pack de compatibilité Windows* se rapporte à la mise à disposition d’un grand nombre de ces technologies afin que la création d’applications .NET Core et de bibliothèques .NET Standard devienne beaucoup plus viable pour le code existant.

Ce package est une [extension logique de.NET Standard 2.0](../whats-new/index.md#api-changes-and-library-support) qui augmente considérablement l’ensemble d’API et le code existant est compilé sans presque aucune modification. Toutefois, pour respecter l’engagement de .NET Standard (« il s’agit de l’ensemble d’API fourni par toutes les implémentations .NET »), cela ne comprend pas les technologies qui ne peuvent pas fonctionner sur toutes les plateformes, telles que le Registre, WMI (Windows Management Instrumentation), ou les API d’émission de réflexion.

Le *pack de compatibilité Windows* repose sur .NET Standard et permet d’accéder aux technologies Windows uniquement. Il est particulièrement utile pour les clients qui veulent passer à .NET Core, mais envisagent de rester sur Windows pour commencer. Dans ce scénario, le fait de ne pas pouvoir utiliser les technologies Windows uniquement est juste un obstacle à la migration sans aucun avantage en matière d’architecture.

## <a name="package-contents"></a>Contenu du package

Le *pack de compatibilité Windows* est fourni via le package NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) et peut être référencé à partir de projets ciblant .NET Core ou .NET Standard.

Il fournit environ 20 000 API, dont des API Windows uniquement ainsi des API multiplateformes des domaines technologiques suivants :

* Pages de codes
* CodeDom
* Configuration
* Services d'annuaire
* Dessin
* ODBC
* Autorisations
* Ports
* Listes de contrôle d’accès Windows
* Windows Communication Foundation (WCF)
* Chiffrement Windows
* Journal des événements Windows
* WMI (Windows Management Instrumentation)
* Compteurs de performances Windows
* Registre Windows
* Mise en cache Windows Runtime
* services Windows

Pour plus d’informations, consultez la [spécification du pack de compatibilité](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Prise en main

1. Avant le portage, veillez à examiner le [processus de portage](index.md).

2. Lors du portage du code existant vers .NET Core ou .NET Standard, installez le package NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

3. Si vous souhaitez rester sur Windows, vous êtes prêt.

4. Si vous souhaitez exécuter l’application .NET Core ou la bibliothèque .NET Standard sur Linux ou macOS, utilisez [l’analyseur d’API](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) pour trouver l’usage des API qui ne fonctionnent pas sur toutes les plateformes.

5. Supprimez les usages de ces API, remplacez-les par des alternatives multiplateformes ou protégez-les à l’aide d’une vérification de la plateforme, par exemple :

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

Pour obtenir une démonstration, regardez la [vidéo de Channel 9 sur le pack de compatibilité Windows](https://channel9.msdn.com/Events/Connect/2017/T123).

