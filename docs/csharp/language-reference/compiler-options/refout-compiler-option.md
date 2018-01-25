---
title: -refout (Options du compilateur C#)
ms.date: 08/08/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fbae6f461304c37ba2ef10da16b5d520377bb225
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="6ea9c-102">-refout (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="6ea9c-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="6ea9c-103">L’option **-refout** spécifie un chemin de fichier où l’assembly de référence doit être généré.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="6ea9c-104">Cela se traduit par `metadataPeStream` dans l’API Emit.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-104">This translates to `metadataPeStream` in the Emit API.</span></span>

## <a name="syntax"></a><span data-ttu-id="6ea9c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ea9c-105">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="6ea9c-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="6ea9c-106">Arguments</span></span>

 <span data-ttu-id="6ea9c-107">`filepath` Chemin de l’assembly de référence.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-107">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="6ea9c-108">Il doit généralement correspondre à celui de l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-108">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="6ea9c-109">La convention recommandée (utilisée par MSBuild) consiste à placer l’assembly de référence dans un sous-dossier « ref/ » par rapport à l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-109">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ea9c-110">Notes</span><span class="sxs-lookup"><span data-stu-id="6ea9c-110">Remarks</span></span>

<span data-ttu-id="6ea9c-111">Les assemblys de métadonnées uniquement ont leurs corps de méthode remplacés par un corps `throw null` unique, mais incluent tous les membres à l’exception des types anonymes.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-111">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="6ea9c-112">L’utilisation de corps `throw null` (plutôt qu’aucun corps) permet la bonne exécution de PEVerify (et, par voie de conséquence, la validation de la conformité des métadonnées).</span><span class="sxs-lookup"><span data-stu-id="6ea9c-112">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="6ea9c-113">Les assemblys de référence incluent un attribut `ReferenceAssembly` de niveau assembly.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-113">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="6ea9c-114">Cet attribut peut être spécifié dans la source (le compilateur n’a plus alors besoin de le synthétiser).</span><span class="sxs-lookup"><span data-stu-id="6ea9c-114">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="6ea9c-115">En raison de cet attribut, les runtimes refusent de charger les assemblys de référence pour l’exécution (mais ils peuvent toujours être chargés en mode de réflexion uniquement).</span><span class="sxs-lookup"><span data-stu-id="6ea9c-115">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="6ea9c-116">Les outils reflétés dans les assemblys doivent absolument charger les assemblys de référence en mode réflexion uniquement, sinon ils reçoivent une erreur de chargement de type de la part du runtime.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-116">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="6ea9c-117">En outre, les assemblys de référence suppriment les métadonnées (membres privés) des assemblys de métadonnées uniquement :</span><span class="sxs-lookup"><span data-stu-id="6ea9c-117">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="6ea9c-118">Un assembly de référence a uniquement des références pour ce dont il a besoin dans la surface de l’API.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-118">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="6ea9c-119">L’assembly réel peut avoir des références supplémentaires relatives à des implémentations spécifiques.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-119">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="6ea9c-120">Par exemple, l’assembly de référence pour `class C { private void M() { dynamic d = 1; ... } }` ne référence aucun des types requis pour `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-120">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="6ea9c-121">Les membres de fonction privés (méthodes, propriétés et événements) sont supprimés si leur suppression n’affecte pas la compilation sensiblement.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-121">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="6ea9c-122">S’il n’y a aucun attribut `InternalsVisibleTo`, faites de même pour les membres de fonction internes.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-122">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="6ea9c-123">Toutefois, tous les types (y compris les types privés ou imbriqués) sont conservés dans les assemblys de référence.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-123">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="6ea9c-124">Tous les attributs sont conservés (même les attributs internes).</span><span class="sxs-lookup"><span data-stu-id="6ea9c-124">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="6ea9c-125">Toutes les méthodes virtuelles sont conservées.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-125">All virtual methods are kept.</span></span> <span data-ttu-id="6ea9c-126">Les implémentations d’interface explicite sont conservées.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-126">Explicit interface implementations are kept.</span></span> <span data-ttu-id="6ea9c-127">Les propriétés et les événements implémentés explicitement sont conservés, car leurs accesseurs sont virtuels (et donc conservés).</span><span class="sxs-lookup"><span data-stu-id="6ea9c-127">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="6ea9c-128">Tous les champs d’un struct sont conservés.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-128">All fields of a struct are kept.</span></span> <span data-ttu-id="6ea9c-129">(Candidat pour une optimisation future de C# 7.1)</span><span class="sxs-lookup"><span data-stu-id="6ea9c-129">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="6ea9c-130">Les options `-refout` et [`-refonly`](refonly-compiler-option.md) s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="6ea9c-130">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ea9c-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ea9c-131">See Also</span></span>
 [<span data-ttu-id="6ea9c-132">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="6ea9c-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="6ea9c-133">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="6ea9c-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
