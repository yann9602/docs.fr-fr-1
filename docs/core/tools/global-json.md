---
title: "Informations de référence sur global.json"
description: "Consultez le schéma du fichier global.json, qui permet de définir la version des outils .NET Core."
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
ms.workload: dotnetcore
ms.openlocfilehash: c7e64995ed00a6b2df1b7e1dfa43c6bea5cf4535
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="globaljson-reference"></a><span data-ttu-id="6b183-104">Informations de référence sur global.json</span><span class="sxs-lookup"><span data-stu-id="6b183-104">global.json reference</span></span>

<span data-ttu-id="6b183-105">Le fichier *global.json* permet de sélectionner la version des outils .NET Core utilisée par le biais de la propriété `sdk`.</span><span class="sxs-lookup"><span data-stu-id="6b183-105">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="6b183-106">Les outils CLI .NET Core recherchent ce fichier dans le répertoire de travail actif (qui n’est pas forcément le même que le répertoire du projet) ou dans l’un de ses répertoires parents.</span><span class="sxs-lookup"><span data-stu-id="6b183-106">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="6b183-107">sdk</span><span class="sxs-lookup"><span data-stu-id="6b183-107">sdk</span></span>
<span data-ttu-id="6b183-108">Type : object</span><span class="sxs-lookup"><span data-stu-id="6b183-108">Type: Object</span></span>

<span data-ttu-id="6b183-109">Spécifie des informations sur le SDK.</span><span class="sxs-lookup"><span data-stu-id="6b183-109">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="6b183-110">version</span><span class="sxs-lookup"><span data-stu-id="6b183-110">version</span></span>
<span data-ttu-id="6b183-111">Type : chaîne</span><span class="sxs-lookup"><span data-stu-id="6b183-111">Type: String</span></span>

<span data-ttu-id="6b183-112">Version du SDK à utiliser.</span><span class="sxs-lookup"><span data-stu-id="6b183-112">The version of the SDK to use.</span></span>

<span data-ttu-id="6b183-113">Exemple :</span><span class="sxs-lookup"><span data-stu-id="6b183-113">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```
