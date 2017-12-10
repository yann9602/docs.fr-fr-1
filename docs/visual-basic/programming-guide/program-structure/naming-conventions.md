---
title: Conventions d'affectation de noms Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dfdb403519d7e29602fc87445ce32aeb0e55250e
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="f6fb8-102">Conventions d'affectation de noms Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6fb8-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="f6fb8-103">Lorsque vous nommez un élément dans votre application Visual Basic, le premier caractère de ce nom doit être un caractère alphabétique ou un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="f6fb8-104">Toutefois, notez que les noms commençant par un trait de soulignement ne sont pas compatibles avec la [indépendance du langage et composants indépendants du langage](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="f6fb8-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="f6fb8-105">Les suggestions suivantes s’appliquent aux noms.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-105">The following suggestions apply to naming.</span></span>  
  
-   <span data-ttu-id="f6fb8-106">Commencer chaque mot distinct d’un nom par une lettre majuscule, comme dans `FindLastRecord` et `RedrawMyForm`.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
-   <span data-ttu-id="f6fb8-107">Commencer les noms de fonction et de méthode avec un verbe, comme dans `InitNameArray` ou `CloseDialog`.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
-   <span data-ttu-id="f6fb8-108">Commencer la classe, structure, module et noms de propriété avec un nom, comme dans `EmployeeName` ou `CarAccessory`.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
-   <span data-ttu-id="f6fb8-109">Commencer les noms d’interface avec le préfixe « I », suivi par un nom ou une expression nominale, tel que `IComponent`, ou d’un adjectif décrivant le comportement de l’interface, comme `IPersistable`.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="f6fb8-110">Évitez d’utiliser le trait de soulignement et utilisez les abréviations modérément, car les abréviations peuvent entraîner une confusion.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
-   <span data-ttu-id="f6fb8-111">Commencer les noms de gestionnaires d’événements avec un nom qui décrit le type d’événement suivi par la «`EventHandler`« de suffixe, comme dans »`MouseEventHandler`».</span><span class="sxs-lookup"><span data-stu-id="f6fb8-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
-   <span data-ttu-id="f6fb8-112">Dans les noms de classes d’argument d’événement, ajoutez le «`EventArgs`» suffixe.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
-   <span data-ttu-id="f6fb8-113">Si un événement a un concept de « before » ou « after », utilisez un suffixe dans le présent ou le passé, comme dans «`ControlAdd`« ou »`ControlAdded`».</span><span class="sxs-lookup"><span data-stu-id="f6fb8-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
-   <span data-ttu-id="f6fb8-114">Pour les termes longs ou fréquemment utilisés, utilisez des abréviations pour limiter la longueur, par exemple, « HTML », au lieu de « Hypertext Markup Language ».</span><span class="sxs-lookup"><span data-stu-id="f6fb8-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="f6fb8-115">En général, les noms de variables de plus de 32 caractères sont difficiles à lire sur un écran avec une faible résolution.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="f6fb8-116">Assurez-vous également que vos abréviations sont cohérentes dans toute l’application.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="f6fb8-117">Basculement de façon aléatoire dans un projet entre « HTML » et « Hypertext Markup Language » peut prêter à confusion.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
-   <span data-ttu-id="f6fb8-118">Évitez d’utiliser des noms dans une portée interne qui sont les mêmes que les noms dans une portée externe.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="f6fb8-119">Erreurs peuvent résulter si la variable incorrecte est accessible.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="f6fb8-120">En cas de conflit entre une variable et le mot clé portant le même nom, vous devez identifier le mot clé en la faisant précéder de la bibliothèque de types appropriée.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="f6fb8-121">Par exemple, si vous disposez d’une variable appelée `Date`, vous pouvez utiliser la fonction intrinsèque `Date` fonction uniquement en appelant <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f6fb8-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6fb8-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6fb8-122">See Also</span></span>  
 [<span data-ttu-id="f6fb8-123">Utilisation des mots clés comme noms d’éléments dans le code</span><span class="sxs-lookup"><span data-stu-id="f6fb8-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [<span data-ttu-id="f6fb8-124">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="f6fb8-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="f6fb8-125">Noms d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="f6fb8-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="f6fb8-126">Structure de programme et conventions de codage</span><span class="sxs-lookup"><span data-stu-id="f6fb8-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="f6fb8-127">Informations de référence sur le langage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6fb8-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
