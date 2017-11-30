---
title: "Conception de la couche d’application microservice et l’API Web"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Conception de la couche d’application microservice et l’API Web"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7509b470a30005dd48fa88eefa91f7ed241e4e09
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="8fccb-104">Conception de la couche d’application microservice et l’API Web</span><span class="sxs-lookup"><span data-stu-id="8fccb-104">Designing the microservice application layer and Web API</span></span>

## <a name="using-solid-principles-and-dependency-injection"></a><span data-ttu-id="8fccb-105">À l’aide de solides principes et Injection de dépendance</span><span class="sxs-lookup"><span data-stu-id="8fccb-105">Using SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="8fccb-106">Principes de solides sont critiques techniques à utiliser dans des applications modernes et critiques, tels que le développement d’un microservice avec des modèles de DDD.</span><span class="sxs-lookup"><span data-stu-id="8fccb-106">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="8fccb-107">SOLIDE est l’acronyme groupes cinq des principes fondamentaux :</span><span class="sxs-lookup"><span data-stu-id="8fccb-107">SOLID is an acronym that groups five fundamental principles:</span></span>

-   <span data-ttu-id="8fccb-108">Principe de responsabilité unique</span><span class="sxs-lookup"><span data-stu-id="8fccb-108">Single Responsibility principle</span></span>

-   <span data-ttu-id="8fccb-109">Principe d’ouverture/fermeture</span><span class="sxs-lookup"><span data-stu-id="8fccb-109">Open/closed principle</span></span>

-   <span data-ttu-id="8fccb-110">Principe de substitution de Liskov</span><span class="sxs-lookup"><span data-stu-id="8fccb-110">Liskov substitution principle</span></span>

-   <span data-ttu-id="8fccb-111">Principe d’inversion de la segmentation</span><span class="sxs-lookup"><span data-stu-id="8fccb-111">Inversion Segregation principle</span></span>

-   <span data-ttu-id="8fccb-112">Principe d’Inversion de dépendance</span><span class="sxs-lookup"><span data-stu-id="8fccb-112">Dependency Inversion principle</span></span>

<span data-ttu-id="8fccb-113">SOLIDE est plus sur la façon dont vous concevez votre application ou les couches interne de microservice et découplage des dépendances entre eux.</span><span class="sxs-lookup"><span data-stu-id="8fccb-113">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="8fccb-114">Il n’est pas lié au domaine, mais à la conception technique de l’application.</span><span class="sxs-lookup"><span data-stu-id="8fccb-114">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="8fccb-115">Le principe final, le principe d’Inversion de dépendance (DI), vous permet de découpler la couche d’infrastructure du reste des couches, ce qui permet une implémentation de mieux découplée des couches DDD.</span><span class="sxs-lookup"><span data-stu-id="8fccb-115">The final principle, the Dependency Inversion (DI) principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="8fccb-116">DI est une façon d’implémenter le principe d’Inversion de dépendance.</span><span class="sxs-lookup"><span data-stu-id="8fccb-116">DI is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="8fccb-117">Il est une technique de couplage lâche entre les objets et leurs dépendances.</span><span class="sxs-lookup"><span data-stu-id="8fccb-117">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="8fccb-118">Au lieu d’instancier directement des collaborateurs, ou à l’aide de références statiques, les objets dont une classe a besoin pour effectuer ses actions sont fournies à (ou « injecter ») la classe.</span><span class="sxs-lookup"><span data-stu-id="8fccb-118">Rather than directly instantiating collaborators, or using static references, the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="8fccb-119">En règle générale, les classes déclarer leurs dépendances via leur constructeur, ce qui leur permet de respecter le principe de dépendances explicites.</span><span class="sxs-lookup"><span data-stu-id="8fccb-119">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="8fccb-120">DI est généralement basée sur des conteneurs d’Inversion de contrôle (IoC) spécifiques.</span><span class="sxs-lookup"><span data-stu-id="8fccb-120">DI is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="8fccb-121">ASP.NET Core fournit un simple conteneur inversion de contrôle intégré, mais vous pouvez également utiliser votre conteneur IoC favoris, tels que Autofac ou Ninject.</span><span class="sxs-lookup"><span data-stu-id="8fccb-121">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="8fccb-122">En suivant les principes solides, vos classes tendent naturellement être petit, bien factorisée et facilement testées.</span><span class="sxs-lookup"><span data-stu-id="8fccb-122">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="8fccb-123">Mais comment vous saurez si trop de dépendances sont en cours injectées dans vos classes ?</span><span class="sxs-lookup"><span data-stu-id="8fccb-123">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="8fccb-124">Si vous utilisez DI via le constructeur, il sera facile de détecter qu’en examinant le nombre de paramètres pour votre constructeur.</span><span class="sxs-lookup"><span data-stu-id="8fccb-124">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="8fccb-125">S’il y a trop de dépendances, il s’agit généralement d’un signe (un [code odeur](http://deviq.com/code-smells/)) que votre classe essaie de faire de façon trop importante et probablement viole le principe de responsabilité unique.</span><span class="sxs-lookup"><span data-stu-id="8fccb-125">If there are too many dependencies, this is generally a sign (a [code smell](http://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="8fccb-126">Il faudrait un autre guide pour couvrir solide en détail.</span><span class="sxs-lookup"><span data-stu-id="8fccb-126">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="8fccb-127">Par conséquent, ce guide vous oblige à ont des connaissances minimales des rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="8fccb-127">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="8fccb-128">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="8fccb-128">Additional resources</span></span>

-   <span data-ttu-id="8fccb-129">**SOLIDE : Principes de programmation orientée objet fondamentaux**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span><span class="sxs-lookup"><span data-stu-id="8fccb-129">**SOLID: Fundamental OOP Principles**
[*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span></span>

-   <span data-ttu-id="8fccb-130">**Inversion des conteneurs de contrôle et le modèle d’Injection de dépendances**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span><span class="sxs-lookup"><span data-stu-id="8fccb-130">**Inversion of Control Containers and the Dependency Injection pattern**
[*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span></span>

-   <span data-ttu-id="8fccb-131">**Steve Smith. Nouveaux est de type Glue**
    [*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span><span class="sxs-lookup"><span data-stu-id="8fccb-131">**Steve Smith. New is Glue**
[*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="8fccb-132">[Précédente] (nosql-base de données-persistance-infrastructure.md) [suivant] (microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="8fccb-132">[Previous] (nosql-database-persistence-infrastructure.md) [Next] (microservice-application-layer-implementation-web-api.md)</span></span>
