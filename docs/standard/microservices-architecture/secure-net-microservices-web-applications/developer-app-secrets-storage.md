---
title: "Le stockage des secrets de l’application en toute sécurité pendant le développement"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Le stockage des secrets de l’application en toute sécurité pendant le développement"
keywords: Docker, microservices, ASP.NET, conteneur
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f1b8b257a3e677c7e665e1d394a8adf7e651bec2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="storing-application-secrets-safely-during-development"></a>Le stockage des secrets de l’application en toute sécurité pendant le développement

Pour vous connecter avec d’autres services et ressources protégées, les applications ASP.NET Core devront généralement utiliser des chaînes de connexion, les mots de passe ou autres informations d’identification qui contiennent des informations sensibles. Ces informations sensibles sont appelées *secrets*. Il est recommandé de ne pas inclure de secrets dans le code source et certainement ne pas pour stocker des secrets dans le contrôle de code source. Au lieu de cela, vous devez utiliser le modèle de configuration ASP.NET Core pour lire les clés secrètes à partir des emplacements plus sécurisés.

Vous devez séparer les secrets pour l’accès de développement et de mise en lots des ressources à partir de celles utilisées pour accéder aux ressources de production, étant donné que différents utilisateurs devront accéder à ces différents jeux de clés secrètes. Pour stocker les secrets utilisés pendant le développement, les approches courantes sont soit stocker des clés secrètes dans les variables d’environnement ou à l’aide de l’outil Gestionnaire de Secret principal ASP.NET. Pour le stockage le plus sécurisé dans les environnements de production, microservices peut stocker des secrets dans un coffre de clés Azure.

## <a name="storing-secrets-in-environment-variables"></a>Le stockage de secrets dans des variables d’environnement

Un moyen de maintenir les secrets de code source est destiné aux développeurs définir la chaîne en fonction des secrets en tant que [variables d’environnement](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) sur leurs ordinateurs de développement. Lorsque vous utilisez des variables d’environnement pour stocker des clés secrètes avec des noms hiérarchiques (ceux imbriqués dans les sections de configuration), créez un nom pour les variables d’environnement qui inclut la hiérarchie complète du nom de la clé secrète, délimité par des deux-points ( :).

Par exemple, définissant une variable d’environnement LogLevel:Default : l’enregistrement de débogage est équivalente à une valeur de configuration à partir du fichier JSON suivant :

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Pour accéder à ces valeurs à partir de variables d’environnement, l’application doit simplement appeler AddEnvironmentVariables sur son ConfigurationBuilder lors de la construction d’un objet IConfigurationRoot.

Notez que les variables d’environnement sont généralement stockés en texte brut, donc, si l’ordinateur ou un processus avec les variables d’environnement est compromise, les valeurs de variable d’environnement seront visibles.

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a>Le stockage de secrets à l’aide du Gestionnaire de Secret principal ASP.NET

Le cœur d’ASP.NET [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) outil fournit une autre méthode de conservation des secrets de code source. Pour utiliser l’outil Gestionnaire de clé secrète, inclure une référence d’outils (DotNetCliToolReference) au package Microsoft.Extensions.SecretManager.Tools dans votre fichier projet. Une fois cette dépendance n’est présente et a été restaurée, la commande de clés secrètes de l’utilisateur dotnet peut être utilisée pour définir la valeur de secrets à partir de la ligne de commande. Ces clés secrètes sont stockées dans un fichier JSON dans le répertoire du profil utilisateur (les détails varient par système d’exploitation), en s’éloignant de code source.

Secrets définies par l’outil Gestionnaire de clé secrète sont organisés par la propriété UserSecretsId du projet qui utilise les clés secrètes. Par conséquent, veillez à définir la propriété UserSecretsId dans votre fichier projet (comme indiqué dans l’extrait de code ci-dessous). La chaîne réelle utilisée comme l’ID n’est pas importante, tant qu’il est unique dans le projet.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

À l’aide de clés secrètes stockées avec le Gestionnaire de secret principal dans une application s’effectue en appelant AddUserSecrets&lt;T&gt; sur l’instance ConfigurationBuilder pour inclure des secrets de l’application dans sa configuration. Le paramètre générique T doit être un type à partir de l’assembly qui le UserSecretId a été appliqué à. Habituellement à l’aide de AddUserSecrets&lt;démarrage&gt; est correct.


>[!div class="step-by-step"]
[Précédente] (autorisation-net-microservices-web-applications.md) [suivant] (azure-key-coffre-protège-secrets.md)
