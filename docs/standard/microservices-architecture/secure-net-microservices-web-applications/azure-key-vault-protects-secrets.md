---
title: "À l’aide d’Azure Key Vault pour protéger les clés secrètes au moment de la production"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | À l’aide d’Azure Key Vault pour protéger les clés secrètes au moment de la production"
keywords: Docker, microservices, ASP.NET, conteneur
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7f922997e8d0c63e206cd68f4efda14985c86b72
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a>À l’aide d’Azure Key Vault pour protéger les clés secrètes au moment de la production

Secrets stockés en tant que variables d’environnement ou par l’outil Gestionnaire de la clé secrète sont toujours stockés localement et non chiffrés sur l’ordinateur. Une option plus sécurisée pour le stockage des clés secrètes est [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), qui fournit un emplacement central pour le stockage des clés et les secrets sécurisé.

Le package Microsoft.Extensions.Configuration.AzureKeyVault permet à une application ASP.NET Core lire les informations de configuration d’Azure Key Vault. Pour commencer à utiliser des secrets à partir d’un coffre de clés Azure, vous procédez comme suit :

Tout d’abord, inscrire votre application comme une application Azure AD. (Accès à des coffres de clé est géré par Azure AD). Cela est possible via le portail de gestion Azure.

Si vous souhaitez que votre application pour s’authentifier à l’aide d’un certificat au lieu d’un secret de mot de passe ou client, vous pouvez également utiliser le [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) applet de commande PowerShell. Le certificat que vous inscrivez avec Azure Key Vault doit uniquement votre clé publique. (Votre application utilisera la clé privée).

En second lieu, donnez à l’accès de l’application inscrite dans le coffre de clés en créant une nouvelle entité de service. Pour cela, à l’aide des commandes PowerShell suivantes :

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

Troisièmement, incluent le coffre de clés comme source de configuration dans votre application en appelant la méthode d’extension IConfigurationBuilder.AddAzureKeyVault lorsque vous créez une instance de IConfigurationRoot. Notez que l’appel AddAzureKeyVault nécessite l’ID d’application qui a été enregistré et obtiennent un accès pour le coffre de clés dans les étapes précédentes.

  Actuellement, .NET Standard et .NET Core prennent en charge l’obtention des informations de configuration à partir d’un coffre de clés Azure à l’aide d’un ID client et la clé secrète du client. Les applications .NET framework peuvent utiliser une surcharge de IConfigurationBuilder.AddAzureKeyVault qui accepte un certificat à la place de la clé secrète du client. À ce jour, le travail est [en cours d’exécution](https://github.com/aspnet/Configuration/issues/605) pour rendre cette surcharge disponible dans .NET Standard Edition et .NET Core. Jusqu'à ce que la surcharge AddAzureKeyVault qui accepte qu'un certificat est disponible, les applications ASP.NET Core peuvent accéder à un coffre de clés Azure avec l’authentification basée sur certificat en créant explicitement un objet KeyVaultClient, comme indiqué dans l’exemple suivant :

```csharp
// Configure Key Vault client
var kvClient = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(async
    (authority, resource, scope) =>
    {
        var cert = // Get certificate from local store/file/key vault etc. as needed
        // From the Microsoft.IdentityModel.Clients.ActiveDirectory pacakge
        var authContext = new AuthenticationContext(authority,
            TokenCache.DefaultShared);
        var result = await authContext.AcquireTokenAsync(resource,
            // From the Microsoft.Rest.ClientRuntime.Azure.Authentication pacakge
            new ClientAssertionCertificate("{Application ID}", cert));
        return result.AccessToken;
    }));

    // Get configuration values from Key Vault
    var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        // Other configuration providers go here.
        .AddAzureKeyVault("{KeyValueUri}", kvClient,
        new DefaultKeyVaultSecretManager());
```

Dans cet exemple, l’appel à AddAzureKeyVault est fourni à la fin de l’inscription du fournisseur de configuration. Il est plus pratique d’enregistrer le coffre de clés Azure en tant que le dernier fournisseur de configuration afin qu’il ait la possibilité de remplacer les valeurs de configuration à partir des fournisseurs précédents, et afin qu’aucune valeur de configuration à partir d’autres sources ne remplacent celles du coffre de clés.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **À l’aide d’Azure Key Vault pour protéger la confidentialité de l’application**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)

-   **Stockage sécurisé des secrets d’application pendant le développement**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)

-   **Configuration de la protection des données**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)

-   **Gestion et la durée de vie de la clé**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#protection des données-paramètres par défaut*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

-   **Microsoft.Extensions.Configuration.DockerSecrets.** Référentiel GitHub.
    [*https://github.com/ASPNET/configuration/Tree/dev/src/Microsoft.extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
[Précédente] (developer-app-secrets-storage.md) [suivant] (.. / takeaways.md de clé)
