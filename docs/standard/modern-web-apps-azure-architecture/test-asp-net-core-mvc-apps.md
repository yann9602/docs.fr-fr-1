---
title: Test ASP.NET Core les applications MVC
description: Architecture des Applications Web avec ASP.NET Core et Azure | Test ASP.NET Core les applications MVC
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d23d0accc33fb8335dff602d6e1d6c8689972906
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="test-aspnet-core-mvc-apps"></a>Test ASP.NET Core les applications MVC

> _« Si vous n’aimez pas votre produit de tests unitaires, très probablement vos clients ne sont pas tels que pour le tester, soit. »_
> _- Anonymous-

## <a name="summary"></a>Récapitulatif

Logiciels complexes peuvent échouer de façon inattendue en réponse aux modifications. Par conséquent, il est requis pour toutes les applications plus anecdotiques (ou moins critiques) de test après avoir apporté des modifications. Un test manuel est la plus lente, façon moins fiable, la plus coûteuse pour tester un logiciel. Malheureusement, si les applications ne sont pas conçues pour être testable, il peut être la seule méthode disponible. Les applications écrites suit les principes d’architecture présentés dans le chapitre X doivent être unité testable, et les applications ASP.NET Core prennent en charge l’intégration automatisée et également les tests fonctionnels.

## <a name="kinds-of-automated-tests"></a>Types de Tests automatisés

Il existe de nombreux types de tests automatisés pour les applications logicielles. La plus simple, test au niveau le plus bas est le test unitaire. À un niveau légèrement supérieur des tests d’intégration et les tests fonctionnels. Autres types de tests, tels que les tests, les tests de charge, les tests de contrainte et tests de détection de fumée, l’interface utilisateur n’entrent pas dans le cadre de ce document.

### <a name="unit-tests"></a>Tests unitaires

Un test unitaire teste une seule partie de la logique de votre application. Un peut décrire plus précisément en répertoriant les éléments dont il n’est pas. Un test unitaire ne teste pas comment votre code fonctionne avec des dépendances ou d’infrastructure – ce que l’intégration des tests est destinés. Un test unitaire ne teste pas le cadre de sur que votre code est écrit : vous partez du principe qu’il fonctionne ou, si vous trouvez qu’il ne, signaler un bogue et une solution de contournement du code. Un test unitaire s’exécute entièrement en mémoire et dans le processus. Elle ne communique pas avec le système de fichiers, le réseau ou une base de données. Tests unitaires doivent uniquement tester votre code.

Les tests unitaires, du fait qu’elle teste uniquement une seule unité de votre code, sans dépendances externes, doivent s’exécuter très rapidement. Par conséquent, vous devez pouvoir exécuter des suites de tests de centaines de tests unitaires dans quelques secondes. Exécuter fréquemment, idéalement avant chaque par émission de données à un référentiel de contrôle de code source partagé et certainement avec chaque build automatisée sur votre serveur de builds.

### <a name="integration-tests"></a>Tests d’intégration

Même s’il est judicieux d’encapsuler votre code qui interagit avec l’infrastructure, notamment les bases de données et les systèmes de fichiers, vous devez toujours partie de ce code, et vous aurez probablement besoin de le tester. En outre, vous devez vérifier que les couches de votre code interagissent comme prévu lorsque les dépendances de votre application sont entièrement résolus. Il s’agit de la responsabilité des tests d’intégration. Tests d’intégration ont tendance à être plus lent et plus difficile à configurer que les tests unitaires, car ils dépendent souvent infrastructure et des dépendances externes. Par conséquent, vous devez éviter d’éléments qui peuvent être des tests avec des tests unitaires dans les tests d’intégration de test. Si vous pouvez tester un scénario donné avec un test unitaire, vous devez la tester avec un test unitaire. Si vous ne pouvez pas le cas, envisagez d’utiliser un test d’intégration.

Tests d’intégration ont souvent le programme d’installation plus complexe et les procédures de démontage que les tests unitaires. Par exemple, un test d’intégration qui passe par rapport à une base de données réelle devez un moyen de retourner la base de données à un état connu avant chaque série de tests. Comme de nouveaux tests sont ajoutés et le schéma de base de données de production évolue, ces scripts auront tendance à croître en taille et la complexité de test. Dans de nombreux systèmes de grande taille, il est peu pratique d’exécuter les suites de tests d’intégration complètes sur les stations de travail de développement avant d’archiver les modifications apportées au contrôle de code source partagé. Dans ces cas, les tests d’intégration peuvent être exécutées sur un serveur de builds.

La classe d’implémentation LocalFileImageService implémente la logique de l’extraction et renvoyer les octets d’un fichier image à partir d’un dossier spécifique, un id donné :

```cs
public class LocalFileImageService : IImageService
{
    private readonly IHostingEnvironment _env;
    public LocalFileImageService(IHostingEnvironment env)
    {
        _env = env;
    }
    public byte[] GetImageBytesById(int id)
    {
        try
        {
            var contentRoot = _env.ContentRootPath + "//Pics";
            var path = Path.Combine(contentRoot, id + ".png");
            return File.ReadAllBytes(path);
```

### <a name="functional-tests"></a>Tests fonctionnels

Tests d’intégration sont écrites du point de vue du développeur, pour vérifier que certains composants du système fonctionnent correctement ensemble. Les tests fonctionnels sont écrites du point de vue de l’utilisateur et vérifiez l’exactitude du système en fonction de ses besoins. L’extrait suivant offre une analogie utile pour savoir comment tenir compte des tests fonctionnels, par rapport aux tests unitaires :

> « Nombre de fois où le développement d’un système est comparée à la création d’une maison. Alors que cette analogie n’est pas tout à fait correcte, nous pouvons l’étendre pour mieux comprendre la différence entre les unités et les tests fonctionnels. Test unitaire est analogue à un inspecteur de construction sur site de construction d’une maison. Il se concentre sur les différents systèmes internes de la maison, la Fondation, reformulation, électrique, plomberie et ainsi de suite. Il garantit (tests) que les parties de la maison seront fonctionne correctement et en toute sécurité, autrement dit, répondent à la génération code. Dans ce scénario, les tests fonctionnels sont analogues au propriétaire sur ce même site de construction. Il part du principe que les systèmes internes seront comporte de manière appropriée, que l’inspecteur de construction effectue sa tâche. Le propriétaire est axé sur ce que ce sera comme de vie de cette maison. Il concerne à quoi ressemble la maison, sont les différentes salles de conversation d’une taille à l’aise, la maison besoins de la famille, sont les fenêtres dans une zone correcte pour intercepter le soleil matin. Le propriétaire exécute les tests fonctionnels sur la maison. Il dispose de l’utilisateur. L’inspecteur de génération en exécution des tests unitaires sur la maison. Il dispose du point de vue du générateur. »

Source : [unité de test et les Tests fonctionnels](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

J’aime » en tant que développeurs, nous échouer de deux manières : nous créons la chose incorrecte ou que nous créons un objet erroné. » Tests unitaires Assurez-vous que vous travaillez sur la droite chose ; les tests fonctionnels Vérifiez que vous générez l’attitude.

Étant donné que les tests fonctionnels fonctionnent au niveau du système, ils peuvent nécessitent un certain degré d’automatisation de l’interface utilisateur. Comme tests d’intégration, ils fonctionnent généralement avec un type de l’infrastructure de test ainsi. Cela les rend plus lent et plus fragile que les tests unitaires et l’intégration. Vous devez avoir uniquement des tests fonctionnels autant que nécessaire pour être certain que le système se comporte comme les utilisateurs s’y attendre.

### <a name="testing-pyramid"></a>Test en pyramide

Martin Fowler a écrit sur la test en pyramide, un exemple de ce qui est indiqué dans la Figure 9-1.

![](./media/image9-1.png)

La figure 9-1 test en pyramide

Les différentes couches de la pyramide et leurs tailles relatives, représentent par différents types de tests et le nombre, vous devez écrire pour votre application. Comme vous pouvez le voir, la recommandation consiste à disposer d’une grande base de tests unitaires, pris en charge par une couche inférieure de tests d’intégration, avec une couche plus petite de tests fonctionnels. Chaque couche dans l’idéal, ne doit avoir des tests qui ne peut pas être effectuée correctement sur une couche inférieure. Gardez à l’esprit la pyramide test lorsque vous essayez de déterminer le type de test que vous avez besoin pour un scénario particulier.

### <a name="what-to-test"></a>Que se passe-t-il au Test

Un problème courant pour les développeurs peu familiarisés avec l’écriture de tests automatisés arrive avec les éléments à tester. Il est un bon point de départ pour tester la logique conditionnelle. Partout où vous avez une méthode avec un comportement qui change en fonction d’une instruction conditionnelle (if-else, de basculer, etc.), vous devez être en mesure de proposer au moins deux des tests qui confirment que le comportement approprié à certaines conditions. Si votre code a des conditions d’erreur, il est judicieux d’écrire d’au moins un test pour le chemin « bon » via le code (avec aucune erreur) et au moins un test pour le « chemin d’accès sad » (avec des erreurs ou des résultats atypiques) pour confirmer que votre application se comporte comme prévu en cas d’erreurs. Enfin, essayez de vous concentrer sur les éléments qui peuvent échouer de test, plutôt que de vous concentrer sur des métriques telles que la couverture du code. Plus de couverture du code est inférieure, en général. Toutefois, l’écriture quelques tests plus d’une méthode très complexe et critique d’entreprise est généralement une meilleure utilisation de temps que l’écriture de tests pour des propriétés automatiques simplement optimiser les métriques de couverture du code de test.

## <a name="organizing-test-projects"></a>Organisation des projets de Test

Pour organiser des projets de test mais fonctionne mieux pour vous. Il est judicieux de séparer les tests par type (test unitaire, test d’intégration) et par qu’ils testent (par projet, espace de noms). Si cette séparation est constituée des dossiers au sein d’un projet de test ou de plusieurs projets de test, est une décision de conception. Un projet est la plus simple, mais pour les projets volumineux avec le nombre de tests ou pour exécuter plus facilement les différents ensembles de tests, vous pouvez avoir plusieurs projets de test différentes. De nombreuses équipes organiser les projets de test basés sur le projet que testez, qui, pour les applications avec plusieurs projets, peut entraîner un grand nombre de projets de test, en particulier si vous toujours décomposez ces selon quels sont les types de tests dans chaque projet. Une approche de compromis consiste à disposer d’un projet par type de test, par application, avec les dossiers contenus dans les projets de test pour indiquer le projet (et la classe) en cours de test.

Une approche courante consiste à organiser les projets d’application dans un dossier 'src' et les projets de test de l’application dans un dossier « tests » parallèle. Vous pouvez créer des dossiers de solution correspondant dans Visual Studio, si vous trouvez cette organisation utile.

![](./media/image9-2.png)

Organisation de Test de la figure 9-2 dans votre solution

Vous pouvez utiliser quelle que soit l’infrastructure de test que vous préférez. L’infrastructure xUnit fonctionne bien et ce que tous les tests ASP.NET Core et EF Core sont écrits. Vous pouvez ajouter un projet de test xUnit dans Visual Studio en utilisant le modèle indiqué dans la Figure 9-3, ou à partir de l’interface CLI à l’aide de xunit de nouveau dotnet.

![](./media/image9-3.png)

Figure 9-3 Ajouter un projet de Test xUnit dans Visual Studio

### <a name="test-naming"></a>Test d’affectation de noms

Vous devez nommer vos tests de façon cohérente, avec des noms qui indiquent la signification de chaque test. J’ai un grand succès avec consiste à des classes de test de nom en fonction de la classe et la méthode qu'ils testent. Il en résulte dans de nombreuses classes de test peu, mais il rend extrêmement effacer ce que chaque test est responsable. Avec le nom de classe de test configuré pour identifier la classe et la méthode à tester, le nom de la méthode de test peut être utilisé pour spécifier le comportement qui est testé. Cela doit inclure le comportement attendu et des entrées ou des hypothèses sur lesquelles doivent atteindre ce comportement. Certains exemples de noms de test :

-   CatalogControllerGetImage.CallsImageServiceWithId

-   CatalogControllerGetImage.LogsWarningGivenImageMissingException

-   CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess

-   CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException

Une variante de cette approche termine chaque nom de classe de test avec « Doit » et modifie la conjugaison légèrement :

-   CatalogControllerGetImage**Should**.**Call**ImageServiceWithId

-   CatalogControllerGetImage**Should**.**Log**WarningGivenImageMissingException

Certaines équipes de recherchent la deuxième approche d’affectation des noms plus claire, bien que légèrement plus détaillée. Dans tous les cas, essayez d’utiliser une convention d’affectation de noms qui permet de comprendre le comportement de test, afin que lorsqu’un ou plusieurs tests échouent, il est évident au vu de leurs noms, les cas qui ont échoué. Éviter de nommer vous tests vaguement, telles que ControllerTests.Test1, car ceux-ci n’offrent aucune valeur lorsque vous les voyez dans les résultats des tests.

Si vous suivez une convention d’affectation de noms comme celle ci-dessus qui génère des classes de test peu nombreuses, il est judicieux pour organiser davantage vos tests à l’aide des dossiers et des espaces de noms. Figure 9-4 présente une approche pour organiser des tests par dossier au sein de plusieurs projets de test.

![](./media/image9-4.png)

**Figure 9-4.** Organisation des classes de test par dossier en fonction de la classe en cours de test.

Bien entendu, si une classe d’application particulier possède de nombreuses méthodes testées (et par conséquent, plusieurs classes de test), il peut être judicieux de le placer dans un dossier correspondant à la classe d’application. Cette organisation n’est pas différente de la façon dont vous pouvez organiser les fichiers dans des dossiers ailleurs. Si vous avez plus de trois ou quatre fichiers associés dans un dossier contenant de nombreux autres fichiers, il est souvent utile de les déplacer vers leur propre sous-dossier.

## <a name="unit-testing-aspnet-core-apps"></a>Unité de test des applications ASP.NET Core

Dans une application ASP.NET Core bien conçue, la majeure partie de la complexité et la logique métier sera encapsulée dans les entités commerciales et une variété de services. L’application ASP.NET MVC de base, avec ses contrôleurs, de filtres, ViewModel et vues, doit nécessitent très peu de tests unitaires. Une grande partie de la fonctionnalité d’une action donnée se trouve en dehors de la méthode d’action. Tester si le routage fonctionne correctement ou la gestion des erreurs global, ne peut pas être effectuée efficacement avec un test unitaire. De même, les filtres, notamment l’authentification et la validation du modèle et les filtres d’autorisation, ne peut pas être des tests unitaires. Sans ces sources de comportement, la plupart des méthodes d’action doivent être plus simplement petites, la majeure partie de leur travail à des services qui peuvent être testés indépendant du contrôleur qui les utilise la délégation.

Vous devez parfois à refactoriser votre code dans le test unitaire son ordre. Cela implique souvent identifier des abstractions et à l’aide de l’injection de dépendances pour accéder à l’abstraction dans le code que vous souhaitez tester, plutôt que directement sur l’infrastructure de codage. Par exemple, considérez cette méthode d’action simple pour afficher des images :

```cs
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

Cette méthode de test unitaire est rendue difficile par sa dépendance directe vis-à-vis System.IO.File, qu’il utilise pour lire à partir du système de fichiers. Vous pouvez tester ce comportement pour vous assurer qu’il fonctionne comme prévu, mais avec des fichiers réels est un test d’intégration. Il est important de noter vous ne pouvez pas tester les itinéraires de cette méthode, vous allez apprendre à effectuer cette opération avec un test fonctionnel dans quelques instants.

Si vous ne pouvez pas le test unitaire le comportement de système de fichiers directement, et vous ne pouvez pas tester l’itinéraire, ce qui est il à tester ? Ainsi, après la refactorisation pour faire des tests unitaires, vous risquez de découvrir des cas de test et le comportement manquante, telles que la gestion des erreurs. Quelle est la méthode ? lorsqu’un fichier n’est pas trouvé. Ce qu’il doit faire ? Dans cet exemple, la méthode refactorisée ressemble à ceci :

```cs
[HttpGet("[controller]/pic/{id}")\]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

Le \_enregistreur d’événements et \_imageService sont injectées en tant que dépendances. Maintenant vous pouvez tester que le même id qui est passé à la méthode d’action est transmis à la \_imageService, et que les octets obtenus sont retournées dans le cadre de la FileResult. Vous pouvez également tester que l’enregistrement des erreurs qui se passe comme prévu, et qu’un résultat introuvable est retourné si l’image est manquante, en supposant que ce soit le comportement de l’application importante (autrement dit, pas simplement code temporaire le développeur ajouté afin de diagnostiquer un problème). La logique de fichier réel a été déplacé dans un service de mise en œuvre distincte et qu’il a été augmentée pour retourner une exception spécifique à l’application dans le cas d’un fichier manquant. Vous pouvez tester cette implémentation indépendamment, à l’aide d’un test d’intégration.

## <a name="integration-testing-aspnet-core-apps"></a>Intégration de test des applications ASP.NET Core

```cs
    }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

Ce service utilise le IHostingEnvironment, tout comme le CatalogController code fait avant, il a été refactorisé dans un service distinct. Étant donné que c’était le seul code dans le contrôleur qui utilisé IHostingEnvironment, cette dépendance a été supprimée de constructeur de CatalogController.

Pour vérifier que ce service fonctionne correctement, vous devez créer un fichier d’image de test connus et vérifiez que le service retourne donné une entrée spécifique. Vous devez prendre soin afin de ne pas pour utiliser d’objets fictifs sur le comportement que vous souhaitez tester (dans ce cas, la lecture du système de fichiers). Toutefois, objets fictifs peuvent toujours être utiles de définir des tests d’intégration. Dans ce cas, vous pouvez simuler IHostingEnvironment afin que ses ContentRootPath pointe vers le dossier que vous allez utiliser pour votre image de test. La classe de test d’intégration travail terminé est illustrée ici :

```cs
public class LocalFileImageServiceGetImageBytesById
{
    private byte[] _testBytes = new byte[] { 0x01, 0x02, 0x03 };
    private readonly Mock<IHostingEnvironment> _mockEnvironment = new Mock<IHostingEnvironment>();
    private int _testImageId = 123;
    private string _testFileName = "123.png";
    public LocalFileImageServiceGetImageBytesById()
    {
        // create folder if necessary
        Directory.CreateDirectory(Path.Combine(GetFileDirectory(), "Pics"));
        string filePath = GetFilePath(_testFileName);
        System.IO.File.WriteAllBytes(filePath, _testBytes);
        _mockEnvironment.SetupGet<string>(m => m.ContentRootPath).Returns(GetFileDirectory());
    }
    private string GetFilePath(string fileName)
    {
        return Path.Combine(GetFileDirectory(), "Pics", fileName);
        }
            private string GetFileDirectory()
        {
            var location = System.Reflection.Assembly.GetEntryAssembly().Location;
            return Path.GetDirectoryName(location);
        }

        [Fact]
        public void ReturnsFileContentResultGivenValidId()
        {
            var fileService = new LocalFileImageService(_mockEnvironment.Object);
            var result = fileService.GetImageBytesById(_testImageId);
            Assert.Equal(_testBytes, result);
        }
    }
```

> [!NOTE]
> que le test lui-même est très simple : la majeure partie du code est nécessaire pour configurer le système et de créer l’infrastructure de test (dans ce cas, un fichier à lire à partir du disque). Cela est courant pour les tests d’intégration, qui nécessitent généralement des tâches de configuration plus complexe que les tests unitaires.

## <a name="functional-testing-aspnet-core-apps"></a>Applications ASP.NET Core tests fonctionnelles

Pour les applications ASP.NET Core, la classe TestServer rend les tests fonctionnels relativement facile à écrire. Vous configurez un TestServer à l’aide d’un WebHostBuilder, comme vous le feriez normalement pour votre application. Cette WebHostBuilder doit être configuré comme hôte réel de votre application, mais vous pouvez modifier les aspects qui faciliter le test. La plupart du temps, vous allez réutiliser le même TestServer pour plusieurs cas de test, donc vous pouvez l’encapsuler dans une méthode réutilisable (peut-être dans une classe de base) :

```cs
public abstract class BaseWebTest
{
    protected readonly HttpClient _client;
    protected string _contentRoot;

    public BaseWebTest()
    {
        _client = GetClient();
    }
    
    protected HttpClient GetClient()
    {
        var startupAssembly = typeof(Startup).GetTypeInfo().Assembly;
        _contentRoot = GetProjectPath("src", startupAssembly);
        var builder = new WebHostBuilder()
        .UseContentRoot(_contentRoot)
        .UseStartup&lt;Startup&gt;();
        var server = new TestServer(builder);
        var client = server.CreateClient();
        return client;
    }
}
```

La méthode GetProjectPath retourne simplement le chemin d’accès physique au projet web (exemple de solution téléchargement). Le WebHostBuilder dans ce cas simplement spécifie où est la racine du contenu de l’application web et fait référence à la même classe de démarrage, que l’application web réelle utilise. Pour travailler avec le TestServer, vous utilisez le type System.Net.HttpClient standard pour effectuer des demandes à ce dernier. TestServer expose une méthode CreateClient utile qui fournit un client préconfiguré qui est prêt à effectuer des demandes à l’application en cours d’exécution sur le TestServer. Vous utilisez ce client (valeur protégé \_membre de client sur le test de base ci-dessus) lors de l’écriture des tests fonctionnels pour votre application ASP.NET Core :

```cs
public class CatalogControllerGetImage : BaseWebTest
{
    [Fact]
    public async Task ReturnsFileContentResultGivenValidId()
    {
        var testFilePath = Path.Combine(_contentRoot, "pics//1.png");
        var expectedFileBytes = File.ReadAllBytes(testFilePath);
        var response = await _client.GetAsync("/catalog/pic/1");
        response.EnsureSuccessStatusCode();
        var streamResponse = await response.Content.ReadAsStreamAsync();
        byte[] byteResult;
        using (var ms = new MemoryStream())
        {
            streamResponse.CopyTo(ms);
            byteResult = ms.ToArray();
        }
        Assert.Equal(expectedFileBytes, byteResult);
    }
}
```

Ce test fonctionnel teste la pile complète d’applications ASP.NET MVC de base, y compris tous les intergiciels (middleware), filtres, classeurs, etc. qui peuvent être en place. Il vérifie si un compte tenu de l’itinéraire (« / catalogue/pic/1 ») retourne le tableau d’octets attendus pour un fichier dans un emplacement connu. Il fait sans avoir configuré un serveur web réel et évite une grande partie de la fragilité qui peut rencontrer des serveur de test (par exemple, les problèmes liés aux paramètres de pare-feu) à l’aide d’un site web réel. Les tests fonctionnels qui s’exécutent sur TestServer sont généralement plus lents que l’intégration et des tests unitaires, mais il sont beaucoup plus rapides que les tests qui sont exécute sur le réseau à un serveur web de test.

>[!div class="step-by-step"]
[Précédente] (work-with-data-in-asp-net-core-apps.md) [suivant] (développement-processus-de-azure.md)
