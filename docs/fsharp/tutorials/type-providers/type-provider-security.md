---
title: "Sécurité du fournisseur de type"
description: "En savoir plus sur la sécurité du fournisseur de type en F #, notamment comment modifier les paramètres d’approbation pour un fournisseur de type."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9c5a8a1f-5a31-490d-83c0-8beabda75c78
ms.openlocfilehash: c8f03ee90d4dce1d3484a9dfe8951d500d509a2b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="type-provider-security"></a><span data-ttu-id="7d939-104">Sécurité du fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="7d939-104">Type Provider Security</span></span>

<span data-ttu-id="7d939-105">Fournisseurs de type sont des assemblys (DLL) référencés par votre projet F # ou un script qui contiennent du code pour vous connecter aux sources de données externes et d’exposer ces informations de type dans l’environnement de type F #.</span><span class="sxs-lookup"><span data-stu-id="7d939-105">Type providers are assemblies (DLLs) referenced by your F# project or script that contain code to connect to external data sources and surface this type information to the F# type environment.</span></span> <span data-ttu-id="7d939-106">En règle générale, le code dans les assemblys référencés s’exécute seulement lorsque vous compilez et exécutez le code (ou dans le cas d’un script, envoyez le code à F # Interactive).</span><span class="sxs-lookup"><span data-stu-id="7d939-106">Typically, code in referenced assemblies is only run when you compile and then execute the code (or in the case of a script, send the code to F# Interactive).</span></span> <span data-ttu-id="7d939-107">Toutefois, un assembly de fournisseur de type sera exécuté à l’intérieur de Visual Studio lorsque le code est simplement parcouru dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="7d939-107">However, a type provider assembly will run inside Visual Studio when the code is merely browsed in the editor.</span></span> <span data-ttu-id="7d939-108">Cela se produit, car les fournisseurs de type doivent exécuter pour ajouter des informations supplémentaires sur l’éditeur, telles que des info-bulles Info express, aux achèvements IntelliSense et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="7d939-108">This happens because type providers need to run to add extra information to the editor, such as Quick Info tooltips, IntelliSense completions, and so on.</span></span> <span data-ttu-id="7d939-109">Par conséquent, il existe des considérations de sécurité supplémentaires pour le type des assemblys de fournisseur, car ils s’exécuter automatiquement au sein du processus Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d939-109">As a result, there are extra security considerations for type provider assemblies, since they run automatically inside the Visual Studio process.</span></span>


## <a name="security-warning-dialog"></a><span data-ttu-id="7d939-110">Boîte de dialogue sécurité avertissement</span><span class="sxs-lookup"><span data-stu-id="7d939-110">Security Warning Dialog</span></span>
<span data-ttu-id="7d939-111">Lorsque vous utilisez un assembly de fournisseur de type particulier pour la première fois, Visual Studio affiche une boîte de dialogue de sécurité qui vous avertit que le fournisseur de type est prêt à être exécuté.</span><span class="sxs-lookup"><span data-stu-id="7d939-111">When using a particular type provider assembly for the first time, Visual Studio displays a security dialog that warns you that the type provider is about to run.</span></span> <span data-ttu-id="7d939-112">Avant Visual Studio charge le fournisseur de type, il vous donne la possibilité de décider si vous faites confiance à ce fournisseur.</span><span class="sxs-lookup"><span data-stu-id="7d939-112">Before Visual Studio loads the type provider, it gives you the opportunity to decide if you trust this particular provider.</span></span> <span data-ttu-id="7d939-113">Si vous faites confiance à la source du fournisseur de type, puis sélectionnez « Je n’approuver ce fournisseur de type ».</span><span class="sxs-lookup"><span data-stu-id="7d939-113">If you trust the source of the type provider, then select "I trust this type provider."</span></span> <span data-ttu-id="7d939-114">Si vous ne faites pas confiance à la source du fournisseur de type, puis sélectionnez « Je n’autorise pas ce fournisseur de type. »</span><span class="sxs-lookup"><span data-stu-id="7d939-114">If you do not trust the source of the type provider, then select "I do not trust this type provider."</span></span> <span data-ttu-id="7d939-115">Approbation du fournisseur permet à exécuter à l’intérieur de Visual Studio et de fournir IntelliSense et de créer des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="7d939-115">Trusting the provider enables it to run inside Visual Studio and provide IntelliSense and build features.</span></span> <span data-ttu-id="7d939-116">Mais si le fournisseur de type lui-même est malveillant, son code en cours d’exécution susceptibles de compromettre votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7d939-116">But if the type provider itself is malicious, running its code could compromise your machine.</span></span>

<span data-ttu-id="7d939-117">Si votre projet contient du code qui fait référence à des fournisseurs de type que vous avez choisi dans la boîte de dialogue ne pas à approuver, puis au moment de la compilation, le compilateur signale une erreur qui indique que le fournisseur de type n’est pas fiable.</span><span class="sxs-lookup"><span data-stu-id="7d939-117">If your project contains code that references type providers that you chose in the dialog not to trust, then at compile time, the compiler will report an error that indicates that the type provider is untrusted.</span></span> <span data-ttu-id="7d939-118">Tous les types qui en dépendent du fournisseur de type non approuvés sont indiquées par des soulignements ondulés rouges.</span><span class="sxs-lookup"><span data-stu-id="7d939-118">Any types that are dependent on the untrusted type provider are indicated by red squiggles.</span></span> <span data-ttu-id="7d939-119">Il est possible de parcourir le code dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="7d939-119">It is safe to browse the code in the editor.</span></span>

<span data-ttu-id="7d939-120">Si vous décidez de modifier le paramètre de confiance directement dans Visual Studio, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="7d939-120">If you decide to change the trust setting directly in Visual Studio, perform the following steps.</span></span>


#### <a name="to-change-the-trust-settings-for-type-providers"></a><span data-ttu-id="7d939-121">Pour modifier les paramètres d’approbation pour les fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="7d939-121">To change the trust settings for type providers</span></span>

1. <span data-ttu-id="7d939-122">Sur le `Tools` menu, sélectionnez `Options`, puis développez le `F# Tools` nœud.</span><span class="sxs-lookup"><span data-stu-id="7d939-122">On the `Tools` menu, select `Options`, and expand the `F# Tools` node.</span></span>
<br />

2. <span data-ttu-id="7d939-123">Sélectionnez `Type Providers`, dans la liste des fournisseurs de type, sélectionnez la case à cocher pour les fournisseurs de type que vous faites confiance et désactivez la case à cocher pour ceux qui vous ne faites pas confiance.</span><span class="sxs-lookup"><span data-stu-id="7d939-123">Select `Type Providers`, and in the list of type providers, select the check box for type providers you trust, and clear the check box for those you don't trust.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="7d939-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d939-124">See Also</span></span>
[<span data-ttu-id="7d939-125">Fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="7d939-125">Type Providers</span></span>](index.md)
