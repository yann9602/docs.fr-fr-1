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
# <a name="storing-application-secrets-safely-during-development"></a><span data-ttu-id="d1d3f-104">Le stockage des secrets de l’application en toute sécurité pendant le développement</span><span class="sxs-lookup"><span data-stu-id="d1d3f-104">Storing application secrets safely during development</span></span>

<span data-ttu-id="d1d3f-105">Pour vous connecter avec d’autres services et ressources protégées, les applications ASP.NET Core devront généralement utiliser des chaînes de connexion, les mots de passe ou autres informations d’identification qui contiennent des informations sensibles.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-105">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="d1d3f-106">Ces informations sensibles sont appelées *secrets*.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-106">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="d1d3f-107">Il est recommandé de ne pas inclure de secrets dans le code source et certainement ne pas pour stocker des secrets dans le contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-107">It is a best practice to not include secrets in source code and certainly not to store secrets in source control.</span></span> <span data-ttu-id="d1d3f-108">Au lieu de cela, vous devez utiliser le modèle de configuration ASP.NET Core pour lire les clés secrètes à partir des emplacements plus sécurisés.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-108">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="d1d3f-109">Vous devez séparer les secrets pour l’accès de développement et de mise en lots des ressources à partir de celles utilisées pour accéder aux ressources de production, étant donné que différents utilisateurs devront accéder à ces différents jeux de clés secrètes.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-109">You should separate the secrets for accessing development and staging resources from those used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="d1d3f-110">Pour stocker les secrets utilisés pendant le développement, les approches courantes sont soit stocker des clés secrètes dans les variables d’environnement ou à l’aide de l’outil Gestionnaire de Secret principal ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-110">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="d1d3f-111">Pour le stockage le plus sécurisé dans les environnements de production, microservices peut stocker des secrets dans un coffre de clés Azure.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-111">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="storing-secrets-in-environment-variables"></a><span data-ttu-id="d1d3f-112">Le stockage de secrets dans des variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="d1d3f-112">Storing secrets in environment variables</span></span>

<span data-ttu-id="d1d3f-113">Un moyen de maintenir les secrets de code source est destiné aux développeurs définir la chaîne en fonction des secrets en tant que [variables d’environnement](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) sur leurs ordinateurs de développement.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-113">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="d1d3f-114">Lorsque vous utilisez des variables d’environnement pour stocker des clés secrètes avec des noms hiérarchiques (ceux imbriqués dans les sections de configuration), créez un nom pour les variables d’environnement qui inclut la hiérarchie complète du nom de la clé secrète, délimité par des deux-points ( :).</span><span class="sxs-lookup"><span data-stu-id="d1d3f-114">When you use environment variables to store secrets with hierarchical names (those nested in configuration sections), create a name for the environment variables that includes the full hierarchy of the secret’s name, delimited with colons (:).</span></span>

<span data-ttu-id="d1d3f-115">Par exemple, définissant une variable d’environnement LogLevel:Default : l’enregistrement de débogage est équivalente à une valeur de configuration à partir du fichier JSON suivant :</span><span class="sxs-lookup"><span data-stu-id="d1d3f-115">For example, setting an environment variable Logging:LogLevel:Default to Debug would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="d1d3f-116">Pour accéder à ces valeurs à partir de variables d’environnement, l’application doit simplement appeler AddEnvironmentVariables sur son ConfigurationBuilder lors de la construction d’un objet IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-116">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="d1d3f-117">Notez que les variables d’environnement sont généralement stockés en texte brut, donc, si l’ordinateur ou un processus avec les variables d’environnement est compromise, les valeurs de variable d’environnement seront visibles.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-117">Note that environment variables are generally stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a><span data-ttu-id="d1d3f-118">Le stockage de secrets à l’aide du Gestionnaire de Secret principal ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d1d3f-118">Storing secrets using the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="d1d3f-119">Le cœur d’ASP.NET [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) outil fournit une autre méthode de conservation des secrets de code source.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-119">The ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="d1d3f-120">Pour utiliser l’outil Gestionnaire de clé secrète, inclure une référence d’outils (DotNetCliToolReference) au package Microsoft.Extensions.SecretManager.Tools dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-120">To use the Secret Manager tool, include a tools reference (DotNetCliToolReference) to the Microsoft.Extensions.SecretManager.Tools package in your project file.</span></span> <span data-ttu-id="d1d3f-121">Une fois cette dépendance n’est présente et a été restaurée, la commande de clés secrètes de l’utilisateur dotnet peut être utilisée pour définir la valeur de secrets à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-121">Once that dependency is present and has been restored, the dotnet user-secrets command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="d1d3f-122">Ces clés secrètes sont stockées dans un fichier JSON dans le répertoire du profil utilisateur (les détails varient par système d’exploitation), en s’éloignant de code source.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-122">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="d1d3f-123">Secrets définies par l’outil Gestionnaire de clé secrète sont organisés par la propriété UserSecretsId du projet qui utilise les clés secrètes.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-123">Secrets set by the Secret Manager tool are organized by the UserSecretsId property of the project that is using the secrets.</span></span> <span data-ttu-id="d1d3f-124">Par conséquent, veillez à définir la propriété UserSecretsId dans votre fichier projet (comme indiqué dans l’extrait de code ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="d1d3f-124">Therefore, you must be sure to set the UserSecretsId property in your project file (as shown in the snippet below).</span></span> <span data-ttu-id="d1d3f-125">La chaîne réelle utilisée comme l’ID n’est pas importante, tant qu’il est unique dans le projet.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-125">The actual string used as the ID is not important as long as it is unique in the project.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="d1d3f-126">À l’aide de clés secrètes stockées avec le Gestionnaire de secret principal dans une application s’effectue en appelant AddUserSecrets&lt;T&gt; sur l’instance ConfigurationBuilder pour inclure des secrets de l’application dans sa configuration.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-126">Using secrets stored with Secret Manager in an application is accomplished by calling AddUserSecrets&lt;T&gt; on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="d1d3f-127">Le paramètre générique T doit être un type à partir de l’assembly qui le UserSecretId a été appliqué à.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-127">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="d1d3f-128">Habituellement à l’aide de AddUserSecrets&lt;démarrage&gt; est correct.</span><span class="sxs-lookup"><span data-stu-id="d1d3f-128">Usually using AddUserSecrets&lt;Startup&gt; is fine.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d1d3f-129">[Précédente] (autorisation-net-microservices-web-applications.md) [suivant] (azure-key-coffre-protège-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="d1d3f-129">[Previous] (authorization-net-microservices-web-applications.md) [Next] (azure-key-vault-protects-secrets.md)</span></span>
