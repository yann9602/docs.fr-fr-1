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
# <a name="testing-aspnet-core-services-and-web-apps"></a>Test des services ASP.NET principaux et les applications web

Contrôleurs sont un élément central de tout service ASP.NET Core API et l’application Web ASP.NET MVC. Par conséquent, vous devez avoir confiance qu’ils se comportent comme prévu pour votre application. Tests automatisés peuvent vous fournir cette confiance et peuvent détecter les erreurs avant qu’ils atteignent la production.

Vous devez tester le contrôleur de comporte en fonction des entrées valides ou non valides et de tester les réponses du contrôleur en fonction du résultat de l’opération métier qu’il effectue. Toutefois, vous devez avoir ces types de tests votre microservices :

-   Tests unitaires. Ceux-ci assurent que les composants individuels de l’application fonctionnent comme prévu. Assertions de tester l’API du composant.

-   Tests d’intégration. Ceux-ci assurent que les interactions entre les composants fonctionnent comme prévu en fonction des artefacts externes tels que des bases de données. Assertions de tester les API de composant, l’interface utilisateur ou les effets secondaires des actions telles que les e/s de la base de données, la journalisation, etc..

-   Tests fonctionnels pour chaque microservice. Cela permet de garantir que l’application fonctionne comme prévu à partir de l’utilisateur.

-   Tests de service. Cela permet de garantir que les cas d’utilisation de service de bout en bout, notamment le test de plusieurs services en même temps, sont testées. Pour ce type de test, vous devez tout d’abord la préparation de l’environnement. Dans ce cas, cela signifie que le démarrage des services (par exemple, à l’aide de docker-composer des).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>Exécution de tests unitaires pour des API Web ASP.NET Core

Tests unitaires implique le test d’une partie d’une application de manière isolée de son infrastructure et des dépendances. Lorsque la logique du contrôleur, seul le contenu d’une seule action de test unitaire ou méthode est testée, pas le comportement de ses dépendances ou de l’infrastructure elle-même. Tests unitaires ne pas détecteront les problèmes dans l’interaction entre les composants, qui est l’objectif du test d’intégration.

En tant qu’unité vous vos actions de contrôleur de test, assurez-vous que vous concentrer uniquement sur leur comportement. Un test unitaire de contrôleur évite des éléments tels que les filtres, le routage ou la liaison de modèle. Car ils se concentrent sur test plus qu’une chose, tests unitaires sont généralement simple à écrire et rapides à exécuter. Un ensemble bien écrit de tests unitaires peut être exécuté souvent sans la quantité de surcharge.

Tests unitaires sont implémentées selon les infrastructures de test comme xUnit.net, MSTest, Moq ou NUnit. Pour l’exemple d’application eShopOnContainers, nous utilisons XUnit.

Lorsque vous écrivez un test unitaire pour un contrôleur d’API Web, vous instanciez la classe de contrôleur directement à l’aide du mot clé new dans C\#, de sorte que le test s’exécutera aussi rapidement que possible. L’exemple suivant montre comment effectuer cette opération lorsque vous utilisez [XUnit](https://xunit.github.io/) en tant que l’infrastructure de Test.

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Intégration d’application et les tests fonctionnels pour chaque microservice

Comme mentionné, tests d’intégration et les tests fonctionnels ont des objectifs différents. Toutefois, la manière d’implémenter les deux lorsque vous testez les contrôleurs ASP.NET Core étant similaire, dans cette section, nous concentrer sur les tests d’intégration.

Tests d’intégration garantit que les composants d’une application fonctionnent correctement lorsque assemblé. ASP.NET Core prend en charge aux tests d’intégration à l’aide des infrastructures de tests unitaires et un hôte web test intégré qui peut être utilisé pour gérer les demandes sans la surcharge du réseau.

Contrairement aux tests unitaires, tests d’intégration impliquent souvent des problèmes d’infrastructure application, par exemple une base de données, système de fichiers, les ressources réseau, ou de requêtes et réponses web. Tests unitaires utilisent fakes ou simuler des objets à la place de ces problèmes. Mais l’objectif de tests d’intégration consiste à vérifier que le système fonctionne comme prévu avec ces systèmes, afin de tester l’intégration ne pas utiliser les simulations ou simuler des objets. Au lieu de cela, vous incluez l’infrastructure, comme l’appel de base de données access ou de service à partir d’autres services.

Étant donné que les tests d’intégration couvrir des segments de plus grande que les tests unitaires de code, et comme tests d’intégration reposent sur les éléments d’infrastructure, ils ont tendance à être beaucoup plus lente que les tests unitaires. Par conséquent, il est judicieux de limiter le nombre de tests d’intégration vous écrivez et exécutez.

ASP.NET Core inclut un test intégré web hôte peut être utilisé pour gérer les demandes HTTP sans la surcharge du réseau, c'est-à-dire que vous pouvez exécuter ces tests plus rapidement lors de l’utilisation d’un hôte web réel. L’hôte du test web est disponible dans un composant NuGet en Microsoft.AspNetCore.TestHost. Il peut être ajouté aux projets de test d’intégration et utilisé pour l’hôte ASP.NET Core les applications.

Comme vous pouvez le voir dans le code suivant, lorsque vous créez les tests d’intégration pour ASP.NET Core contrôleurs, vous instanciez les contrôleurs via l’hôte de test. Cela est comparable à une requête HTTP, mais il s’exécute plus rapidement.

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

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Steve Smith. Test d’un contrôleur** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)

-   **Steve Smith. Tests d’intégration** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)

-   **Test unitaire dans .NET Core, à l’aide de test de dotnet**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)

-   **xUnit.net**. Site officiel.
    [*https://xUnit.github.IO/*](https://xunit.github.io/)

-   **Concepts de base du Test unitaire. ** 
     [ *https://msdn.microsoft.com/en-us/library/hh694602.aspx*](https://msdn.microsoft.com/en-us/library/hh694602.aspx)

-   **Moq**. Référentiel GitHub.
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   **NUnit**. Site officiel.
    [*https://www.NUnit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Implémentation de service des tests sur une application conteneur multiples 

Comme indiqué précédemment, lorsque vous testez des applications conteneur multiples, tous les microservices doivent exécuter au sein du cluster hôte ou du conteneur de Docker. Tests de service de bout en bout qui incluent plusieurs opérations impliquant plusieurs microservices vous obliger à déployer et démarrer l’application entière dans l’hôte Docker par docker en cours d’exécution-composer à distance (ou un mécanisme comparable si vous utilisez un orchestrator). Une fois que l’application entière et tous ses services est en cours d’exécution, vous pouvez exécuter l’intégration de bout en bout et les tests fonctionnels.

Il existe quelques approches que vous pouvez utiliser. Dans le fichier docker-compose.yml que vous utilisez pour déployer l’application (ou celles similaires, tels que docker-compose.ci.build.yml), au niveau de la solution vous pouvez développer le point d’entrée à utiliser [dotnet test](https://docs.microsoft.com/dotnet/core/tools/dotnet-test). Vous pouvez également utiliser un autre fichier de message qui serait d’exécuter vos tests dans l’image que vous ciblez. En utilisant un autre fichier de message pour les tests d’intégration qui inclut votre microservices et les bases de données sur les conteneurs, vous assurer que les données associées sont toujours réinitialisées à son état d’origine avant d’exécuter les tests.

Une fois que l’application de la composition est en cours d’exécution, vous pouvez tirer parti des points d’arrêt et des exceptions si vous exécutez Visual Studio. Ou vous pouvez exécuter les tests d’intégration automatiquement dans votre pipeline de l’élément de configuration dans Visual Studio Team Services ou tout autre système de l’élément de configuration/CD qui prend en charge des conteneurs Docker.

>[!div class="step-by-step"]
[Précédente] (s’abonner-events.md) [suivant] (.. /microservice-ddd-CQRS-Patterns/index.MD)
