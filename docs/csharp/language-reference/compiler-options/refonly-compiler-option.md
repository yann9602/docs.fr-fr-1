---
title: -refonly (Options du compilateur C#)
ms.date: 07/08/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 25b0f6e024e194dff641fd5069755d0ea112a50b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="45dc8-102">-refonly (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="45dc8-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="45dc8-103">L’option **-refonly** indique qu’un assembly de référence doit être généré à la place d’un assembly d’implémentation, en tant que sortie principale.</span><span class="sxs-lookup"><span data-stu-id="45dc8-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="45dc8-104">Le paramètre `-refonly` désactive sans assistance la génération de fichiers PDB, car les assemblys de référence ne peuvent pas être exécutés.</span><span class="sxs-lookup"><span data-stu-id="45dc8-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="45dc8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45dc8-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="45dc8-106">Notes</span><span class="sxs-lookup"><span data-stu-id="45dc8-106">Remarks</span></span>

<span data-ttu-id="45dc8-107">Les assemblys de métadonnées uniquement ont leurs corps de méthode remplacés par un corps `throw null` unique, mais incluent tous les membres à l’exception des types anonymes.</span><span class="sxs-lookup"><span data-stu-id="45dc8-107">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="45dc8-108">L’utilisation de corps `throw null` (plutôt qu’aucun corps) permet la bonne exécution de PEVerify (et, par voie de conséquence, la validation de la conformité des métadonnées).</span><span class="sxs-lookup"><span data-stu-id="45dc8-108">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="45dc8-109">Les assemblys de référence incluent un attribut `ReferenceAssembly` de niveau assembly.</span><span class="sxs-lookup"><span data-stu-id="45dc8-109">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="45dc8-110">Cet attribut peut être spécifié dans la source (le compilateur n’a plus alors besoin de le synthétiser).</span><span class="sxs-lookup"><span data-stu-id="45dc8-110">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="45dc8-111">En raison de cet attribut, les runtimes refusent de charger les assemblys de référence pour l’exécution (mais ils peuvent toujours être chargés en mode de réflexion uniquement).</span><span class="sxs-lookup"><span data-stu-id="45dc8-111">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="45dc8-112">Les outils reflétés dans les assemblys doivent absolument charger les assemblys de référence en mode réflexion uniquement, sinon ils reçoivent une erreur de chargement de type de la part du runtime.</span><span class="sxs-lookup"><span data-stu-id="45dc8-112">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="45dc8-113">En outre, les assemblys de référence suppriment les métadonnées (membres privés) des assemblys de métadonnées uniquement :</span><span class="sxs-lookup"><span data-stu-id="45dc8-113">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="45dc8-114">Un assembly de référence a uniquement des références pour ce dont il a besoin dans la surface de l’API.</span><span class="sxs-lookup"><span data-stu-id="45dc8-114">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="45dc8-115">L’assembly réel peut avoir des références supplémentaires relatives à des implémentations spécifiques.</span><span class="sxs-lookup"><span data-stu-id="45dc8-115">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="45dc8-116">Par exemple, l’assembly de référence pour `class C { private void M() { dynamic d = 1; ... } }` ne référence aucun des types requis pour `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="45dc8-116">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="45dc8-117">Les membres de fonction privés (méthodes, propriétés et événements) sont supprimés si leur suppression n’affecte pas la compilation sensiblement.</span><span class="sxs-lookup"><span data-stu-id="45dc8-117">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="45dc8-118">S’il n’y a aucun attribut `InternalsVisibleTo`, faites de même pour les membres de fonction internes.</span><span class="sxs-lookup"><span data-stu-id="45dc8-118">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="45dc8-119">Toutefois, tous les types (y compris les types privés ou imbriqués) sont conservés dans les assemblys de référence.</span><span class="sxs-lookup"><span data-stu-id="45dc8-119">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="45dc8-120">Tous les attributs sont conservés (même les attributs internes).</span><span class="sxs-lookup"><span data-stu-id="45dc8-120">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="45dc8-121">Toutes les méthodes virtuelles sont conservées.</span><span class="sxs-lookup"><span data-stu-id="45dc8-121">All virtual methods are kept.</span></span> <span data-ttu-id="45dc8-122">Les implémentations d’interface explicite sont conservées.</span><span class="sxs-lookup"><span data-stu-id="45dc8-122">Explicit interface implementations are kept.</span></span> <span data-ttu-id="45dc8-123">Les propriétés et les événements implémentés explicitement sont conservés, car leurs accesseurs sont virtuels (et donc conservés).</span><span class="sxs-lookup"><span data-stu-id="45dc8-123">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="45dc8-124">Tous les champs d’un struct sont conservés.</span><span class="sxs-lookup"><span data-stu-id="45dc8-124">All fields of a struct are kept.</span></span> <span data-ttu-id="45dc8-125">(Candidat pour une optimisation future de C# 7.1)</span><span class="sxs-lookup"><span data-stu-id="45dc8-125">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="45dc8-126">Les options `-refonly` et [`-refout`](refout-compiler-option.md) s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="45dc8-126">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="45dc8-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45dc8-127">See also</span></span>
 [<span data-ttu-id="45dc8-128">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="45dc8-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="45dc8-129">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="45dc8-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
