---
title: "Révision de l'adaptabilité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7633c7fe9e99bde96ee108460e983eff48f1c7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="localizability-review"></a><span data-ttu-id="798d9-102">Révision de l'adaptabilité</span><span class="sxs-lookup"><span data-stu-id="798d9-102">Localizability Review</span></span>
<span data-ttu-id="798d9-103">La revue de l’adaptabilité est une étape intermédiaire du développement d’une application mondialisable.</span><span class="sxs-lookup"><span data-stu-id="798d9-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="798d9-104">Il vérifie qu'une application globalisée est prête pour la localisation et identifie tout code ou tous les aspects de l'interface utilisateur qui nécessitent une gestion spéciale.</span><span class="sxs-lookup"><span data-stu-id="798d9-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="798d9-105">Cette étape permet également de s'assurer que le processus de localisation n'introduira pas de défauts fonctionnels dans votre application.</span><span class="sxs-lookup"><span data-stu-id="798d9-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="798d9-106">Lorsque tous les problèmes générés par l'examen de l'adaptabilité ont été traités, votre application est prête pour la localisation.</span><span class="sxs-lookup"><span data-stu-id="798d9-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="798d9-107">Si l'examen de l'adaptabilité est complet, vous n'aurez pas à modifier le code source pendant le processus de localisation.</span><span class="sxs-lookup"><span data-stu-id="798d9-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>  
  
 <span data-ttu-id="798d9-108">La revue de l’adaptabilité inclut les trois contrôles suivants :</span><span class="sxs-lookup"><span data-stu-id="798d9-108">The localizability review consists of the following three checks:</span></span>  
  
-   [<span data-ttu-id="798d9-109">Les recommandations de globalisation sont implémentées ?</span><span class="sxs-lookup"><span data-stu-id="798d9-109">Are the globalization recommendations implemented?</span></span>](#global)  
  
-   [<span data-ttu-id="798d9-110">Fonctionnalités dépendantes de la culture sont gérées correctement ?</span><span class="sxs-lookup"><span data-stu-id="798d9-110">Are culture-sensitive features handled correctly?</span></span>](#culture)  
  
-   [<span data-ttu-id="798d9-111">Avez-vous testé votre application avec des données internationales ?</span><span class="sxs-lookup"><span data-stu-id="798d9-111">Have you tested your application with international data?</span></span>](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a><span data-ttu-id="798d9-112">Implémentation des recommandations de globalisation</span><span class="sxs-lookup"><span data-stu-id="798d9-112">Implementing globalization recommendations</span></span>  
 <span data-ttu-id="798d9-113">Si vous avez conçu et développé votre application à l’esprit la localisation, et si vous avez suivi les recommandations décrites dans le [globalisation](../../../docs/standard/globalization-localization/globalization.md) article, l’adaptabilité est essentiellement un test d’assurance qualité .</span><span class="sxs-lookup"><span data-stu-id="798d9-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="798d9-114">Sinon, au cours de cette étape, vous devez examiner et mettre en œuvre des recommandations concernant la [globalisation](../../../docs/standard/globalization-localization/globalization.md)et corriger les erreurs dans le code source qui empêchent la localisation.</span><span class="sxs-lookup"><span data-stu-id="798d9-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md), and fix the errors in source code that prevent localization.</span></span>  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a><span data-ttu-id="798d9-115">Gestion des fonctionnalités dépendantes de la culture</span><span class="sxs-lookup"><span data-stu-id="798d9-115">Handling culture-sensitive features</span></span>  
 <span data-ttu-id="798d9-116">.NET Framework ne fournit pas de prise en charge de programmation dans plusieurs éléments qui varient considérablement par la culture.</span><span class="sxs-lookup"><span data-stu-id="798d9-116">The .NET Framework does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="798d9-117">Dans la plupart des cas, vous devez écrire un code personnalisé pour gérer les zones de fonctionnalités telles que les suivantes :</span><span class="sxs-lookup"><span data-stu-id="798d9-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>  
  
-   <span data-ttu-id="798d9-118">Adresses.</span><span class="sxs-lookup"><span data-stu-id="798d9-118">Addresses.</span></span>  
  
-   <span data-ttu-id="798d9-119">Numéros de téléphone.</span><span class="sxs-lookup"><span data-stu-id="798d9-119">Telephone numbers.</span></span>  
  
-   <span data-ttu-id="798d9-120">Formats de papier.</span><span class="sxs-lookup"><span data-stu-id="798d9-120">Paper sizes.</span></span>  
  
-   <span data-ttu-id="798d9-121">Unités de mesure utilisées pour les longueurs, les poids, les aires, les volumes et les températures.</span><span class="sxs-lookup"><span data-stu-id="798d9-121">Units of measure used for lengths, weights, area, volume, and temperatures.</span></span> <span data-ttu-id="798d9-122">Bien que .NET Framework n'offre pas prise en charge intégrée pour convertir les unités de mesure, vous pouvez utiliser la propriété de <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> pour déterminer si un pays ou une région spécifique utilise le système métrique, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="798d9-122">Although the .NET Framework does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a><span data-ttu-id="798d9-123">Test de votre application</span><span class="sxs-lookup"><span data-stu-id="798d9-123">Testing your application</span></span>  
 <span data-ttu-id="798d9-124">Avant de localiser votre application, vous devriez la tester à l'aide des données internationales dans les versions internationales du système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="798d9-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="798d9-125">Bien que la plupart des interfaces utilisateur ne pourront pas être localisées à ce stade, vous serez en mesure de détecter les problèmes tels que :</span><span class="sxs-lookup"><span data-stu-id="798d9-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>  
  
-   <span data-ttu-id="798d9-126">Les données sérialisées qui ne désérialisent pas correctement sur plusieurs versions du système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="798d9-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>  
  
-   <span data-ttu-id="798d9-127">Les données numériques qui ne reflètent pas les conventions de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="798d9-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="798d9-128">Par exemple, les nombres peuvent s'afficher avec des séparateurs de groupes, des séparateurs décimaux ou des symboles monétaires inexacts.</span><span class="sxs-lookup"><span data-stu-id="798d9-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>  
  
-   <span data-ttu-id="798d9-129">Les données de date et d'heure qui ne reflètent pas les conventions de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="798d9-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="798d9-130">Par exemple, les chiffres qui représentent le mois et le jour peuvent apparaître dans le désordre, les séparateurs de date peuvent être inexacts ou les informations de fuseau horaire peuvent être inexactes.</span><span class="sxs-lookup"><span data-stu-id="798d9-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>  
  
-   <span data-ttu-id="798d9-131">Les ressources introuvables, car vous n'avez pas identifié de culture par défaut pour votre application.</span><span class="sxs-lookup"><span data-stu-id="798d9-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>  
  
-   <span data-ttu-id="798d9-132">Les chaînes affichées dans un ordre inhabituel pour une culture spécifique.</span><span class="sxs-lookup"><span data-stu-id="798d9-132">Strings that are displayed in an unusual order for the specific culture.</span></span>  
  
-   <span data-ttu-id="798d9-133">Les comparaisons de chaînes ou les comparaisons d'égalité qui retournent des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="798d9-133">String comparisons or comparisons for equality that return unexpected results.</span></span>  
  
 <span data-ttu-id="798d9-134">Si vous avez suivi les recommandations de globalisation lors du développement de votre application, les fonctionnalités dépendantes de la culture sont-elles gérées correctement et identifié et résolu les problèmes de localisation est survenue pendant le test, vous pouvez passer à l’étape suivante, [Localisation](../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="798d9-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="798d9-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="798d9-135">See Also</span></span>  
 [<span data-ttu-id="798d9-136">Globalisation et localisation</span><span class="sxs-lookup"><span data-stu-id="798d9-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
 [<span data-ttu-id="798d9-137">Localisation</span><span class="sxs-lookup"><span data-stu-id="798d9-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
 [<span data-ttu-id="798d9-138">Globalisation</span><span class="sxs-lookup"><span data-stu-id="798d9-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 [<span data-ttu-id="798d9-139">Ressources dans des applications de bureau</span><span class="sxs-lookup"><span data-stu-id="798d9-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
