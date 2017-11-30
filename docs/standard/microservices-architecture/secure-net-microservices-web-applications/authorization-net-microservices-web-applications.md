---
title: Sur les autorisations dans .NET microservices et les applications web
description: Architecture de Microservices .NET pour les Applications .NET en conteneur | Sur les autorisations dans .NET microservices et les applications web
keywords: Docker, microservices, ASP.NET, conteneur
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 51adda4f5bdb28154f17b9a988ee2d887bf1d461
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>Sur les autorisations dans .NET microservices et les applications web

Après l’authentification et des API Web ASP.NET Core devez autoriser l’accès. Ce processus permet à un service rendre les API disponibles pour certains utilisateurs authentifiés, mais pas à l’ensemble. [Autorisation](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) peut être basé sur les rôles d’utilisateurs ou selon une stratégie personnalisée, qui peut-être inclure en inspectant les revendications ou autres heuristiques.

Restreindre l’accès à un itinéraire ASP.NET MVC de base est aussi simple que l’application d’un attribut de l’autoriser à la méthode d’action (ou à la classe du contrôleur si les actions de tous les du contrôleur requièrent une autorisation), comme l’exemple suivant montre :

```csharp
public class AccountController : Controller
{
    public ActionResult Login()
    {
    }

    [Authorize]
    public ActionResult Logout()
    {
    }
}
```

Par défaut, ajout d’un attribut Authorize sans paramètres limitera l’accès aux utilisateurs authentifiés pour ce contrôleur ou d’action. Pour limiter davantage une API pour le rendre disponible pour des utilisateurs spécifiques, l’attribut peut être étendu pour spécifier les rôles requis ou des stratégies que les utilisateurs doivent satisfaire.

## <a name="implementing-role-based-authorization"></a>Implémentation de l’autorisation basée sur les rôles

Identité de ASP.NET Core a un concept intégré de rôles. En plus des utilisateurs, ASP.NET Core Identity stocke des informations sur les différents rôles utilisés par l’application et effectue le suivi de quels utilisateurs sont affectés à des rôles. Ces assignations peuvent être modifiées par programmation avec le type RoleManager (qui met à jour des rôles dans le stockage persistant) et le type de UserManager (qui permettre affecter ou supprimer l’affectation d’utilisateurs à partir de rôles).

Si vous vous authentifiez avec jetons de support JSON, l’intergiciel d’authentification de support ASP.NET Core JWT remplira les rôles d’un utilisateur basés sur les revendications de rôle trouvées dans le jeton. Pour limiter l’accès à une action MVC ou d’un contrôleur pour les utilisateurs des rôles spécifiques, vous pouvez inclure un paramètre de rôles dans l’en-tête Authorize, comme indiqué dans l’exemple suivant :

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
public class ControlPanelController : Controller
{
    public ActionResult SetTime()
    {
    }

    [Authorize(Roles = "Administrator")]
    public ActionResult ShutDown()
    {
    }
}
```

Dans cet exemple, seuls les utilisateurs aux rôles administrateur ou PowerUser peuvent accéder aux API dans le contrôleur du Panneau de configuration (par exemple, l’exécution de l’action SetTime). L’API d’arrêt est encore limitée pour autoriser l’accès uniquement aux utilisateurs dans le rôle d’administrateur.

Pour exiger un utilisateur dans plusieurs rôles, vous utilisez plusieurs attributs d’autoriser, comme indiqué dans l’exemple suivant :

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

Dans cet exemple, pour appeler API1, un utilisateur doit :

-   Dans l’administrateur *ou* PowerUser rôle, *et*

-   Dans le rôle RemoteEmployee, *et*

-   Remplir un gestionnaire personnalisé pour l’autorisation de CustomPolicy.

## <a name="implementing-policy-based-authorization"></a>Implémentation de l’autorisation basée sur des stratégies

Règles d’autorisation personnalisés peuvent également être écrites à l’aide de [stratégies d’autorisation](https://docs.asp.net/en/latest/security/authorization/policies.html). Dans cette section, nous fournissons une vue d’ensemble. Plus de détails est disponible en ligne [atelier d’autorisation ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Stratégies d’autorisation personnalisées sont inscrits dans la méthode Startup.ConfigureServices à l’aide du service. Méthode de AddAuthorization. Cette méthode prend un délégué qui configure un argument AuthorizationOptions.

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("AdministratorsOnly", policy =>
        policy.RequireRole("Administrator"));
    options.AddPolicy("EmployeesOnly", policy =>
        policy.RequireClaim("EmployeeNumber"));
    options.AddPolicy("Over21", policy =>
        policy.Requirements.Add(new MinimumAgeRequirement(21)));
});
```

Comme indiqué dans l’exemple, les stratégies peuvent être associés à différents types d’exigences. Une fois inscrits, les stratégies peuvent être appliquées à une action ou d’un contrôleur en passant un nom de la stratégie en tant que l’argument de la stratégie de l’attribut Authorize (par exemple, \[Authorize(Policy="EmployeesOnly")\]) des stratégies peuvent avoir. plusieurs exigences, pas un seul (comme indiqué dans ces exemples).

Dans l’exemple précédent, le premier appel AddPolicy est simplement une autre façon d’autorisation par rôle. Si \[Authorize(Policy="AdministratorsOnly")\] est appliqué à une API, seuls les utilisateurs du rôle d’administrateur seront en mesure d’y accéder.

Le deuxième appel AddPolicy montre un moyen simple pour exiger qu’une demande de remboursement particulier doit être présent pour l’utilisateur. La méthode RequireClaim accepte également les valeurs attendues pour la revendication. Si les valeurs sont spécifiées, la condition est remplie uniquement si l’utilisateur dispose à la fois une revendication du type correct et qu’une des valeurs spécifiées. Si vous utilisez l’intergiciel d’authentification de support JSON, toutes les propriétés JSON seront accessible en tant que revendications de l’utilisateur.

La stratégie plus intéressante indiquée ici est la troisième méthode AddPolicy, car elle utilise une demande d’autorisation personnalisée. À l’aide des spécifications d’autorisation personnalisée, vous pouvez avoir beaucoup de contrôle sur la façon dont l’autorisation est effectuée. Pour ce faire, vous devez implémenter ces types :

-   Un type de configuration requise qui dérive de IAuthorizationRequirement et qui contient les champs spécifiant les détails de la demande. Dans l’exemple, il s’agit d’un champ d’expiration pour le type de MinimumAgeRequirement exemple.

-   Un gestionnaire qui implémente AuthorizationHandler&lt;T&gt;, où T est le type de IAuthorizationRequirement le gestionnaire peut satisfaire. Le gestionnaire doit implémenter la méthode HandleRequirementAsync, qui vérifie si un contexte spécifié qui contient des informations sur l’utilisateur répond à l’exigence.

Si l’utilisateur répond à la spécification, un appel au contexte. Réussir va indiquer que l’utilisateur est autorisé. S’il existe plusieurs méthodes pour qu’un utilisateur peut satisfaire une demande d’autorisation, plusieurs gestionnaires peuvent être créés.

En plus de l’inscription des exigences de la stratégie personnalisée avec les appels de AddPolicy, vous devez également enregistrer des gestionnaires de demande personnalisée via l’Injection de dépendances (services. AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).

Un exemple d’une exigence d’autorisation personnalisée et un gestionnaire pour la vérification de l’âge d’un utilisateur (en fonction d’une revendication DateOfBirth) est disponible dans le noyau ASP.NET [documentation de l’autorisation](https://docs.asp.net/en/latest/security/authorization/policies.html).

## <a name="additional-resources"></a>Ressources supplémentaires

-   **L’authentification ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Autorisation de ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)

-   **Autorisation basée sur les rôles**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)

-   **D’autorisation personnalisée basée sur des stratégies**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)




>[!div class="step-by-step"]
[Précédente] (index.md) [suivant] (développeur-app-secrets-storage.md)
