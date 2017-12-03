---
title: "Écriture d'une application du Windows Store qui consomme un service OData"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: csharp
ms.assetid: 9917a0e9-ec93-49e5-a366-fd39b892eb8b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eeee9dcf27d63f5bc40dfdfce1ff7d8104060b6a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="writing-a-windows-store-app-that-consumes-an-odata-service"></a><span data-ttu-id="e79c4-102">Écriture d'une application du Windows Store qui consomme un service OData</span><span class="sxs-lookup"><span data-stu-id="e79c4-102">Writing a Windows Store App that consumes an OData Service</span></span>
<span data-ttu-id="e79c4-103">Windows 8 introduit un nouveau type d’application : l’application du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="e79c4-103">Windows 8 introduces a new type of application: the Windows Store app.</span></span> <span data-ttu-id="e79c4-104">Les applications du Windows Store ont une nouvelle apparence, s'exécutent sur un large éventail de périphériques et sont rendues disponibles dans le Windows Store.</span><span class="sxs-lookup"><span data-stu-id="e79c4-104">Windows Store apps have a brand new look and feel, run on a variety of devices, and are made available on the Windows Store.</span></span> <span data-ttu-id="e79c4-105">Cette rubrique explique comment écrire une application du Windows Store qui utilise un service OData, spécifiquement le service OData du catalogue NetFlix.</span><span class="sxs-lookup"><span data-stu-id="e79c4-105">This topic describes how to write a Windows Store app that consumes an OData service, specifically the NetFlix Catalog OData service.</span></span> <span data-ttu-id="e79c4-106">Pour plus d’informations sur les applications du Windows Store, lisez [mise en route avec les applications du Windows Store](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).</span><span class="sxs-lookup"><span data-stu-id="e79c4-106">For more information about Windows Store Apps, please read [Getting Started with Windows Store apps](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e79c4-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e79c4-107">Prerequisites</span></span>  
  
1.  [<span data-ttu-id="e79c4-108">Microsoft Windows 8</span><span class="sxs-lookup"><span data-stu-id="e79c4-108">Microsoft Windows 8</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266654)  
  
2.  [<span data-ttu-id="e79c4-109">Microsoft Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="e79c4-109">Microsoft Visual Studio 2012</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266655)  
  
3.  [<span data-ttu-id="e79c4-110">Services de données WCF</span><span class="sxs-lookup"><span data-stu-id="e79c4-110">WCF Data Services</span></span>](http://msdn.microsoft.com/data/bb931106)  
  
#### <a name="creating-the-default-windows-store-grid-application"></a><span data-ttu-id="e79c4-111">Création de l'application Grille par défaut du Windows Store</span><span class="sxs-lookup"><span data-stu-id="e79c4-111">Creating the default Windows Store Grid Application</span></span>  
  
1.  <span data-ttu-id="e79c4-112">Créez une nouvelle application Grille du Windows Store à l'aide de C# et XAML.</span><span class="sxs-lookup"><span data-stu-id="e79c4-112">Create a new Windows Store Grid Application using C# and XAML.</span></span> <span data-ttu-id="e79c4-113">Nommez l'application OData.WindowsStore.NetflixDemo :</span><span class="sxs-lookup"><span data-stu-id="e79c4-113">Name the application OData.WindowsStore.NetflixDemo:</span></span>  
  
     <span data-ttu-id="e79c4-114">![Boîte de dialogue Nouveau projet](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")</span><span class="sxs-lookup"><span data-stu-id="e79c4-114">![New Project Dialog](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")</span></span>  
  
2.  <span data-ttu-id="e79c4-115">Ouvrez le Package.appxmanifest et entrez un nom convivial dans la zone de texte Nom complet.</span><span class="sxs-lookup"><span data-stu-id="e79c4-115">Open the Package.appxmanifest and enter a friendly name in the Display name text box.</span></span> <span data-ttu-id="e79c4-116">Cela indique le nom de l'application utilisée avec la fonctionnalité de recherche Windows 8.</span><span class="sxs-lookup"><span data-stu-id="e79c4-116">This specifies the application name used with the Windows 8 search functionality.</span></span>  
  
     <span data-ttu-id="e79c4-117">![Fichier manifeste d’application](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")</span><span class="sxs-lookup"><span data-stu-id="e79c4-117">![Application manifest file](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")</span></span>  
  
3.  <span data-ttu-id="e79c4-118">Entrez un nom convivial dans le \<AppName > élément dans le fichier App.xaml.</span><span class="sxs-lookup"><span data-stu-id="e79c4-118">Enter a friendly name in the \<AppName> element in the App.xaml file.</span></span> <span data-ttu-id="e79c4-119">Cela définit le nom de l'application affiché lorsque l'application est lancée :</span><span class="sxs-lookup"><span data-stu-id="e79c4-119">This sets the application name that is displayed when the application is launched:</span></span>  
  
     <span data-ttu-id="e79c4-120">![Fichier App.XAML](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")</span><span class="sxs-lookup"><span data-stu-id="e79c4-120">![App.xaml file](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")</span></span>  
  
4.  <span data-ttu-id="e79c4-121">Générez et lancez l'application.</span><span class="sxs-lookup"><span data-stu-id="e79c4-121">Build and launch the application.</span></span> <span data-ttu-id="e79c4-122">L'écran de démarrage de l'application s'affiche en premier.</span><span class="sxs-lookup"><span data-stu-id="e79c4-122">You first see the application’s splash screen.</span></span> <span data-ttu-id="e79c4-123">La capture d'écran ci-dessous affiche l'écran de démarrage par défaut.</span><span class="sxs-lookup"><span data-stu-id="e79c4-123">The screenshot below displays the default splash screen.</span></span> <span data-ttu-id="e79c4-124">Image utilisée est stockée dans le dossier Assets du projet.</span><span class="sxs-lookup"><span data-stu-id="e79c4-124">The image used is stored in the project’s Assets folder.</span></span>  
  
     <span data-ttu-id="e79c4-125">![L’écran de démarrage d’application par défaut](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")</span><span class="sxs-lookup"><span data-stu-id="e79c4-125">![The default app splash screen](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")</span></span>  
  
     <span data-ttu-id="e79c4-126">L'application est alors affichée.</span><span class="sxs-lookup"><span data-stu-id="e79c4-126">Then the application will be displayed.</span></span>  
  
     <span data-ttu-id="e79c4-127">![L’application par défaut](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")</span><span class="sxs-lookup"><span data-stu-id="e79c4-127">![The default application](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")</span></span>  
  
     <span data-ttu-id="e79c4-128">L'application par défaut définit un ensemble de classes dans SampleDataSource.cs : SampleDataGroup et SampleDataItem, qui sont dérivées de SampleDataCommon, qui elle-même est dérivée de BindableBase.</span><span class="sxs-lookup"><span data-stu-id="e79c4-128">The default application defines a set of classes in SampleDataSource.cs: SampleDataGroup and SampleDataItem, both of which are derived from SampleDataCommon, which itself is derived from BindableBase.</span></span> <span data-ttu-id="e79c4-129">SampleDataGroup et SampleDataItem sont liés au GridView par défaut.</span><span class="sxs-lookup"><span data-stu-id="e79c4-129">SampleDataGroup and SampleDataItem are bound to the default GridView.</span></span> <span data-ttu-id="e79c4-130">SampleDataSource.cs se trouve dans le dossier DataModel du projet NetflixDemo.</span><span class="sxs-lookup"><span data-stu-id="e79c4-130">SampleDataSource.cs is located in the DataModel folder within the NetflixDemo project.</span></span> <span data-ttu-id="e79c4-131">L'application affiche une collection groupée.</span><span class="sxs-lookup"><span data-stu-id="e79c4-131">The application displays a grouped collection.</span></span> <span data-ttu-id="e79c4-132">Chaque groupe contient un certain nombre d'éléments, représentés par SampleDataGroup et SampleDataItem, respectivement.</span><span class="sxs-lookup"><span data-stu-id="e79c4-132">Each group contains any number of items, represented by SampleDataGroup and SampleDataItem, respectively.</span></span> <span data-ttu-id="e79c4-133">Dans la capture d'écran précédente vous pouvez afficher un groupe appelé Group Title 1 et tous les éléments du groupe affichés ensemble.</span><span class="sxs-lookup"><span data-stu-id="e79c4-133">In the previous screen shot you can see a group called Group Title 1 and all of the items in the group displayed together.</span></span>  
  
     <span data-ttu-id="e79c4-134">La page principale de l'application est GroupedItemsPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="e79c4-134">The main page of the application is GroupedItemsPage.xaml.</span></span> <span data-ttu-id="e79c4-135">Elle contient un GridView qui affiche les exemples de données créés par la classe SampleDataSource.cs.</span><span class="sxs-lookup"><span data-stu-id="e79c4-135">It contains a GridView that displays the sample data created by the SampleDataSource.cs class.</span></span> <span data-ttu-id="e79c4-136">Le GroupedItemsPage est chargé par App.xaml.cs dans un appel à rootFrame.Navigate :</span><span class="sxs-lookup"><span data-stu-id="e79c4-136">The GroupedItemsPage is loaded by the App.xaml.cs in a call to rootFrame.Navigate:</span></span>  
  
    ```csharp  
    if (!rootFrame.Navigate(typeof(GroupedItemsPage), "AllGroups"))  
    {  
        throw new Exception("Failed to create initial page");  
    }  
    ```  
  
     <span data-ttu-id="e79c4-137">Ceci entraîne l'instanciation du GroupedItemsPage et sa méthode LoadState est appelée.</span><span class="sxs-lookup"><span data-stu-id="e79c4-137">This causes the GroupedItemsPage to be instantiated and it’s LoadState method is called.</span></span> <span data-ttu-id="e79c4-138">LoadState entraîne la création de l'instance SampleDataSource statique, qui crée une collection d'objets SampleDataGroup.</span><span class="sxs-lookup"><span data-stu-id="e79c4-138">LoadState causes the static SampleDataSource instance to be created, which creates a collection of SampleDataGroup objects.</span></span> <span data-ttu-id="e79c4-139">Chaque objet SampleDataGroup contient une collection d'objets SampleDataItem.</span><span class="sxs-lookup"><span data-stu-id="e79c4-139">Each SampleDataGroup object contains a collection of SampleDataItem objects.</span></span> <span data-ttu-id="e79c4-140">LoadState inscrit la collection d'objets SampleDataGroup dans le DefaultViewModel :</span><span class="sxs-lookup"><span data-stu-id="e79c4-140">LoadState stores the collection of SampleDataGroup objects in the DefaultViewModel:</span></span>  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     <span data-ttu-id="e79c4-141">Le DefaultViewModel est ensuite lié au GridView.</span><span class="sxs-lookup"><span data-stu-id="e79c4-141">The DefaultViewModel is then bound to the GridView.</span></span> <span data-ttu-id="e79c4-142">Cela est référencé dans le fichier GroupedItemsPage.xaml lors de la configuration de la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="e79c4-142">This is referenced in the GroupedItemsPage.xaml file when configuring the data binding.</span></span>  
  
    ```xaml
    <CollectionViewSource  
                x:Name="groupedItemsViewSource"  
                Source="{Binding Groups}"  
                IsSourceGrouped="true"  
                ItemsPath="TopItems"  
                d:Source="{Binding AllGroups, Source={d:DesignInstance Type=data:SampleDataSource, IsDesignTimeCreatable=True}}"/>  
    ```  
  
     <span data-ttu-id="e79c4-143">CollectionViewSource est utilisé comme proxy pour gérer les collections groupées.</span><span class="sxs-lookup"><span data-stu-id="e79c4-143">The CollectionViewSource is used as a proxy for handling grouped collections.</span></span> <span data-ttu-id="e79c4-144">Lorsque la liaison se produit, elle effectue une itération au sein de la collection d'objets SampleDataGroup pour remplir le GridView.</span><span class="sxs-lookup"><span data-stu-id="e79c4-144">When binding occurs, it iterates through the collection of SampleDataGroup objects to populate the GridView.</span></span>  <span data-ttu-id="e79c4-145">L'attribut ItemsPath indique au CollectionViewSource quelle propriété utiliser sur chaque objet SampleDataGroup pour trouver le SampleDataItems qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="e79c4-145">The ItemsPath attribute tells the CollectionViewSource what property on each SampleDataGroup object to use to find the SampleDataItems it contains.</span></span> <span data-ttu-id="e79c4-146">Dans ce cas, chaque objet SampleDataGroup contient une collection TopItems d'objets SampleDataItem.</span><span class="sxs-lookup"><span data-stu-id="e79c4-146">In this case each SampleDataGroup object contains a TopItems collection of SampleDataItem objects.</span></span>  
  
     <span data-ttu-id="e79c4-147">Pour l'application Netflix, les films sont regroupés par genre.</span><span class="sxs-lookup"><span data-stu-id="e79c4-147">For the Netflix application, movies are grouped by genre.</span></span> <span data-ttu-id="e79c4-148">Ainsi l'application affiche un certain nombre de genres et une liste de films de ce genre.</span><span class="sxs-lookup"><span data-stu-id="e79c4-148">So the application displays a number of genres and a list of movies within that genre.</span></span>  
  
#### <a name="add-a-service-reference-to-the-netflix-odata-service"></a><span data-ttu-id="e79c4-149">Ajouter une référence de service au service OData Netflix</span><span class="sxs-lookup"><span data-stu-id="e79c4-149">Add a Service Reference to the Netflix OData Service</span></span>  
  
1.  <span data-ttu-id="e79c4-150">Avant d'appeler le service OData de Netflix, vous devez ajouter une référence de service.</span><span class="sxs-lookup"><span data-stu-id="e79c4-150">Before we can make any calls to the Netflix OData service we need to add a service reference.</span></span> <span data-ttu-id="e79c4-151">Cliquez avec le bouton droit sur le projet dans l'Explorateur de solutions et sélectionnez Ajouter une référence de service.</span><span class="sxs-lookup"><span data-stu-id="e79c4-151">Right-click the project in the Solution Explorer and select Add Service Reference…</span></span>  
  
     <span data-ttu-id="e79c4-152">![Ajouter la boîte de dialogue de Service référence](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")</span><span class="sxs-lookup"><span data-stu-id="e79c4-152">![Add Service Reference Dialog](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")</span></span>  
  
2.  <span data-ttu-id="e79c4-153">Entrez l'URL du service OData de Netflix dans la barre d'adresse et cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="e79c4-153">Enter the URL for the Netflix OData service in the Address bar and click Go.</span></span> <span data-ttu-id="e79c4-154">Définir l'espace de noms de la référence de service à Netflix et cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="e79c4-154">Set the Namespace of the service reference to Netflix and click OK.</span></span>  
  
     <span data-ttu-id="e79c4-155">![Ajouter l’erreur de référence de Service](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")</span><span class="sxs-lookup"><span data-stu-id="e79c4-155">![Add Service Reference Error](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e79c4-156">Si vous n’avez pas encore installé [WCF données Services Tools pour applications du Windows Store](http://go.microsoft.com/fwlink/p/?LinkId=266652), vous serez invité par un message comme celui illustré ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="e79c4-156">If you have not yet installed [WCF Data Services Tools for Windows Store Apps](http://go.microsoft.com/fwlink/p/?LinkId=266652), you will be prompted with a message such as the one above.</span></span> <span data-ttu-id="e79c4-157">Vous devrez télécharger et installer les outils référencés dans le lien pour continuer.</span><span class="sxs-lookup"><span data-stu-id="e79c4-157">You will need to download and install the tools referenced in the link to continue.</span></span>  
  
 <span data-ttu-id="e79c4-158">L'ajout d'une référence de service génère les classes fortement typées que les services de données WCF utiliseront pour analyser l'OData retourné par le service OData de Netflix.</span><span class="sxs-lookup"><span data-stu-id="e79c4-158">Adding a service reference generates strongly typed classes that WCF Data Services will use to parse the OData returned by the Netflix OData service.</span></span> <span data-ttu-id="e79c4-159">Les classes définies dans SampleDataSource.cs peuvent être liées au GridView ; vous devez donc transférer les données des classes clientes OData générées dans les classes susceptibles d'être liées définies dans SampleDataSource.cs.</span><span class="sxs-lookup"><span data-stu-id="e79c4-159">The classes defined in SampleDataSource.cs can be bound to the GridView so we need to transfer the data from the generated OData client classes into the bindable classes defined in SampleDataSource.cs.</span></span>  <span data-ttu-id="e79c4-160">Pour cela, vous devez apporter certaines modifications au modèle de données défini dans SampleDataSource.cs.</span><span class="sxs-lookup"><span data-stu-id="e79c4-160">In order to do this, we need to make some changes to the data model defined in SampleDataSource.cs.</span></span>  
  
#### <a name="update-the-data-model-for-the-application"></a><span data-ttu-id="e79c4-161">Mettre à jour le modèle de données pour l'application</span><span class="sxs-lookup"><span data-stu-id="e79c4-161">Update the data model for the application</span></span>  
  
1.  <span data-ttu-id="e79c4-162">Remplacez le code existant dans le fichier SampleDataSource.cs par le code à partir de [cette idée](https://gist.github.com/3419288).</span><span class="sxs-lookup"><span data-stu-id="e79c4-162">Replace the existing code in SampleDataSource.cs with the code from [this gist](https://gist.github.com/3419288).</span></span> <span data-ttu-id="e79c4-163">Le code mis à jour ajoute une méthode LoadMovies (à la classe SampleDataSource) qui effectue une requête sur le service OData de Netflix et remplit une liste de genres (allGroups) et dans chaque genre une liste de films.</span><span class="sxs-lookup"><span data-stu-id="e79c4-163">The updated code adds a LoadMovies method (to the SampleDataSource class)  that performs a query against the Netflix OData service and populates a list of genres (allGroups) and within each genre a list of movies.</span></span> <span data-ttu-id="e79c4-164">La classe SampleDataGroup est utilisée pour représenter un genre et la classe SampleDataItem est utilisée pour représenter un film.</span><span class="sxs-lookup"><span data-stu-id="e79c4-164">The SampleDataGroup class is used to represent a genre and the SampleDataItem class is used to represent a movie.</span></span>  
  
    ```csharp  
    public static async void LoadMovies()  
    {  
        IEnumerable<Title> titles = await ((DataServiceQuery<Title>)Context.Titles  
            .Expand("Genres,AudioFormats,AudioFormats/Language,Awards,Cast")  
            .Where(t => t.Rating == "PG")  
            .OrderByDescending(t => t.ReleaseYear)  
            .Take(300)).ExecuteAsync();  
  
        foreach (Title title in titles)  
        {  
            foreach (Genre netflixGenre in title.Genres)  
            {  
                SampleDataGroup genre = GetGroup(netflixGenre.Name);  
                if (genre == null)  
                {  
                    genre = new SampleDataGroup(netflixGenre.Name, netflixGenre.Name, String.Empty, title.BoxArt.LargeUrl, String.Empty);  
                    Instance.AllGroups.Add(genre);  
                }  
                var content = new StringBuilder();  
                // Write additional things to content here if you want them to display in the item detail.  
                genre.Items.Add(new SampleDataItem(title.Id, title.Name, String.Format("{0}rnrn{1} ({2})", title.Synopsis, title.Rating, title.ReleaseYear), title.BoxArt.HighDefinitionUrl ?? title.BoxArt.LargeUrl, "Description", content.ToString()));  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="e79c4-165">Le [modèle asynchrone basé sur des tâches](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) est utilisé pour obtenir de façon asynchrone 300 (Take) récents (OrderByDescending) PG-évalués (Rated Where) de Netflix.</span><span class="sxs-lookup"><span data-stu-id="e79c4-165">The [Task-based Asynchronous Pattern](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) is used to asynchronously get 300 (Take) recent (OrderByDescending) PG-rated (Where) movies back from Netflix.</span></span> <span data-ttu-id="e79c4-166">Le reste du code construit SimpleDataItems et SimpleDataGroups à partir des entités retournées dans le flux OData.</span><span class="sxs-lookup"><span data-stu-id="e79c4-166">The rest of the code constructs SimpleDataItems and SimpleDataGroups from the entities that were returned in the OData feed.</span></span>  
  
     <span data-ttu-id="e79c4-167">La classe SampleDataSource applique également une méthode simple de recherche.</span><span class="sxs-lookup"><span data-stu-id="e79c4-167">The SampleDataSource class also implements a simple search method.</span></span> <span data-ttu-id="e79c4-168">Dans ce cas, elle effectue une recherche simple des films chargés en mémoire.</span><span class="sxs-lookup"><span data-stu-id="e79c4-168">In this case, it does a simple in-memory search of the loaded movies.</span></span>  
  
    ```csharp  
    public static IEnumerable<SampleDataItem> Search(string searchString)  
    {  
            var regex = new Regex(searchString, RegexOptions.CultureInvariant | RegexOptions.IgnoreCase | RegexOptions.IgnorePatternWhitespace);  
            return Instance.AllGroups  
                .SelectMany(g => g.Items)  
                .Where(m => regex.IsMatch(m.Title) || regex.IsMatch(m.Subtitle))  
                    .Distinct(new SampleDataItemComparer());  
    }  
    ```  
  
     <span data-ttu-id="e79c4-169">En outre, dans SampleDataSource.cs, une classe appelée ExtensionMethods est définie.</span><span class="sxs-lookup"><span data-stu-id="e79c4-169">Also in SampleDataSource.cs a class called ExtensionMethods is defined.</span></span> <span data-ttu-id="e79c4-170">Chacune de ces méthodes d'extension utilise le modèle TAP pour permettre au SampleDataSource d'exécuter une requête OData sans se bloquer l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e79c4-170">Each of these extension methods uses the TAP pattern to allow the SampleDataSource to execute an OData query without blocking the UI.</span></span> <span data-ttu-id="e79c4-171">Par exemple, le code suivant utilise la méthode Task.Factory.FromAsync pour implémenter TAP.</span><span class="sxs-lookup"><span data-stu-id="e79c4-171">For example, the following code uses the Task.Factory.FromAsync method to implement TAP.</span></span>  
  
    ```csharp  
    public static async Task<IEnumerable<T>> ExecuteAsync<T>(this DataServiceQuery<T> query)  
    {  
        return await Task.Factory.FromAsync<IEnumerable<T>>(query.BeginExecute(null, null), query.EndExecute);  
    }  
    ```  
  
     <span data-ttu-id="e79c4-172">Comme dans l'application par défaut, la page principale de l'application est GroupedItemsPage.</span><span class="sxs-lookup"><span data-stu-id="e79c4-172">As in the default application, the main page of the application is GroupedItemsPage.</span></span> <span data-ttu-id="e79c4-173">Cette fois, cependant, il affiche les films récupérés auprès de Netflix regroupés par genre.</span><span class="sxs-lookup"><span data-stu-id="e79c4-173">This time, however, it displays the movies retrieved from Netflix grouped by genre.</span></span>  <span data-ttu-id="e79c4-174">Lors de l'instanciation du GroupedItemsPage, sa méthode LoadState est appelée.</span><span class="sxs-lookup"><span data-stu-id="e79c4-174">When the GroupedItemsPage is instantiated, its LoadState method is called.</span></span> <span data-ttu-id="e79c4-175">LoadState entraîne la création de l'instance SampleDataSource statique, en appelant le service OData de Netflix comme décrit précédemment.</span><span class="sxs-lookup"><span data-stu-id="e79c4-175">LoadState causes the static SampleDataSource instance to be created, making a call to the Netflix OData service as discussed previously.</span></span> <span data-ttu-id="e79c4-176">LoadState inscrit la collection de genres (objets SampleDataGroup) dans le DefaultViewModel :</span><span class="sxs-lookup"><span data-stu-id="e79c4-176">LoadState stores the collection of genres (SampleDataGroup objects) in the DefaultViewModel:</span></span>  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     <span data-ttu-id="e79c4-177">Comme décrit précédemment, le DefaultViewModel est ensuite utilisé pour lier les données au GridView.</span><span class="sxs-lookup"><span data-stu-id="e79c4-177">As described previously, the DefaultViewModel is then used to bind the data to the GridView.</span></span>  
  
#### <a name="add-a-search-contract-to-allow-the-application-to-participate-in-windows-search"></a><span data-ttu-id="e79c4-178">Ajouter un contrat de recherche pour permettre à l'application de participer à la recherche Windows</span><span class="sxs-lookup"><span data-stu-id="e79c4-178">Add a search contract to allow the application to participate in Windows search</span></span>  
  
1.  <span data-ttu-id="e79c4-179">Ajoutez un contrat de recherche à l'application.</span><span class="sxs-lookup"><span data-stu-id="e79c4-179">Add a search contract to the application.</span></span> <span data-ttu-id="e79c4-180">Cela permet à l'application de s'intégrer avec l'expérience de recherche Windows 8.</span><span class="sxs-lookup"><span data-stu-id="e79c4-180">This allows the application to integrate with the Windows 8 search experience.</span></span> <span data-ttu-id="e79c4-181">Nommer le contrat de recherche SearchResultsPage.xaml</span><span class="sxs-lookup"><span data-stu-id="e79c4-181">Name the search contract SearchResultsPage.xaml</span></span>  
  
     <span data-ttu-id="e79c4-182">![Ajouter un contrat de recherche](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")</span><span class="sxs-lookup"><span data-stu-id="e79c4-182">![Add a search contract](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")</span></span>  
  
2.  <span data-ttu-id="e79c4-183">Modifier la ligne 58 de SearchResultsPage.xaml.cs en supprimant les guillemets incorporés qui encadrent queryText.</span><span class="sxs-lookup"><span data-stu-id="e79c4-183">Modify line 58 of SearchResultsPage.xaml.cs by removing the embedded quotes around queryText.</span></span>  
  
    ```csharp  
    // Communicate results through the view model  
    this.DefaultViewModel["QueryText"] = queryText;  
    this.DefaultViewModel["Filters"] = filterList;  
    this.DefaultViewModel["ShowFilters"] = filterList.Count > 1;  
    ```  
  
3.  <span data-ttu-id="e79c4-184">Insérez les deux lignes de code suivantes à la ligne 81 dans SearchResultsPage.xaml.cs pour récupérer les résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="e79c4-184">Insert the following two lines of code at line 81 in SearchResultsPage.xaml.cs to retrieve the search results.</span></span>  
  
    ```csharp  
    // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                    //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                    var searchValue = (string)this.DefaultViewModel["QueryText"];  
                    this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
    ```  
  
 <span data-ttu-id="e79c4-185">Lorsqu'un utilisateur appelle la fonction de recherche Windows, entre un terme à rechercher et clique sur l'icône de l'application de démonstration Netflix dans la barre de recherche, la méthode LoadState de SearchResultsPage s'exécute.</span><span class="sxs-lookup"><span data-stu-id="e79c4-185">When a user invokes Windows search, types in a search term and then touches the Netflix Demo app icon in the search bar, the LoadState method of the SearchResultsPage is executed.</span></span> <span data-ttu-id="e79c4-186">Le paramètre de navigation envoyé à LoadState contient le texte de la requête.</span><span class="sxs-lookup"><span data-stu-id="e79c4-186">The navigation parameter sent to LoadState contains the query text.</span></span> <span data-ttu-id="e79c4-187">La méthode Filter_SelectionChanged est appelée, et appelle à son tour la méthode Search sur la classe SampleDataSource.</span><span class="sxs-lookup"><span data-stu-id="e79c4-187">Next the Filter_SelectionChanged method is called which then calls the Search method on the SampleDataSource class.</span></span> <span data-ttu-id="e79c4-188">Les résultats sont retournés et affichés dans la page SearchResultsPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="e79c4-188">The results are returned and displayed in the SearchResultsPage.xaml page.</span></span>  
  
```csharp  
/// <summary>  
        /// Invoked when a filter is selected using the ComboBox in snapped view state.  
        /// </summary>  
        /// <param name="sender">The ComboBox instance.</param>  
        /// <param name="e">Event data describing how the selected filter was changed.</param>  
        void Filter_SelectionChanged(object sender, SelectionChangedEventArgs e)  
        {  
            // Determine what filter was selected  
            var selectedFilter = e.AddedItems.FirstOrDefault() as Filter;  
            if (selectedFilter != null)  
            {  
                // Mirror the results into the corresponding Filter object to allow the  
                // RadioButton representation used when not snapped to reflect the change  
                selectedFilter.Active = true;  
  
                // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                var searchValue = (string)this.DefaultViewModel["QueryText"];  
                this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
  
                // Ensure results are found  
                object results;  
                ICollection resultsCollection;  
                if (this.DefaultViewModel.TryGetValue("Results", out results) &&  
                    (resultsCollection = results as ICollection) != null &&  
                    resultsCollection.Count != 0)  
                {  
                    VisualStateManager.GoToState(this, "ResultsFound", true);  
                    return;  
                }  
            }  
  
            // Display informational text when there are no search results.  
            VisualStateManager.GoToState(this, "NoResultsFound", true);  
        }  
```  
  
 <span data-ttu-id="e79c4-189">Pour plus d’informations sur l’intégration de recherche dans une application, consultez [recherche : intégration dans l’expérience de recherche Windows 8](http://go.microsoft.com/fwlink/p/?LinkId=266650).</span><span class="sxs-lookup"><span data-stu-id="e79c4-189">For more information on integrating search into an application see, [Search: integrating into the Windows 8 search experience](http://go.microsoft.com/fwlink/p/?LinkId=266650).</span></span>  
  
## <a name="run-the-application"></a><span data-ttu-id="e79c4-190">Exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="e79c4-190">Run the application</span></span>  
 <span data-ttu-id="e79c4-191">Lancez l'application en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="e79c4-191">Launch the application by pressing F5.</span></span> <span data-ttu-id="e79c4-192">Notez que quelques secondes sont nécessaires pour charger les images au démarrage de l'application.</span><span class="sxs-lookup"><span data-stu-id="e79c4-192">Note that it will take a few seconds to load the images upon application launch.</span></span> <span data-ttu-id="e79c4-193">Votre première tentative de recherche ne retourne aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="e79c4-193">Also, your first search attempt may not return any results.</span></span> <span data-ttu-id="e79c4-194">Dans une application réelle, vous souhaiteriez traiter ces deux problèmes.</span><span class="sxs-lookup"><span data-stu-id="e79c4-194">In a real-world application, you would want to deal with both of these issues.</span></span>  
  
 <span data-ttu-id="e79c4-195">L'application appelle le service OData de Netflix, reçoit les données dans les classes clientes OData générées, puis transfère les données aux classes de données susceptibles d'être liées (SampleDataSource, SampleDataGroup et SampleDataItem).</span><span class="sxs-lookup"><span data-stu-id="e79c4-195">The application calls the Netflix OData service, receives the data in the generated OData client classes and then transfers that data to bindable data classes (SampleDataSource, SampleDataGroup, and SampleDataItem).</span></span> <span data-ttu-id="e79c4-196">Elle utilise ces classes susceptibles d'être liées pour lier les données dans le GridView.</span><span class="sxs-lookup"><span data-stu-id="e79c4-196">It uses these bindable classes to bind the data to the GridView.</span></span> <span data-ttu-id="e79c4-197">Si vous n’êtes pas familiarisé avec le mode de fonctionnement de la liaison de données XAML, consultez [comment grouper des éléments dans une liste ou grille (applications du Windows Store en C# / VB/C++ et XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).</span><span class="sxs-lookup"><span data-stu-id="e79c4-197">If you are unfamiliar with how XAML databinding works see [How to group items in a list or grid (Windows Store apps using C#/VB/C++ and XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).</span></span>
