---
title: Test des services ASP.NET principaux et les applications web
description: Architecture de Microservices .NET pour les Applications .NET en conteneur | Test des services ASP.NET principaux et les applications web
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f756a679befee676db2bf6d402fd7e34b1621b9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="c1d1f-104">Test des services ASP.NET principaux et les applications web</span><span class="sxs-lookup"><span data-stu-id="c1d1f-104">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="c1d1f-105">Contrôleurs sont un élément central de tout service ASP.NET Core API et l’application Web ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-105">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="c1d1f-106">Par conséquent, vous devez avoir confiance qu’ils se comportent comme prévu pour votre application.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-106">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="c1d1f-107">Tests automatisés peuvent vous fournir cette confiance et peuvent détecter les erreurs avant qu’ils atteignent la production.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-107">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="c1d1f-108">Vous devez tester le contrôleur de comporte en fonction des entrées valides ou non valides et de tester les réponses du contrôleur en fonction du résultat de l’opération métier qu’il effectue.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-108">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="c1d1f-109">Toutefois, vous devez avoir ces types de tests votre microservices :</span><span class="sxs-lookup"><span data-stu-id="c1d1f-109">However, you should have these types of tests your microservices:</span></span>

-   <span data-ttu-id="c1d1f-110">Tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-110">Unit tests.</span></span> <span data-ttu-id="c1d1f-111">Ceux-ci assurent que les composants individuels de l’application fonctionnent comme prévu.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-111">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="c1d1f-112">Assertions de tester l’API du composant.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-112">Assertions test the component API.</span></span>

-   <span data-ttu-id="c1d1f-113">Tests d’intégration.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-113">Integration tests.</span></span> <span data-ttu-id="c1d1f-114">Ceux-ci assurent que les interactions entre les composants fonctionnent comme prévu en fonction des artefacts externes tels que des bases de données.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-114">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="c1d1f-115">Assertions de tester les API de composant, l’interface utilisateur ou les effets secondaires des actions telles que les e/s de la base de données, la journalisation, etc..</span><span class="sxs-lookup"><span data-stu-id="c1d1f-115">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

-   <span data-ttu-id="c1d1f-116">Tests fonctionnels pour chaque microservice.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-116">Functional tests for each microservice.</span></span> <span data-ttu-id="c1d1f-117">Cela permet de garantir que l’application fonctionne comme prévu à partir de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-117">These ensure that the application works as expected from the user’s perspective.</span></span>

-   <span data-ttu-id="c1d1f-118">Tests de service.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-118">Service tests.</span></span> <span data-ttu-id="c1d1f-119">Cela permet de garantir que les cas d’utilisation de service de bout en bout, notamment le test de plusieurs services en même temps, sont testées.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-119">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="c1d1f-120">Pour ce type de test, vous devez tout d’abord la préparation de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-120">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="c1d1f-121">Dans ce cas, cela signifie que le démarrage des services (par exemple, à l’aide de docker-composer des).</span><span class="sxs-lookup"><span data-stu-id="c1d1f-121">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="c1d1f-122">Exécution de tests unitaires pour des API Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c1d1f-122">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="c1d1f-123">Tests unitaires implique le test d’une partie d’une application de manière isolée de son infrastructure et des dépendances.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-123">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="c1d1f-124">Lorsque la logique du contrôleur, seul le contenu d’une seule action de test unitaire ou méthode est testée, pas le comportement de ses dépendances ou de l’infrastructure elle-même.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-124">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="c1d1f-125">Tests unitaires ne pas détecteront les problèmes dans l’interaction entre les composants, qui est l’objectif du test d’intégration.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-125">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="c1d1f-126">En tant qu’unité vous vos actions de contrôleur de test, assurez-vous que vous concentrer uniquement sur leur comportement.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-126">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="c1d1f-127">Un test unitaire de contrôleur évite des éléments tels que les filtres, le routage ou la liaison de modèle.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-127">A controller unit test avoids things like filters, routing, or model binding.</span></span> <span data-ttu-id="c1d1f-128">Car ils se concentrent sur test plus qu’une chose, tests unitaires sont généralement simple à écrire et rapides à exécuter.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-128">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="c1d1f-129">Un ensemble bien écrit de tests unitaires peut être exécuté souvent sans la quantité de surcharge.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-129">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="c1d1f-130">Tests unitaires sont implémentées selon les infrastructures de test comme xUnit.net, MSTest, Moq ou NUnit.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-130">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="c1d1f-131">Pour l’exemple d’application eShopOnContainers, nous utilisons XUnit.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-131">For the eShopOnContainers sample application, we are using XUnit.</span></span>

<span data-ttu-id="c1d1f-132">Lorsque vous écrivez un test unitaire pour un contrôleur d’API Web, vous instanciez la classe de contrôleur directement à l’aide du mot clé new dans C\#, de sorte que le test s’exécutera aussi rapidement que possible.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-132">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="c1d1f-133">L’exemple suivant montre comment effectuer cette opération lorsque vous utilisez [XUnit](https://xunit.github.io/) en tant que l’infrastructure de Test.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-133">The following example shows how to do this when using [XUnit](https://xunit.github.io/) as the Test framework.</span></span>

```csharp
[Fact]
public void Add_new_Order_raises_new_event()
{
    // Arrange
    var street = " FakeStreet ";
    var city = "FakeCity";
    // Other variables omitted for brevity ...
    // Act
    var fakeOrder = new Order(new Address(street, city, state, country, zipcode),
        cardTypeId, cardNumber,
        cardSecurityNumber, cardHolderName,
        cardExpiration);
    // Assert
    Assert.Equal(fakeOrder.DomainEvents.Count, expectedResult);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="c1d1f-134">Intégration d’application et les tests fonctionnels pour chaque microservice</span><span class="sxs-lookup"><span data-stu-id="c1d1f-134">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="c1d1f-135">Comme mentionné, tests d’intégration et les tests fonctionnels ont des objectifs différents.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-135">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="c1d1f-136">Toutefois, la manière d’implémenter les deux lorsque vous testez les contrôleurs ASP.NET Core étant similaire, dans cette section, nous concentrer sur les tests d’intégration.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-136">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="c1d1f-137">Tests d’intégration garantit que les composants d’une application fonctionnent correctement lorsque assemblé.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-137">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="c1d1f-138">ASP.NET Core prend en charge aux tests d’intégration à l’aide des infrastructures de tests unitaires et un hôte web test intégré qui peut être utilisé pour gérer les demandes sans la surcharge du réseau.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-138">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="c1d1f-139">Contrairement aux tests unitaires, tests d’intégration impliquent souvent des problèmes d’infrastructure application, par exemple une base de données, système de fichiers, les ressources réseau, ou de requêtes et réponses web.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-139">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="c1d1f-140">Tests unitaires utilisent fakes ou simuler des objets à la place de ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-140">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="c1d1f-141">Mais l’objectif de tests d’intégration consiste à vérifier que le système fonctionne comme prévu avec ces systèmes, afin de tester l’intégration ne pas utiliser les simulations ou simuler des objets.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-141">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="c1d1f-142">Au lieu de cela, vous incluez l’infrastructure, comme l’appel de base de données access ou de service à partir d’autres services.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-142">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="c1d1f-143">Étant donné que les tests d’intégration couvrir des segments de plus grande que les tests unitaires de code, et comme tests d’intégration reposent sur les éléments d’infrastructure, ils ont tendance à être beaucoup plus lente que les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-143">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="c1d1f-144">Par conséquent, il est judicieux de limiter le nombre de tests d’intégration vous écrivez et exécutez.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-144">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="c1d1f-145">ASP.NET Core inclut un test intégré web hôte peut être utilisé pour gérer les demandes HTTP sans la surcharge du réseau, c'est-à-dire que vous pouvez exécuter ces tests plus rapidement lors de l’utilisation d’un hôte web réel.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-145">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="c1d1f-146">L’hôte du test web est disponible dans un composant NuGet en Microsoft.AspNetCore.TestHost.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-146">The test web host is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="c1d1f-147">Il peut être ajouté aux projets de test d’intégration et utilisé pour l’hôte ASP.NET Core les applications.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-147">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="c1d1f-148">Comme vous pouvez le voir dans le code suivant, lorsque vous créez les tests d’intégration pour ASP.NET Core contrôleurs, vous instanciez les contrôleurs via l’hôte de test.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-148">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="c1d1f-149">Cela est comparable à une requête HTTP, mais il s’exécute plus rapidement.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-149">This is comparable to an HTTP request, but it runs faster.</span></span>

```csharp
public class PrimeWebDefaultRequestShould
{
    private readonly TestServer _server;
    private readonly HttpClient _client;

    public PrimeWebDefaultRequestShould()
    {
        // Arrange
        _server = new TestServer(new WebHostBuilder()
           .UseStartup<Startup>());
           _client = _server.CreateClient();
    }

    [Fact]
    public async Task ReturnHelloWorld()
    {
        // Act
        var response = await _client.GetAsync("/");
        response.EnsureSuccessStatusCode();
        var responseString = await response.Content.ReadAsStringAsync();
        // Assert
        Assert.Equal("Hello World!", responseString);
    }
}
```

#### <a name="additional-resources"></a><span data-ttu-id="c1d1f-150">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="c1d1f-150">Additional resources</span></span>

-   <span data-ttu-id="c1d1f-151">**Steve Smith. Test d’un contrôleur** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)</span><span class="sxs-lookup"><span data-stu-id="c1d1f-151">**Steve Smith. Testing controllers** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)</span></span>

-   <span data-ttu-id="c1d1f-152">**Steve Smith. Tests d’intégration** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)</span><span class="sxs-lookup"><span data-stu-id="c1d1f-152">**Steve Smith. Integration testing** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)</span></span>

-   <span data-ttu-id="c1d1f-153">**Test unitaire dans .NET Core, à l’aide de test de dotnet**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)</span><span class="sxs-lookup"><span data-stu-id="c1d1f-153">**Unit testing in .NET Core using dotnet test**
[*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)</span></span>

-   <span data-ttu-id="c1d1f-154">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-154">**xUnit.net**.</span></span> <span data-ttu-id="c1d1f-155">Site officiel.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-155">Official site.</span></span>
    [<span data-ttu-id="c1d1f-156">*https://xUnit.github.IO/*</span><span class="sxs-lookup"><span data-stu-id="c1d1f-156">*https://xunit.github.io/*</span></span>](https://xunit.github.io/)

-   <span data-ttu-id="c1d1f-157">**Concepts de base du Test unitaire. ** 
     [ *https://msdn.microsoft.com/en-us/library/hh694602.aspx*](https://msdn.microsoft.com/en-us/library/hh694602.aspx)</span><span class="sxs-lookup"><span data-stu-id="c1d1f-157">**Unit Test Basics.**
[*https://msdn.microsoft.com/en-us/library/hh694602.aspx*](https://msdn.microsoft.com/en-us/library/hh694602.aspx)</span></span>

-   <span data-ttu-id="c1d1f-158">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-158">**Moq**.</span></span> <span data-ttu-id="c1d1f-159">Référentiel GitHub.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-159">GitHub repo.</span></span>
    [<span data-ttu-id="c1d1f-160">*https://github.com/moq/moq*</span><span class="sxs-lookup"><span data-stu-id="c1d1f-160">*https://github.com/moq/moq*</span></span>](https://github.com/moq/moq)

-   <span data-ttu-id="c1d1f-161">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-161">**NUnit**.</span></span> <span data-ttu-id="c1d1f-162">Site officiel.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-162">Official site.</span></span>
    [<span data-ttu-id="c1d1f-163">*https://www.NUnit.org/*</span><span class="sxs-lookup"><span data-stu-id="c1d1f-163">*https://www.nunit.org/*</span></span>](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="c1d1f-164">Implémentation de service des tests sur une application conteneur multiples</span><span class="sxs-lookup"><span data-stu-id="c1d1f-164">Implementing service tests on a multi-container application</span></span> 

<span data-ttu-id="c1d1f-165">Comme indiqué précédemment, lorsque vous testez des applications conteneur multiples, tous les microservices doivent exécuter au sein du cluster hôte ou du conteneur de Docker.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-165">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="c1d1f-166">Tests de service de bout en bout qui incluent plusieurs opérations impliquant plusieurs microservices vous obliger à déployer et démarrer l’application entière dans l’hôte Docker par docker en cours d’exécution-composer à distance (ou un mécanisme comparable si vous utilisez un orchestrator).</span><span class="sxs-lookup"><span data-stu-id="c1d1f-166">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="c1d1f-167">Une fois que l’application entière et tous ses services est en cours d’exécution, vous pouvez exécuter l’intégration de bout en bout et les tests fonctionnels.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-167">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="c1d1f-168">Il existe quelques approches que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-168">There are a few approaches you can use.</span></span> <span data-ttu-id="c1d1f-169">Dans le fichier docker-compose.yml que vous utilisez pour déployer l’application (ou celles similaires, tels que docker-compose.ci.build.yml), au niveau de la solution vous pouvez développer le point d’entrée à utiliser [dotnet test](https://docs.microsoft.com/dotnet/core/tools/dotnet-test).</span><span class="sxs-lookup"><span data-stu-id="c1d1f-169">In the docker-compose.yml file that you use to deploy the application (or similar ones, like docker-compose.ci.build.yml), at the solution level you can expand the entry point to use [dotnet test](https://docs.microsoft.com/dotnet/core/tools/dotnet-test).</span></span> <span data-ttu-id="c1d1f-170">Vous pouvez également utiliser un autre fichier de message qui serait d’exécuter vos tests dans l’image que vous ciblez.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-170">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="c1d1f-171">En utilisant un autre fichier de message pour les tests d’intégration qui inclut votre microservices et les bases de données sur les conteneurs, vous assurer que les données associées sont toujours réinitialisées à son état d’origine avant d’exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-171">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="c1d1f-172">Une fois que l’application de la composition est en cours d’exécution, vous pouvez tirer parti des points d’arrêt et des exceptions si vous exécutez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-172">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="c1d1f-173">Ou vous pouvez exécuter les tests d’intégration automatiquement dans votre pipeline de l’élément de configuration dans Visual Studio Team Services ou tout autre système de l’élément de configuration/CD qui prend en charge des conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="c1d1f-173">Or you can run the integration tests automatically in your CI pipeline in Visual Studio Team Services or any other CI/CD system that supports Docker containers.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="c1d1f-174">[Précédente] (s’abonner-events.md) [suivant] (.. /microservice-ddd-CQRS-Patterns/index.MD)</span><span class="sxs-lookup"><span data-stu-id="c1d1f-174">[Previous] (subscribe-events.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>
