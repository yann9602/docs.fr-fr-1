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
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="fbce9-104">Sur les autorisations dans .NET microservices et les applications web</span><span class="sxs-lookup"><span data-stu-id="fbce9-104">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="fbce9-105">Après l’authentification et des API Web ASP.NET Core devez autoriser l’accès.</span><span class="sxs-lookup"><span data-stu-id="fbce9-105">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="fbce9-106">Ce processus permet à un service rendre les API disponibles pour certains utilisateurs authentifiés, mais pas à l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="fbce9-106">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="fbce9-107">[Autorisation](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) peut être basé sur les rôles d’utilisateurs ou selon une stratégie personnalisée, qui peut-être inclure en inspectant les revendications ou autres heuristiques.</span><span class="sxs-lookup"><span data-stu-id="fbce9-107">[Authorization](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="fbce9-108">Restreindre l’accès à un itinéraire ASP.NET MVC de base est aussi simple que l’application d’un attribut de l’autoriser à la méthode d’action (ou à la classe du contrôleur si les actions de tous les du contrôleur requièrent une autorisation), comme l’exemple suivant montre :</span><span class="sxs-lookup"><span data-stu-id="fbce9-108">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="fbce9-109">Par défaut, ajout d’un attribut Authorize sans paramètres limitera l’accès aux utilisateurs authentifiés pour ce contrôleur ou d’action.</span><span class="sxs-lookup"><span data-stu-id="fbce9-109">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="fbce9-110">Pour limiter davantage une API pour le rendre disponible pour des utilisateurs spécifiques, l’attribut peut être étendu pour spécifier les rôles requis ou des stratégies que les utilisateurs doivent satisfaire.</span><span class="sxs-lookup"><span data-stu-id="fbce9-110">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implementing-role-based-authorization"></a><span data-ttu-id="fbce9-111">Implémentation de l’autorisation basée sur les rôles</span><span class="sxs-lookup"><span data-stu-id="fbce9-111">Implementing role-based authorization</span></span>

<span data-ttu-id="fbce9-112">Identité de ASP.NET Core a un concept intégré de rôles.</span><span class="sxs-lookup"><span data-stu-id="fbce9-112">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="fbce9-113">En plus des utilisateurs, ASP.NET Core Identity stocke des informations sur les différents rôles utilisés par l’application et effectue le suivi de quels utilisateurs sont affectés à des rôles.</span><span class="sxs-lookup"><span data-stu-id="fbce9-113">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="fbce9-114">Ces assignations peuvent être modifiées par programmation avec le type RoleManager (qui met à jour des rôles dans le stockage persistant) et le type de UserManager (qui permettre affecter ou supprimer l’affectation d’utilisateurs à partir de rôles).</span><span class="sxs-lookup"><span data-stu-id="fbce9-114">These assignments can be changed programmatically with the RoleManager type (which updates roles in persisted storage) and UserManager type (which can assign or unassign users from roles).</span></span>

<span data-ttu-id="fbce9-115">Si vous vous authentifiez avec jetons de support JSON, l’intergiciel d’authentification de support ASP.NET Core JWT remplira les rôles d’un utilisateur basés sur les revendications de rôle trouvées dans le jeton.</span><span class="sxs-lookup"><span data-stu-id="fbce9-115">If you are authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="fbce9-116">Pour limiter l’accès à une action MVC ou d’un contrôleur pour les utilisateurs des rôles spécifiques, vous pouvez inclure un paramètre de rôles dans l’en-tête Authorize, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="fbce9-116">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize header, as shown in the following example:</span></span>

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

<span data-ttu-id="fbce9-117">Dans cet exemple, seuls les utilisateurs aux rôles administrateur ou PowerUser peuvent accéder aux API dans le contrôleur du Panneau de configuration (par exemple, l’exécution de l’action SetTime).</span><span class="sxs-lookup"><span data-stu-id="fbce9-117">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="fbce9-118">L’API d’arrêt est encore limitée pour autoriser l’accès uniquement aux utilisateurs dans le rôle d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="fbce9-118">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="fbce9-119">Pour exiger un utilisateur dans plusieurs rôles, vous utilisez plusieurs attributs d’autoriser, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="fbce9-119">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="fbce9-120">Dans cet exemple, pour appeler API1, un utilisateur doit :</span><span class="sxs-lookup"><span data-stu-id="fbce9-120">In this example, to call API1, a user must:</span></span>

-   <span data-ttu-id="fbce9-121">Dans l’administrateur *ou* PowerUser rôle, *et*</span><span class="sxs-lookup"><span data-stu-id="fbce9-121">Be in the Adminstrator *or* PowerUser role, *and*</span></span>

-   <span data-ttu-id="fbce9-122">Dans le rôle RemoteEmployee, *et*</span><span class="sxs-lookup"><span data-stu-id="fbce9-122">Be in the RemoteEmployee role, *and*</span></span>

-   <span data-ttu-id="fbce9-123">Remplir un gestionnaire personnalisé pour l’autorisation de CustomPolicy.</span><span class="sxs-lookup"><span data-stu-id="fbce9-123">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implementing-policy-based-authorization"></a><span data-ttu-id="fbce9-124">Implémentation de l’autorisation basée sur des stratégies</span><span class="sxs-lookup"><span data-stu-id="fbce9-124">Implementing policy-based authorization</span></span>

<span data-ttu-id="fbce9-125">Règles d’autorisation personnalisés peuvent également être écrites à l’aide de [stratégies d’autorisation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="fbce9-125">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="fbce9-126">Dans cette section, nous fournissons une vue d’ensemble.</span><span class="sxs-lookup"><span data-stu-id="fbce9-126">In this section we provide an overview.</span></span> <span data-ttu-id="fbce9-127">Plus de détails est disponible en ligne [atelier d’autorisation ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="fbce9-127">More detail is available in the online [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="fbce9-128">Stratégies d’autorisation personnalisées sont inscrits dans la méthode Startup.ConfigureServices à l’aide du service. Méthode de AddAuthorization.</span><span class="sxs-lookup"><span data-stu-id="fbce9-128">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="fbce9-129">Cette méthode prend un délégué qui configure un argument AuthorizationOptions.</span><span class="sxs-lookup"><span data-stu-id="fbce9-129">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="fbce9-130">Comme indiqué dans l’exemple, les stratégies peuvent être associés à différents types d’exigences.</span><span class="sxs-lookup"><span data-stu-id="fbce9-130">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="fbce9-131">Une fois inscrits, les stratégies peuvent être appliquées à une action ou d’un contrôleur en passant un nom de la stratégie en tant que l’argument de la stratégie de l’attribut Authorize (par exemple, \[Authorize(Policy="EmployeesOnly")\]) des stratégies peuvent avoir. plusieurs exigences, pas un seul (comme indiqué dans ces exemples).</span><span class="sxs-lookup"><span data-stu-id="fbce9-131">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, \[Authorize(Policy="EmployeesOnly")\]) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="fbce9-132">Dans l’exemple précédent, le premier appel AddPolicy est simplement une autre façon d’autorisation par rôle.</span><span class="sxs-lookup"><span data-stu-id="fbce9-132">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="fbce9-133">Si \[Authorize(Policy="AdministratorsOnly")\] est appliqué à une API, seuls les utilisateurs du rôle d’administrateur seront en mesure d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="fbce9-133">If \[Authorize(Policy="AdministratorsOnly")\] is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="fbce9-134">Le deuxième appel AddPolicy montre un moyen simple pour exiger qu’une demande de remboursement particulier doit être présent pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fbce9-134">The second AddPolicy call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="fbce9-135">La méthode RequireClaim accepte également les valeurs attendues pour la revendication.</span><span class="sxs-lookup"><span data-stu-id="fbce9-135">The RequireClaim method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="fbce9-136">Si les valeurs sont spécifiées, la condition est remplie uniquement si l’utilisateur dispose à la fois une revendication du type correct et qu’une des valeurs spécifiées.</span><span class="sxs-lookup"><span data-stu-id="fbce9-136">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="fbce9-137">Si vous utilisez l’intergiciel d’authentification de support JSON, toutes les propriétés JSON seront accessible en tant que revendications de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fbce9-137">If you are using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="fbce9-138">La stratégie plus intéressante indiquée ici est la troisième méthode AddPolicy, car elle utilise une demande d’autorisation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="fbce9-138">The most interesting policy shown here is in the third AddPolicy method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="fbce9-139">À l’aide des spécifications d’autorisation personnalisée, vous pouvez avoir beaucoup de contrôle sur la façon dont l’autorisation est effectuée.</span><span class="sxs-lookup"><span data-stu-id="fbce9-139">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="fbce9-140">Pour ce faire, vous devez implémenter ces types :</span><span class="sxs-lookup"><span data-stu-id="fbce9-140">For this to work, you must implement these types:</span></span>

-   <span data-ttu-id="fbce9-141">Un type de configuration requise qui dérive de IAuthorizationRequirement et qui contient les champs spécifiant les détails de la demande.</span><span class="sxs-lookup"><span data-stu-id="fbce9-141">A Requirements type that derives from IAuthorizationRequirement and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="fbce9-142">Dans l’exemple, il s’agit d’un champ d’expiration pour le type de MinimumAgeRequirement exemple.</span><span class="sxs-lookup"><span data-stu-id="fbce9-142">In the example, this is an age field for the sample MinimumAgeRequirement type.</span></span>

-   <span data-ttu-id="fbce9-143">Un gestionnaire qui implémente AuthorizationHandler&lt;T&gt;, où T est le type de IAuthorizationRequirement le gestionnaire peut satisfaire.</span><span class="sxs-lookup"><span data-stu-id="fbce9-143">A handler that implements AuthorizationHandler&lt;T&gt;, where T is the type of IAuthorizationRequirement that the handler can satisfy.</span></span> <span data-ttu-id="fbce9-144">Le gestionnaire doit implémenter la méthode HandleRequirementAsync, qui vérifie si un contexte spécifié qui contient des informations sur l’utilisateur répond à l’exigence.</span><span class="sxs-lookup"><span data-stu-id="fbce9-144">The handler must implement the HandleRequirementAsync method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="fbce9-145">Si l’utilisateur répond à la spécification, un appel au contexte. Réussir va indiquer que l’utilisateur est autorisé.</span><span class="sxs-lookup"><span data-stu-id="fbce9-145">If the user meets the requirement, a call to context.Succeed will indicate that the user is authorized.</span></span> <span data-ttu-id="fbce9-146">S’il existe plusieurs méthodes pour qu’un utilisateur peut satisfaire une demande d’autorisation, plusieurs gestionnaires peuvent être créés.</span><span class="sxs-lookup"><span data-stu-id="fbce9-146">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="fbce9-147">En plus de l’inscription des exigences de la stratégie personnalisée avec les appels de AddPolicy, vous devez également enregistrer des gestionnaires de demande personnalisée via l’Injection de dépendances (services. AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span><span class="sxs-lookup"><span data-stu-id="fbce9-147">In addition to registering custom policy requirements with AddPolicy calls, you also need to register custom requirement handlers via Dependency Injection (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span></span>

<span data-ttu-id="fbce9-148">Un exemple d’une exigence d’autorisation personnalisée et un gestionnaire pour la vérification de l’âge d’un utilisateur (en fonction d’une revendication DateOfBirth) est disponible dans le noyau ASP.NET [documentation de l’autorisation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="fbce9-148">An example of a custom authorization requirement and handler for checking a user’s age (based on a DateOfBirth claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fbce9-149">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="fbce9-149">Additional resources</span></span>

-   <span data-ttu-id="fbce9-150">**L’authentification ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="fbce9-150">**ASP.NET Core Authentication**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="fbce9-151">**Autorisation de ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span><span class="sxs-lookup"><span data-stu-id="fbce9-151">**ASP.NET Core Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span></span>

-   <span data-ttu-id="fbce9-152">**Autorisation basée sur les rôles**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span><span class="sxs-lookup"><span data-stu-id="fbce9-152">**Role based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span></span>

-   <span data-ttu-id="fbce9-153">**D’autorisation personnalisée basée sur des stratégies**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span><span class="sxs-lookup"><span data-stu-id="fbce9-153">**Custom Policy-Based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="fbce9-154">[Précédente] (index.md) [suivant] (développeur-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="fbce9-154">[Previous] (index.md) [Next] (developer-app-secrets-storage.md)</span></span>
