---
title: Utilisation de Microsoft XML Serializer Generator sur .NET Core
description: "Vue d’ensemble de Microsoft XML Serializer Generator."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2017
ms.topic: tutorial
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 4b838cafe1f4835c1c5aa6086c0997a4a9e39a9e
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2018
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="d1312-103">Utilisation de Microsoft XML Serializer Generator sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="d1312-103">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="d1312-104">Ce didacticiel montre comment utiliser Microsoft XML Serializer Generator dans une application C# .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d1312-104">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="d1312-105">Au cours de ce didacticiel, vous apprenez à :</span><span class="sxs-lookup"><span data-stu-id="d1312-105">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="d1312-106">Créer une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="d1312-106">How to create a .NET Core app</span></span>
> * <span data-ttu-id="d1312-107">Ajouter une référence au package Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="d1312-107">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> * <span data-ttu-id="d1312-108">Modifier votre fichier MyApp.csproj pour ajouter des dépendances</span><span class="sxs-lookup"><span data-stu-id="d1312-108">How to edit your MyApp.csproj to add dependencies</span></span>
> * <span data-ttu-id="d1312-109">Ajouter une classe et un XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="d1312-109">How to add a class and an XmlSerializer</span></span>
> * <span data-ttu-id="d1312-110">Générer et exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="d1312-110">How to build and run the application</span></span> 

<span data-ttu-id="d1312-111">Comme l’outil [XML Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pour le .NET Framework, le [package NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) est l’équivalent pour les projets .NET Core et .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d1312-111">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="d1312-112">Il crée un assembly de sérialisation XML pour les types contenus dans un assembly afin d’améliorer les performances de démarrage de la sérialisation XML pendant la sérialisation ou la désérialisation des objets de ces types avec <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d1312-112">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d1312-113">Prérequis</span><span class="sxs-lookup"><span data-stu-id="d1312-113">Prerequisites</span></span>

<span data-ttu-id="d1312-114">Pour suivre ce didacticiel :</span><span class="sxs-lookup"><span data-stu-id="d1312-114">To complete this tutorial:</span></span>

* <span data-ttu-id="d1312-115">Installez le [SDK .NET Core 2.1.3 ou version ultérieure](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="d1312-115">Install [.NET Core SDK 2.1.3 or later](https://www.microsoft.com/net/download)</span></span>
* <span data-ttu-id="d1312-116">Installez votre éditeur de code favori, si ce n’est pas déjà fait.</span><span class="sxs-lookup"><span data-stu-id="d1312-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="d1312-117">Vous avez besoin d’installer un éditeur de code ?</span><span class="sxs-lookup"><span data-stu-id="d1312-117">Need to install a code editor?</span></span> <span data-ttu-id="d1312-118">Essayez [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) !</span><span class="sxs-lookup"><span data-stu-id="d1312-118">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>
  
## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="d1312-119">Utiliser Microsoft XML Serializer Generator dans une application console .NET Core</span><span class="sxs-lookup"><span data-stu-id="d1312-119">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span> 

<span data-ttu-id="d1312-120">Les instructions suivantes montrent comment utiliser XML Serializer Generator dans une application console .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d1312-120">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="d1312-121">Créer une application console .NET Core</span><span class="sxs-lookup"><span data-stu-id="d1312-121">Create a .NET Core console application</span></span>

<span data-ttu-id="d1312-122">Ouvrez une invite de commandes et créez un dossier nommé *MyApp*.</span><span class="sxs-lookup"><span data-stu-id="d1312-122">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="d1312-123">Accédez au dossier créé et tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="d1312-123">Navigate to the folder you created and type the following command:</span></span>

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="d1312-124">Ajouter une référence au package Microsoft.XmlSerializer.Generator dans le projet MyApp</span><span class="sxs-lookup"><span data-stu-id="d1312-124">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="d1312-125">Utilisez la commande [`dotnet add package`](../tools//dotnet-add-package.md) pour ajouter la référence dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="d1312-125">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span> 

<span data-ttu-id="d1312-126">Tapez :</span><span class="sxs-lookup"><span data-stu-id="d1312-126">Type:</span></span>
 
 ```console
 dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
 ```
 
### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="d1312-127">Vérifier les modifications apportées à MyApp.csproj après l’ajout du package</span><span class="sxs-lookup"><span data-stu-id="d1312-127">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="d1312-128">Ouvrez votre éditeur de code et c’est parti !</span><span class="sxs-lookup"><span data-stu-id="d1312-128">Open your code editor and let's get started!</span></span> <span data-ttu-id="d1312-129">Nous travaillons encore à partir du répertoire *MyApp* dans lequel nous avons créé l’application.</span><span class="sxs-lookup"><span data-stu-id="d1312-129">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="d1312-130">Ouvrez *MyApp.csproj* dans votre éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="d1312-130">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="d1312-131">Après l’exécution de la commande [`dotnet add package`](../tools//dotnet-add-package.md), les lignes suivantes sont ajoutées à votre fichier projet *MyApp.csproj* :</span><span class="sxs-lookup"><span data-stu-id="d1312-131">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="d1312-132">Ajouter une autre section ItemGroup pour la prise en charge de l’outil d’interface CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="d1312-132">Add another ItemGroup section for .NET Core CLI Tool support</span></span>
 
 <span data-ttu-id="d1312-133">Ajoutez les lignes suivantes après la section `ItemGroup` que nous avons inspectée :</span><span class="sxs-lookup"><span data-stu-id="d1312-133">Add the following lines after the `ItemGroup` section that we inspected:</span></span>
 
 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-a-class-in-the-application"></a><span data-ttu-id="d1312-134">Ajouter une classe dans l’application</span><span class="sxs-lookup"><span data-stu-id="d1312-134">Add a class in the application</span></span>

<span data-ttu-id="d1312-135">Ouvrez *Program.cs* dans votre éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="d1312-135">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="d1312-136">Ajoutez la classe nommée *MyClass* dans *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="d1312-136">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="d1312-137">Créer un `XmlSerializer` pour MyClass</span><span class="sxs-lookup"><span data-stu-id="d1312-137">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="d1312-138">Ajoutez la ligne suivante à l’intérieur de *Main* pour créer un `XmlSerializer` pour MyClass :</span><span class="sxs-lookup"><span data-stu-id="d1312-138">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="d1312-139">Générer et exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="d1312-139">Build and run the application</span></span>

<span data-ttu-id="d1312-140">Toujours dans le dossier *MyApp*, exécutez l’application avec [`dotnet run`](../tools/dotnet-run.md). Elle se charge automatiquement et utilise les sérialiseurs prégénérés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d1312-140">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="d1312-141">Tapez la commande suivante dans la fenêtre de console :</span><span class="sxs-lookup"><span data-stu-id="d1312-141">Type the following command in your console window:</span></span>

 ```console
 $ dotnet run
 ```
> [!NOTE]
> <span data-ttu-id="d1312-142">[`dotnet run`](../tools/dotnet-run.md) appelle [`dotnet build`](../tools/dotnet-build.md) pour garantir que les cibles de génération ont été générées, puis appelle `dotnet <assembly.dll>` pour exécuter l’application cible.</span><span class="sxs-lookup"><span data-stu-id="d1312-142">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1312-143">Les commandes et les étapes indiquées dans ce didacticiel pour exécuter votre application sont utilisées uniquement au moment du développement.</span><span class="sxs-lookup"><span data-stu-id="d1312-143">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="d1312-144">Une fois que vous êtes prêt à déployer votre application, consultez les différentes [stratégies de déploiement](../deploying/index.md) pour les applications .NET Core et la commande [`dotnet publish`](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="d1312-144">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="d1312-145">Si tout fonctionne, un assembly nommé *MyApp.XmlSerializers.dll* est généré dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="d1312-145">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span> 



<span data-ttu-id="d1312-146">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="d1312-146">Congratulations!</span></span> <span data-ttu-id="d1312-147">Vous venez de :</span><span class="sxs-lookup"><span data-stu-id="d1312-147">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="d1312-148">Créer une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="d1312-148">Created a .NET Core app.</span></span>
> * <span data-ttu-id="d1312-149">Ajouter une référence au package Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="d1312-149">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> * <span data-ttu-id="d1312-150">Modifier votre fichier MyApp.csproj pour ajouter des dépendances</span><span class="sxs-lookup"><span data-stu-id="d1312-150">Edited your MyApp.csproj to add dependencies.</span></span>
> * <span data-ttu-id="d1312-151">Ajouter une classe et un XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="d1312-151">Added a class and an XmlSerializer.</span></span>
> * <span data-ttu-id="d1312-152">Générer et exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="d1312-152">Built and ran the application.</span></span> 

## <a name="related-resources"></a><span data-ttu-id="d1312-153">Ressources connexes</span><span class="sxs-lookup"><span data-stu-id="d1312-153">Related Resources</span></span>

* [<span data-ttu-id="d1312-154">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="d1312-154">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
* [<span data-ttu-id="d1312-155">Guide pratique pour sérialiser à l’aide de XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="d1312-155">How to: Serialize Using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)
* [<span data-ttu-id="d1312-156">Guide pratique pour sérialiser à l’aide de XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1312-156">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)