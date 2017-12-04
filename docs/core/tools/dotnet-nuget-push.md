---
title: Commande dotnet nuget push - Interface CLI .NET Core
description: "La commande dotnet nuget push exécute un envoi (push) d’un package sur le serveur et le publie."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: dc4250ab7417c9f19babdf37c556daf7c3bd6a81
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="a6c5f-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="a6c5f-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a6c5f-104">Nom</span><span class="sxs-lookup"><span data-stu-id="a6c5f-104">Name</span></span>

<span data-ttu-id="a6c5f-105">`dotnet nuget push` - Exécute un push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a6c5f-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="a6c5f-106">Synopsis</span></span>

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="a6c5f-107">Description</span><span class="sxs-lookup"><span data-stu-id="a6c5f-107">Description</span></span>

<span data-ttu-id="a6c5f-108">La commande `dotnet nuget push` exécute un push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-108">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="a6c5f-109">La commande push utilise les informations serveur et d’identification trouvées dans le fichier ou la chaîne de fichiers de configuration NuGet du système.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-109">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="a6c5f-110">Pour plus d’informations sur les fichiers de configuration, consultez [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior) (Configuration du comportement de NuGet ).</span><span class="sxs-lookup"><span data-stu-id="a6c5f-110">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="a6c5f-111">La configuration par défaut de NuGet est obtenue en chargeant *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS), puis en chargeant tout fichier *nuget.config* ou *.nuget\nuget.config* à partir de la racine du lecteur jusqu’au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-111">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="a6c5f-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="a6c5f-112">Arguments</span></span>

`ROOT`

<span data-ttu-id="a6c5f-113">Spécifiez le chemin d’accès au package et votre clé API pour effectuer une transmission de type push du package vers le serveur.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-113">Specify the path to the package and your API key to push the package to the server.</span></span>

## <a name="options"></a><span data-ttu-id="a6c5f-114">Options</span><span class="sxs-lookup"><span data-stu-id="a6c5f-114">Options</span></span>

`-h|--help`

<span data-ttu-id="a6c5f-115">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-115">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="a6c5f-116">Spécifie l’URL du serveur.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-116">Specifies the server URL.</span></span> <span data-ttu-id="a6c5f-117">Cette option est obligatoire, sauf si la valeur de configuration de `DefaultPushSource` est définie dans le fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-117">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`--symbol-source <SOURCE>`

<span data-ttu-id="a6c5f-118">Spécifie l’URL du serveur de symboles.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-118">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="a6c5f-119">Spécifie le délai d’attente, en secondes, pour effectuer un push vers un serveur.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-119">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="a6c5f-120">La valeur par défaut est 300 secondes (5 minutes).</span><span class="sxs-lookup"><span data-stu-id="a6c5f-120">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="a6c5f-121">Si vous spécifiez 0 (zéro seconde), la valeur par défaut s’applique.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-121">Specifying 0 (zero seconds) applies the default value.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="a6c5f-122">Clé d’API pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-122">The API key for the server.</span></span>

`--symbol-api-key <API_KEY>`

<span data-ttu-id="a6c5f-123">Clé d’API pour le serveur de symboles.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-123">The API key for the symbol server.</span></span>

`-d|--disable-buffering`

<span data-ttu-id="a6c5f-124">Désactive la mise en mémoire tampon pendant le transfert push vers un serveur HTTP(S) afin de réduire l’utilisation de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-124">Disables buffering when pushing to an HTTP(S) server to decrease memory usage.</span></span>

`-n|--no-symbols`

<span data-ttu-id="a6c5f-125">N’envoie pas les symboles (même s’ils sont présents).</span><span class="sxs-lookup"><span data-stu-id="a6c5f-125">Doesn't push symbols (even if present).</span></span>

`--force-english-output`

<span data-ttu-id="a6c5f-126">Force toutes les sorties enregistrées à être en anglais.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-126">Forces all logged output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="a6c5f-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="a6c5f-127">Examples</span></span>

<span data-ttu-id="a6c5f-128">Effectuer une transmission de type push de *foo.nupkg* vers la source de push par défaut, en fournissant une clé API :</span><span class="sxs-lookup"><span data-stu-id="a6c5f-128">Pushes *foo.nupkg* to the default push source, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="a6c5f-129">Effectuer une transmission de type push de *foo.nupkg* vers la source de push personnalisée `http://customsource`, en fournissant une clé API :</span><span class="sxs-lookup"><span data-stu-id="a6c5f-129">Push *foo.nupkg* to the custom push source `http://customsource`, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="a6c5f-130">Effectuer une transmission de type push de *foo.nupkg* vers la source de push par défaut :</span><span class="sxs-lookup"><span data-stu-id="a6c5f-130">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="a6c5f-131">Effectuer une transmission de type push de *foo.symbols.nupkg* vers la source de symboles par défaut :</span><span class="sxs-lookup"><span data-stu-id="a6c5f-131">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="a6c5f-132">Effectuer une transmission de type push de *foo.nupkg* vers la source de push par défaut, en spécifiant un délai d’attente de 360 secondes :</span><span class="sxs-lookup"><span data-stu-id="a6c5f-132">Pushes *foo.nupkg* to the default push source, specifying a 360 second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="a6c5f-133">Effectuer une transmission de type push de tous les fichiers *.nupkg* du répertoire actif vers la source de push par défaut :</span><span class="sxs-lookup"><span data-stu-id="a6c5f-133">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`

<span data-ttu-id="a6c5f-134">Effectuer une transmission de type push de tous les fichiers *.nupkg* du répertoire actif vers la source de push par défaut, en spécifiant un fichier de configuration personnalisé *./config/My.Config* :</span><span class="sxs-lookup"><span data-stu-id="a6c5f-134">Pushes all *.nupkg* files in the current directory to the default push source, specifying a custom config file *./config/My.Config*:</span></span>

`dotnet nuget push *.nupkg --config-file ./config/My.Config`

<span data-ttu-id="a6c5f-135">Effectuer une transmission de type push de tous les fichiers *.nupkg* du répertoire actif vers la source de push par défaut, avec le maximum de commentaires :</span><span class="sxs-lookup"><span data-stu-id="a6c5f-135">Push all *.nupkg* files in the current directory to the default push source with maximum verbosity:</span></span>

`dotnet nuget push *.nupkg --verbosity detailed`
