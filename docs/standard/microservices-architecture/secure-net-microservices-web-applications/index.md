---
title: "Sécurisation des microservices .NET et des applications web"
description: "Architecture des microservices .NET pour les applications .NET en conteneur | Sécurisation des microservices .NET et des applications web"
keywords: Docker, microservices, ASP.NET, conteneur
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 147aa099e440f5e5eb1dd6450946274aef91033a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="securing-net-microservices-and-web-applications"></a>Sécurisation des microservices .NET et des applications web

Il est souvent nécessaire de limiter l’accès aux ressources et aux API exposées par un service à certains utilisateurs ou clients approuvés. La première étape d’une telle décision d’approbation au niveau des API passe par l’authentification. L’authentification est le processus qui consiste à vérifier de manière fiable l’identité d’un utilisateur.

Dans les scénarios de microservice, l’authentification est généralement gérée de façon centralisée. Si vous utilisez une passerelle d’API, celle-ci est parfaitement indiquée pour l’authentification, comme l’illustre la figure 11-1. Si vous utilisez cette approche, vérifiez que les différents microservices ne sont pas directement accessibles (sans la passerelle d’API), à moins qu’un dispositif de sécurité supplémentaire ait été mis en place pour authentifier les messages en provenance ou non de la passerelle.

![](./media/image1.png)

**Figure 11-1** : authentification centralisée avec une passerelle d’API

Si les services sont directement accessibles, il est possible d’authentifier les utilisateurs à l’aide d’un service d’authentification comme Azure Active Directory ou un microservice d’authentification dédié faisant office de service d’émission jeton de sécurité (STS). Les décisions d’approbation sont partagées entre les services au moyen de jetons de sécurité ou de cookies. (Elles peuvent être partagées entre applications, si nécessaire, dans ASP.NET Core avec les [services de protection des données](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Ce modèle est illustré dans la figure 11-2.

![](./media/image2.png)

**(Figure 11-2)** : authentification par un microservice d’identité ; l’approbation est partagée à l’aide d’un jeton d’autorisation

## <a name="authenticating-using-aspnet-core-identity"></a>Authentification à l’aide d’ASP.NET Core Identity

Dans ASP.NET Core, le principal mécanisme d’identification des utilisateurs d’une application est le système d’appartenance [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity). ASP.NET Core Identity stocke les informations utilisateur (notamment les informations de connexion, les rôles et les revendications) dans un magasin de données configuré par le développeur. En règle générale, le magasin de données d’ASP.NET Core Identity est un magasin Entity Framework fourni avec le package Microsoft.AspNetCore.Identity.EntityFrameworkCore. Cependant, il est possible d’utiliser des magasins personnalisés ou d’autres packages tiers pour stocker les informations d’identité dans le Stockage Table Azure, DocumentDB ou à d’autres emplacements.

Le code ci-dessous est extrait du modèle de projet d’application web ASP.NET Core avec l’authentification de compte d’utilisateur individuel sélectionnée. Il montre comment configurer ASP.NET Core Identity en utilisant EntityFramework.Core dans la méthode Startup.ConfigureServices.

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

Une fois ASP.NET Core Identity configuré, il convient de l’activer en appelant app.UseIdentity dans la méthode Startup.Configure du service.

L’utilisation d’ASP.NET Code Identity autorise plusieurs scénarios :

-   Création d’informations utilisateur à l’aide du type UserManager (userManager.CreateAsync).

-   Authentification des utilisateurs à l’aide du type SignInManager. Vous pouvez utiliser signInManager.SignInAsync pour permettre aux utilisateurs de se connecter directement ou signInManager.PasswordSignInAsync pour vérifier que leur mot de passe est correct avant de les connecter.

-   Identification d’un utilisateur en fonction des informations stockées dans un cookie (qui est lu par l’intergiciel ASP.NET Core Identity) de telle sorte que les requêtes suivantes d’un navigateur incluent l’identité et les revendications de l’utilisateur connecté.

Par ailleurs, ASP.NET Core Identity prend en charge l’[authentification à deux facteurs](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).

Pour les scénarios d’authentification qui utilisent un magasin de données utilisateur local et qui conservent l’identité entre les requêtes au moyen de cookies (comme c’est généralement le cas avec les applications web MVC), ASP.NET Core Identity est une solution recommandée.

## <a name="authenticating-using-external-providers"></a>Authentification à l’aide de fournisseurs externes

ASP.NET Core prend aussi en charge l’utilisation de [fournisseurs d’authentification externes](https://docs.microsoft.com/aspnet/core/security/authentication/social/) pour permettre aux utilisateurs de se connecter via des flux [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2). Cela signifie que les utilisateurs peuvent se connecter en utilisant les processus d’authentification existants de certains fournisseurs tels que Microsoft, Google, Facebook ou Twitter et associer ces identités à une identité ASP.NET Core dans votre application.

Pour utiliser l’authentification externe, vous devez intégrer l’intergiciel (middleware) d’authentification approprié au pipeline de traitement des requêtes HTTP de votre application. Cet intergiciel est chargé de gérer les requêtes pour retourner les itinéraires d’URI du fournisseur d’authentification, capturant ainsi les informations d’identité et les mettant à disposition via la méthode SignInManager.GetExternalLoginInfo.

Les fournisseurs d’authentification externes courants et les packages NuGet qui leur sont associés vous sont présentés ci-dessous.

**Microsoft :** Microsoft.AspNetCore.Authentication.MicrosoftAccount

**Google :** Microsoft.AspNetCore.Authentication.Google

**Facebook :** Microsoft.AspNetCore.Authentication.Facebook

**Twitter :** Microsoft.AspNetCore.Authentication.Twitter

Dans tous les cas, l’intergiciel est inscrit avec un appel à une méthode d’inscription similaire à app.Use{ExternalProvider}Authentication dans Startup.Configure. Ces méthodes d’inscription prennent un objet d’options qui contient un ID d’application et des informations confidentielles (par exemple, un mot de passe), selon les besoins du fournisseur. Les fournisseurs d’authentification externes exigent l’inscription des applications (comme expliqué dans la [documentation ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) de façon à faire savoir aux utilisateurs quelle application demande l’accès à leur identité.

Une fois que l’intergiciel est inscrit dans Startup.Configure, vous pouvez inviter les utilisateurs à se connecter à partir de n’importe quelle action de contrôleur. Pour ce faire, vous devez créer un objet AuthenticationProperties contenant le nom du fournisseur d’authentification et une URL de redirection. Retournez ensuite une réponse de test qui transmet l’objet AuthenticationProperties. Le code ci-dessous illustre cela.

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

Le paramètre redirectUrl comprend l’URL vers laquelle le fournisseur externe doit rediriger l’utilisateur une fois celui-ci authentifié. L’URL doit représenter une action qui va connecter l’utilisateur à partir d’informations d’identité externes, comme dans l’exemple simplifié ci-dessous :

```csharp
// Sign in the user with this external login provider if the user
// already has a login.
var result = await _signInManager.ExternalLoginSignInAsync(info.LoginProvider, info.ProviderKey, isPersistent: false);

if (result.Succeeded)
{
    return RedirectToLocal(returnUrl);
}
else
{
    ApplicationUser newUser = new ApplicationUser
    {
        // The user object can be constructed with claims from the
        // external authentication provider, combined with information
        // supplied by the user after they have authenticated with
        // the external provider.
        UserName = info.Principal.FindFirstValue(ClaimTypes.Name),
        Email = info.Principal.FindFirstValue(ClaimTypes.Email)
    };
    var identityResult = await _userManager.CreateAsync(newUser);
    if (identityResult.Succeeded)
    {
        identityResult = await _userManager.AddLoginAsync(newUser, info);
        if (identityResult.Succeeded)
        {
            await _signInManager.SignInAsync(newUser, isPersistent: false);
        }
        return RedirectToLocal(returnUrl);
    }
}
```

Si vous optez pour l’option d’authentification **Compte d’utilisateur individuel** au moment de créer le projet d’application web ASP.NET Code dans Visual Studio, l’ensemble du code nécessaire à la connexion avec un fournisseur externe est déjà présent dans le projet, comme le montre la figure 11-3.

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

**(Figure 11-3)** : sélection d’une option visant à utiliser l’authentification externe pendant la création d’un projet d’application web

Outre les fournisseurs d’authentification externe mentionnés ci-dessus, il existe des packages tiers qui proposent un intergiciel permettant l’utilisation d’un nombre bien plus important de fournisseurs d’authentification externe. Pour obtenir la liste, consultez le dépôt [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) sur GitHub.

Bien entendu, vous pouvez aussi créer votre propre intergiciel d’authentification externe.

## <a name="authenticating-with-bearer-tokens"></a>Authentification avec des jetons du porteur

L’authentification avec ASP.NET Core Identity (ou Identity couplé à des fournisseurs d’authentification externe) est parfaitement adaptée à de nombreux scénarios d’application web dans lesquels il est approprié de stocker les informations utilisateur dans un cookie. En revanche, dans d’autres scénarios, il n’est pas commun de conserver et de transmettre les données au moyen de cookies.

Par exemple, dans une API web ASP.NET Core qui expose les points de terminaison RESTful potentiellement accessibles par des applications à page unique, des clients natifs, voire d’autres API web, l’authentification par jeton du porteur est généralement privilégiée. Les applications de ce type n’utilisent pas de cookies, mais elles peuvent facilement récupérer un jeton du porteur et l’inclure dans l’en-tête d’autorisation des requêtes suivantes. Pour activer l’authentification par jeton, ASP.NET Core prend en charge plusieurs options en vue d’utiliser [OAuth 2.0](https://oauth.net/2/) et [OpenID Connect](http://openid.net/connect/).

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a>Authentification avec un fournisseur d’identité OpenID Connect ou OAuth 2.0

Si les informations utilisateur sont stockées dans Azure Active Directory ou une autre solution d’identité qui prend en charge OpenID Connect ou OAuth 2.0, vous pouvez utiliser le package Microsoft.AspNetCore.Authentication.OpenIdConnect pour une authentification à l’aide du flux de travail OpenID Connect. Par exemple, pour s’[authentifier auprès d’Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), une application web ASP.NET Core peut utiliser l’intergiciel de ce package, comme dans l’exemple suivant :

```csharp
// Configure the OWIN pipeline to use OpenID Connect auth
app.UseOpenIdConnectAuthentication(new OpenIdConnectOptions
{
    ClientId = Configuration["AzureAD:ClientId"],
    Authority = String.Format(Configuration["AzureAd:AadInstance"],
    Configuration["AzureAd:Tenant"]),
    ResponseType = OpenIdConnectResponseType.IdToken,
    PostLogoutRedirectUri = Configuration["AzureAd:PostLogoutRedirectUri"]
});
```

Les valeurs de configuration sont les valeurs d’Azure Active Directory créées au moment où votre application est [inscrite en tant que client Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad). Un même ID client peut être partagé entre plusieurs microservices d’une application s’ils doivent tous authentifier les utilisateurs authentifiés via Azure Active Directory.

Notez que lorsque vous utilisez ce flux de travail, l’intergiciel ASP.NET Core Identity n’est pas nécessaire dans la mesure où le stockage des informations utilisateur et l’authentification sont assurés par Azure Active Directory.

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a>Émission de jetons de sécurité à partir d’un service ASP.NET Core

Si vous préférez émettre des jetons de sécurité pour les utilisateurs locaux d’ASP.NET Core Identity plutôt que de faire appel à un fournisseur d’identité externe, vous pouvez profiter de quelques bibliothèques intéressantes.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) et [OpenIddict](https://github.com/openiddict/openiddict-core) sont des fournisseurs OpenID Connect qui s’intègrent facilement à ASP.NET Core Identity pour vous permettre d’émettre des jetons de sécurité à partir d’un service ASP.NET Core. La [documentation IdentityServer4](https://identityserver4.readthedocs.io/en/release/) explique en détail comment utiliser la bibliothèque. Ceci étant, voici sommairement comment émettre des jetons à l’aide d’IdentityServer4 :

1.  Appelez app.UseIdentityServer dans la méthode Startup.Configure pour ajouter IdentityServer4 au pipeline de traitement des requêtes HTTP de l’application. Cela permet à la bibliothèque de remettre les requêtes aux points de terminaison OpenID Connect et OAuth2 comme connect/token.

2.  Configurez IdentityServer4 dans Startup.ConfigureServices en effectuant un appel à services.AddIdentityServer.

3.  Configurez le serveur d’identité en fournissant les données suivantes :

-   Les [informations d’identification](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) à utiliser pour la signature.

-   Les [ressources d’identité et d’API](https://identityserver4.readthedocs.io/en/release/topics/resources.html) auxquelles les utilisateurs pourraient demander à accéder :

<!-- -->

-   Les ressources d’API représentent les données protégées ou les fonctionnalités auxquelles un utilisateur peut accéder avec un jeton d’accès. Par exemple, il peut s’agit d’une API web (ou un ensemble d’API) qui nécessite une autorisation.

-   Les ressources d’identité représentent les informations (revendications) qui sont fournies à un client pour identifier un utilisateur. Les revendications peuvent inclure le nom d’utilisateur, l’adresse de messagerie, etc.

<!-- -->

-   Les [clients](https://identityserver4.readthedocs.io/en/release/topics/clients.html) appelés à se connecter pour demander des jetons.

-   Le mécanisme de stockage des informations de l’utilisateur, tel que [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) ou une solution équivalente.

Au moment de spécifier les clients et les ressources que doit utiliser IdentityServer4, vous pouvez transmettre une collection IEnumerable&lt;T&gt; du type approprié aux méthodes qui acceptent les magasins de clients ou de ressources en mémoire. Pour les scénarios plus complexes, vous pouvez aussi indiquer des types de fournisseurs de clients ou de ressources via l’injection de dépendances.

Voici un exemple de configuration qui vise à faire utiliser à IdentityServer4 les ressources et les clients en mémoire fournis par un type IClientStore personnalisé :

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a>Utilisation de jetons de sécurité

L’authentification auprès d’un point de terminaison OpenID Connect ou l’émission de vos propres jetons de sécurité recouvrent certains scénarios. Mais qu’en est-il d’un service qui doit simplement limiter l’accès aux utilisateurs disposant de jetons de sécurité valides qui ont été fournis par un autre service ?

Pour ce scénario, l’intergiciel d’authentification qui gère les jetons JWT est disponible dans le package Microsoft.AspNetCore.Authentication.JwtBearer. JWT est l’acronyme de « [JSON Web Token](https://tools.ietf.org/html/rfc7519) » (jeton web JSON). Il s’agit d’un format de jeton de sécurité courant (défini par la norme RFC 7519) destiné à communiquer les revendications de sécurité. L’exemple simple présenté ci-dessous montre comment utiliser les jetons de ce type avec l’intergiciel. Ce code doit précéder les appels à l’intergiciel ASP.NET Core MVC (appn.UseMvc).

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

Les paramètres utilisés dans ce cas sont les suivants :

-   Audience représente le récepteur du jeton entrant ou la ressource à laquelle le jeton accorde l’accès. Si la valeur spécifiée dans ce paramètre ne correspond pas à celle du paramètre aud du jeton, celui-ci est rejeté.

-   Authority est l’adresse du serveur d’authentification émetteur de jetons. L’intergiciel d’authentification du porteur de jeton JWT utilise cet URI pour obtenir la clé publique qui permet de valider la signature du jeton. Par ailleurs, l’intergiciel vérifie que la valeur du paramètre iss du jeton correspond à cet URI.

-   AutomaticAuthenticate est une valeur booléenne qui indique si l’utilisateur défini par le jeton doit être connecté automatiquement.

Un autre paramètre, RequireHttpsMetadata, n’est pas utilisé dans cet exemple. Il est utile pour les tests ; la valeur false est affectée à ce paramètre pour effectuer des tests dans des environnements dépourvus de certificats. Dans les déploiements réels, les jetons du porteur JWT doivent toujours être transmis uniquement sur HTTPS.

Quand cet intergiciel est en place, les jetons JWT sont automatiquement extraits des en-têtes d’autorisation. Ils sont ensuite désérialisés, validés (en utilisant les valeurs des paramètres Audience et Authority) puis stockés en tant qu’informations utilisateur pour être référencées par la suite par des actions MVC ou des filtres d’autorisation.

L’intergiciel d’authentification du porteur JWT peut aussi prendre en charge des scénarios plus avancés, tels que l’utilisation d’un certificat local pour valider un jeton si l’autorité n’est pas disponible. Pour ce scénario, vous pouvez spécifier un objet TokenValidationParameters dans l’objet JwtBearerOptions.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Partage de cookies entre applications**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)

-   **Présentation d’Identity**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Rick Anderson. Authentification à deux facteurs par SMS**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)

-   **Activation de l’authentification via Facebook, Google et d’autres fournisseurs externes**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)

-   **Michell Anicas. An Introduction to OAuth 2**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

-   **AspNet.Security.OAuth.Providers** (dépôt GitHub pour fournisseurs d’autorisation OAuth ASP.NET :
    [*https://github.com/ASPNET-contrib/ASPNET.Security.OAuth.Providers/Tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src))

-   **Danny Strockis. Intégration d’Azure AD à une application web ASP.NET Core**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

-   **IdentityServer4. Documentation officielle**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)


>[!div class="step-by-step"]
[Précédent] (../implement-resilient-applications/monitor-app-health.md) [Suivant] (authorization-net-microservices-web-applications.md)
