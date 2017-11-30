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
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="8c770-104">À l’aide d’Azure Key Vault pour protéger les clés secrètes au moment de la production</span><span class="sxs-lookup"><span data-stu-id="8c770-104">Using Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="8c770-105">Secrets stockés en tant que variables d’environnement ou par l’outil Gestionnaire de la clé secrète sont toujours stockés localement et non chiffrés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8c770-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="8c770-106">Une option plus sécurisée pour le stockage des clés secrètes est [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), qui fournit un emplacement central pour le stockage des clés et les secrets sécurisé.</span><span class="sxs-lookup"><span data-stu-id="8c770-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="8c770-107">Le package Microsoft.Extensions.Configuration.AzureKeyVault permet à une application ASP.NET Core lire les informations de configuration d’Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="8c770-107">The Microsoft.Extensions.Configuration.AzureKeyVault package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="8c770-108">Pour commencer à utiliser des secrets à partir d’un coffre de clés Azure, vous procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8c770-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

<span data-ttu-id="8c770-109">Tout d’abord, inscrire votre application comme une application Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8c770-109">First, register your application as an Azure AD application.</span></span> <span data-ttu-id="8c770-110">(Accès à des coffres de clé est géré par Azure AD). Cela est possible via le portail de gestion Azure.</span><span class="sxs-lookup"><span data-stu-id="8c770-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>

<span data-ttu-id="8c770-111">Si vous souhaitez que votre application pour s’authentifier à l’aide d’un certificat au lieu d’un secret de mot de passe ou client, vous pouvez également utiliser le [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) applet de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c770-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="8c770-112">Le certificat que vous inscrivez avec Azure Key Vault doit uniquement votre clé publique.</span><span class="sxs-lookup"><span data-stu-id="8c770-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="8c770-113">(Votre application utilisera la clé privée).</span><span class="sxs-lookup"><span data-stu-id="8c770-113">(Your application will use the private key.)</span></span>

<span data-ttu-id="8c770-114">En second lieu, donnez à l’accès de l’application inscrite dans le coffre de clés en créant une nouvelle entité de service.</span><span class="sxs-lookup"><span data-stu-id="8c770-114">Second, give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="8c770-115">Pour cela, à l’aide des commandes PowerShell suivantes :</span><span class="sxs-lookup"><span data-stu-id="8c770-115">You can do this using the following PowerShell commands:</span></span>

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

<span data-ttu-id="8c770-116">Troisièmement, incluent le coffre de clés comme source de configuration dans votre application en appelant la méthode d’extension IConfigurationBuilder.AddAzureKeyVault lorsque vous créez une instance de IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="8c770-116">Third, include the key vault as a configuration source in your application by calling the IConfigurationBuilder.AddAzureKeyVault extension method when you create an IConfigurationRoot instance.</span></span> <span data-ttu-id="8c770-117">Notez que l’appel AddAzureKeyVault nécessite l’ID d’application qui a été enregistré et obtiennent un accès pour le coffre de clés dans les étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="8c770-117">Note that calling AddAzureKeyVault will require the application ID that was registered and given access to the key vault in the previous steps.</span></span>

  <span data-ttu-id="8c770-118">Actuellement, .NET Standard et .NET Core prennent en charge l’obtention des informations de configuration à partir d’un coffre de clés Azure à l’aide d’un ID client et la clé secrète du client.</span><span class="sxs-lookup"><span data-stu-id="8c770-118">Currently, .NET Standard and .NET Core support getting configuration information from an Azure Key Vault using a client ID and client secret.</span></span> <span data-ttu-id="8c770-119">Les applications .NET framework peuvent utiliser une surcharge de IConfigurationBuilder.AddAzureKeyVault qui accepte un certificat à la place de la clé secrète du client.</span><span class="sxs-lookup"><span data-stu-id="8c770-119">.NET Framework applications can use an overload of IConfigurationBuilder.AddAzureKeyVault that takes a certificate in place of the client secret.</span></span> <span data-ttu-id="8c770-120">À ce jour, le travail est [en cours d’exécution](https://github.com/aspnet/Configuration/issues/605) pour rendre cette surcharge disponible dans .NET Standard Edition et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c770-120">As of this writing, work is [in progress](https://github.com/aspnet/Configuration/issues/605) to make that overload available in .NET Standard and .NET Core.</span></span> <span data-ttu-id="8c770-121">Jusqu'à ce que la surcharge AddAzureKeyVault qui accepte qu'un certificat est disponible, les applications ASP.NET Core peuvent accéder à un coffre de clés Azure avec l’authentification basée sur certificat en créant explicitement un objet KeyVaultClient, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8c770-121">Until the AddAzureKeyVault overload that accepts a certificate is available, ASP.NET Core applications can access an Azure Key Vault with certificate-based authentication by explicitly creating a KeyVaultClient object, as shown in the following example:</span></span>

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

<span data-ttu-id="8c770-122">Dans cet exemple, l’appel à AddAzureKeyVault est fourni à la fin de l’inscription du fournisseur de configuration.</span><span class="sxs-lookup"><span data-stu-id="8c770-122">In this example, the call to AddAzureKeyVault comes at the end of configuration provider registration.</span></span> <span data-ttu-id="8c770-123">Il est plus pratique d’enregistrer le coffre de clés Azure en tant que le dernier fournisseur de configuration afin qu’il ait la possibilité de remplacer les valeurs de configuration à partir des fournisseurs précédents, et afin qu’aucune valeur de configuration à partir d’autres sources ne remplacent celles du coffre de clés.</span><span class="sxs-lookup"><span data-stu-id="8c770-123">It is a best practice to register Azure Key Vault as the last configuration provider so that it has an opportunity to override configuration values from previous providers, and so that no configuration values from other sources override those from the key vault.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8c770-124">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="8c770-124">Additional resources</span></span>

-   <span data-ttu-id="8c770-125">**À l’aide d’Azure Key Vault pour protéger la confidentialité de l’application**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span><span class="sxs-lookup"><span data-stu-id="8c770-125">**Using Azure Key Vault to protect application secrets**
[*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span></span>

-   <span data-ttu-id="8c770-126">**Stockage sécurisé des secrets d’application pendant le développement**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="8c770-126">**Safe storage of app secrets during development**
[*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span></span>

-   <span data-ttu-id="8c770-127">**Configuration de la protection des données**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span><span class="sxs-lookup"><span data-stu-id="8c770-127">**Configuring data protection**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span></span>

-   <span data-ttu-id="8c770-128">**Gestion et la durée de vie de la clé**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#protection des données-paramètres par défaut*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span><span class="sxs-lookup"><span data-stu-id="8c770-128">**Key management and lifetime**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span></span>

-   <span data-ttu-id="8c770-129">**Microsoft.Extensions.Configuration.DockerSecrets.**</span><span class="sxs-lookup"><span data-stu-id="8c770-129">**Microsoft.Extensions.Configuration.DockerSecrets.**</span></span> <span data-ttu-id="8c770-130">Référentiel GitHub.</span><span class="sxs-lookup"><span data-stu-id="8c770-130">GitHub repo.</span></span>
    [<span data-ttu-id="8c770-131">*https://github.com/ASPNET/configuration/Tree/dev/src/Microsoft.extensions.Configuration.DockerSecrets*</span><span class="sxs-lookup"><span data-stu-id="8c770-131">*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*</span></span>](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
<span data-ttu-id="8c770-132">[Précédente] (developer-app-secrets-storage.md) [suivant] (.. / takeaways.md de clé)</span><span class="sxs-lookup"><span data-stu-id="8c770-132">[Previous] (developer-app-secrets-storage.md) [Next] (../key-takeaways.md)</span></span>
