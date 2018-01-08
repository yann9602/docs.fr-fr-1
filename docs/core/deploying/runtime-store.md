---
title: Magasin de packages de runtime
description: "Cette rubrique décrit le magasin de packages de runtime et les manifestes cibles utilisés par .NET Core."
keywords: .NET, .NET Core, magasin dotnet, magasin de packages de runtime
author: bleroy
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 9521d8b4-25fc-412b-a65b-4c975ebf6bfd
ms.workload: dotnetcore
ms.openlocfilehash: de1aa4d29abae6bc6c26c0686bafe9bd9cc10ee1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="runtime-package-store"></a><span data-ttu-id="0acd7-104">Magasin de packages de runtime</span><span class="sxs-lookup"><span data-stu-id="0acd7-104">Runtime package store</span></span>

<span data-ttu-id="0acd7-105">À compter de .NET Core 2.0, vous pouvez empaqueter et déployer des applications sur un jeu connu de packages qui existent dans l’environnement cible.</span><span class="sxs-lookup"><span data-stu-id="0acd7-105">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="0acd7-106">Les avantages sont une accélération des déploiements, une utilisation réduite de l’espace disque et une amélioration du niveau de performance du démarrage dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="0acd7-106">The benefits are faster deployments, lower disk space use, and improved startup performance in some cases.</span></span>

<span data-ttu-id="0acd7-107">Cette fonctionnalité est implémentée en tant que *magasin de packages de runtime*, qui est un répertoire sur le disque où sont stockés les packages (généralement */usr/local/share/dotnet/store* sur macOS/Linux et *C:/Program Files/dotnet/store* sur Windows).</span><span class="sxs-lookup"><span data-stu-id="0acd7-107">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="0acd7-108">Ce répertoire contient des sous-répertoires pour les architectures et les [frameworks cibles](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0acd7-108">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="0acd7-109">La disposition de fichier est similaire à la [disposition des composants NuGet sur le disque](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure) :</span><span class="sxs-lookup"><span data-stu-id="0acd7-109">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

<span data-ttu-id="0acd7-110">\dotnet</span><span class="sxs-lookup"><span data-stu-id="0acd7-110">\dotnet</span></span>   
<span data-ttu-id="0acd7-111">&nbsp;&nbsp;\store</span><span class="sxs-lookup"><span data-stu-id="0acd7-111">&nbsp;&nbsp;\store</span></span>   
<span data-ttu-id="0acd7-112">&nbsp;&nbsp;&nbsp;&nbsp;\x64</span><span class="sxs-lookup"><span data-stu-id="0acd7-112">&nbsp;&nbsp;&nbsp;&nbsp;\x64</span></span>   
<span data-ttu-id="0acd7-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="0acd7-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span></span>   
<span data-ttu-id="0acd7-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span><span class="sxs-lookup"><span data-stu-id="0acd7-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span></span>   
<span data-ttu-id="0acd7-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span><span class="sxs-lookup"><span data-stu-id="0acd7-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span></span>   
<span data-ttu-id="0acd7-116">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span><span class="sxs-lookup"><span data-stu-id="0acd7-116">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span></span>   
<span data-ttu-id="0acd7-117">&nbsp;&nbsp;&nbsp;&nbsp;\x86</span><span class="sxs-lookup"><span data-stu-id="0acd7-117">&nbsp;&nbsp;&nbsp;&nbsp;\x86</span></span>   
<span data-ttu-id="0acd7-118">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="0acd7-118">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span></span>   
<span data-ttu-id="0acd7-119">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span><span class="sxs-lookup"><span data-stu-id="0acd7-119">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span></span>   
<span data-ttu-id="0acd7-120">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span><span class="sxs-lookup"><span data-stu-id="0acd7-120">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span></span>   
<span data-ttu-id="0acd7-121">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span><span class="sxs-lookup"><span data-stu-id="0acd7-121">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span></span>   

<span data-ttu-id="0acd7-122">Un fichier *manifeste cible* liste les packages dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="0acd7-122">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="0acd7-123">Les développeurs peuvent cibler ce manifeste quand ils publient leur application.</span><span class="sxs-lookup"><span data-stu-id="0acd7-123">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="0acd7-124">Le manifeste cible est généralement fourni par le propriétaire de l’environnement de production ciblé.</span><span class="sxs-lookup"><span data-stu-id="0acd7-124">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="0acd7-125">Préparation d’un environnement d’exécution</span><span class="sxs-lookup"><span data-stu-id="0acd7-125">Preparing a runtime environment</span></span>

<span data-ttu-id="0acd7-126">L’administrateur d’un environnement d’exécution peut optimiser les applications afin qu’elles se déploient plus rapidement et qu’elles utilisent moins d’espace disque en créant un magasin de packages de runtime et le manifeste cible correspondant.</span><span class="sxs-lookup"><span data-stu-id="0acd7-126">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="0acd7-127">La première étape consiste à créer un *manifeste de magasin de packages* listant les packages qui composent le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="0acd7-127">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="0acd7-128">Ce format de fichier est compatible avec le format de fichier projet (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="0acd7-128">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="0acd7-129">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0acd7-129">**Example**</span></span>

<span data-ttu-id="0acd7-130">L’exemple de manifeste de magasin de packages suivant (*packages.csproj*) est utilisé pour ajouter [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) et [`Moq`](https://www.nuget.org/packages/moq/) à un magasin de packages de runtime :</span><span class="sxs-lookup"><span data-stu-id="0acd7-130">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="0acd7-131">Approvisionner le magasin de packages de runtime en exécutant `dotnet store` avec le manifeste de magasin de packages, le runtime et le framework :</span><span class="sxs-lookup"><span data-stu-id="0acd7-131">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="0acd7-132">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0acd7-132">**Example**</span></span>

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="0acd7-133">Vous pouvez passer plusieurs chemins de manifeste de magasin de packages cible à une seule commande [`dotnet store`](../tools/dotnet-store.md) en répétant l’option et le chemin dans la commande.</span><span class="sxs-lookup"><span data-stu-id="0acd7-133">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="0acd7-134">Par défaut, la sortie de la commande est un magasin de packages sous le sous-répertoire *.dotnet/store* du profil de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0acd7-134">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="0acd7-135">Vous pouvez spécifier un autre emplacement à l’aide de l’option `--output <OUTPUT_DIRECTORY>`.</span><span class="sxs-lookup"><span data-stu-id="0acd7-135">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="0acd7-136">Le répertoire racine du magasin contient un fichier manifeste cible *artifact.xml*.</span><span class="sxs-lookup"><span data-stu-id="0acd7-136">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="0acd7-137">Ce fichier peut être mis à disposition en téléchargement et servir aux auteurs d’application qui souhaitent cibler ce magasin au moment de la publication.</span><span class="sxs-lookup"><span data-stu-id="0acd7-137">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="0acd7-138">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0acd7-138">**Example**</span></span>

<span data-ttu-id="0acd7-139">Le fichier *artifact.xml* suivant est issu de l’exécution de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="0acd7-139">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="0acd7-140">[`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) étant une dépendance de `Moq`, il est inclus automatiquement et apparaît dans le fichier manifeste *artifacts.xml*.</span><span class="sxs-lookup"><span data-stu-id="0acd7-140">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="0acd7-141">Publication d’une application par rapport à un manifeste cible</span><span class="sxs-lookup"><span data-stu-id="0acd7-141">Publishing an app against a target manifest</span></span>

<span data-ttu-id="0acd7-142">Si vous avez un fichier manifeste cible sur le disque, vous spécifiez le chemin du fichier quand vous publiez votre application avec la commande [`dotnet publish`](../tools/dotnet-publish.md) :</span><span class="sxs-lookup"><span data-stu-id="0acd7-142">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="0acd7-143">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="0acd7-143">**Example**</span></span>

```console
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="0acd7-144">Vous déployez l’application publiée résultante sur un environnement qui détient les packages décrits dans le manifeste cible.</span><span class="sxs-lookup"><span data-stu-id="0acd7-144">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="0acd7-145">En cas d’échec, l’application ne parvient pas à démarrer.</span><span class="sxs-lookup"><span data-stu-id="0acd7-145">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="0acd7-146">Spécifiez plusieurs manifestes cible quand vous publiez une application en répétant l’option et le chemin (par exemple, `--manifest manifest1.xml --manifest manifest2.xml`).</span><span class="sxs-lookup"><span data-stu-id="0acd7-146">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="0acd7-147">Ainsi, l’application est épurée pour réunir les packages spécifiés dans les fichiers manifeste cibles fournis à la commande.</span><span class="sxs-lookup"><span data-stu-id="0acd7-147">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="0acd7-148">Spécification de manifestes cibles dans le fichier projet</span><span class="sxs-lookup"><span data-stu-id="0acd7-148">Specifying target manifests in the project file</span></span>

<span data-ttu-id="0acd7-149">Au lieu de spécifier des manifestes cibles avec la commande [`dotnet publish`](../tools/dotnet-publish.md), vous pouvez les spécifier dans le fichier projet sous forme de liste de chemins délimitée par des points-virgules sous une balise **\<TargetManifestFiles>**.</span><span class="sxs-lookup"><span data-stu-id="0acd7-149">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="0acd7-150">Spécifiez les manifestes cibles dans le fichier projet uniquement quand l’environnement cible de l’application est bien connu, à l’image des projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0acd7-150">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="0acd7-151">Ce n’est pas le cas des projets open source.</span><span class="sxs-lookup"><span data-stu-id="0acd7-151">This isn't the case for open-source projects.</span></span> <span data-ttu-id="0acd7-152">En général, les utilisateurs d’un projet open source le déploient sur des environnements de production différents.</span><span class="sxs-lookup"><span data-stu-id="0acd7-152">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="0acd7-153">Ces environnements de production ont généralement différents ensembles de packages préinstallés.</span><span class="sxs-lookup"><span data-stu-id="0acd7-153">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="0acd7-154">Vous ne pouvez pas faire de suppositions quant au manifeste cible dans de tels environnements ; vous devez donc utiliser l’option `--manifest` de [`dotnet publish`](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="0acd7-154">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store"></a><span data-ttu-id="0acd7-155">Magasin ASP.NET Core implicite</span><span class="sxs-lookup"><span data-stu-id="0acd7-155">ASP.NET Core implicit store</span></span>

<span data-ttu-id="0acd7-156">La fonctionnalité de magasin de packages de runtime est implicitement utilisée par une application ASP.NET Core quand celle-ci est déployée en tant qu’application [à déploiement dépendant du framework](index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="0acd7-156">The runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app.</span></span> <span data-ttu-id="0acd7-157">Les cibles dans [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) contiennent les manifestes référençant le magasin de packages implicite sur le système cible.</span><span class="sxs-lookup"><span data-stu-id="0acd7-157">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="0acd7-158">De plus, toute application à déploiement dépendant du framework qui est tributaire du package `Microsoft.AspNetCore.All` aboutit à une application publiée qui contient uniquement l’application et ses composants et non les packages listés dans le métapackage `Microsoft.AspNetCore.All`.</span><span class="sxs-lookup"><span data-stu-id="0acd7-158">Additionally, any FDD app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="0acd7-159">Ces packages sont censés être présents sur le système cible.</span><span class="sxs-lookup"><span data-stu-id="0acd7-159">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="0acd7-160">Le magasin de packages de runtime est installé sur l’hôte quand le SDK .NET Core est installé.</span><span class="sxs-lookup"><span data-stu-id="0acd7-160">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="0acd7-161">D’autres programmes d’installation peuvent fournir le magasin de packages de runtime, notamment les installations Zip/tarball du SDK .NET Core, `apt-get`, Red Hat Yum, le bundle .NET Core Windows Server Hosting et les installations de magasin de packages de runtime manuelles.</span><span class="sxs-lookup"><span data-stu-id="0acd7-161">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="0acd7-162">Quand vous déployez une application [à déploiement dépendant du framework](index.md#framework-dependent-deployments-fdd), vérifiez que le SDK .NET Core est installé sur l’environnement cible.</span><span class="sxs-lookup"><span data-stu-id="0acd7-162">When deploying a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="0acd7-163">Si l’application est déployée sur un environnement qui n’a pas ASP.NET Core, vous pouvez ne pas utiliser le magasin implicite en définissant **\<PublishWithAspNetCoreTargetManifest>** sur `false` dans le fichier projet, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0acd7-163">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE] 
> <span data-ttu-id="0acd7-164">Dans le cas des applications [à déploiement autonome](index.md#self-contained-deployments-scd), le système peut ne pas contenir les packages de manifestes nécessaires.</span><span class="sxs-lookup"><span data-stu-id="0acd7-164">For [self-contained deployment (SCD)](index.md#self-contained-deployments-scd) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="0acd7-165">Par conséquent, **\<PublishWithAspNetCoreTargetManifest>** ne peut pas être défini avec la valeur `true` pour une application à déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="0acd7-165">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an SCD app.</span></span>

<span data-ttu-id="0acd7-166">Si vous déployez une application et que le déploiement comprend une dépendance de manifeste (l’assembly est présent dans le dossier *bin*), le magasin de packages de runtime *n’est pas utilisé* sur l’hôte pour cet assembly.</span><span class="sxs-lookup"><span data-stu-id="0acd7-166">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="0acd7-167">L’assembly dans le dossier *bin* est utilisé indépendamment de sa présence dans le magasin de packages de runtime sur l’hôte.</span><span class="sxs-lookup"><span data-stu-id="0acd7-167">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="0acd7-168">La version de la dépendance indiquée dans le manifeste doit correspondre à la version de la dépendance dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="0acd7-168">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="0acd7-169">Si la dépendance dans le manifeste cible et la version présente dans le magasin de packages de runtime sont incompatibles et que le déploiement de l’application n’inclut pas la version du package requise, l’application ne démarre pas.</span><span class="sxs-lookup"><span data-stu-id="0acd7-169">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="0acd7-170">L’exception contient le nom du manifeste cible qui a appelé l’assembly du magasin de packages de runtime, ce qui vous permet de résoudre l’incompatibilité.</span><span class="sxs-lookup"><span data-stu-id="0acd7-170">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="0acd7-171">Quand le déploiement est *épuré* à la publication, seules les versions spécifiques des packages de manifestes que vous indiquez sont retirées de la sortie publiée.</span><span class="sxs-lookup"><span data-stu-id="0acd7-171">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="0acd7-172">Les packages aux versions indiquées doivent être présents sur l’hôte pour que l’application démarre.</span><span class="sxs-lookup"><span data-stu-id="0acd7-172">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="see-also"></a><span data-ttu-id="0acd7-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0acd7-173">See also</span></span>
 [<span data-ttu-id="0acd7-174">dotnet-publish</span><span class="sxs-lookup"><span data-stu-id="0acd7-174">dotnet-publish</span></span>](../tools/dotnet-publish.md)  
 [<span data-ttu-id="0acd7-175">dotnet-store</span><span class="sxs-lookup"><span data-stu-id="0acd7-175">dotnet-store</span></span>](../tools/dotnet-store.md)  
